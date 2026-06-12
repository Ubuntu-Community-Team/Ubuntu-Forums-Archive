---
title: "wireless error"
date: 2007-09-15
forum: Networking &amp; Wireless
---

### Post by Seeker84 on 2007-09-15
I'm Using Edgy Eft on Dell Inspiron 700m

I was getting onto my wireless network at home, and when I finally did I got this error:

Memory status: size: 70545408 vsize: 0 resident: 70545408 share: 0 rss: 13758464 rss_rlim: 0
CPU usage: start_time: 1189868650 rtime: 0 utime: 125 stime: 0 cutime:119 cstime: 0 timeout: 6 it_real_value: 0 frequency: 0

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
[New Thread -1225836880 (LWP 5515)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
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
#1  0xb7307323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7e9b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0x082c9ef0 in ?? ()
#5  0xb766d79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#6  0xb767db93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
#7  0xb767f0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#8  0xb767f279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#9  0xb7a4c0f1 in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#10 0xb7b46d41 in gtk_widget_hide () from /usr/lib/libgtk-x11-2.0.so.0
#11 0xb7b53006 in _gtk_window_unset_focus_and_default ()
   from /usr/lib/libgtk-x11-2.0.so.0
#12 0xb766fe30 in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
#13 0xb7a4bdfe in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#14 0xb7b46f25 in gtk_widget_destroy () from /usr/lib/libgtk-x11-2.0.so.0
#15 0xb7a262d9 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#16 0xb78af7ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
#17 0xb75a3802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#18 0xb75a67df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
#19 0xb75a6b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#20 0xb7a26574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#21 0x08057ecd in ?? ()
#22 0x080d2000 in ?? ()
#23 0x08094cc0 in ?? ()
#24 0x08054d50 in ?? ()
#25 0x00000000 in ?? ()

Thread 1 (Thread -1225836880 (LWP 5515)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb7307323 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7e9b1b6 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x082c9ef0 in ?? ()
No symbol table info available.
#5  0xb766d79b in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#6  0xb767db93 in g_signal_chain_from_overridden ()
   from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#7  0xb767f0b7 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#8  0xb767f279 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#9  0xb7a4c0f1 in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#10 0xb7b46d41 in gtk_widget_hide () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#11 0xb7b53006 in _gtk_window_unset_focus_and_default ()
   from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#12 0xb766fe30 in g_object_run_dispose () from /usr/lib/libgobject-2.0.so.0
No symbol table info available.
#13 0xb7a4bdfe in gtk_object_destroy () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#14 0xb7b46f25 in gtk_widget_destroy () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#15 0xb7a262d9 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#16 0xb78af7ea in _gdk_events_init () from /usr/lib/libgdk-x11-2.0.so.0
No symbol table info available.
#17 0xb75a3802 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#18 0xb75a67df in g_main_context_check () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#19 0xb75a6b89 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
No symbol table info available.
#20 0xb7a26574 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
No symbol table info available.
#21 0x08057ecd in ?? ()
No symbol table info available.
#22 0x080d2000 in ?? ()
No symbol table info available.
#23 0x08094cc0 in ?? ()
No symbol table info available.
#24 0x08054d50 in ?? ()
No symbol table info available.
#25 0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()

---

