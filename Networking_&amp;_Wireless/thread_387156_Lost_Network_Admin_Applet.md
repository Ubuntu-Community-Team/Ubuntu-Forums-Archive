---
title: "Lost Network Admin Applet"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by Gnowm on 2007-03-17
Hi there all

When changing from DHCP to static IP's I tried to use the GUI applet accessed from the menu System --> Administration --> Networking
and it initially started bug buddy with a loooong error message (see below) or nothing at all happens, no sign of it in ps aux and no cpu usage. This applet has worked on numerous occasions before and I have changed nothing (that I am aware of anyways) regarding it.

I have tried to run it from the Debian Menu and I get the following error popup

> You are not allowed to access the system configuration.


```

Memory status: size: 28409856 vsize: 0 resident: 28409856 share: 0 rss: 11886592 rss_rlim: 0
CPU usage: start_time: 1173394874 rtime: 0 utime: 54 stime: 0 cutime:48 cstime: 0 timeout: 6 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/network-admin'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
~
+ a number of the same
~
[Thread debugging using libthread_db enabled]
[New Thread -1225128272 (LWP 3112)]
(no debugging symbols found)
~
+ a number of the same
~
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb73b4323 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f481b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb76678f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#5  0xb7643ecc in g_hash_table_remove_all () from /usr/lib/libglib-2.0.so.0
#6  0xb7644639 in g_hash_table_insert () from /usr/lib/libglib-2.0.so.0
#7  0xb7cf422d in pango_fc_font_map_get_type ()
   from /usr/lib/libpangoft2-1.0.so.0
#8  0xb78b8fe0 in pango_font_map_load_fontset ()
   from /usr/lib/libpango-1.0.so.0
#9  0xb78b7072 in pango_context_get_font_description ()
   from /usr/lib/libpango-1.0.so.0
#10 0xb78b73b2 in pango_itemize_with_base_dir ()
   from /usr/lib/libpango-1.0.so.0
#11 0xb78bf38b in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
#12 0xb78bff6b in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
#13 0xb7ac4ec0 in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
#14 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#15 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#16 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#17 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#18 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#19 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#20 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#21 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#22 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#23 0xb7a92df3 in gtk_frame_new () from /usr/lib/libgtk-x11-2.0.so.0
#24 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#25 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#26 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#27 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#28 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#29 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#30 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#31 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#32 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#33 0xb7be8450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#34 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#35 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#36 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#37 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#38 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#39 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#40 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#41 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#42 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#43 0xb7af50de in gtk_notebook_new () from /usr/lib/libgtk-x11-2.0.so.0
#44 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#45 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#46 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#47 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#48 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#49 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#50 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#51 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#52 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#53 0xb7be8450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#54 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#55 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#56 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#57 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#58 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#59 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#60 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#61 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#62 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#63 0xb7be8450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#64 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#65 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#66 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#67 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#68 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#69 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#70 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#71 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#72 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#73 0xb7bf9990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#74 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#75 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#76 0xb771a79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#77 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#78 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#79 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#80 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#81 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#82 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#83 0xb7bf9d10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#84 0xb7c02fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#85 0xb7727b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#86 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#87 0xb771a79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#88 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#89 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#90 0xb772c279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#91 0xb7bf2b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#92 0x08057f19 in ?? ()
#93 0x080e5000 in ?? ()
#94 0x08097eb0 in ?? ()
#95 0x08054d50 in ?? ()
#96 0x00000000 in ?? ()

Thread 1 (Thread -1225128272 (LWP 3112)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb73b4323 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f481b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb76678f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0xb7643ecc in g_hash_table_remove_all () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7644639 in g_hash_table_insert () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb7cf422d in pango_fc_font_map_get_type ()
   from /usr/lib/libpangoft2-1.0.so.0
No symbol table info available.
#8  0xb78b8fe0 in pango_font_map_load_fontset ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#9  0xb78b7072 in pango_context_get_font_description ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#10 0xb78b73b2 in pango_itemize_with_base_dir ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#11 0xb78bf38b in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#12 0xb78bff6b in pango_layout_iter_get_char_extents ()
   from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#13 0xb7ac4ec0 in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#14 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#20 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#22 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#23 0xb7a92df3 in gtk_frame_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#24 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#29 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#30 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#31 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#32 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#33 0xb7be8450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#34 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#35 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#36 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#37 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#38 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#39 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#40 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#41 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#42 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#43 0xb7af50de in gtk_notebook_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#44 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#45 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#46 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#47 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#48 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#49 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#50 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#51 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#52 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#53 0xb7be8450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#54 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#55 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#56 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#57 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#58 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#59 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#60 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#61 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#62 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#63 0xb7be8450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#64 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#65 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#66 0xb771a87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#67 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#68 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#69 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#70 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#71 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#72 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#73 0xb7bf9990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#74 0xb7727199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#75 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#76 0xb771a79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#77 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#78 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#79 0xb772ee9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#80 0xb7b3ccf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#81 0xb7b3cf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#82 0xb7bf1b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#83 0xb7bf9d10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#84 0xb7c02fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#85 0xb7727b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#86 0xb7718fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#87 0xb771a79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#88 0xb772b02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#89 0xb772c0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#90 0xb772c279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#91 0xb7bf2b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#92 0x08057f19 in ?? ()
No symbol table info available.
#93 0x080e5000 in ?? ()
No symbol table info available.
#94 0x08097eb0 in ?? ()
No symbol table info available.
#95 0x08054d50 in ?? ()
No symbol table info available.
#96 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

```

I have the network running by hand editing the file 
```

/etc/networks/interfaces

```
but I would like to know how to get the GUI manager back in case I need to walk my parents through the same thing. BTW, the NetworkManager Applet 0.6.3 in the sys tray shows that there is no network connection...?

Anyone have an idea?

---

### Post by Floppyjoe on 2007-03-18
I'm not positive about this but I don't think network-manager works with static IP's

---

