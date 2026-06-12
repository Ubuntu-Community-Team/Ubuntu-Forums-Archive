---
title: "Ubuntu Networking Tool Crashing"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by kseise on 2007-02-26
My desktop has been working fine with Edgy for a couple of months now.  I recently added a laptop to my network.  I added the laptop as a known host by using System>Administration>Networking and adding the host entry.  The host is added.  Now when I try to launch the same tool, it crashes after asking for my sudo password.  I am attaching the Bug Buddy entry that it creates.  Can anyone tell me how to fix this?


> 
Memory status: size: 27848704 vsize: 0 resident: 27848704 share: 0 rss: 11198464 rss_rlim: 0
CPU usage: start_time: 1172538986 rtime: 0 utime: 51 stime: 0 cutime:47 cstime: 0 timeout: 4 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/bin/network-admin'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1225774704 (LWP 14409)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7315323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ea91b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb75c88f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#5  0xb759f536 in g_datalist_id_set_data_full ()
   from /usr/lib/libglib-2.0.so.0
#6  0xb7680852 in g_object_class_override_property ()
   from /usr/lib/libgobject-2.0.so.0
#7  0xb769c6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#8  0xb7683952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#9  0xb7681bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#10 0xb768273f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#11 0xb76828f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#12 0xb7820876 in pango_layout_new () from /usr/lib/libpango-1.0.so.0
#13 0xb7b51973 in gtk_widget_create_pango_layout ()
   from /usr/lib/libgtk-x11-2.0.so.0
#14 0xb797b5c2 in gtk_cell_renderer_text_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#15 0xb797bc58 in gtk_cell_renderer_text_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
#16 0xb7974914 in gtk_cell_renderer_get_size ()
   from /usr/lib/libgtk-x11-2.0.so.0
#17 0xb797e405 in gtk_cell_view_get_cell_renderers ()
   from /usr/lib/libgtk-x11-2.0.so.0
#18 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#19 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#20 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#21 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#22 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#23 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#24 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#25 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#26 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#27 0xb79a2ca9 in gtk_combo_box_popup () from /usr/lib/libgtk-x11-2.0.so.0
#28 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#29 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#30 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#31 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#32 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#33 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#34 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#35 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#36 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#37 0xb79f9040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#38 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#39 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#40 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#41 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#42 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#43 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#44 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#45 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#46 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#47 0xb7b4a450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#48 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#49 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#50 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#51 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#52 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#53 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#54 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#55 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#56 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#57 0xb7b4a450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#58 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#59 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#60 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#61 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#62 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#63 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#64 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#65 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#66 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#67 0xb7b5b990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#68 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#69 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#70 0xb767c79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#71 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#72 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#73 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#74 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#75 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#76 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#77 0xb7b5bd10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#78 0xb7b64fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#79 0xb7689b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#80 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#81 0xb767c79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#82 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#83 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#84 0xb768e279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#85 0xb7b54b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#86 0x08057f19 in ?? ()
#87 0x080dc008 in ?? ()
#88 0x08097440 in ?? ()
#89 0x08054d50 in ?? ()
#90 0x00000000 in ?? ()

Thread 1 (Thread -1225774704 (LWP 14409)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7315323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ea91b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb75c88f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0xb759f536 in g_datalist_id_set_data_full ()
   from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7680852 in g_object_class_override_property ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb769c6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb7683952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb7681bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0xb768273f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#11 0xb76828f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#12 0xb7820876 in pango_layout_new () from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#13 0xb7b51973 in gtk_widget_create_pango_layout ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#14 0xb797b5c2 in gtk_cell_renderer_text_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#15 0xb797bc58 in gtk_cell_renderer_text_new ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#16 0xb7974914 in gtk_cell_renderer_get_size ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#17 0xb797e405 in gtk_cell_view_get_cell_renderers ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#18 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#20 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#21 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#23 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#25 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#26 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#27 0xb79a2ca9 in gtk_combo_box_popup () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#28 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#29 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#30 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#31 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#32 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#33 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#34 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#35 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#36 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#37 0xb79f9040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#38 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#39 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#40 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#41 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#42 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#43 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#44 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#45 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#46 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#47 0xb7b4a450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#48 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#49 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#50 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#51 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#52 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#53 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#54 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#55 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#56 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#57 0xb7b4a450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#58 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#59 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#60 0xb767c87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#61 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#62 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#63 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#64 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#65 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#66 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#67 0xb7b5b990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#68 0xb7689199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#69 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#70 0xb767c79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#71 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#72 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#73 0xb7690e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#74 0xb7a9ecf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#75 0xb7a9ef4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#76 0xb7b53b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#77 0xb7b5bd10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#78 0xb7b64fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#79 0xb7689b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#80 0xb767afb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#81 0xb767c79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#82 0xb768d02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#83 0xb768e0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#84 0xb768e279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#85 0xb7b54b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#86 0x08057f19 in ?? ()
No symbol table info available.
#87 0x080dc008 in ?? ()
No symbol table info available.
#88 0x08097440 in ?? ()
No symbol table info available.
#89 0x08054d50 in ?? ()
No symbol table info available.
#90 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()



---

