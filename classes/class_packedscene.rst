.. Generated automatically by doc/tools/makerst.py in Godot's source tree.
.. DO NOT EDIT THIS FILE, but the PackedScene.xml source instead.
.. The source is found in doc/classes or modules/<name>/doc_classes.

.. _class_PackedScene:

PackedScene
===========

**Inherits:** :ref:`Resource<class_resource>` **<** :ref:`Reference<class_reference>` **<** :ref:`Object<class_object>`

**Category:** Core

Brief Description
-----------------

An abstraction of a serialized scene.

Member Functions
----------------

+----------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
| :ref:`bool<class_bool>`                | :ref:`can_instance<class_PackedScene_can_instance>` **(** **)** const                                                         |
+----------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
| :ref:`SceneState<class_scenestate>`    | :ref:`get_state<class_PackedScene_get_state>` **(** **)**                                                                     |
+----------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Node<class_node>`                | :ref:`instance<class_PackedScene_instance>` **(** :ref:`GenEditState<enum_packedscene_geneditstate>` edit_state=0 **)** const |
+----------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+
| :ref:`Error<enum_@globalscope_error>`  | :ref:`pack<class_PackedScene_pack>` **(** :ref:`Node<class_node>` path **)**                                                  |
+----------------------------------------+-------------------------------------------------------------------------------------------------------------------------------+

Member Variables
----------------

  .. _class_PackedScene__bundled:

- :ref:`Dictionary<class_dictionary>` **_bundled** - A dictionary representation of the scene contents.

Available keys include "rnames" and "variants" for resources, "node_count", "nodes", "node_paths" for nodes, "editable_instances" for base scene children overrides, "conn_count" and "conns" for signal connections, and "version" for the format style of the PackedScene.


Enums
-----

  .. _enum_PackedScene_GenEditState:

enum **GenEditState**

- **GEN_EDIT_STATE_DISABLED** = **0** --- If passed to :ref:`instance<class_PackedScene_instance>`, blocks edits to the scene state.
- **GEN_EDIT_STATE_INSTANCE** = **1** --- If passed to :ref:`instance<class_PackedScene_instance>`, provides local scene resources to the local scene. Requires tools compiled.
- **GEN_EDIT_STATE_MAIN** = **2** --- If passed to :ref:`instance<class_PackedScene_instance>`, provides local scene resources to the local scene. Only the main scene should receive the main edit state. Requires tools compiled.


Description
-----------

A simplified interface to a scene file. Provides access to operations and checks that can be performed on the scene resource itself.

Can be used to save a node to a file. When saving, the node as well as all the node it owns get saved (see ``owner`` property on :ref:`Node<class_node>`). Note that the node doesn't need to own itself.

Example of saving a node:

::

    var scene = PackedScene.new()
    var result = scene.pack(child)
    if result == OK:
        ResourceSaver.save("res://path/name.scn", scene) // or user://...

Member Function Description
---------------------------

.. _class_PackedScene_can_instance:

- :ref:`bool<class_bool>` **can_instance** **(** **)** const

Returns ``true`` if the scene file has nodes.

.. _class_PackedScene_get_state:

- :ref:`SceneState<class_scenestate>` **get_state** **(** **)**

Returns the ``SceneState`` representing the scene file contents.

.. _class_PackedScene_instance:

- :ref:`Node<class_node>` **instance** **(** :ref:`GenEditState<enum_packedscene_geneditstate>` edit_state=0 **)** const

Instantiates the scene's node hierarchy. Triggers child scene instantiation(s). Triggers the :ref:`NOTIFICATION_INSTANCED<enum_object_notification_instanced>` notification on the root node.

.. _class_PackedScene_pack:

- :ref:`Error<enum_@globalscope_error>` **pack** **(** :ref:`Node<class_node>` path **)**

Pack will ignore any sub-nodes not owned by given node. See :ref:`Node.set_owner<class_Node_set_owner>`.


