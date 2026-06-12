---
title: "network-admin gone bad"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by angelot on 2007-02-27
This is from bug-buddy:

```
Memory status: size: 33161216 vsize: 0 resident: 33161216 share: 0 rss: 12091392 rss_rlim: 0
CPU usage: start_time: 1172580787 rtime: 0 utime: 36 stime: 0 cutime:34 cstime: 0 timeout: 2 it_real_value: 0 frequency: 0

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
[New Thread -1225648464 (LWP 6396)]
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
#1  0xb7335323 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7ec91b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7a9cf6a in gtk_rc_style_unref () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb7a9d573 in gtk_rc_get_style () from /usr/lib/libgtk-x11-2.0.so.0
#6  0xb7b730b0 in gtk_widget_set_usize () from /usr/lib/libgtk-x11-2.0.so.0
#7  0xb7abdcd7 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#8  0xb7abdf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#9  0xb7b72b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#10 0xb79847c4 in _gtk_button_box_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7a17710 in gtk_hbutton_box_new () from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb76a8199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#13 0xb7699fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#14 0xb769b87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#15 0xb76ac02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#16 0xb76ad0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#17 0xb76afe9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#18 0xb7abdcf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#19 0xb7abdf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#20 0xb7b72b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#21 0xb7b69450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
#22 0xb76a8199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#23 0xb7699fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#24 0xb769b87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#25 0xb76ac02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#26 0xb76ad0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#27 0xb76afe9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#28 0xb7abdcf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#29 0xb7abdf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#30 0xb7b72b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#31 0xb7b7a990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#32 0xb76a8199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
#33 0xb7699fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#34 0xb769b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#35 0xb76ac02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#36 0xb76ad0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#37 0xb76afe9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
#38 0xb7abdcf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#39 0xb7abdf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
#40 0xb7b72b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
#41 0xb7b7ad10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
#42 0xb7b83fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
#43 0xb76a8b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#44 0xb7699fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
#45 0xb769b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#46 0xb76ac02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#47 0xb76ad0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#48 0xb76ad279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#49 0xb7b73b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
#50 0x08057f19 in ?? ()
#51 0x08100818 in ?? ()
#52 0x08096748 in ?? ()
#53 0x08054d50 in ?? ()
#54 0x00000000 in ?? ()

Thread 1 (Thread -1225648464 (LWP 6396)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7335323 in __waitpid_nocancel () from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7ec91b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7a9cf6a in gtk_rc_style_unref () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#5  0xb7a9d573 in gtk_rc_get_style () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#6  0xb7b730b0 in gtk_widget_set_usize () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#7  0xb7abdcd7 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#8  0xb7abdf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#9  0xb7b72b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0xb79847c4 in _gtk_button_box_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7a17710 in gtk_hbutton_box_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb76a8199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb7699fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#14 0xb769b87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#15 0xb76ac02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#16 0xb76ad0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#17 0xb76afe9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#18 0xb7abdcf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#19 0xb7abdf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#20 0xb7b72b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0xb7b69450 in gtk_vbox_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#22 0xb76a8199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#23 0xb7699fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#24 0xb769b87d in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#25 0xb76ac02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#26 0xb76ad0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#27 0xb76afe9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#28 0xb7abdcf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#29 0xb7abdf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#30 0xb7b72b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#31 0xb7b7a990 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#32 0xb76a8199 in g_cclosure_marshal_VOID__BOXED ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#33 0xb7699fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#34 0xb769b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#35 0xb76ac02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#36 0xb76ad0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#37 0xb76afe9e in g_signal_emit_by_name () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#38 0xb7abdcf6 in _gtk_size_group_get_child_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#39 0xb7abdf4a in _gtk_size_group_compute_requisition ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#40 0xb7b72b2c in gtk_widget_size_request () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#41 0xb7b7ad10 in gtk_window_get_group () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#42 0xb7b83fc1 in gtk_window_new () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#43 0xb76a8b29 in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#44 0xb7699fb9 in g_value_set_boxed () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#45 0xb769b79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#46 0xb76ac02a in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#47 0xb76ad0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#48 0xb76ad279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#49 0xb7b73b18 in gtk_widget_show () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#50 0x08057f19 in ?? ()
No symbol table info available.
#51 0x08100818 in ?? ()
No symbol table info available.
#52 0x08096748 in ?? ()
No symbol table info available.
#53 0x08054d50 in ?? ()
No symbol table info available.
#54 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
```

Network is up and /etc/network/interfaces are configured correctly. I just can't get network admin to start....

---

### Post by jazzgossen on 2007-03-05
I have a similar problem with network-admin. The network is working (mostly) but network-admin crashes no matter how I start it (from menu, from terminal, with sudo or gksudo...). I filed a bug on it [here]("http://http://bugzilla.gnome.org/show_bug.cgi?id=407803"), and apparently it's solved in the newest version of gnome-system-tools. However, that doesn't seem to be available for 6.10. I tried to compile it, but there are a number of unmet dependencies. 

If anybody knows of a workaround for Edgy, I'd be very grateful.

It all started after I fiddled with /etc/network/interfaces and stuff. I think I've restored the interfaces file to its original state, but network-admin still crashes.

---

### Post by jimchristiansen on 2007-03-05
OK,  I'm running Edgy 32 bit on a DellM65.  Running great since install but I've just recently moved it to another docking station at another location and when I went to change my network location using network-admin found out that it had quit working...  The last time I changed locations and used it was more than a week ago.  Here are the errors from the Bug Reporting tool:

Any ideas??

Thanks

===================Log Details ====================
Memory status: size: 30412800 vsize: 0 resident: 30412800 share: 0 rss: 11587584 rss_rlim: 0
CPU usage: start_time: 1173147907 rtime: 0 utime: 22 stime: 0 cutime:21 cstime: 0 timeout: 1 it_real_value: 0 frequency: 0

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
[New Thread -1225427280 (LWP 5491)]
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
0xb7355bfe in __waitpid_nocancel () from /lib/libpthread.so.0
#0  0xb7355bfe in __waitpid_nocancel () from /lib/libpthread.so.0
#1  0xb7ee71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#2  <signal handler called>
#3  0xb76068f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
#4  0xb75ed5d6 in g_list_prepend () from /usr/lib/libglib-2.0.so.0
#5  0xb75e901f in g_key_file_to_data () from /usr/lib/libglib-2.0.so.0
#6  0xb75ebada in g_key_file_get_keys () from /usr/lib/libglib-2.0.so.0
#7  0xb75ebe40 in g_key_file_get_keys () from /usr/lib/libglib-2.0.so.0
#8  0xb75ec185 in g_key_file_load_from_data () from /usr/lib/libglib-2.0.so.0
#9  0xb75ec6e7 in g_key_file_load_from_file () from /usr/lib/libglib-2.0.so.0
#10 0x0804fabe in ?? ()
#11 0x0826c028 in ?? ()
#12 0x0826d5b0 in ?? ()
#13 0x00000000 in ?? ()

Thread 1 (Thread -1225427280 (LWP 5491)):
#0  0xb7355bfe in __waitpid_nocancel () from /lib/libpthread.so.0
No symbol table info available.
#1  0xb7ee71b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#2  <signal handler called>
No symbol table info available.
#3  0xb76068f0 in g_slice_alloc () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#4  0xb75ed5d6 in g_list_prepend () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#5  0xb75e901f in g_key_file_to_data () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#6  0xb75ebada in g_key_file_get_keys () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#7  0xb75ebe40 in g_key_file_get_keys () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#8  0xb75ec185 in g_key_file_load_from_data () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#9  0xb75ec6e7 in g_key_file_load_from_file () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#10 0x0804fabe in ?? ()
No symbol table info available.
#11 0x0826c028 in ?? ()
No symbol table info available.
#12 0x0826d5b0 in ?? ()
No symbol table info available.
#13 0x00000000 in ?? ()
No symbol table info available.
#0  0xb7355bfe in __waitpid_nocancel () from /lib/libpthread.so.0

---

### Post by jazzgossen on 2007-03-06
I just fixed my problem by also restoring the /etc/resolv.conf file. So if you have backups of /etc/resolv.conf, /etc/hosts and /etc/network/interfaces, you should try restoring those. If network-admin still doesn't work, I don't know what to do. Or, if you can find a way to install gnome-system-tools version 2.17.91 or later, that might help, as said in the bug report I linked to above.

---

### Post by jimchristiansen on 2007-03-06
How do I down-grade the gnome-system-tools to the version that I had before network-admin went bad??

I had to down-grade beryl a month ago or so due to upgrading to a newer non-working version.  I found the working packages listed by some guru in this forum.

I guess I should be asking where do I find a slightly older version and working version??

Thanks,  Jim

---

### Post by jimchristiansen on 2007-03-06
OK, after some reading about similar troubles other people were having I commented out the additions that I made to my hosts file.  Network-admin fires right up as happy as ever...   Soooo... if you're having troubles check out the /etc/hosts file and put it back to stock.  Good luck!

---

