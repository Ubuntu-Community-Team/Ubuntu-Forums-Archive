---
title: "Network Tool Crashes"
date: 2006-12-02
forum: Networking &amp; Wireless
---

### Post by CSE_Boilermaker on 2006-12-02
I'm working with a brand new installation of 6.10, and the first thing I did was go into System -> Networking and do the following:

1. Disable wireless connection
2. Enable and configure the LAN connection as static and the appropriate IP/Mask/etc.
3. Couldn't get a connection so I rebooted.

Now, whenever I try to go to the Networking tool it crashes and shoots right to Bug Buddy. No connection currently works and the laptop can't connect to the network. Any ideas?

The wireless connection worked all last week fwiw.

The card is on a laptop Realtek 8139/C/C+ and it's eth0 while the wireless is on eth1.

Here's the details from Bug Buddy:


Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 31895552 vsize: 0 resident: 31895552 share: 0 rss: 11370496 rss_rlim: 0
CPU usage: start_time: 1165097501 rtime: 0 utime: 30 stime: 0 cutime:27 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

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
[New Thread -1225767248 (LWP 4556)]
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
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb7318323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7eac1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb75cb8f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#5  0xb75a2536 in g_datalist_id_set_data_full ()
   from /usr/lib/libglib-2.0.so.0
#6  0xb7682852 in g_object_class_override_property ()
   from /usr/lib/libgobject-2.0.so.0
#7  0xb769e6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
#8  0xb7685952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
#9  0xb7683bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
#10 0xb768473f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
#11 0xb76848f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
#12 0xb7822876 in pango_layout_new () from /usr/lib/libpango-1.0.so.0
#13 0xb7b53973 in gtk_widget_create_pango_layout ()
   from /usr/lib/libgtk-x11-2.0.so.0
#14 0xb7a23a49 in gtk_label_get_angle () from /usr/lib/libgtk-x11-2.0.so.0
#15 0xb7a28d4e in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
#16 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#17 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#18 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#19 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#20 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#21 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#22 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#23 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#24 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#25 0xb79fb040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#26 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#27 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#28 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#29 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#30 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#31 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#32 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#33 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#34 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#35 0xb796206f in gtk_alignment_new () from /usr/lib/libgtk-x11-2.0.so.0
#36 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#37 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#38 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#39 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#40 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#41 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#42 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#43 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#44 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#45 0xb796f24f in gtk_button_set_alignment ()
   from /usr/lib/libgtk-x11-2.0.so.0
#46 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#47 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#48 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#49 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#50 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#51 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#52 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#53 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#54 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#55 0xb79677c4 in _gtk_button_box_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#56 0xb7b4bbf0 in gtk_vbutton_box_new () from /usr/lib/libgtk-x11-2.0.so.0
#57 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#58 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#59 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#60 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#61 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#62 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#63 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#64 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#65 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#66 0xb79fb040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#67 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#68 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#69 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#70 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#71 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#72 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#73 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#74 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#75 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#76 0xb7a590de in gtk_notebook_new () from /usr/lib/libgtk-x11-2.0.so.0
#77 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#78 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#79 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#80 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#81 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#82 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#83 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#84 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#85 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#86 0xb7b4c450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#87 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#88 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#89 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#90 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#91 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#92 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#93 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#94 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#95 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#96 0xb7b4c450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#97 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#98 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#99 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#100 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#101 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#102 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#103 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#104 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#105 0xb7b55b2c in gtk_widget_size_request ()
   from /usr/lib/libgtk-x11-2.0.so.0
#106 0xb7b5d990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#107 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#108 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#109 0xb767e79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#110 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#111 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#112 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#113 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#114 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#115 0xb7b55b2c in gtk_widget_size_request ()
   from /usr/lib/libgtk-x11-2.0.so.0
#116 0xb7b5dd10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#117 0xb7b66fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#118 0xb768bb29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#119 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#120 0xb767e79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#121 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#122 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#123 0xb7690279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#124 0xb7b56b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#125 0x08057f19 in ?? ()
#126 0x080f2818 in ?? ()
#127 0x08095540 in ?? ()
#128 0x08054d50 in ?? ()
#129 0x00000000 in ?? ()

Thread 1 (Thread -1225767248 (LWP 4556)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7318323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7eac1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb75cb8f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0xb75a2536 in g_datalist_id_set_data_full ()
   from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb7682852 in g_object_class_override_property ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb769e6ce in g_type_create_instance () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb7685952 in g_object_set () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb7683bdb in g_object_newv () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#10 0xb768473f in g_object_new_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#11 0xb76848f0 in g_object_new () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#12 0xb7822876 in pango_layout_new () from /usr/lib/libpango-1.0.so.0
No symbol table info available.
#13 0xb7b53973 in gtk_widget_create_pango_layout ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#14 0xb7a23a49 in gtk_label_get_angle () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#15 0xb7a28d4e in gtk_label_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#16 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#19 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#20 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#21 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#22 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#23 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#24 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#25 0xb79fb040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#26 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#29 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#30 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#31 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#32 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#33 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#34 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#35 0xb796206f in gtk_alignment_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#36 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#37 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#38 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#39 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#40 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#41 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#42 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#43 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#44 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#45 0xb796f24f in gtk_button_set_alignment ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#46 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#47 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#48 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#49 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#50 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#51 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#52 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#53 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#54 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#55 0xb79677c4 in _gtk_button_box_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#56 0xb7b4bbf0 in gtk_vbutton_box_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#57 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#58 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#59 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#60 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#61 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#62 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#63 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#64 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#65 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#66 0xb79fb040 in gtk_hbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#67 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#68 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#69 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#70 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#71 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#72 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#73 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#74 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#75 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#76 0xb7a590de in gtk_notebook_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#77 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#78 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#79 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#80 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#81 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#82 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#83 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#84 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#85 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#86 0xb7b4c450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#87 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#88 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#89 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#90 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#91 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#92 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#93 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#94 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#95 0xb7b55b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#96 0xb7b4c450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#97 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#98 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#99 0xb767e87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#100 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#101 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#102 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#103 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#104 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#105 0xb7b55b2c in gtk_widget_size_request ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#106 0xb7b5d990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#107 0xb768b199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#108 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#109 0xb767e79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#110 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#111 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#112 0xb7692e9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#113 0xb7aa0cf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#114 0xb7aa0f4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#115 0xb7b55b2c in gtk_widget_size_request ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#116 0xb7b5dd10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#117 0xb7b66fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#118 0xb768bb29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#119 0xb767cfb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#120 0xb767e79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#121 0xb768f02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#122 0xb76900b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#123 0xb7690279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#124 0xb7b56b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#125 0x08057f19 in ?? ()
No symbol table info available.
#126 0x080f2818 in ?? ()
No symbol table info available.
#127 0x08095540 in ?? ()
No symbol table info available.
#128 0x08054d50 in ?? ()
No symbol table info available.
#129 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

### Post by CSE_Boilermaker on 2006-12-02
well, I searched a bit more and seems I have gotten things working. For any others that have this happen to them, simply open a terminal window and sudo network-admin. My other issue turned out that I needed to edit my /etc/resolv.conf for my router's IP.

Thanks for looking ;)

---

### Post by imjustabill on 2006-12-04
Thanks a lot! I was having the exact same problem. Also, if you don't want to constantly have to open the terminal to change your network settings, just edit the shortcut for it, and change the command from "network-admin" to "gksudo network admin".

---

