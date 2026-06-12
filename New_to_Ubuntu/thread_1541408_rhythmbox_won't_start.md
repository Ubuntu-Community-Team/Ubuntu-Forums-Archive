---
title: "rhythmbox won't start"
date: 2010-07-29
forum: New to Ubuntu
---

### Post by Gunnlaugur on 2010-07-29
Hi.

I'm having problem starting rhythmbox when I have my iPod video 80GB connected to my laptop. I've tried to uninstall rhythmbox and install again but with no luck. I've also googled this and tried out some of the results and also with no luck.

I ran rhythmbox -d in commandline and here is the output.
> 
(08:58:37) [0x9549028] [rb_debug_init_match] rb-debug.c:213: Debugging enabled
(08:58:37) [0x9549028] [main] main.c:177: initializing Rhythmbox 0.12.8
(08:58:37) [0x9549028] [rb_threads_init] rb-util.c:482: GMutex isn't recursive
(08:58:37) [0x9549028] [main] main.c:185: going to create DBus object
(08:58:37) [0x9549028] [main] main.c:267: Going to create a new shell
(08:58:37) [0x9549028] [rb_shell_constructed] rb-shell.c:1488: Constructing shell
(08:58:37) [0x9549028] [construct_db] rb-shell.c:1136: creating database object
(08:58:37) [0x9549028] [rb_find_user_file] rb-file-helpers.c:224: found user dir path for 'rhythmdb.xml': /home/gunnl/.local/share/rhythmbox/rhythmdb.xml
(08:58:37) [0x9549028] [construct_widgets] rb-shell.c:1203: shell: initializing shell services
(08:58:37) [0x9549028] [gconf_network_buffer_size_changed] rb-shell-player.c:3834: network buffer size changed
(08:58:37) [0x9549028] [rb_header_sync] rb-header.c:487: syncing with entry = <null>
(08:58:37) [0x9549028] [rb_header_sync] rb-header.c:549: not playing
(08:58:37) [0x9549028] [rb_shell_player_set_playing_source_internal] rb-shell-player.c:3104: setting playing source to (nil)
(08:58:37) [0x9549028] [rb_shell_player_sync_with_source] rb-shell-player.c:2928: playing source: (nil), active entry: (nil)
(08:58:37) [0x9549028] [rb_shell_player_sync_control_state] rb-shell-player.c:2443: syncing control state
(08:58:37) [0x9549028] [rb_shell_player_repeat_changed_cb] rb-shell-player.c:2654: repeat changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x95f6a88 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x95f6af8 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x95f6a88
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x95f6a88
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x969bab0 ()
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x969ba30 (Track)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x978f000 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x978f100 (Genre)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x978f200 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x978f300 (Album)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x978f400 (Year)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x969be30 (Time)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x978f680 (Quality)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9790a28 (Rating)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9790928 (Play Count)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x978f500 (Location)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x978f700 (Last Played)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97908a8 (Date Added)
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x95f6b68 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x95f6b68 chaining to base model 0x95f6af8
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0858 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9796190 (Play Queue)
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x97a0858
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x97a0858
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x9778820 to group library
(08:58:37) [0x9549028] [rb_shell_constructed] rb-shell.c:1508: shell: adding gconf notification
(08:58:37) [0x9549028] [rb_shell_constructed] rb-shell.c:1541: shell: syncing with gconf
(08:58:37) [0x9549028] [rb_source_set_property] rb-source.c:626: Setting Play Queue visibility to 1
(08:58:37) [0x9549028] [visibility_notify_cb] rb-sourcelist.c:1017: Source visibility changed: Play Queue
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0938 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97ae100 (Track)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97ae300 (Title)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97ae400 (Genre)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97ae500 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97ae200 (Album)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97ae600 (Year)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b2960 (Time)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b2be0 (Quality)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b2860 (Play Count)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b2a60 (Location)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_browser_source_state_prefs_sync] rb-browser-source.c:759: syncing state
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a09a8 chaining to base model (nil)
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x97a0938
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x97a0938
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0a18 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b2c60 (Rating)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [songs_view_sort_order_changed_cb] rb-browser-source.c:623: sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b2ce0 (Last Played)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [songs_view_sort_order_changed_cb] rb-browser-source.c:623: sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b2f60 (Date Added)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [songs_view_sort_order_changed_cb] rb-browser-source.c:623: sort order changed
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x9774df8 to group library
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0af8 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b5aa8 (Date)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b2de0 (Title)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b5828 (Feed)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b5b28 (Time)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b5da8 (Rating)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b5ea8 (Play Count)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97bd0b0 (Last Played)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97b5ba8 (Status)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0b68 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 1
(08:58:37) [0x9549028] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x9549028] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x9549028] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x9549028] [idle_process_update] rhythmdb-query-model.c:1186: inserting 0 rows
(08:58:37) [0x9549028] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9549028] [rb_podcast_source_state_prefs_sync] rb-podcast-source.c:989: syncing state
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0c60 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x97a0af8
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x97a0af8
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 2
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x97b7068 to group library
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0cd0 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0db0 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x97a0db0
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x97a0db0
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97bd530 (Track)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97bd730 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97bd5b0 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97c6098 (Album)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97c6198 (Location)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97c6298 (Last Seen)
(08:58:37) [0x9549028] [rb_source_set_property] rb-source.c:626: Setting Missing Files visibility to 0
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x97bf010 to group library
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0e20 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x97a0db0 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x97a0db0
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x97a0db0
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97c6598 (Location)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97c6318 (Error)
(08:58:37) [0x9549028] [rb_source_set_property] rb-source.c:626: Setting Import Errors visibility to 0
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x97bf438 to group library
(08:58:37) [0x9549028] [rb_find_user_file] rb-file-helpers.c:224: found user dir path for 'playlists.xml': /home/gunnl/.local/share/rhythmbox/playlists.xml
(08:58:37) [0x9549028] [construct_sources] rb-shell.c:1375: shell: creating playlist manager
(08:58:37) [0x9549028] [construct_sources] rb-shell.c:1387: shell: creating removable media manager
(08:58:37) [0x9549028] [construct_load_ui] rb-shell.c:1409: shell: loading ui
(08:58:37) [0x97c17a0] [query_thread_main] rhythmdb.c:4149: entering query thread
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x97c17a0] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x97c17a0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9549028] [rb_shell_select_source] rb-shell.c:2126: selecting source 0x9774df8
(08:58:37) [0x9549028] [rb_shell_clipboard_set_source_internal] rb-shell-clipboard.c:354: selected source 0x9774df8
(08:58:37) [0x9549028] [rb_shell_clipboard_sync] rb-shell-clipboard.c:600: syncing clipboard
(08:58:37) [0x9549028] [rebuild_playlist_menu] rb-shell-clipboard.c:1034: rebuilding add-to-playlist menu
(08:58:37) [0x9549028] [rb_shell_player_set_source_internal] rb-shell-player.c:1098: selected source 0x9774df8
(08:58:37) [0x9549028] [rb_shell_player_sync_with_selected_source] rb-shell-player.c:3377: syncing with selected source: 0x9774df8
(08:58:37) [0x9549028] [rb_shell_player_sync_with_selected_source] rb-shell-player.c:3380: no playing source, new source is 0x9774df8
(08:58:37) [0x9549028] [rb_shell_player_sync_with_source] rb-shell-player.c:2928: playing source: (nil), active entry: (nil)
(08:58:37) [0x9549028] [rb_shell_set_window_title] rb-shell.c:2178: clearing title
(08:58:37) [0x9549028] [rb_shell_player_sync_buttons] rb-shell-player.c:3023: syncing with source 0x9774df8
(08:58:37) [0x9549028] [rb_source_header_set_source_internal] rb-source-header.c:501: selected source 0x9774df8
(08:58:37) [0x9549028] [rb_source_header_view_browser_changed_cb] rb-source-header.c:836: got view browser toggle
(08:58:37) [0x9549028] [rb_source_header_view_browser_changed_cb] rb-source-header.c:849: got view browser toggle
(08:58:37) [0x9549028] [rb_statusbar_set_property] rb-statusbar.c:325: selected source 0x9774df8
(08:58:37) [0x9549028] [rb_statusbar_sync_status] rb-statusbar.c:444: updating status with: '0 songs', '', -1.000000
(08:58:37) [0x9549028] [_uri_handle_recurse] rb-file-helpers.c:768: error enumerating file:///home/gunnl/.gnome2/rhythmbox/plugins: No such file or directory
(08:58:37) [0x9549028] [_uri_handle_recurse] rb-file-helpers.c:768: error enumerating file:///home/gunnl/.local/share/rhythmbox/plugins: No such file or directory
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/cd-recorder/cd-recorder.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/cd-recorder/cd-recorder.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Audio CD Recorder loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x99dbd20 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/cd-recorder/libcd-recorder.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-disc-recorder-plugin.c:106: Registering plugin RBDiscRecorderPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBDiscRecorderPlugin
(08:58:37) [0x9549028] [rb_disc_recorder_plugin_init] rb-disc-recorder-plugin.c:144: RBDiscRecorderPlugin initialized
(08:58:37) [0x9549028] [impl_activate] rb-disc-recorder-plugin.c:685: RBDiscRecorderPlugin activating
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/artdisplay/artdisplay.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/artdisplay/artdisplay.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Cover art loaded
(08:58:37) [0x9549028] [rb_python_module_init] rb-python-module.c:440: Init of python module
(08:58:37) [0x9549028] [rb_python_object_get_type] rb-python-plugin.c:274: Registering python plugin instance: ArtDisplayPlugin+RBPythonPlugin
(08:58:37) [0x9549028] [rb_python_module_new_object] rb-python-module.c:413: Creating object of type ArtDisplayPlugin+RBPythonPlugin
(08:58:37) [0x9549028] [rb_python_object_init] rb-python-plugin.c:204: Creating python plugin instance
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/artdisplay/rhythmbox-missing-artwork.svg' when searching for file 'rhythmbox-missing-artwork.svg' for plugin 'artdisplay'
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/audiocd/audiocd.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/audiocd/audiocd.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Audio CD Player loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x96f5a00 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/audiocd/libaudiocd.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-audiocd-plugin.c:87: Registering plugin RBAudioCdPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBAudioCdPlugin
(08:58:37) [0x9549028] [rb_audiocd_plugin_init] rb-audiocd-plugin.c:106: RBAudioCdPlugin initialising
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/audioscrobbler/audioscrobbler.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Last.fm loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x99dbd50 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/audioscrobbler/libaudioscrobbler.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-audioscrobbler-plugin.c:82: Registering plugin RBAudioscrobblerPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBAudioscrobblerPlugin
(08:58:37) [0x9549028] [rb_audioscrobbler_plugin_init] rb-audioscrobbler-plugin.c:100: RBAudioscrobblerPlugin initialising
(08:58:37) [0x9549028] [rb_audioscrobbler_init] rb-audioscrobbler.c:260: Initialising Audioscrobbler
(08:58:37) [0x9549028] [rb_audioscrobbler_init] rb-audioscrobbler.c:262: Plugin ID: rbx, Version 0.12.8 (Protocol 1.2)
(08:58:37) [0x9549028] [rb_find_user_file] rb-file-helpers.c:224: found user dir path for 'audioscrobbler.queue': /home/gunnl/.local/share/rhythmbox/audioscrobbler.queue
(08:58:37) [0x9549028] [rb_audioscrobbler_load_queue] rb-audioscrobbler.c:1219: loading Audioscrobbler queue from "/home/gunnl/.local/share/rhythmbox/audioscrobbler.queue"
(08:58:37) [0x9549028] [rb_audioscrobbler_add_timeout] rb-audioscrobbler.c:429: Adding Audioscrobbler timer (15 seconds)
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/audioscrobbler/audioscrobbler-ui.xml' when searching for file 'audioscrobbler-ui.xml' for plugin 'audioscrobbler'
(08:58:37) [0x9549028] [rhythmdb_tree_entry_type_registered] rhythmdb-tree.c:2691: no entries of newly registered type lastfm-station loaded from db
(08:58:37) [0x9549028] [rhythmdb_tree_entry_type_registered] rhythmdb-tree.c:2691: no entries of newly registered type lastfm-track loaded from db
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9811348 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97f9760 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97f9660 (Rating)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97f94e0 (Last Played)
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x981a4c0 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x97f9560 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0xb2618208 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0xb2618308 (Album)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0xb2618408 (Time)
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x981a530 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 3
(08:58:37) [0x9549028] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x9549028] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x9549028] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x9549028] [idle_process_update] rhythmdb-query-model.c:1186: inserting 0 rows
(08:58:37) [0x9549028] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x9811348
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x9811348
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x981a5a0 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x981a4c0
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x981a4c0
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/audioscrobbler/as-icon.png' when searching for file 'as-icon.png' for plugin 'audioscrobbler'
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x9685320 to group library
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/context/context.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/context/context.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Context Pane loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/daap/daap.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/daap/daap.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin DAAP Music Sharing loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x9c6f6f0 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/daap/libdaap.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-daap-plugin.c:121: Registering plugin RBDaapPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBDaapPlugin
(08:58:37) [0x9549028] [rb_daap_plugin_init] rb-daap-plugin.c:164: RBDaapPlugin initialising
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/daap/daap-ui.xml' when searching for file 'daap-ui.xml' for plugin 'daap'
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/fmradio/fmradio.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/fmradio/fmradio.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin FM Radio loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/generic-player/generic-player.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/generic-player/generic-player.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Portable Players loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x99dbec0 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/generic-player/libgeneric-player.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-generic-player-plugin.c:92: Registering plugin RBGenericPlayerPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBGenericPlayerPlugin
(08:58:37) [0x9549028] [rb_generic_player_plugin_init] rb-generic-player-plugin.c:126: RBGenericPlayerPlugin initialising
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/im-status/im-status.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/im-status/im-status.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin IM Status loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/ipod/ipod.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/ipod/ipod.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Portable Players - iPod loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x99dbcf0 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/ipod/libipod.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-ipod-plugin.c:98: Registering plugin RBIpodPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBIpodPlugin
(08:58:37) [0x9549028] [rb_ipod_plugin_init] rb-ipod-plugin.c:140: RBIpodPlugin initialising
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/ipod/ipod-ui.xml' when searching for file 'ipod-ui.xml' for plugin 'ipod'
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/iradio/iradio.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/iradio/iradio.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Internet Radio loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x96f5b50 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/iradio/libiradio.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-iradio-plugin.c:76: Registering plugin RBIRadioPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBIRadioPlugin
(08:58:37) [0x9549028] [rb_iradio_plugin_init] rb-iradio-plugin.c:81: RBIRadioPlugin initialising
(08:58:37) [0x9549028] [rhythmdb_tree_entry_type_registered] rhythmdb-tree.c:2691: no entries of newly registered type iradio loaded from db
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x981a680 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0xb2618588 (Title)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0xb2618488 (Genre)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d5d0b8 (Rating)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d5d1b8 (Last Played)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Title:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_iradio_source_state_prefs_sync] rb-iradio-source.c:675: syncing state
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x981a6f0 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 4
(08:58:37) [0x9549028] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x9549028] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x9549028] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x9549028] [idle_process_update] rhythmdb-query-model.c:1186: inserting 0 rows
(08:58:37) [0x9549028] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x981a680
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x981a680
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0xb261d018 to group library
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/iradio/iradio-ui.xml' when searching for file 'iradio-ui.xml' for plugin 'iradio'
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/jamendo/jamendo.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/jamendo/jamendo.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Jamendo loaded
(08:58:37) [0x9549028] [rb_python_module_init] rb-python-module.c:440: Init of python module
(08:58:37) [0x9549028] [rb_python_object_get_type] rb-python-plugin.c:274: Registering python plugin instance: Jamendo+RBPythonPlugin
(08:58:37) [0x9549028] [rb_python_module_new_object] rb-python-module.c:413: Creating object of type Jamendo+RBPythonPlugin
(08:58:37) [0x9549028] [rb_python_object_init] rb-python-plugin.c:204: Creating python plugin instance
(08:58:37) [0x9549028] [rhythmdb_tree_entry_type_registered] rhythmdb-tree.c:2691: no entries of newly registered type JamendoEntryType loaded from db
(08:58:37) [0x9549028] [rb_find_user_file] rb-file-helpers.c:224: found user dir path for 'jamendo': /home/gunnl/.cache/rhythmbox/jamendo
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x981a858 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d90ad8 (Track)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d90bd8 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d90cd8 (Genre)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d90dd8 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d90ed8 (Album)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d96018 (Year)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d96298 (Time)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d96118 (Quality)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d96318 (Play Count)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d96598 (Location)
(08:58:37) [0x9549028] [rb_browser_source_state_prefs_sync] rb-browser-source.c:759: syncing state
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x981a8c8 chaining to base model (nil)
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x981a858
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x981a858
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x981a858 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 5
(08:58:37) [0x97c17a0] [query_thread_main] rhythmdb.c:4149: entering query thread
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x97c17a0] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x97c17a0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x9d8f838 to group stores
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/lyrics/lyrics.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/lyrics/lyrics.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Song Lyrics loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/magnatune/magnatune.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/magnatune/magnatune.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Magnatune Store loaded
(08:58:37) [0x9549028] [rb_python_module_init] rb-python-module.c:440: Init of python module
(08:58:37) [0x9549028] [rb_python_object_get_type] rb-python-plugin.c:274: Registering python plugin instance: Magnatune+RBPythonPlugin
(08:58:37) [0x9549028] [rb_python_module_new_object] rb-python-module.c:413: Creating object of type Magnatune+RBPythonPlugin
(08:58:37) [0x9549028] [rb_python_object_init] rb-python-plugin.c:204: Creating python plugin instance
(08:58:37) [0x9549028] [rhythmdb_tree_entry_type_registered] rhythmdb-tree.c:2691: no entries of newly registered type MagnatuneEntryType loaded from db
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9d9ff00 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d98bd8 (Track)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d98dd8 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d98ed8 (Genre)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d98cd8 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e04030 (Album)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e04130 (Year)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e043b0 (Time)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e04530 (Quality)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e04230 (Play Count)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e04430 (Location)
(08:58:37) [0x9549028] [rb_browser_source_state_prefs_sync] rb-browser-source.c:759: syncing state
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9d9ff70 chaining to base model (nil)
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x9d9ff00
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x9d9ff00
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e02048 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 6
(08:58:37) [0x97c17a0] [query_thread_main] rhythmdb.c:4149: entering query thread
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x97c17a0] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x97c17a0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1111: inserting source 0x9d8f910 to group stores
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/mmkeys/mmkeys.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/mmkeys/mmkeys.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Media Player Keys loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x96f8780 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/mmkeys/libmmkeys.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-mmkeys-plugin.c:86: Registering plugin RBMMKeysPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBMMKeysPlugin
(08:58:37) [0x9549028] [rb_mmkeys_plugin_init] rb-mmkeys-plugin.c:93: RBMMKeysPlugin initialising
(08:58:37) [0x9549028] [impl_activate] rb-mmkeys-plugin.c:310: activating media player keys plugin
(08:58:37) [0x9549028] [impl_activate] rb-mmkeys-plugin.c:363: created dbus proxy for org.gnome.SettingsDaemon.MediaKeys; grabbing keys
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/mtpdevice/mtpdevice.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/mtpdevice/mtpdevice.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Portable Players - MTP loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x971aa60 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/mtpdevice/libmtpdevice.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-mtp-plugin.c:119: Registering plugin RBMtpPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBMtpPlugin
(08:58:37) [0x9549028] [rb_mtp_plugin_init] rb-mtp-plugin.c:156: RBMtpPlugin initialising
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/mtpdevice/mtp-ui.xml' when searching for file 'mtp-ui.xml' for plugin 'mtpdevice'
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/power-manager/power-manager.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/power-manager/power-manager.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Power Manager loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/python-console/pythonconsole.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/python-console/pythonconsole.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Python Console loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/rblirc/lirc.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/rblirc/lirc.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin LIRC  loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/replaygain/replaygain.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/replaygain/replaygain.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin ReplayGain loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/sendto/sendto.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/sendto/sendto.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:238: Could not find 'Website' in /usr/lib/rhythmbox/plugins/sendto/sendto.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Send tracks loaded
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/status-icon/status-icon.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/status-icon/status-icon.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Status Icon loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x96dd630 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/status-icon/libstatus-icon.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-status-icon-plugin.c:139: Registering plugin RBStatusIconPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBStatusIconPlugin
(08:58:37) [0x9549028] [rb_status_icon_plugin_init] rb-status-icon-plugin.c:1520: RBStatusIconPlugin initialising
(08:58:37) [0x9549028] [impl_activate] rb-status-icon-plugin.c:1328: activating status icon plugin
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/status-icon/status-icon-ui.xml' when searching for file 'status-icon-ui.xml' for plugin 'status-icon'
(08:58:37) [0x9549028] [rb_shell_player_get_playing_song_duration] rb-shell-player.c:3363: Did not get playing entry : return -1 as length
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:116: Loading plugin: /usr/lib/rhythmbox/plugins/visualizer/visualizer.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load] rb-plugins-engine.c:206: Could not find 'Icon' in /usr/lib/rhythmbox/plugins/visualizer/visualizer.rb-plugin
(08:58:37) [0x9549028] [rb_plugins_engine_load_cb] rb-plugins-engine.c:299: Plugin Visualization loaded
(08:58:37) [0x9549028] [rb_module_init] rb-module.c:140: RBModule 0x9706fb0 initialising
(08:58:37) [0x9549028] [rb_module_load] rb-module.c:72: Loading /usr/lib/rhythmbox/plugins/visualizer/libvisualizer.so
(08:58:37) [0x9549028] [register_rb_plugin] rb-visualizer-plugin.c:249: Registering plugin RBVisualizerPlugin
(08:58:37) [0x9549028] [rb_module_new_object] rb-module.c:125: Creating object of type RBVisualizerPlugin
(08:58:37) [0x9549028] [rb_visualizer_plugin_init] rb-visualizer-plugin.c:275: RBVisualizerPlugin initialising
(08:58:37) [0x9549028] [impl_activate] rb-visualizer-plugin.c:1638: using playbin-based visualization
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/visualizer/visualizer-ui.xml' when searching for file 'visualizer-ui.xml' for plugin 'visualizer'
(08:58:37) [0x9549028] [rb_plugin_find_file] rb-plugin.c:329: found '/usr/lib/rhythmbox/plugins/visualizer/visualizer-controls.ui' when searching for file 'visualizer-controls.ui' for plugin 'visualizer'
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1937: building vis plugin list
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: libvisual oinksie plugin plugin v.0.1 (libvisual_oinksie)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: libvisual libvisual scope plugin v.0.1 (libvisual_lv_scope)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: libvisual libvisual analyzer plugin v.1.0 (libvisual_lv_analyzer)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: libvisual jess plugin plugin v.0.1 (libvisual_jess)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: libvisual Jakdaw plugin plugin v.0.0.1 (libvisual_jakdaw)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: libvisual infinite plugin plugin v.0.1 (libvisual_infinite)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: libvisual libvisual corona plugin plugin v.0.1 (libvisual_corona)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: libvisual Bumpscope plugin plugin v.0.0.1 (libvisual_bumpscope)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: Monoscope (monoscope)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: GOOM: what a GOOM! 2k1 edition (goom2k1)
(08:58:37) [0x9549028] [get_vis_plugin_list] rb-visualizer-plugin.c:1950: adding visualizer element: GOOM: what a GOOM! (goom)
(08:58:37) [0x9549028] [populate_combo_boxes] rb-visualizer-plugin.c:2089: populating screen selection combo box with 1 screens
(08:58:37) [0x9549028] [populate_combo_boxes] rb-visualizer-plugin.c:2110: populating screen selection combo box with 2 monitors from screen 0
(08:58:37) [0x9549028] [populate_combo_boxes] rb-visualizer-plugin.c:2117: appending <0,0> to store
(08:58:37) [0x9549028] [populate_combo_boxes] rb-visualizer-plugin.c:2117: appending <0,1> to store
(08:58:37) [0x9549028] [populate_combo_boxes] rb-visualizer-plugin.c:2126: current output is on 0.0, id 0
(08:58:37) [0x9549028] [screen_list_cell_data] rb-visualizer-plugin.c:2000: displaying 0.0 (0xbf947740)
(08:58:37) [0x9549028] [screen_list_cell_data] rb-visualizer-plugin.c:2000: displaying 0.1 (0xbf947740)
(08:58:37) [0x9549028] [can_draw_on_desktop] rb-visualizer-plugin.c:370: screen is composited: probably can't draw on desktop
(08:58:37) [0x9549028] [show_controls] rb-visualizer-plugin.c:869: showing controls
(08:58:37) [0x9549028] [rb_shell_constructed] rb-shell.c:1568: loading database
(08:58:37) [0x9549028] [rb_shell_constructed] rb-shell.c:1571: shell: syncing window state
(08:58:37) [0x9549028] [visibility_changing_cb] rb-status-icon-plugin.c:1080: setting initial visibility 0 from gconf
(08:58:37) [0x9549028] [rb_shell_set_visibility] rb-shell.c:1688: hiding main window
(08:58:37) [0x9549028] [shell_selected_source_notify_cb] rb-disc-recorder-plugin.c:655: RBDiscRecorderPlugin selected source changed
(rhythmbox:2733): Rhythmbox-DEBUG: Received SaveYourself(SmSaveLocal, !Shutdown, SmInteractStyleNone, !Fast) in state idle
(rhythmbox:2733): Rhythmbox-DEBUG: Setting initial properties
(rhythmbox:2733): Rhythmbox-DEBUG: Sending SaveYourselfDone(True) for initial SaveYourself
(rhythmbox:2733): Rhythmbox-DEBUG: Received SaveComplete message in state save-yourself-done
(08:58:37) [0x9549028] [rb_browser_source_state_pref_changed] rb-browser-source.c:749: state prefs changed
(08:58:37) [0x9549028] [rb_browser_source_state_prefs_sync] rb-browser-source.c:759: syncing state
(08:58:37) [0x9549028] [rb_statusbar_sync_status] rb-statusbar.c:444: updating status with: '0 songs', '', -1.000000
(08:58:37) [0x9549028] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:807: entryview changed
(08:58:37) [0x9549028] [rb_shell_clipboard_entryview_changed_cb] rb-shell-clipboard.c:807: entryview changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e1f738 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e29c60 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x9e1f738
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x9e1f738
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e2b108 ()
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e2b008 (Track)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e2b308 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e2b408 (Genre)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e2b508 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e2b608 (Album)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e2b708 (Year)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d40898 (Time)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d40998 (Quality)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d40c98 (Rating)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d40d98 (Play Count)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d40e98 (Location)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d40b98 (Last Played)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9d40a98 (Date Added)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_playlist_source_songs_sort_order_changed_cb] rb-playlist-source.c:1127: sort order changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e29cd0 chaining to base model (nil)
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x9e29c60
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x9e29c60
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 7
(08:58:37) [0x97c17a0] [query_thread_main] rhythmdb.c:4149: entering query thread
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x97c17a0] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x97c17a0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9e2e2a8] [rhythmdb_tree_parser_start_element] rhythmdb-tree.c:379: loading database version 1.6 (160)
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1098: inserting source 0x9e1e2d0 with parent 0x9774df8
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e29db0 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e29e20 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x9e29db0
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x9e29db0
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c46660 ()
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c4c0b8 (Track)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c4c2b8 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c4c3b8 (Genre)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c4c1b8 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c46760 (Album)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c4c4b8 (Year)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c4c738 (Time)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e30210 (Quality)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c4c638 (Rating)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9c4c538 (Play Count)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e30110 (Location)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e30310 (Last Played)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e30590 (Date Added)
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1153: Updating EntryView sort order to Track:0
(08:58:37) [0x9549028] [rb_entry_view_sync_sorting] rb-entry-view.c:1164: emitting sort order changed
(08:58:37) [0x9549028] [rb_playlist_source_songs_sort_order_changed_cb] rb-playlist-source.c:1127: sort order changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e29e90 chaining to base model (nil)
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x9e29e20
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x9e29e20
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 8
(08:58:37) [0x97c17a0] [query_thread_main] rhythmdb.c:4149: entering query thread
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x97c17a0] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x97c17a0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9549028] [rb_sourcelist_append] rb-sourcelist.c:1098: inserting source 0x9e1e3c0 with parent 0x9774df8
(08:58:37) [0x9549028] [idle_process_update] rhythmdb-query-model.c:1186: inserting 0 rows
(08:58:37) [0x9549028] [idle_process_update] rhythmdb-query-model.c:1186: inserting 0 rows
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [idle_process_update] rhythmdb-query-model.c:1186: inserting 0 rows
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [dump_volume_identifiers] rb-removable-media-manager.c:664: uuid = D6D7-74C4
(08:58:37) [0x9549028] [dump_volume_identifiers] rb-removable-media-manager.c:664: unix-device = /dev/sdb2
(08:58:37) [0x9549028] [dump_volume_identifiers] rb-removable-media-manager.c:664: label = GUNNLAUGUR'
(08:58:37) [0x9549028] [rb_removable_media_manager_add_volume] rb-removable-media-manager.c:709: Unhandled media
(08:58:37) [0x9549028] [dump_volume_identifiers] rb-removable-media-manager.c:664: uuid = D6D7-74C4
(08:58:37) [0x9549028] [dump_volume_identifiers] rb-removable-media-manager.c:664: unix-device = /dev/sdb2
(08:58:37) [0x9549028] [dump_volume_identifiers] rb-removable-media-manager.c:664: label = GUNNLAUGUR'
found device path /dev/sdb2 for mount /media/GUNNLAUGUR'
found ID_MEDIA_PLAYER tag apple-1261_1262 for device /dev/sdb2
device information (system database)
information read from system device database
model: iPod
vendor: Apple
filesystem uuid: D6D7-74C4
drive type: (none)
requires eject: false
access protocols:
    storage
    ipod
output formats:
    audio/mpeg
    audio/aac
    audio/x-wav
    audio/x-aiff
    video/mp4
input formats: (none)
playlist formats: (none)
playlist path: (none)
audio folders: (none)
folder depth: -1
/media/GUNNLAUGUR' is already a mount point
override file /media/GUNNLAUGUR'/.is_audio_player not found on mount /media/GUNNLAUGUR'
(08:58:37) [0x9549028] [rhythmdb_tree_entry_type_registered] rhythmdb-tree.c:2691: no entries of newly registered type ipod: /dev/sdb2 loaded from db
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e29db0 chaining to base model (nil)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e421d8 (Track)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e423d8 (Title)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e424d8 (Genre)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e425d8 (Artist)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e42258 (Album)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e426d8 (Year)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e469d0 (Time)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e46c50 (Quality)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e42758 (Play Count)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e46ad0 (Location)
(08:58:37) [0x9549028] [rb_browser_source_state_prefs_sync] rb-browser-source.c:759: syncing state
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e29c60 chaining to base model (nil)
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 0 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 1 - reusing parent model
(08:58:37) [0x9549028] [rebuild_child_model] rb-library-browser.c:692: no selection for browser 2 - reusing parent model
(08:58:37) [0x9549028] [rhythmdb_query_model_dispose] rhythmdb-query-model.c:730: disposing query model 0x9e29db0
(08:58:37) [0x9549028] [rhythmdb_query_model_finalize] rhythmdb-query-model.c:778: finalizing query model 0x9e29db0
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rb_property_view_selection_changed_cb] rb-property-view.c:834: selection changed
(08:58:37) [0x9549028] [rhythmdb_query_model_chain] rhythmdb-query-model.c:896: query model 0x9e1f738 chaining to base model (nil)
(08:58:37) [0x9549028] [rhythmdb_read_enter] rhythmdb.c:1253: counter: 9
(08:58:37) [0x97c17a0] [query_thread_main] rhythmdb.c:4149: entering query thread
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4126: doing query
(08:58:37) [0x97c17a0] [do_query_recurse] rhythmdb-tree.c:2252: doing recursive query, 1 conjunctions
(08:58:37) [0x97c17a0] [rhythmdb_query_model_add_results] rhythmdb-query-model.c:2247: adding 0 entries
(08:58:37) [0x97c17a0] [rhythmdb_query_internal] rhythmdb.c:4132: completed
(08:58:37) [0x9549028] [rb_removable_media_source_constructed] rb-removable-media-source.c:187: details from mount: display name = GUNNLAUGUR', icon = 0x959bc78
(08:58:37) [0x9549028] [rb_removable_media_source_constructed] rb-removable-media-source.c:215: looking up themed icon: multimedia-player-apple-ipod
(08:58:37) [0x9549028] [rb_removable_media_source_constructed] rb-removable-media-source.c:215: looking up themed icon: multimedia-player-apple
(08:58:37) [0x9549028] [rb_removable_media_source_constructed] rb-removable-media-source.c:215: looking up themed icon: multimedia-player
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e468d0 (Rating)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e46d50 (Last Played)
(08:58:37) [0x9549028] [rb_entry_view_insert_column_custom] rb-entry-view.c:1755: appending column: 0x9e4b850 (Date Added)
Bus error
Any help would be greatly appreciated

Thanks
Gunnlaugur

---

### Post by evstevemd on 2010-07-29
have you tried to re-install?
what went wrong and how?
do  sudo apt-get remove rhythmbox && sudo apt-get install rhythmbox

I have both RB and Banshee. To me Banshee is far superior as far as I have tried it.
Give it a shot sudo apt-get install banshee

---

### Post by Gunnlaugur on 2010-07-29
Before I posted my initial post I removed it using Synaptic Package Manager and then re-installed it again. But no luck. It starts if my ipod is not connected and I can play what ever file located on my laptop.

Then I followed your advice and used apt-get and still the same problem.
I also started rhythmbox and then connect my ipod, but then I get the following error from rhythmbox. 
> 
DBus error org.gtk.Private.RemoteVolumeMonitor.NotFound: The given volume was not found
If I open up Disk Utility I can see my ipod there marked as Apple iPod. But when I look in there Mount Point reads Not Mounted. If I try to mount it from there I get the flollowing error.

Error:
> 
An error occurred while performing an operation on "iPod" (Partition 1 of Apple iPod): Filesystem driver not installed
Details:
> 
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


---

### Post by Gunnlaugur on 2010-08-03
I still havent been able to fix this issue. 
Any chance someone can come with more ideas for me to try out in my tempt to fix this.

---

