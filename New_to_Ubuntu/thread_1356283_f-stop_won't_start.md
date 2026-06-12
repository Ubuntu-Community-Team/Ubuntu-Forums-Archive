---
title: "f-stop won't start"
date: 2009-12-15
forum: New to Ubuntu
---

### Post by mrabcdefg on 2009-12-15
I just installed Kaola, and F-stop won't start.  Can anyone help?  The following is what happens when I try to start it:

```
[Info  19:22:22.228] Initializing DBus
[Info  19:22:22.506] Initializing Mono.Addins
[Info  19:22:22.906] Starting new FSpot server (f-spot 0.6.1.5)

** (f-spot:2505): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2505): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2505): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2505): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed

** (f-spot:2505): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
[Info  19:22:25.122] Starting BeagleService
[Info  19:22:25.177] Hack for gnome-settings-daemon engaged

(f-spot:2505): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Stacktrace:

  at (wrapper managed-to-native) Gtk.Style.gtk_paint_box (intptr,intptr,int,int,intptr,intptr,intptr,int,int,int,int) <0x00004>
  at (wrapper managed-to-native) Gtk.Style.gtk_paint_box (intptr,intptr,int,int,intptr,intptr,intptr,int,int,int,int) <0xffffffff>
  at Gtk.Style.PaintBox (Gtk.Style,Gdk.Drawable,Gtk.StateType,Gtk.ShadowType,Gdk.Rectangle,Gtk.Widget,string,int,int,int,int) <0x000cd>
  at FSpot.GroupSelector/Limit.Draw (Gdk.Rectangle) <0x00159>
  at FSpot.GroupSelector.OnExposeEvent (Gdk.EventExpose) <0x005f4>
  at Gtk.Widget.exposeevent_cb (intptr,intptr) <0x00069>
  at (wrapper native-to-managed) Gtk.Widget.exposeevent_cb (intptr,intptr) <0xffffffff>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0x00004>
  at (wrapper managed-to-native) Gtk.Application.gtk_main () <0xffffffff>
  at Gtk.Application.Run () <0x0000a>
  at FSpot.Driver.Main (string[]) <0x01a86>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_object (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

    f-spot [0x80c8824]
    f-spot [0x80f4693]
    [0xdce410]
    /lib/tls/i686/cmov/libc.so.6(memcpy+0x46) [0x185006]
    [0x8a39ef0]
    /usr/lib/libgdk-x11-2.0.so.0 [0xe81ca6]
    /usr/lib/libgdk-x11-2.0.so.0 [0xe6f7e9]
    /usr/lib/libgdk-x11-2.0.so.0(gdk_draw_pixbuf+0x13f) [0xe4b72f]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xba1e67]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xba34f0]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xb9fd29]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xba0a49]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_paint_shadow+0xee) [0x29f198e]
    /usr/lib/libgtk-x11-2.0.so.0 [0x29f9ca8]
    /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so [0xba0e95]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_paint_box+0xee) [0x29f144e]
    [0x6033392]
    [0x60332fe]
    [0x6033092]
    [0x603240d]
    [0x6031de2]
    [0x4f8b747]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2973474]
    /usr/lib/libgobject-2.0.so.0 [0x6d86f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd [0x6d9f98]
    /usr/lib/libgobject-2.0.so.0 [0x6ef49e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64 [0x6f09b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6f0fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2a8f96e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x28de683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28de6b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28ab9b5]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x28df1f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28e04aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2973474]
    /usr/lib/libgobject-2.0.so.0 [0x6d86f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd [0x6d9f98]
    /usr/lib/libgobject-2.0.so.0 [0x6ef49e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64 [0x6f09b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6f0fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2a8f96e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x28de683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28de6b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x299a63d]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x28df1f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28e04aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x299d29f]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2973474]
    /usr/lib/libgobject-2.0.so.0 [0x6d86f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd [0x6d9f98]
    /usr/lib/libgobject-2.0.so.0 [0x6ef49e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64 [0x6f09b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6f0fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2a8f96e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x28de683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28de6b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28ab9b5]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x28df1f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28e04aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2973474]
    /usr/lib/libgobject-2.0.so.0 [0x6d86f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd [0x6d9f98]
    /usr/lib/libgobject-2.0.so.0 [0x6ef49e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64 [0x6f09b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6f0fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2a8f96e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x28de683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28de6b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28ab9b5]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x28df1f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28e04aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2973474]
    /usr/lib/libgobject-2.0.so.0 [0x6d86f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0xd [0x6d9f98]
    /usr/lib/libgobject-2.0.so.0 [0x6ef49e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64 [0x6f09b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6f0fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2a8f96e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_propagate_expose+0x1a3) [0x28de683]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28de6b1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28a782d]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_forall+0xa4) [0x28df1f4]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28e04aa]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2aaa6a1]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2973474]
    /usr/lib/libgobject-2.0.so.0 [0x6d86f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x6da072]
    /usr/lib/libgobject-2.0.so.0 [0x6ef49e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x64 [0x6f09b8]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6f0fb6]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2a8f96e]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_main_do_event+0x500) [0x296d190]
    /usr/lib/libgdk-x11-2.0.so.0 [0xe711d4]
    /usr/lib/libgdk-x11-2.0.so.0 [0xe94734]
    /usr/lib/libgdk-x11-2.0.so.0 [0xe6887f]
    /usr/lib/libgdk-x11-2.0.so.0(gdk_window_process_updates+0x150) [0xe6ca50]
    /usr/lib/libgtk-x11-2.0.so.0 [0x2aaa273]
    /usr/lib/libgobject-2.0.so.0(g_cclosure_marshal_VOID__VOID+0x7c) [0x6e79fc]
    /usr/lib/libgobject-2.0.so.0 [0x6d86f9]
    /usr/lib/libgobject-2.0.so.0(g_closure_invoke+0x1b2) [0x6da072]
    /usr/lib/libgobject-2.0.so.0 [0x6ef49e]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit_valist+0x7bd) [0x6f0b2d]
    /usr/lib/libgobject-2.0.so.0(g_signal_emit+0x26) [0x6f0fb6]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_container_check_resize+0x8a) [0x28df31a]
    /usr/lib/libgtk-x11-2.0.so.0 [0x28df370]
    /usr/lib/libgdk-x11-2.0.so.0 [0xe46f78]
    /lib/libglib-2.0.so.0 [0x3f60f1]
    /lib/libglib-2.0.so.0(g_main_context_dispatch+0x1f [0x3f7e78]
    /lib/libglib-2.0.so.0 [0x3fb720]
    /lib/libglib-2.0.so.0(g_main_loop_run+0x1bf) [0x3fbb8f]
    /usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9) [0x296d419]
    [0x5b17c50]
    [0x5b17c13]
    [0x2d6d6f]
    [0x2d5203]
    f-spot(mono_runtime_exec_main+0x15b) [0x811132b]
    f-spot(mono_runtime_run_main+0x15a) [0x81134da]
    f-spot(mono_main+0x1aad) [0x80b19bd]
    f-spot [0x805aba5]
    /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6) [0x126b56]
    f-spot [0x805aae1]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
[New Thread 0x1be1b70 (LWP 2512)]
[New Thread 0x1ae0b70 (LWP 2511)]
[New Thread 0x40e5b70 (LWP 2509)]
[New Thread 0xa48b70 (LWP 2507)]
[New Thread 0xb1bb70 (LWP 2506)]
0x00dce422 in __kernel_vsyscall ()
  6 Thread 0xb1bb70 (LWP 2506)  0x00dce422 in __kernel_vsyscall ()
  5 Thread 0xa48b70 (LWP 2507)  0x00dce422 in __kernel_vsyscall ()
  4 Thread 0x40e5b70 (LWP 2509)  0x00dce422 in __kernel_vsyscall ()
  3 Thread 0x1ae0b70 (LWP 2511)  0x00dce422 in __kernel_vsyscall ()
  2 Thread 0x1be1b70 (LWP 2512)  0x00dce422 in __kernel_vsyscall ()
* 1 Thread 0x6ce6f0 (LWP 2505)  0x00dce422 in __kernel_vsyscall ()

Thread 6 (Thread 0xb1bb70 (LWP 2506)):
#0  0x00dce422 in __kernel_vsyscall ()
#1  0x00ab3466 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a3658 in ?? ()
#3  0x00aab80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0x001dc7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xa48b70 (LWP 2507)):
#0  0x00dce422 in __kernel_vsyscall ()
#1  0x00ab1f75 in sem_wait@@GLIBC_2.1 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0812bb29 in ?? ()
#3  0x0814f96c in ?? ()
#4  0x081bf9f2 in ?? ()
#5  0x081de055 in ?? ()
#6  0x00aab80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0x001dc7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0x40e5b70 (LWP 2509)):
#0  0x00dce422 in __kernel_vsyscall ()
#1  0x00aafe15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a84f4 in ?? ()
#4  0x081c3dcf in ?? ()
#5  0x0814c923 in ?? ()
#6  0x00e1524d in ?? ()
#7  0x00e14fad in ?? ()
#8  0x00e14ec1 in ?? ()
#9  0x002e3f90 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x00aab80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x001dc7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0x1ae0b70 (LWP 2511)):
#0  0x00dce422 in __kernel_vsyscall ()
#1  0x00aafe15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a84f4 in ?? ()
#4  0x081c3dcf in ?? ()
#5  0x0814b189 in ?? ()
#6  0x017b85d8 in ?? ()
#7  0x017b84d3 in ?? ()
#8  0x017b838c in ?? ()
#9  0x002e3f90 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x00aab80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x001dc7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0x1be1b70 (LWP 2512)):
#0  0x00dce422 in __kernel_vsyscall ()
#1  0x00aafe15 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081a843b in ?? ()
#3  0x081a84f4 in ?? ()
#4  0x081c3dcf in ?? ()
#5  0x0814b189 in ?? ()
#6  0x017b85d8 in ?? ()
#7  0x017b84d3 in ?? ()
#8  0x017b8781 in ?? ()
#9  0x002e3f90 in ?? ()
#10 0x0810e6a4 in mono_runtime_delegate_invoke ()
#11 0x0814f9d7 in ?? ()
#12 0x081bf9f2 in ?? ()
#13 0x081de055 in ?? ()
#14 0x00aab80e in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#15 0x001dc7ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0x6ce6f0 (LWP 2505)):
#0  0x00dce422 in __kernel_vsyscall ()
#1  0x00ab2c8b in read () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x080c89be in ?? ()
#3  0x080f4693 in ?? ()
#4  <signal handler called>
#5  0x00185006 in memcpy () from /lib/tls/i686/cmov/libc.so.6
#6  0x08a39ef0 in ?? ()
#7  0x00e81ca6 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#8  0x00e6f7e9 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#9  0x00e4b72f in gdk_draw_pixbuf () from /usr/lib/libgdk-x11-2.0.so.0
#10 0x00ba1e67 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#11 0x00ba34f0 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#12 0x00b9fd29 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#13 0x00ba0a49 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#14 0x029f198e in gtk_paint_shadow () from /usr/lib/libgtk-x11-2.0.so.0
#15 0x029f9ca8 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#16 0x00ba0e95 in ?? () from /usr/lib/gtk-2.0/2.10.0/engines/libpixmap.so
#17 0x029f144e in gtk_paint_box () from /usr/lib/libgtk-x11-2.0.so.0
#18 0x06033392 in ?? ()
#19 0x060332fe in ?? ()
#20 0x06033092 in ?? ()
#21 0x0603240d in ?? ()
#22 0x06031de2 in ?? ()
#23 0x04f8b747 in ?? ()
#24 0x02973474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#25 0x006d86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#26 0x006d9f98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#27 0x006ef49e in ?? () from /usr/lib/libgobject-2.0.so.0
#28 0x006f09b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#29 0x006f0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#30 0x02a8f96e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#31 0x028de683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#32 0x028de6b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#33 0x028ab9b5 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#34 0x028df1f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#35 0x028e04aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#36 0x02973474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#37 0x006d86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#38 0x006d9f98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#39 0x006ef49e in ?? () from /usr/lib/libgobject-2.0.so.0
#40 0x006f09b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#41 0x006f0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#42 0x02a8f96e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#43 0x028de683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#44 0x028de6b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#45 0x0299a63d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#46 0x028df1f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#47 0x028e04aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#48 0x0299d29f in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#49 0x02973474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#50 0x006d86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#51 0x006d9f98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#52 0x006ef49e in ?? () from /usr/lib/libgobject-2.0.so.0
#53 0x006f09b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#54 0x006f0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#55 0x02a8f96e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#56 0x028de683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#57 0x028de6b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#58 0x028ab9b5 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#59 0x028df1f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#60 0x028e04aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#61 0x02973474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#62 0x006d86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#63 0x006d9f98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#64 0x006ef49e in ?? () from /usr/lib/libgobject-2.0.so.0
#65 0x006f09b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#66 0x006f0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#67 0x02a8f96e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#68 0x028de683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#69 0x028de6b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#70 0x028ab9b5 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#71 0x028df1f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#72 0x028e04aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#73 0x02973474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#74 0x006d86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#75 0x006d9f98 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#76 0x006ef49e in ?? () from /usr/lib/libgobject-2.0.so.0
#77 0x006f09b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#78 0x006f0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#79 0x02a8f96e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#80 0x028de683 in gtk_container_propagate_expose ()
   from /usr/lib/libgtk-x11-2.0.so.0
#81 0x028de6b1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#82 0x028a782d in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#83 0x028df1f4 in gtk_container_forall () from /usr/lib/libgtk-x11-2.0.so.0
#84 0x028e04aa in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#85 0x02aaa6a1 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#86 0x02973474 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#87 0x006d86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#88 0x006da072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#89 0x006ef49e in ?? () from /usr/lib/libgobject-2.0.so.0
#90 0x006f09b8 in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#91 0x006f0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#92 0x02a8f96e in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#93 0x0296d190 in gtk_main_do_event () from /usr/lib/libgtk-x11-2.0.so.0
#94 0x00e711d4 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#95 0x00e94734 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#96 0x00e6887f in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#97 0x00e6ca50 in gdk_window_process_updates ()
   from /usr/lib/libgdk-x11-2.0.so.0
#98 0x02aaa273 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#99 0x006e79fc in g_cclosure_marshal_VOID__VOID ()
   from /usr/lib/libgobject-2.0.so.0
#100 0x006d86f9 in ?? () from /usr/lib/libgobject-2.0.so.0
#101 0x006da072 in g_closure_invoke () from /usr/lib/libgobject-2.0.so.0
#102 0x006ef49e in ?? () from /usr/lib/libgobject-2.0.so.0
#103 0x006f0b2d in g_signal_emit_valist () from /usr/lib/libgobject-2.0.so.0
#104 0x006f0fb6 in g_signal_emit () from /usr/lib/libgobject-2.0.so.0
#105 0x028df31a in gtk_container_check_resize ()
   from /usr/lib/libgtk-x11-2.0.so.0
#106 0x028df370 in ?? () from /usr/lib/libgtk-x11-2.0.so.0
#107 0x00e46f78 in ?? () from /usr/lib/libgdk-x11-2.0.so.0
#108 0x003f60f1 in ?? () from /lib/libglib-2.0.so.0
#109 0x003f7e78 in g_main_context_dispatch () from /lib/libglib-2.0.so.0
#110 0x003fb720 in ?? () from /lib/libglib-2.0.so.0
#111 0x003fbb8f in g_main_loop_run () from /lib/libglib-2.0.so.0
#112 0x0296d419 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#113 0x05b17c50 in ?? ()
#114 0x05b17c13 in ?? ()
#115 0x002d6d6f in ?? ()
#116 0x002d5203 in ?? ()
#117 0x0811132b in mono_runtime_exec_main ()
#118 0x081134da in mono_runtime_run_main ()
#119 0x080b19bd in mono_main ()
#120 0x0805aba5 in ?? ()
#121 0x00126b56 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#122 0x0805aae1 in ?? ()

=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================
```

---

### Post by lavinog on 2009-12-18
it might be a corrupted install.
Try removing it with synaptic and reinstalling.

---

