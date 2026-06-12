---
title: "Pidgin-Latex Installation"
date: 2009-08-28
forum: New to Ubuntu
---

### Post by Matuku on 2009-08-28
I'm trying to install pidgin-latex but when I run the "make" command the following output occurs:

```

user@user-desktop ~/Source Install/pidgin-latex $ make
Package pidgin was not found in the pkg-config search path.
Perhaps you should add the directory containing `pidgin.pc'
to the PKG_CONFIG_PATH environment variable
No package 'pidgin' found
Package gtk+-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gtk+-2.0.pc'
to the PKG_CONFIG_PATH environment variable
No package 'gtk+-2.0' found
gcc  -fPIC -c LaTeX.c -o LaTeX.o   -DHAVE_CONFIG_H
In file included from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/account.h:30:18: error: glib.h: No such file or directory
/usr/include/libpurple/account.h:31:25: error: glib-object.h: No such file or directory
In file included from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/account.h:38: error: expected declaration specifiers or ‘...’ before ‘*’ token
/usr/include/libpurple/account.h:38: error: ‘gboolean’ declared as function returning a function
In file included from /usr/include/libpurple/connection.h:147,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/plugin.h:32:24: error: glib/glist.h: No such file or directory
/usr/include/libpurple/plugin.h:33:21: error: gmodule.h: No such file or directory
In file included from /usr/include/libpurple/signals.h:30,
                 from /usr/include/libpurple/plugin.h:34,
                 from /usr/include/libpurple/connection.h:147,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/value.h:97: error: field ‘boolean_data’ declared as a function
/usr/include/libpurple/value.h:104: error: expected specifier-qualifier-list before ‘gint64’
/usr/include/libpurple/value.h:225: error: ‘purple_value_is_outgoing’ declared as function returning a function
/usr/include/libpurple/value.h:305: error: expected declaration specifiers or ‘...’ before ‘gint64’
/usr/include/libpurple/value.h:313: error: expected declaration specifiers or ‘...’ before ‘guint64’
/usr/include/libpurple/value.h:380: error: ‘purple_value_get_boolean’ declared as function returning a function
/usr/include/libpurple/value.h:443: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_value_get_int64’
/usr/include/libpurple/value.h:452: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_value_get_uint64’
In file included from /usr/include/libpurple/plugin.h:34,
                 from /usr/include/libpurple/connection.h:147,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/signals.h:35: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:82: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_signal_register’
/usr/include/libpurple/signals.h:134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_signal_connect_priority’
/usr/include/libpurple/signals.h:154: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_signal_connect’
/usr/include/libpurple/signals.h:180: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_signal_connect_priority_vargs’
/usr/include/libpurple/signals.h:203: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_signal_connect_vargs’
/usr/include/libpurple/signals.h:247: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:275: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:295: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:297: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:299: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:301: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:303: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:305: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:307: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:309: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:311: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:313: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:315: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:317: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:319: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:321: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:323: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:325: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:328: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:330: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:332: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:334: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:337: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:339: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:341: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:343: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:345: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:347: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:349: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:351: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:354: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:357: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:359: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:361: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:363: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/signals.h:365: error: expected declaration specifiers or ‘...’ before ‘va_list’
In file included from /usr/include/libpurple/pluginpref.h:51,
                 from /usr/include/libpurple/plugin.h:51,
                 from /usr/include/libpurple/connection.h:147,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/prefs.h:63: error: expected declaration specifiers or ‘...’ before ‘gconstpointer’
/usr/include/libpurple/prefs.h:63: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/prefs.h:133: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/prefs.h:152: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/prefs.h:189: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/prefs.h:221: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/prefs.h:237: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/prefs.h:246: error: ‘purple_prefs_exists’ declared as function returning a function
/usr/include/libpurple/prefs.h:262: error: ‘purple_prefs_get_bool’ declared as function returning a function
/usr/include/libpurple/prefs.h:286: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/prefs.h:302: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/prefs.h:314: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/prefs.h:319: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_prefs_connect_callback’
/usr/include/libpurple/prefs.h:325: error: expected ‘)’ before ‘callback_id’
/usr/include/libpurple/prefs.h:340: error: ‘purple_prefs_load’ declared as function returning a function
In file included from /usr/include/libpurple/plugin.h:51,
                 from /usr/include/libpurple/connection.h:147,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/pluginpref.h:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/pluginpref.h:204: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/pluginpref.h:212: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/pluginpref.h:244: error: ‘purple_plugin_pref_get_masked’ declared as function returning a function
In file included from /usr/include/libpurple/connection.h:147,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/plugin.h:86: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/plugin.h:121: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/plugin.h:139: error: field ‘native_plugin’ declared as a function
/usr/include/libpurple/plugin.h:140: error: field ‘loaded’ declared as a function
/usr/include/libpurple/plugin.h:147: error: field ‘unloadable’ declared as a function
/usr/include/libpurple/plugin.h:148: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/plugin.h:190: error: expected specifier-qualifier-list before ‘gpointer’
/usr/include/libpurple/plugin.h:273: error: ‘purple_plugin_register’ declared as function returning a function
/usr/include/libpurple/plugin.h:285: error: ‘purple_plugin_load’ declared as function returning a function
/usr/include/libpurple/plugin.h:297: error: ‘purple_plugin_unload’ declared as function returning a function
/usr/include/libpurple/plugin.h:321: error: ‘purple_plugin_reload’ declared as function returning a function
/usr/include/libpurple/plugin.h:337: error: ‘purple_plugin_is_loaded’ declared as function returning a function
/usr/include/libpurple/plugin.h:351: error: ‘purple_plugin_is_unloadable’ declared as function returning a function
/usr/include/libpurple/plugin.h:360: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:369: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:378: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:387: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:396: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:405: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:414: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:440: error: ‘purple_plugin_ipc_register’ declared as function returning a function
/usr/include/libpurple/plugin.h:470: error: ‘purple_plugin_ipc_get_params’ declared as function returning a function
/usr/include/libpurple/plugin.h:539: error: ‘purple_plugins_enabled’ declared as function returning a function
/usr/include/libpurple/plugin.h:648: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:658: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/plugin.h:665: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/libpurple/buddyicon.h:38,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/imgstore.h:63: error: expected ‘)’ before ‘data’
/usr/include/libpurple/imgstore.h:96: error: expected ‘)’ before ‘data’
/usr/include/libpurple/imgstore.h:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_imgstore_get_data’
In file included from /usr/include/libpurple/prpl.h:66,
                 from /usr/include/libpurple/buddyicon.h:39,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/ft.h:91: error: expected specifier-qualifier-list before ‘guint’
/usr/include/libpurple/ft.h:174: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/ft.h:266: error: ‘purple_xfer_is_canceled’ declared as function returning a function
/usr/include/libpurple/ft.h:275: error: ‘purple_xfer_is_completed’ declared as function returning a function
/usr/include/libpurple/ft.h:451: error: expected declaration specifiers or ‘...’ before ‘gssize’
/usr/include/libpurple/ft.h:460: error: expected declaration specifiers or ‘...’ before ‘gssize’
/usr/include/libpurple/ft.h:469: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/ft.h:531: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_xfer_read’
/usr/include/libpurple/ft.h:542: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_xfer_write’
In file included from /usr/include/libpurple/prpl.h:68,
                 from /usr/include/libpurple/buddyicon.h:39,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/notify.h:42: error: expected ‘)’ before ‘user_data’
/usr/include/libpurple/notify.h:93: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/notify.h:126: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/notify.h:127: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/notify.h:163: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/notify.h:213: error: expected declaration specifiers or ‘...’ before ‘PurpleNotifyCloseCallback’
/usr/include/libpurple/notify.h:214: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/notify.h:293: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/notify.h:312: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_notify_searchresults_get_rows_count’
/usr/include/libpurple/notify.h:333: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_notify_searchresults_get_columns_count’
/usr/include/libpurple/notify.h:355: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/notify.h:403: error: expected declaration specifiers or ‘...’ before ‘PurpleNotifyCloseCallback’
/usr/include/libpurple/notify.h:404: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/notify.h:422: error: expected declaration specifiers or ‘...’ before ‘PurpleNotifyCloseCallback’
/usr/include/libpurple/notify.h:423: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/notify.h:445: error: expected declaration specifiers or ‘...’ before ‘PurpleNotifyCloseCallback’
/usr/include/libpurple/notify.h:445: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/notify.h:466: error: expected declaration specifiers or ‘...’ before ‘PurpleNotifyCloseCallback’
/usr/include/libpurple/notify.h:466: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/notify.h:484: error: expected declaration specifiers or ‘...’ before ‘PurpleNotifyCloseCallback’
/usr/include/libpurple/notify.h:485: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/notify.h:519: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/notify.h:638: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/notify.h:655: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/libpurple/proxy.h:30,
                 from /usr/include/libpurple/prpl.h:69,
                 from /usr/include/libpurple/buddyicon.h:39,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/eventloop.h:50: error: expected ‘)’ before ‘PurpleInputCondition’
/usr/include/libpurple/eventloop.h:85: error: expected specifier-qualifier-list before ‘guint’
/usr/include/libpurple/eventloop.h:178: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_timeout_add’
/usr/include/libpurple/eventloop.h:198: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_timeout_add_seconds’
/usr/include/libpurple/eventloop.h:207: error: expected ‘)’ before ‘handle’
/usr/include/libpurple/eventloop.h:220: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_input_add’
/usr/include/libpurple/eventloop.h:229: error: expected ‘)’ before ‘handle’
In file included from /usr/include/libpurple/prpl.h:69,
                 from /usr/include/libpurple/buddyicon.h:39,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/proxy.h:62: error: expected ‘)’ before ‘data’
/usr/include/libpurple/proxy.h:249: error: expected declaration specifiers or ‘...’ before ‘PurpleProxyConnectFunction’
/usr/include/libpurple/proxy.h:249: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/proxy.h:275: error: expected declaration specifiers or ‘...’ before ‘PurpleProxyConnectFunction’
/usr/include/libpurple/proxy.h:275: error: expected declaration specifiers or ‘...’ before ‘gpointer’
In file included from /usr/include/libpurple/prpl.h:71,
                 from /usr/include/libpurple/buddyicon.h:39,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/roomlist.h:71: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/roomlist.h:84: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/libpurple/roomlist.h:95: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/libpurple/roomlist.h:106: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/roomlist.h:174: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/roomlist.h:196: error: ‘purple_roomlist_get_in_progress’ declared as function returning a function
/usr/include/libpurple/roomlist.h:248: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/roomlist.h:266: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/roomlist.h:276: error: expected declaration specifiers or ‘...’ before ‘gconstpointer’
/usr/include/libpurple/roomlist.h:317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/roomlist.h:338: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/roomlist.h:368: error: ‘purple_roomlist_field_get_hidden’ declared as function returning a function
In file included from /usr/include/libpurple/prpl.h:73,
                 from /usr/include/libpurple/buddyicon.h:39,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/whiteboard.h:50: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/whiteboard.h:86: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/whiteboard.h:159: error: expected ‘)’ before ‘*’ token
/usr/include/libpurple/whiteboard.h:170: error: ‘purple_whiteboard_get_dimensions’ declared as function returning a function
/usr/include/libpurple/whiteboard.h:198: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/whiteboard.h:245: error: ‘purple_whiteboard_get_brush’ declared as function returning a function
In file included from /usr/include/libpurple/buddyicon.h:39,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/prpl.h:96: error: field ‘required’ declared as a function
/usr/include/libpurple/prpl.h:97: error: field ‘is_int’ declared as a function
/usr/include/libpurple/prpl.h:100: error: field ‘secret’ declared as a function
/usr/include/libpurple/prpl.h:115: error: expected specifier-qualifier-list before ‘gpointer’
/usr/include/libpurple/prpl.h:207: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/prpl.h:704: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/prpl.h:718: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/libpurple/prpl.h:728: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/libpurple/prpl.h:739: error: expected declaration specifiers or ‘...’ before ‘guint’
In file included from /usr/include/libpurple/util.h:35,
                 from /usr/include/libpurple/buddyicon.h:40,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/xmlnode.h:59: error: expected specifier-qualifier-list before ‘GHashTable’
/usr/include/libpurple/xmlnode.h:127: error: expected declaration specifiers or ‘...’ before ‘gssize’
/usr/include/libpurple/xmlnode.h:282: error: expected declaration specifiers or ‘...’ before ‘gssize’
In file included from /usr/include/libpurple/buddyicon.h:40,
                 from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/util.h:48: error: expected specifier-qualifier-list before ‘gpointer’
/usr/include/libpurple/util.h:62: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/libpurple/util.h:79: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/util.h:79: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/util.h:111: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/util.h:150: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:167: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:181: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:202: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:219: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:240: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:431: error: expected declaration specifiers or ‘...’ before ‘GData’
/usr/include/libpurple/util.h:431: error: ‘purple_markup_find_tag’ declared as function returning a function
/usr/include/libpurple/util.h:462: error: ‘purple_markup_extract_info_field’ declared as function returning a function
/usr/include/libpurple/util.h:529: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/libpurple/util.h:529: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/libpurple/util.h:576: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/util.h:594: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:640: error: expected declaration specifiers or ‘...’ before ‘gssize’
/usr/include/libpurple/util.h:640: error: ‘purple_util_write_data_to_file’ declared as function returning a function
/usr/include/libpurple/util.h:660: error: expected declaration specifiers or ‘...’ before ‘gssize’
/usr/include/libpurple/util.h:660: error: ‘purple_util_write_data_to_file_absolute’ declared as function returning a function
/usr/include/libpurple/util.h:706: error: expected ‘)’ before ‘data’
/usr/include/libpurple/util.h:711: error: expected ‘)’ before ‘image_data’
/usr/include/libpurple/util.h:720: error: expected ‘)’ before ‘image_data’
/usr/include/libpurple/util.h:737: error: ‘purple_program_is_valid’ declared as function returning a function
/usr/include/libpurple/util.h:744: error: ‘purple_running_gnome’ declared as function returning a function
/usr/include/libpurple/util.h:751: error: ‘purple_running_kde’ declared as function returning a function
/usr/include/libpurple/util.h:758: error: ‘purple_running_osx’ declared as function returning a function
/usr/include/libpurple/util.h:819: error: ‘purple_str_has_prefix’ declared as function returning a function
/usr/include/libpurple/util.h:830: error: ‘purple_str_has_suffix’ declared as function returning a function
/usr/include/libpurple/util.h:840: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:889: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:931: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:963: error: expected ‘)’ before ‘sec’
/usr/include/libpurple/util.h:978: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/libpurple/util.h:1002: error: ‘purple_url_parse’ declared as function returning a function
/usr/include/libpurple/util.h:1019: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/util.h:1019: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/util.h:1068: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/util.h:1090: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/util.h:1132: error: ‘purple_email_is_valid’ declared as function returning a function
/usr/include/libpurple/util.h:1141: error: ‘purple_ip_address_is_valid’ declared as function returning a function
/usr/include/libpurple/util.h:1152: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:1166: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:1184: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:1195: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/util.h:1207: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘gchar’
/usr/include/libpurple/util.h:1234: error: ‘purple_utf8_has_word’ declared as function returning a function
/usr/include/libpurple/util.h:1255: error: expected declaration specifiers or ‘...’ before ‘gssize’
/usr/include/libpurple/util.h:1255: error: ‘purple_message_meify’ declared as function returning a function
/usr/include/libpurple/util.h:1319: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/libpurple/blist.h:85,
                 from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/buddyicon.h:107: error: expected declaration specifiers or ‘...’ before ‘guchar’
/usr/include/libpurple/buddyicon.h:148: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_buddy_icon_get_data’
/usr/include/libpurple/buddyicon.h:259: error: expected declaration specifiers or ‘...’ before ‘guchar’
/usr/include/libpurple/buddyicon.h:283: error: ‘purple_buddy_icons_node_has_custom_icon’ declared as function returning a function
/usr/include/libpurple/buddyicon.h:320: error: expected declaration specifiers or ‘...’ before ‘guchar’
/usr/include/libpurple/buddyicon.h:338: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/buddyicon.h:349: error: ‘purple_buddy_icons_has_custom_icon’ declared as function returning a function
/usr/include/libpurple/buddyicon.h:370: error: expected declaration specifiers or ‘...’ before ‘guchar’
/usr/include/libpurple/buddyicon.h:389: error: ‘purple_buddy_icons_is_caching’ declared as function returning a function
In file included from /usr/include/libpurple/status.h:117,
                 from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/blist.h:104: error: expected specifier-qualifier-list before ‘GHashTable’
/usr/include/libpurple/blist.h:133: error: field ‘priority_valid’ declared as a function
/usr/include/libpurple/blist.h:155: error: expected specifier-qualifier-list before ‘GHashTable’
/usr/include/libpurple/blist.h:167: error: expected specifier-qualifier-list before ‘GHashTable’
/usr/include/libpurple/blist.h:407: error: expected declaration specifiers or ‘...’ before ‘GHashTable’
/usr/include/libpurple/blist.h:592: error: ‘purple_contact_on_account’ declared as function returning a function
/usr/include/libpurple/blist.h:718: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/blist.h:766: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/blist.h:785: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/blist.h:795: error: ‘purple_group_on_account’ declared as function returning a function
/usr/include/libpurple/blist.h:908: error: ‘purple_blist_node_get_bool’ declared as function returning a function
/usr/include/libpurple/blist.h:994: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/libpurple/connection.h:148,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/status.h:298: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/status.h:336: error: ‘purple_status_type_is_saveable’ declared as function returning a function
/usr/include/libpurple/status.h:347: error: ‘purple_status_type_is_user_settable’ declared as function returning a function
/usr/include/libpurple/status.h:359: error: ‘purple_status_type_is_independent’ declared as function returning a function
/usr/include/libpurple/status.h:368: error: ‘purple_status_type_is_exclusive’ declared as function returning a function
/usr/include/libpurple/status.h:379: error: ‘purple_status_type_is_available’ declared as function returning a function
/usr/include/libpurple/status.h:408: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/status.h:419: error: expected ‘)’ before ‘*’ token
/usr/include/libpurple/status.h:523: error: expected declaration specifiers or ‘...’ before ‘va_list’
/usr/include/libpurple/status.h:538: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/status.h:622: error: ‘purple_status_is_independent’ declared as function returning a function
/usr/include/libpurple/status.h:634: error: ‘purple_status_is_exclusive’ declared as function returning a function
/usr/include/libpurple/status.h:648: error: ‘purple_status_is_available’ declared as function returning a function
/usr/include/libpurple/status.h:657: error: ‘purple_status_is_active’ declared as function returning a function
/usr/include/libpurple/status.h:666: error: ‘purple_status_is_online’ declared as function returning a function
/usr/include/libpurple/status.h:688: error: ‘purple_status_get_attr_boolean’ declared as function returning a function
/usr/include/libpurple/status.h:721: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_status_compare’
/usr/include/libpurple/status.h:791: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/status.h:893: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/status.h:924: error: ‘purple_presence_is_available’ declared as function returning a function
/usr/include/libpurple/status.h:933: error: ‘purple_presence_is_online’ declared as function returning a function
/usr/include/libpurple/status.h:946: error: ‘purple_presence_is_status_active’ declared as function returning a function
/usr/include/libpurple/status.h:960: error: ‘purple_presence_is_status_primitive_active’ declared as function returning a function
/usr/include/libpurple/status.h:971: error: ‘purple_presence_is_idle’ declared as function returning a function
/usr/include/libpurple/status.h:1001: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_presence_compare’
In file included from /usr/include/libpurple/sslconn.h:37,
                 from /usr/include/libpurple/connection.h:149,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/certificate.h:62: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/certificate.h:74: error: expected specifier-qualifier-list before ‘gpointer’
/usr/include/libpurple/certificate.h:86: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/libpurple/certificate.h:152: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/libpurple/certificate.h:275: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/libpurple/certificate.h:328: error: expected specifier-qualifier-list before ‘gchar’
/usr/include/libpurple/certificate.h:376: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:413: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:430: error: expected ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:443: error: ‘purple_certificate_signed_by’ declared as function returning a function
/usr/include/libpurple/certificate.h:458: error: expected ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:468: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:478: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:489: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:498: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:508: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:520: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:530: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:543: error: ‘purple_certificate_get_times’ declared as function returning a function
/usr/include/libpurple/certificate.h:562: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:575: error: ‘purple_certificate_pool_usable’ declared as function returning a function
/usr/include/libpurple/certificate.h:595: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:604: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:617: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:627: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:636: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:645: error: expected ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:670: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_certificate_get_handle’
/usr/include/libpurple/certificate.h:677: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:685: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:697: error: ‘purple_certificate_register_scheme’ declared as function returning a function
/usr/include/libpurple/certificate.h:707: error: ‘purple_certificate_unregister_scheme’ declared as function returning a function
/usr/include/libpurple/certificate.h:715: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:723: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:733: error: ‘purple_certificate_register_verifier’ declared as function returning a function
/usr/include/libpurple/certificate.h:742: error: ‘purple_certificate_unregister_verifier’ declared as function returning a function
/usr/include/libpurple/certificate.h:750: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/certificate.h:758: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/certificate.h:768: error: ‘purple_certificate_register_pool’ declared as function returning a function
/usr/include/libpurple/certificate.h:777: error: ‘purple_certificate_unregister_pool’ declared as function returning a function
In file included from /usr/include/libpurple/connection.h:149,
                 from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/sslconn.h:45: error: expected ‘)’ before ‘PurpleSslConnection’
/usr/include/libpurple/sslconn.h:48: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/sslconn.h:59: error: expected specifier-qualifier-list before ‘PurpleSslInputFunction’
/usr/include/libpurple/sslconn.h:94: error: ‘init’ declared as function returning a function
/usr/include/libpurple/sslconn.h:136: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/sslconn.h:157: error: ‘purple_ssl_is_supported’ declared as function returning a function
/usr/include/libpurple/sslconn.h:165: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/sslconn.h:185: error: expected declaration specifiers or ‘...’ before ‘PurpleSslInputFunction’
/usr/include/libpurple/sslconn.h:204: error: expected declaration specifiers or ‘...’ before ‘PurpleSslInputFunction’
/usr/include/libpurple/sslconn.h:224: error: expected declaration specifiers or ‘...’ before ‘PurpleSslInputFunction’
/usr/include/libpurple/sslconn.h:237: error: expected declaration specifiers or ‘...’ before ‘PurpleSslInputFunction’
/usr/include/libpurple/sslconn.h:279: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/libpurple/account.h:43,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/connection.h:240: error: expected specifier-qualifier-list before ‘GSList’
/usr/include/libpurple/connection.h:490: error: ‘purple_connection_error_is_fatal’ declared as function returning a function
/usr/include/libpurple/connection.h:510: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/connection.h:517: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/libpurple/account.h:44,
                 from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/log.h:55: error: expected ‘)’ before ‘*’ token
/usr/include/libpurple/log.h:72: error: expected specifier-qualifier-list before ‘gsize’
/usr/include/libpurple/log.h:173: error: field ‘buddy’ declared as a function
/usr/include/libpurple/log.h:250: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/log.h:268: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/log.h:276: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/log.h:306: error: ‘purple_log_is_deletable’ declared as function returning a function
/usr/include/libpurple/log.h:314: error: ‘purple_log_delete’ declared as function returning a function
/usr/include/libpurple/log.h:335: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_log_compare’
/usr/include/libpurple/log.h:344: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_log_set_compare’
/usr/include/libpurple/log.h:395: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/log.h:449: error: ‘purple_log_common_deleter’ declared as function returning a function
/usr/include/libpurple/log.h:464: error: ‘purple_log_common_is_deletable’ declared as function returning a function
/usr/include/libpurple/log.h:539: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/libpurple/conversation.h:146,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/account.h:120: error: field ‘remember_pass’ declared as a function
/usr/include/libpurple/account.h:125: error: field ‘disconnecting’ declared as a function
/usr/include/libpurple/account.h:127: error: expected specifier-qualifier-list before ‘GHashTable’
/usr/include/libpurple/account.h:305: error: expected declaration specifiers or ‘...’ before ‘GCallback’
/usr/include/libpurple/account.h:306: error: expected declaration specifiers or ‘...’ before ‘GCallback’
/usr/include/libpurple/account.h:421: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/account.h:451: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/account.h:529: error: ‘purple_account_is_connected’ declared as function returning a function
/usr/include/libpurple/account.h:538: error: ‘purple_account_is_connecting’ declared as function returning a function
/usr/include/libpurple/account.h:547: error: ‘purple_account_is_disconnected’ declared as function returning a function
/usr/include/libpurple/account.h:628: error: ‘purple_account_get_remember_password’ declared as function returning a function
/usr/include/libpurple/account.h:637: error: ‘purple_account_get_check_mail’ declared as function returning a function
/usr/include/libpurple/account.h:649: error: ‘purple_account_get_enabled’ declared as function returning a function
/usr/include/libpurple/account.h:730: error: ‘purple_account_is_status_active’ declared as function returning a function
/usr/include/libpurple/account.h:739: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/account.h:776: error: ‘purple_account_get_bool’ declared as function returning a function
/usr/include/libpurple/account.h:816: error: ‘purple_account_get_ui_bool’ declared as function returning a function
/usr/include/libpurple/account.h:854: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/account.h:877: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/account.h:878: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/account.h:904: error: ‘purple_account_supports_offline_message’ declared as function returning a function
/usr/include/libpurple/account.h:963: error: expected declaration specifiers or ‘...’ before ‘gint’
/usr/include/libpurple/account.h:970: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/account.h:979: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
In file included from /usr/include/libpurple/conversation.h:149,
                 from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/server.h:62: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/libpurple/server.h:77: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/libpurple/server.h:88: error: expected declaration specifiers or ‘...’ before ‘guint’
/usr/include/libpurple/server.h:148: error: expected declaration specifiers or ‘...’ before ‘GHashTable’
/usr/include/libpurple/server.h:154: error: expected declaration specifiers or ‘...’ before ‘GHashTable’
/usr/include/libpurple/server.h:169: error: expected declaration specifiers or ‘...’ before ‘GHashTable’
/usr/include/libpurple/server.h:182: error: expected declaration specifiers or ‘...’ before ‘GHashTable’
In file included from LaTeX.h:46,
                 from LaTeX.c:33:
/usr/include/libpurple/conversation.h:202: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/conversation.h:215: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/conversation.h:230: error: ‘has_focus’ declared as function returning a function
/usr/include/libpurple/conversation.h:233: error: ‘custom_smiley_add’ declared as function returning a function
/usr/include/libpurple/conversation.h:235: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/conversation.h:236: error: expected ‘;’ before ‘void’
/usr/include/libpurple/conversation.h:259: error: expected specifier-qualifier-list before ‘guint’
/usr/include/libpurple/conversation.h:273: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/conversation.h:297: error: field ‘buddy’ declared as a function
/usr/include/libpurple/conversation.h:335: error: field ‘logging’ declared as a function
/usr/include/libpurple/conversation.h:337: error: expected specifier-qualifier-list before ‘GList’
/usr/include/libpurple/conversation.h:529: error: ‘purple_conversation_is_logging’ declared as function returning a function
/usr/include/libpurple/conversation.h:576: error: expected declaration specifiers or ‘...’ before ‘gpointer’
/usr/include/libpurple/conversation.h:586: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_conversation_get_data’
/usr/include/libpurple/conversation.h:595: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:602: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:609: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:672: error: ‘purple_conversation_has_focus’ declared as function returning a function
/usr/include/libpurple/conversation.h:700: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:833: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_conv_im_get_typing_timeout’
/usr/include/libpurple/conversation.h:879: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_conv_im_get_send_typed_timeout’
/usr/include/libpurple/conversation.h:914: error: ‘purple_conv_present_error’ declared as function returning a function
/usr/include/libpurple/conversation.h:968: error: ‘purple_conv_custom_smiley_add’ declared as function returning a function
/usr/include/libpurple/conversation.h:982: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
/usr/include/libpurple/conversation.h:1025: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:1034: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:1060: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:1069: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:1097: error: ‘purple_conv_chat_is_user_ignored’ declared as function returning a function
/usr/include/libpurple/conversation.h:1195: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/conversation.h:1195: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/conversation.h:1196: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/conversation.h:1227: error: expected declaration specifiers or ‘...’ before ‘GList’
/usr/include/libpurple/conversation.h:1238: error: ‘purple_conv_chat_find_user’ declared as function returning a function
/usr/include/libpurple/conversation.h:1311: error: ‘purple_conv_chat_has_left’ declared as function returning a function
/usr/include/libpurple/conversation.h:1360: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘*’ token
/usr/include/libpurple/conversation.h:1375: error: expected ‘;’, ‘,’ or ‘)’ before ‘*’ token
In file included from LaTeX.h:48,
                 from LaTeX.c:33:
/usr/include/libpurple/debug.h:54: error: ‘is_enabled’ declared as function returning a function
/usr/include/libpurple/debug.h: In function ‘purple_debug’:
/usr/include/libpurple/debug.h:77: error: expected declaration specifiers before ‘G_GNUC_PRINTF’
/usr/include/libpurple/debug.h:90: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘G_GNUC_PRINTF’
/usr/include/libpurple/debug.h:103: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘G_GNUC_PRINTF’
/usr/include/libpurple/debug.h:116: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘G_GNUC_PRINTF’
/usr/include/libpurple/debug.h:129: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘G_GNUC_PRINTF’
/usr/include/libpurple/debug.h:142: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘G_GNUC_PRINTF’
/usr/include/libpurple/debug.h:156: error: ‘purple_debug_is_enabled’ declared as function returning a function
In file included from LaTeX.h:55,
                 from LaTeX.c:33:
/usr/include/libpurple/version.h:53: error: expected ‘)’ before ‘required_major’
/usr/include/libpurple/version.h:62: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_major_version’
/usr/include/libpurple/version.h:71: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_minor_version’
/usr/include/libpurple/version.h:81: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘purple_micro_version’
In file included from LaTeX.c:33:
LaTeX.h:94: error: storage class specified for parameter ‘is_blacklisted’
LaTeX.h:94: error: ‘is_blacklisted’ declared as function returning a function
LaTeX.h:103: error: storage class specified for parameter ‘latex_to_image’
LaTeX.h:103: error: ‘latex_to_image’ declared as function returning a function
LaTeX.h:110: error: storage class specified for parameter ‘analyse’
LaTeX.h:110: error: ‘analyse’ declared as function returning a function
LaTeX.h:121: error: storage class specified for parameter ‘pidgin_latex_write’
LaTeX.h:121: error: ‘pidgin_latex_write’ declared as function returning a function
LaTeX.h:124: error: storage class specified for parameter ‘message_send’
LaTeX.h:124: error: ‘message_send’ declared as function returning a function
LaTeX.h:133: error: storage class specified for parameter ‘getdirname’
LaTeX.h:141: error: storage class specified for parameter ‘get_latex_cmd’
LaTeX.h:149: error: storage class specified for parameter ‘get_dvipng_cmd’
LaTeX.h:177: error: storage class specified for parameter ‘execute’
In file included from LaTeX.c:36:
/usr/include/string.h:40: error: storage class specified for parameter ‘memcpy’
/usr/include/string.h:44: error: storage class specified for parameter ‘memmove’
/usr/include/string.h:53: error: storage class specified for parameter ‘memccpy’
/usr/include/string.h:59: error: storage class specified for parameter ‘memset’
/usr/include/string.h:63: error: storage class specified for parameter ‘memcmp’
/usr/include/string.h:67: error: storage class specified for parameter ‘memchr’
/usr/include/string.h:85: error: storage class specified for parameter ‘strcpy’
/usr/include/string.h:89: error: storage class specified for parameter ‘strncpy’
/usr/include/string.h:93: error: storage class specified for parameter ‘strcat’
/usr/include/string.h:96: error: storage class specified for parameter ‘strncat’
/usr/include/string.h:100: error: storage class specified for parameter ‘strcmp’
/usr/include/string.h:103: error: storage class specified for parameter ‘strncmp’
/usr/include/string.h:107: error: storage class specified for parameter ‘strcoll’
/usr/include/string.h:111: error: storage class specified for parameter ‘strxfrm’
/usr/include/string.h:131: error: storage class specified for parameter ‘strdup’
/usr/include/string.h:168: error: storage class specified for parameter ‘strchr’
/usr/include/string.h:171: error: storage class specified for parameter ‘strrchr’
/usr/include/string.h:185: error: storage class specified for parameter ‘strcspn’
/usr/include/string.h:189: error: storage class specified for parameter ‘strspn’
/usr/include/string.h:192: error: storage class specified for parameter ‘strpbrk’
/usr/include/string.h:195: error: storage class specified for parameter ‘strstr’
/usr/include/string.h:200: error: storage class specified for parameter ‘strtok’
/usr/include/string.h:208: error: storage class specified for parameter ‘__strtok_r’
/usr/include/string.h:212: error: storage class specified for parameter ‘strtok_r’
/usr/include/string.h:243: error: storage class specified for parameter ‘strlen’
/usr/include/string.h:256: error: storage class specified for parameter ‘strerror’
/usr/include/string.h:270: error: storage class specified for parameter ‘strerror_r’
/usr/include/string.h:294: error: storage class specified for parameter ‘__bzero’
/usr/include/string.h:299: error: storage class specified for parameter ‘bcopy’
/usr/include/string.h:302: error: storage class specified for parameter ‘bzero’
/usr/include/string.h:306: error: storage class specified for parameter ‘bcmp’
/usr/include/string.h:310: error: storage class specified for parameter ‘index’
/usr/include/string.h:314: error: storage class specified for parameter ‘rindex’
/usr/include/string.h:318: error: storage class specified for parameter ‘ffs’
/usr/include/string.h:332: error: storage class specified for parameter ‘strcasecmp’
/usr/include/string.h:336: error: storage class specified for parameter ‘strncasecmp’
/usr/include/string.h:356: error: storage class specified for parameter ‘strsep’
In file included from LaTeX.c:37:
/usr/include/unistd.h:226: error: storage class specified for parameter ‘useconds_t’
/usr/include/unistd.h:238: error: storage class specified for parameter ‘intptr_t’
/usr/include/unistd.h:245: error: storage class specified for parameter ‘socklen_t’
/usr/include/unistd.h:258: error: storage class specified for parameter ‘access’
/usr/include/unistd.h:301: error: storage class specified for parameter ‘lseek’
/usr/include/unistd.h:320: error: storage class specified for parameter ‘close’
/usr/include/unistd.h:327: error: storage class specified for parameter ‘read’
/usr/include/unistd.h:333: error: storage class specified for parameter ‘write’
/usr/include/unistd.h:384: error: storage class specified for parameter ‘pipe’
/usr/include/unistd.h:399: error: storage class specified for parameter ‘alarm’
/usr/include/unistd.h:411: error: storage class specified for parameter ‘sleep’
/usr/include/unistd.h:419: error: storage class specified for parameter ‘ualarm’
/usr/include/unistd.h:426: error: storage class specified for parameter ‘usleep’
/usr/include/unistd.h:435: error: storage class specified for parameter ‘pause’
/usr/include/unistd.h:440: error: storage class specified for parameter ‘chown’
/usr/include/unistd.h:444: error: storage class specified for parameter ‘fchown’
/usr/include/unistd.h:450: error: storage class specified for parameter ‘lchown’
/usr/include/unistd.h:463: error: storage class specified for parameter ‘chdir’
/usr/include/unistd.h:467: error: storage class specified for parameter ‘fchdir’
/usr/include/unistd.h:477: error: storage class specified for parameter ‘getcwd’
/usr/include/unistd.h:491: error: storage class specified for parameter ‘getwd’
/usr/include/unistd.h:496: error: storage class specified for parameter ‘dup’
/usr/include/unistd.h:499: error: storage class specified for parameter ‘dup2’
/usr/include/unistd.h:508: error: storage class specified for parameter ‘__environ’
/usr/include/unistd.h:517: error: storage class specified for parameter ‘execve’
/usr/include/unistd.h:529: error: storage class specified for parameter ‘execv’
/usr/include/unistd.h:534: error: storage class specified for parameter ‘execle’
/usr/include/unistd.h:539: error: storage class specified for parameter ‘execl’
/usr/include/unistd.h:544: error: storage class specified for parameter ‘execvp’
/usr/include/unistd.h:550: error: storage class specified for parameter ‘execlp’
/usr/include/unistd.h:555: error: storage class specified for parameter ‘nice’
/usr/include/unistd.h:560: error: storage class specified for parameter ‘_exit’
In file included from LaTeX.c:37:
/usr/include/unistd.h:570: error: storage class specified for parameter ‘pathconf’
/usr/include/unistd.h:573: error: storage class specified for parameter ‘fpathconf’
/usr/include/unistd.h:576: error: storage class specified for parameter ‘sysconf’
/usr/include/unistd.h:580: error: storage class specified for parameter ‘confstr’
/usr/include/unistd.h:585: error: storage class specified for parameter ‘getpid’
/usr/include/unistd.h:588: error: storage class specified for parameter ‘getppid’
/usr/include/unistd.h:593: error: storage class specified for parameter ‘getpgrp’
/usr/include/unistd.h:603: error: storage class specified for parameter ‘__getpgid’
/usr/include/unistd.h:612: error: storage class specified for parameter ‘setpgid’
/usr/include/unistd.h:629: error: storage class specified for parameter ‘setpgrp’
/usr/include/unistd.h:646: error: storage class specified for parameter ‘setsid’
/usr/include/unistd.h:654: error: storage class specified for parameter ‘getuid’
/usr/include/unistd.h:657: error: storage class specified for parameter ‘geteuid’
/usr/include/unistd.h:660: error: storage class specified for parameter ‘getgid’
/usr/include/unistd.h:663: error: storage class specified for parameter ‘getegid’
/usr/include/unistd.h:668: error: storage class specified for parameter ‘getgroups’
/usr/include/unistd.h:679: error: storage class specified for parameter ‘setuid’
/usr/include/unistd.h:684: error: storage class specified for parameter ‘setreuid’
/usr/include/unistd.h:689: error: storage class specified for parameter ‘seteuid’
/usr/include/unistd.h:696: error: storage class specified for parameter ‘setgid’
/usr/include/unistd.h:701: error: storage class specified for parameter ‘setregid’
/usr/include/unistd.h:706: error: storage class specified for parameter ‘setegid’
/usr/include/unistd.h:735: error: storage class specified for parameter ‘fork’
/usr/include/unistd.h:742: error: storage class specified for parameter ‘vfork’
/usr/include/unistd.h:748: error: storage class specified for parameter ‘ttyname’
/usr/include/unistd.h:753: error: storage class specified for parameter ‘ttyname_r’
/usr/include/unistd.h:757: error: storage class specified for parameter ‘isatty’
/usr/include/unistd.h:763: error: storage class specified for parameter ‘ttyslot’
/usr/include/unistd.h:769: error: storage class specified for parameter ‘link’
/usr/include/unistd.h:782: error: storage class specified for parameter ‘symlink’
/usr/include/unistd.h:789: error: storage class specified for parameter ‘readlink’
/usr/include/unistd.h:804: error: storage class specified for parameter ‘unlink’
/usr/include/unistd.h:813: error: storage class specified for parameter ‘rmdir’
/usr/include/unistd.h:817: error: storage class specified for parameter ‘tcgetpgrp’
/usr/include/unistd.h:820: error: storage class specified for parameter ‘tcsetpgrp’
/usr/include/unistd.h:827: error: storage class specified for parameter ‘getlogin’
/usr/include/unistd.h:835: error: storage class specified for parameter ‘getlogin_r’
/usr/include/unistd.h:840: error: storage class specified for parameter ‘setlogin’
In file included from /usr/include/unistd.h:849,
                 from LaTeX.c:37:
/usr/include/getopt.h:59: error: storage class specified for parameter ‘optarg’
/usr/include/getopt.h:73: error: storage class specified for parameter ‘optind’
/usr/include/getopt.h:78: error: storage class specified for parameter ‘opterr’
/usr/include/getopt.h:82: error: storage class specified for parameter ‘optopt’
/usr/include/getopt.h:153: error: storage class specified for parameter ‘getopt’
In file included from LaTeX.c:37:
/usr/include/unistd.h:857: error: storage class specified for parameter ‘gethostname’
/usr/include/unistd.h:865: error: storage class specified for parameter ‘sethostname’
/usr/include/unistd.h:869: error: storage class specified for parameter ‘sethostid’
/usr/include/unistd.h:876: error: storage class specified for parameter ‘getdomainname’
/usr/include/unistd.h:878: error: storage class specified for parameter ‘setdomainname’
/usr/include/unistd.h:884: error: storage class specified for parameter ‘vhangup’
/usr/include/unistd.h:887: error: storage class specified for parameter ‘revoke’
/usr/include/unistd.h:897: error: storage class specified for parameter ‘profil’
/usr/include/unistd.h:903: error: storage class specified for parameter ‘acct’
/usr/include/unistd.h:907: error: storage class specified for parameter ‘getusershell’
/usr/include/unistd.h:908: error: storage class specified for parameter ‘endusershell’
/usr/include/unistd.h:909: error: storage class specified for parameter ‘setusershell’
/usr/include/unistd.h:915: error: storage class specified for parameter ‘daemon’
/usr/include/unistd.h:922: error: storage class specified for parameter ‘chroot’
/usr/include/unistd.h:926: error: storage class specified for parameter ‘getpass’
/usr/include/unistd.h:935: error: storage class specified for parameter ‘fsync’
/usr/include/unistd.h:942: error: storage class specified for parameter ‘gethostid’
/usr/include/unistd.h:945: error: storage class specified for parameter ‘sync’
/usr/include/unistd.h:950: error: storage class specified for parameter ‘getpagesize’
/usr/include/unistd.h:955: error: storage class specified for parameter ‘getdtablesize’
/usr/include/unistd.h:961: error: storage class specified for parameter ‘truncate’
/usr/include/unistd.h:982: error: storage class specified for parameter ‘ftruncate’
/usr/include/unistd.h:1002: error: storage class specified for parameter ‘brk’
/usr/include/unistd.h:1008: error: expected ‘)’ before ‘__delta’
/usr/include/unistd.h:1023: error: storage class specified for parameter ‘syscall’
/usr/include/unistd.h:1046: error: storage class specified for parameter ‘lockf’
/usr/include/unistd.h:1077: error: storage class specified for parameter ‘fdatasync’
In file included from /usr/include/errno.h:36,
                 from LaTeX.c:38:
/usr/include/bits/errno.h:43: error: storage class specified for parameter ‘__errno_location’
In file included from /usr/include/signal.h:33,
                 from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/bits/sigset.h:104: error: storage class specified for parameter ‘__sigismember’
/usr/include/bits/sigset.h:105: error: storage class specified for parameter ‘__sigaddset’
/usr/include/bits/sigset.h:106: error: storage class specified for parameter ‘__sigdelset’
In file included from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/signal.h:41: error: storage class specified for parameter ‘sig_atomic_t’
In file included from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/signal.h:75: error: storage class specified for parameter ‘__sighandler_t’
/usr/include/signal.h:80: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘__sysv_signal’
/usr/include/signal.h:92: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘signal’
/usr/include/signal.h:117: error: storage class specified for parameter ‘kill’
/usr/include/signal.h:124: error: storage class specified for parameter ‘killpg’
/usr/include/signal.h:129: error: storage class specified for parameter ‘raise’
/usr/include/signal.h:134: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘ssignal’
/usr/include/signal.h:136: error: storage class specified for parameter ‘gsignal’
/usr/include/signal.h:141: error: storage class specified for parameter ‘psignal’
/usr/include/signal.h:153: error: storage class specified for parameter ‘__sigpause’
/usr/include/signal.h:181: error: storage class specified for parameter ‘sigblock’
/usr/include/signal.h:184: error: storage class specified for parameter ‘sigsetmask’
/usr/include/signal.h:187: error: storage class specified for parameter ‘siggetmask’
/usr/include/signal.h:201: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘sig_t’
In file included from /usr/include/signal.h:212,
                 from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/bits/siginfo.h:37: error: storage class specified for parameter ‘sigval_t’
/usr/include/bits/siginfo.h:74: error: expected specifier-qualifier-list before ‘sigval_t’
/usr/include/bits/siginfo.h:82: error: expected specifier-qualifier-list before ‘sigval_t’
/usr/include/bits/siginfo.h:108: error: storage class specified for parameter ‘siginfo_t’
/usr/include/bits/siginfo.h:275: error: expected specifier-qualifier-list before ‘sigval_t’
/usr/include/bits/siginfo.h:293: error: storage class specified for parameter ‘sigevent_t’
In file included from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/signal.h:216: error: storage class specified for parameter ‘sigemptyset’
/usr/include/signal.h:219: error: storage class specified for parameter ‘sigfillset’
/usr/include/signal.h:222: error: storage class specified for parameter ‘sigaddset’
/usr/include/signal.h:225: error: storage class specified for parameter ‘sigdelset’
/usr/include/signal.h:229: error: storage class specified for parameter ‘sigismember’
In file included from /usr/include/signal.h:246,
                 from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/bits/sigaction.h:32: error: expected specifier-qualifier-list before ‘__sighandler_t’
In file included from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/signal.h:250: error: storage class specified for parameter ‘sigprocmask’
/usr/include/signal.h:257: error: storage class specified for parameter ‘sigsuspend’
/usr/include/signal.h:261: error: storage class specified for parameter ‘sigaction’
/usr/include/signal.h:264: error: storage class specified for parameter ‘sigpending’
/usr/include/signal.h:272: error: storage class specified for parameter ‘sigwait’
/usr/include/signal.h:280: error: expected declaration specifiers or ‘...’ before ‘siginfo_t’
/usr/include/signal.h:280: error: storage class specified for parameter ‘sigwaitinfo’
/usr/include/signal.h:288: error: expected declaration specifiers or ‘...’ before ‘siginfo_t’
/usr/include/signal.h:290: error: storage class specified for parameter ‘sigtimedwait’
/usr/include/signal.h:295: error: storage class specified for parameter ‘sigqueue’
/usr/include/signal.h:304: error: storage class specified for parameter ‘_sys_siglist’
/usr/include/signal.h:305: error: storage class specified for parameter ‘sys_siglist’
/usr/include/signal.h:310: error: expected specifier-qualifier-list before ‘__sighandler_t’
/usr/include/signal.h:329: error: storage class specified for parameter ‘sigvec’
In file included from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/signal.h:336: error: storage class specified for parameter ‘sigreturn’
In file included from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/signal.h:348: error: storage class specified for parameter ‘siginterrupt’
In file included from /usr/include/signal.h:350,
                 from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/bits/sigstack.h:55: error: storage class specified for parameter ‘stack_t’
In file included from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/signal.h:360: error: storage class specified for parameter ‘sigstack’
/usr/include/signal.h:365: error: storage class specified for parameter ‘sigaltstack’
In file included from /usr/include/signal.h:389,
                 from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/bits/sigthread.h:33: error: storage class specified for parameter ‘pthread_sigmask’
/usr/include/bits/sigthread.h:36: error: storage class specified for parameter ‘pthread_kill’
In file included from /usr/include/sys/wait.h:31,
                 from LaTeX.c:42:
/usr/include/signal.h:396: error: storage class specified for parameter ‘__libc_current_sigrtmin’
/usr/include/signal.h:398: error: storage class specified for parameter ‘__libc_current_sigrtmax’
In file included from /usr/include/sys/resource.h:25,
                 from /usr/include/sys/wait.h:32,
                 from LaTeX.c:42:
/usr/include/bits/resource.h:127: error: storage class specified for parameter ‘rlim_t’
/usr/include/bits/resource.h:138: error: expected specifier-qualifier-list before ‘rlim_t’
In file included from /usr/include/sys/wait.h:32,
                 from LaTeX.c:42:
/usr/include/sys/resource.h:43: error: storage class specified for parameter ‘__rlimit_resource_t’
/usr/include/sys/resource.h:44: error: storage class specified for parameter ‘__rusage_who_t’
/usr/include/sys/resource.h:45: error: storage class specified for parameter ‘__priority_which_t’
/usr/include/sys/resource.h:51: error: expected ‘)’ before ‘__resource’
/usr/include/sys/resource.h:70: error: expected ‘)’ before ‘__resource’
/usr/include/sys/resource.h:88: error: expected ‘)’ before ‘__who’
/usr/include/sys/resource.h:94: error: expected ‘)’ before ‘__which’
/usr/include/sys/resource.h:98: error: expected ‘)’ before ‘__which’
In file included from LaTeX.c:42:
/usr/include/sys/wait.h:67: error: storage class specified for parameter ‘__WAIT_STATUS’
In file included from LaTeX.c:42:
/usr/include/sys/wait.h:107: error: storage class specified for parameter ‘idtype_t’
/usr/include/sys/wait.h:116: error: expected ‘)’ before ‘__stat_loc’
/usr/include/sys/wait.h:139: error: storage class specified for parameter ‘waitpid’
In file included from LaTeX.c:42:
/usr/include/sys/wait.h:155: error: expected ‘)’ before ‘__idtype’
/usr/include/sys/wait.h:169: error: expected ‘)’ before ‘__stat_loc’
/usr/include/sys/wait.h:175: error: expected declaration specifiers or ‘...’ before ‘__WAIT_STATUS’
/usr/include/sys/wait.h:176: error: storage class specified for parameter ‘wait4’
LaTeX.c:51: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:101: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:124: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:146: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:234: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:260: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:265: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:270: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:275: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:302: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:402: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:530: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:566: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:599: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:614: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:626: error: storage class specified for parameter ‘info’
LaTeX.c:626: error: parameter ‘info’ is initialised
LaTeX.c:634: warning: excess elements in struct initialiser
LaTeX.c:634: warning: (near initialisation for ‘info’)
LaTeX.c:635: warning: excess elements in struct initialiser
LaTeX.c:635: warning: (near initialisation for ‘info’)
LaTeX.c:637: warning: excess elements in struct initialiser
LaTeX.c:637: warning: (near initialisation for ‘info’)
LaTeX.c:638: warning: excess elements in struct initialiser
LaTeX.c:638: warning: (near initialisation for ‘info’)
LaTeX.c:639: warning: excess elements in struct initialiser
LaTeX.c:639: warning: (near initialisation for ‘info’)
LaTeX.c:641: warning: excess elements in struct initialiser
LaTeX.c:641: warning: (near initialisation for ‘info’)
LaTeX.c:643: warning: excess elements in struct initialiser
LaTeX.c:643: warning: (near initialisation for ‘info’)
LaTeX.c:644: warning: excess elements in struct initialiser
LaTeX.c:644: warning: (near initialisation for ‘info’)
LaTeX.c:645: warning: excess elements in struct initialiser
LaTeX.c:645: warning: (near initialisation for ‘info’)
LaTeX.c:646: error: ‘plugin_load’ undeclared (first use in this function)
LaTeX.c:646: error: (Each undeclared identifier is reported only once
LaTeX.c:646: error: for each function it appears in.)
LaTeX.c:646: warning: excess elements in struct initialiser
LaTeX.c:646: warning: (near initialisation for ‘info’)
LaTeX.c:647: error: ‘plugin_unload’ undeclared (first use in this function)
LaTeX.c:647: warning: excess elements in struct initialiser
LaTeX.c:647: warning: (near initialisation for ‘info’)
LaTeX.c:648: warning: excess elements in struct initialiser
LaTeX.c:648: warning: (near initialisation for ‘info’)
LaTeX.c:649: warning: excess elements in struct initialiser
LaTeX.c:649: warning: (near initialisation for ‘info’)
LaTeX.c:650: warning: excess elements in struct initialiser
LaTeX.c:650: warning: (near initialisation for ‘info’)
LaTeX.c:651: warning: excess elements in struct initialiser
LaTeX.c:651: warning: (near initialisation for ‘info’)
LaTeX.c:652: warning: excess elements in struct initialiser
LaTeX.c:652: warning: (near initialisation for ‘info’)
LaTeX.c:653: warning: excess elements in struct initialiser
LaTeX.c:653: warning: (near initialisation for ‘info’)
LaTeX.c:654: warning: excess elements in struct initialiser
LaTeX.c:654: warning: (near initialisation for ‘info’)
LaTeX.c:655: warning: excess elements in struct initialiser
LaTeX.c:655: warning: (near initialisation for ‘info’)
LaTeX.c:657: warning: excess elements in struct initialiser
LaTeX.c:657: warning: (near initialisation for ‘info’)
LaTeX.c:663: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘{’ token
LaTeX.c:666: error: expected declaration specifiers before ‘G_MODULE_EXPORT’
LaTeX.c:666: error: expected declaration specifiers before ‘G_MODULE_EXPORT’
LaTeX.c:666: error: old-style parameter declarations in prototyped function definition
LaTeX.c:666: error: expected ‘{’ at end of input
make: *** [LaTeX.o] Error 1

```

Anyone know what it's talking about?

---

### Post by Partyboi2 on 2009-08-30
Hi, looks like you are missing some required packages, try installing 'pidgin-dev' and 'libgtk2.0-dev'. you can also download a deb from [[COLOR=Blue]here[/COLOR]]("http://sourceforge.net/projects/pidgin-latex/") for Pidgin-Latex.

---

