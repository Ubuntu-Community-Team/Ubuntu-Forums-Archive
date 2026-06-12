---
title: "F-Spot Will Not Run"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by silverwolf636 on 2010-01-17
If I attempt to run F-Spot, it shuts down. This is what I get with running from the terminal:
Starting new FSpot server
libGL error: UNIX signal already caught!f-spot: ../../src/xcb_io.c:285: _XAllocID: Assertion `!(dpy->flags & (1L << 3))' failed.
```
Stacktrace:

  at (wrapper managed-to-native) Gdk.Colormap.gdk_colormap_new (intptr,bool) <0x00004>
  at (wrapper managed-to-native) Gdk.Colormap.gdk_colormap_new (intptr,bool) <0xffffffff>
  at Gdk.Colormap..ctor (Gdk.Visual,bool) <0x0005b>
  at GdkGlx.Context.GetColormap () <0x0001e>
  at FSpot.PhotoImageView.HandleRealized (object,System.EventArgs) <0x00076>
  at FSpot.PhotoImageView..ctor (FSpot.BrowsablePointer) <0x0014f>
  at FSpot.PhotoView..ctor (FSpot.IBrowsableCollection) <0x00278>
  at MainWindow..ctor (Db) <0x01963>
  at FSpot.Core.get_MainWindow () <0x00035>
  at FSpot.Core.Organize () <0x0000f>
  at FSpot.Driver.Main (string[]) <0x00f7a>
  at (wrapper runtime-invoke) FSpot.Driver.runtime_invoke_int_string[] (object,intptr,intptr,intptr) <0xffffffff>

Native stacktrace:

	f-spot [0x816b20a]
	[0xb7f21440]
	/lib/tls/i686/cmov/libc.so.6(abort+0x101) [0xb7ce0a01]
	/lib/tls/i686/cmov/libc.so.6(__assert_fail+0xee) [0xb7cd810e]
	/usr/lib/libX11.so.6 [0xb61d4929]
	/usr/lib/libX11.so.6(XCreateColormap+0x58) [0xb61aaea8]
	/usr/lib/libgdk-x11-2.0.so.0(gdk_colormap_new+0x2cb) [0xb65f2e9b]
	[0xb429dd48]
	[0xb429dc44]
	[0xb429dbcf]
	[0xb429d147]
	[0xb429c230]
	[0xb429a8f9]
	[0xb5837cc4]
	[0xb5835d5e]
	[0xb5835cf0]
	[0xb7797773]
	[0xb77961c4]
	f-spot(mono_runtime_exec_main+0x10e) [0x809c68e]
	f-spot(mono_runtime_run_main+0x173) [0x809c933]
	f-spot(mono_main+0x6a9) [0x805acd9]
	f-spot [0x805a122]
	/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb7cca450]
	f-spot [0x805a091]

Debug info from gdb:

(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb7c8b6d0 (LWP 8736)]
[New Thread 0xb43aab90 (LWP 8744)]
[New Thread 0xb44afb90 (LWP 8743)]
[New Thread 0xb5944b90 (LWP 8740)]
[New Thread 0xb7213b90 (LWP 8738)]
[New Thread 0xb7795b90 (LWP 8737)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
0xb7f21410 in __kernel_vsyscall ()
  6 Thread 0xb7795b90 (LWP 8737)  0xb7f21410 in __kernel_vsyscall ()
  5 Thread 0xb7213b90 (LWP 8738)  0xb7f21410 in __kernel_vsyscall ()
  4 Thread 0xb5944b90 (LWP 8740)  0xb7f21410 in __kernel_vsyscall ()
  3 Thread 0xb44afb90 (LWP 8743)  0xb7f21410 in __kernel_vsyscall ()
  2 Thread 0xb43aab90 (LWP 8744)  0xb7f21410 in __kernel_vsyscall ()
  1 Thread 0xb7c8b6d0 (LWP 8736)  0xb7f21410 in __kernel_vsyscall ()

Thread 6 (Thread 0xb7795b90 (LWP 8737)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7e35196 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08105c91 in ?? ()
#3  0xb7e2d4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7d8ae5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb7213b90 (LWP 8738)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7e31aa5 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ff in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080b1c0a in ?? ()
#7  0x080cef04 in ?? ()
#8  0x0811a7c2 in ?? ()
#9  0x081317b5 in ?? ()
#10 0xb7e2d4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7d8ae5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb5944b90 (LWP 8740)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7e31dd2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ba in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080cca8e in ?? ()
#7  0xb5aef0e2 in ?? ()
#8  0xb5aeeed3 in ?? ()
#9  0xb5aedc43 in ?? ()
#10 0xb5aedac2 in ?? ()
#11 0xb7799fc9 in ?? ()
#12 0x08095ea4 in mono_runtime_delegate_invoke ()
#13 0x080cef6e in ?? ()
#14 0x0811a7c2 in ?? ()
#15 0x081317b5 in ?? ()
#16 0xb7e2d4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#17 0xb7d8ae5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb44afb90 (LWP 8743)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7e31dd2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ba in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080cbc7e in ?? ()
#7  0xb44bfbda in ?? ()
#8  0xb44bfabe in ?? ()
#9  0xb44bf9e0 in ?? ()
#10 0xb5aedac2 in ?? ()
#11 0xb7799fc9 in ?? ()
#12 0x08095ea4 in mono_runtime_delegate_invoke ()
#13 0x080cef6e in ?? ()
#14 0x0811a7c2 in ?? ()
#15 0x081317b5 in ?? ()
#16 0xb7e2d4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#17 0xb7d8ae5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb43aab90 (LWP 8744)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7e31dd2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081088ba in ?? ()
#3  0x0810b3cd in ?? ()
#4  0x0810b43c in ?? ()
#5  0x0811ba1a in ?? ()
#6  0x080cbc7e in ?? ()
#7  0xb44bfbda in ?? ()
#8  0xb44bfabe in ?? ()
#9  0xb44bfda6 in ?? ()
#10 0xb5aedac2 in ?? ()
#11 0xb7799fc9 in ?? ()
#12 0x08095ea4 in mono_runtime_delegate_invoke ()
#13 0x080cef6e in ?? ()
#14 0x0811a7c2 in ?? ()
#15 0x081317b5 in ?? ()
#16 0xb7e2d4fb in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#17 0xb7d8ae5e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7c8b6d0 (LWP 8736)):
#0  0xb7f21410 in __kernel_vsyscall ()
#1  0xb7d83881 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eb21d4 in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7eb259c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0816b2a5 in ?? ()
#5  <signal handler called>
#6  0xb7f21410 in __kernel_vsyscall ()
#7  0xb7cdf085 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb7ce0a01 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7cd810e in __assert_fail () from /lib/tls/i686/cmov/libc.so.6
#10 0xb61d4929 in _XAllocID () from /usr/lib/libX11.so.6
#11 0xb61aaea8 in XCreateColormap () from /usr/lib/libX11.so.6
#12 0xb65f2e9b in gdk_colormap_new () from /usr/lib/libgdk-x11-2.0.so.0
#13 0xb429dd48 in ?? ()
#14 0xb429dc44 in ?? ()
#15 0xb429dbcf in ?? ()
#16 0xb429d147 in ?? ()
#17 0xb429c230 in ?? ()
#18 0xb429a8f9 in ?? ()
#19 0xb5837cc4 in ?? ()
#20 0xb5835d5e in ?? ()
#21 0xb5835cf0 in ?? ()
#22 0xb7797773 in ?? ()
#23 0xb77961c4 in ?? ()
#24 0x0809c68e in mono_runtime_exec_main ()
#25 0x0809c933 in mono_runtime_run_main ()
#26 0x0805acd9 in mono_main ()
#27 0x0805a122 in ?? ()
#28 0xb7cca450 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#29 0x0805a091 in ?? ()
#0  0xb7f21410 in __kernel_vsyscall ()


=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted
```

---

### Post by Baelus on 2010-01-19
There's this:

[https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/393367]("https://bugs.launchpad.net/ubuntu/+source/f-spot/+bug/393367")

It looks like the same error, but nobody checked into the bug.

Something else:

[http://ubuntuforums.org/showthread.php?t=354810]("http://ubuntuforums.org/showthread.php?t=354810")

There's a fix in post #2.

Bear in mind, it's from 2007 and running F-Spot on Feisty, so I don't know if this will even apply to your situation. I'm just going from the "LibGL error" at the beginning of the error report.

---

### Post by silverwolf636 on 2010-01-20
Thanx for your reply.  So far none of that has worked but I'm still trying.

---

### Post by wojox on 2010-01-20
That's interesting. I read the bug report and their like upgrade to 9.04 or 9.10. Seems odd.

---

### Post by TnTMike on 2010-01-23
There have been a number of posts about this problem. The same thing was happening to me try thread [http://ubuntuforums.org/showthread.php?t=1307641&highlight=f-spot]("http://ubuntuforums.org/showthread.php?t=1307641&highlight=f-spot") suggests a fix that worked for me as well as a few others.
I changed my desktop theme to human from new wave.

---

### Post by no2498 on 2010-01-23
mine works on 804
but my other computer with 910 karmic it wont do a slide show

---

