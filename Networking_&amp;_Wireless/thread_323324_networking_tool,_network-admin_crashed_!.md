---
title: "networking tool, network-admin crashed !"
date: 2006-12-21
forum: Networking &amp; Wireless
---

### Post by tom_adams on 2006-12-21
This is my first post on the forum.  I am new to linux and have made a lot of progress in the last 2 weeks:  installed ubuntu 64bit on two HP dual-boot laptops, got the wireless working cleanly on the one machine,  created some workaround scripts for wireless startup problems on the other machine, and got ssh running between the machines.   

My problem is that I used the network-admin gui to make a few changes, and the tool no longer functions.    When I try to run the tool a "bug buddy" screen pops up and network-admin fails to launch.   Fortunately the key network components were already functioning so wireless/wired connections are functioning.   The collected bug details are shown below.

Can I somehow simply re-install network-admin?   Does the collected info below suggest any workarounds, or root cause?   Is there an alternate tool that performs similar functionality? 

Thanks.

Buggy Buddy info starts here.
===============================
Distribution: Ubuntu 6.10 (edgy)
Gnome Release: 2.16.1 2006-10-02 (Ubuntu)
BugBuddy Version: 2.16.0

Memory status: size: 114302976 vsize: 114302976 resident: 13619200 share: 9244672 rss: 13619200 rss_rlim: -1
CPU usage: start_time: 1166759475 rtime: 58 utime: 53 stime: 5 cutime:1 cstime: 0 timeout: 0 it_real_value: 0 frequency: 100

Backtrace was generated from '/usr/bin/network-admin'

(no debugging symbols found)
Using host libthread_db library "/lib/libthread_db.so.1".
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
[New Thread 47466680003488 (LWP 7366)]
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
0x00002b2bb1124eb5 in waitpid () from /lib/libpthread.so.0
#0  0x00002b2bb1124eb5 in waitpid () from /lib/libpthread.so.0
#1  0x00002b2bad4d3a07 in gnome_gtk_module_info_get ()
   from /usr/lib64/libgnomeui-2.so.0
#2  <signal handler called>
#3  0x00002b2baf698420 in g_list_find () from /usr/lib64/libglib-2.0.so.0
#4  0x00002b2baf1c836d in g_object_newv () from /usr/lib64/libgobject-2.0.so.0
#5  0x00002b2baf1c8bee in g_object_new_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#6  0x00002b2baf1c8d91 in g_object_new () from /usr/lib64/libgobject-2.0.so.0
#7  0x00002b2bae7c07ba in gdk_pixbuf_new_from_data ()
   from /usr/lib64/libgdk_pixbuf-2.0.so.0
#8  0x00002b2bae176864 in _gtk_icon_cache_get_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#9  0x00002b2bae17c73e in gtk_icon_theme_lookup_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#10 0x00002b2bae17ca07 in gtk_icon_theme_load_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#11 0x00002b2bae1795ac in gtk_icon_set_render_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#12 0x00002b2bae2b03ba in gtk_widget_render_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#13 0x00002b2bae18bc91 in gtk_image_new_from_pixmap ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#14 0x00002b2bae18bcb9 in gtk_image_new_from_pixmap ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#15 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
#16 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
#17 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#18 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
#19 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#20 0x00002b2bae17186e in gtk_hbox_new () from /usr/lib64/libgtk-x11-2.0.so.0
#21 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
#22 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
#23 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#24 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
#25 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#26 0x00002b2bae0e6869 in gtk_alignment_new ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#27 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
#28 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
#29 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#30 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
#31 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#32 0x00002b2bae0f2aa2 in gtk_button_set_alignment ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#33 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
#34 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
#35 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#36 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
#37 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#38 0x00002b2bae0eb98e in _gtk_button_box_child_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#39 0x00002b2bae170fe8 in gtk_hbutton_box_new ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#40 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
#41 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
#42 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#43 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
#44 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#45 0x00002b2bae2a712e in gtk_vbox_new () from /usr/lib64/libgtk-x11-2.0.so.0
#46 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
#47 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
#48 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#49 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
#50 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#51 0x00002b2bae2b6078 in gtk_window_get_group ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#52 0x00002b2baf1c348a in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
#53 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
#54 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#55 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
#56 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#57 0x00002b2bae2b6403 in gtk_window_get_group ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#58 0x00002b2bae2be9a1 in gtk_window_new ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#59 0x00002b2baf1c348a in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
#60 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
#61 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
#62 0x00002b2baf1d4013 in g_signal_emit () from /usr/lib64/libgobject-2.0.so.0
#63 0x00002b2bae2b05bd in gtk_widget_show ()
   from /usr/lib64/libgtk-x11-2.0.so.0
#64 0x0000000000410fe0 in ?? ()
#65 0x00002b2bb13540c4 in __libc_start_main () from /lib/libc.so.6
#66 0x0000000000408419 in ?? ()
#67 0x00007ffffd9884a8 in ?? ()
#68 0x0000000000000000 in ?? ()

Thread 1 (Thread 47466680003488 (LWP 7366)):
#0  0x00002b2bb1124eb5 in waitpid () from /lib/libpthread.so.0
No symbol table info available.
#1  0x00002b2bad4d3a07 in gnome_gtk_module_info_get ()
   from /usr/lib64/libgnomeui-2.so.0
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0x00002b2baf698420 in g_list_find () from /usr/lib64/libglib-2.0.so.0
No symbol table info available.
#4  0x00002b2baf1c836d in g_object_newv () from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#5  0x00002b2baf1c8bee in g_object_new_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#6  0x00002b2baf1c8d91 in g_object_new () from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#7  0x00002b2bae7c07ba in gdk_pixbuf_new_from_data ()
   from /usr/lib64/libgdk_pixbuf-2.0.so.0
No symbol table info available.
#8  0x00002b2bae176864 in _gtk_icon_cache_get_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0x00002b2bae17c73e in gtk_icon_theme_lookup_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0x00002b2bae17ca07 in gtk_icon_theme_load_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0x00002b2bae1795ac in gtk_icon_set_render_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0x00002b2bae2b03ba in gtk_widget_render_icon ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#13 0x00002b2bae18bc91 in gtk_image_new_from_pixmap ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#14 0x00002b2bae18bcb9 in gtk_image_new_from_pixmap ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#15 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#16 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#17 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#18 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#19 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#20 0x00002b2bae17186e in gtk_hbox_new () from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#22 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#23 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#24 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#25 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#26 0x00002b2bae0e6869 in gtk_alignment_new ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#27 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#28 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#29 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#30 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#31 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#32 0x00002b2bae0f2aa2 in gtk_button_set_alignment ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#33 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#34 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#35 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#36 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#37 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#38 0x00002b2bae0eb98e in _gtk_button_box_child_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#39 0x00002b2bae170fe8 in gtk_hbutton_box_new ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#40 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#41 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#42 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#43 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#44 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#45 0x00002b2bae2a712e in gtk_vbox_new () from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#46 0x00002b2baf1c3540 in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#47 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#48 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#49 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#50 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#51 0x00002b2bae2b6078 in gtk_window_get_group ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#52 0x00002b2baf1c348a in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#53 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#54 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#55 0x00002b2baf1d7003 in g_signal_emit_by_name ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#56 0x00002b2bae2094ef in _gtk_size_group_compute_requisition ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#57 0x00002b2bae2b6403 in gtk_window_get_group ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#58 0x00002b2bae2be9a1 in gtk_window_new ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#59 0x00002b2baf1c348a in g_closure_invoke ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#60 0x00002b2baf1d2e58 in g_signal_chain_from_overridden ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#61 0x00002b2baf1d3e43 in g_signal_emit_valist ()
   from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#62 0x00002b2baf1d4013 in g_signal_emit () from /usr/lib64/libgobject-2.0.so.0
No symbol table info available.
#63 0x00002b2bae2b05bd in gtk_widget_show ()
   from /usr/lib64/libgtk-x11-2.0.so.0
No symbol table info available.
#64 0x0000000000410fe0 in ?? ()
No symbol table info available.
#65 0x00002b2bb13540c4 in __libc_start_main () from /lib/libc.so.6
No symbol table info available.
#66 0x0000000000408419 in ?? ()
No symbol table info available.
#67 0x00007ffffd9884a8 in ?? ()
No symbol table info available.
#68 0x0000000000000000 in ?? ()
No symbol table info available.
#0  0x00002b2bb1124eb5 in waitpid () from /lib/libpthread.so.0

---

### Post by tom_adams on 2006-12-22
new info ...
I reloaded what I think were the proper packages .. and network-admin is still busted.

I found 2 workarounds:

1.   I launched network-admin via  "gksu network-admin" and the applet worked.   The only info returned to the gksu screen is  the following  (which could be normal):

(network-admin:5126): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

2.  I launched network-admin via "sudo network-admin" and it works.

Any thoughts on the underlying cause ?

---

### Post by montag on 2006-12-24
Exactly the same problem here!
Running with sudo is ok, but I would like to solve the problem instead of using a work around...
Maybe the problem started after the last apt-get upgrade (but I'm not so sure).

Byez!

---

### Post by montag on 2006-12-24
Reading [this]("http://www.ubuntuforums.org/showthread.php?t=294955") post recalled me that I've added an host just two days ago. Removing this from /etc/host did the trick, network-admin it's now working again.
The problem is that adding a line to this file via either network-admin or nano makes network-admin fail to start.
Maybe it's a (big) known bug?
I'll further investigate... ;)

---

### Post by montag on 2006-12-24
I think it is this bug:
[https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/67936](https://launchpad.net/distros/ubuntu/+source/gnome-system-tools/+bug/67936)

---

