---
title: "slow loading shared folders"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by madmax69 on 2007-04-06
What is the reason for shared ms folders to take so long to load using the file browser

ftp seems ok and if i use XP on the same PC it loads them nice and fast also i have anothe PC and two xboxes with XBMC that load them fine as well ???

another problem also is that amarok and a few other media programes seems to crash when trying to open an mp3 off the network
but media player is ok ?????

---

### Post by madmax69 on 2007-04-06
amarok error log

Amarok has crashed! We are terribly sorry about this :(

But, all is not lost! You could potentially help us fix the crash. Information describing the crash is below, so just click send, or if you have time, write a brief description of how the crash happened first.

Many thanks.







The information below is to help the developers identify the problem, please do not modify it.



======== DEBUG INFORMATION  =======
Version:    1.4.3
Engine:     xine-engine
Build date: Oct 15 2006
CC version: 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)
KDElibs:    3.5.5
Qt:         3.3.6
TagLib:     1.4.0
CPU count:  1
NDEBUG:     true
==== file /usr/lib/amarok/amarokapp =======
/usr/lib/amarok/amarokapp: symbolic link to `/usr/bin/amarokapp'


==== (gdb) bt =====================
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
[Thread debugging using libthread_db enabled]
[New Thread -1248790032 (LWP 23657)]
[New Thread -1296741472 (LWP 23689)]
[New Thread -1288348768 (LWP 23688)]
[New Thread -1278067808 (LWP 23687)]
[New Thread -1252369504 (LWP 23686)]
[New Thread -1260762208 (LWP 23685)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d7134b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d161 in amaroK::Crash::crashHandler ()
#3  <signal handler called>
#4  0x00000000 in ?? ()
#5  0xb42aca70 in _x_rip_plugin_get_instance () from /usr/lib/libxine.so.1
#6  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb6d7134b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0x0804d161 in amaroK::Crash::crashHandler ()
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0x00000000 in ?? ()
No symbol table info available.
#5  0xb42aca70 in _x_rip_plugin_get_instance () from /usr/lib/libxine.so.1
No symbol table info available.
#6  0x00000000 in ?? ()
No symbol table info available.
==== (gdb) thread apply all bt ====
Thread 6 (Thread -1260762208 (LWP 23685)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d6da8c in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb428bdff in _x_metronom_init () from /usr/lib/libxine.so.1
#3  0xb4da445c in ?? ()
#4  0xb4da4464 in ?? ()
#5  0x08678308 in ?? ()
#6  0xb4da445c in ?? ()
#7  0x12d8be48 in ?? ()
#8  0x00000000 in ?? ()
Thread 5 (Thread -1252369504 (LWP 23686)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb69a3803 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb3d6b19f in ?? ()
   from /usr/lib/xine/plugins/1.1.2/xineplug_ao_out_alsa.so
#3  0xb55a53b8 in ?? ()
#4  0x00000001 in ?? ()
#5  0x0000014d in ?? ()
#6  0x00000000 in ?? ()
Thread 4 (Thread -1278067808 (LWP 23687)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d6d816 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb429a1d2 in _x_ao_channels2mode () from /usr/lib/libxine.so.1
#3  0x086b15ec in ?? ()
#4  0x086b15d4 in ?? ()
#5  0x00000000 in ?? ()
Thread 3 (Thread -1288348768 (LWP 23688)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d6d816 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb428f4cc in _x_dummy_fifo_buffer_new () from /usr/lib/libxine.so.1
#3  0x087be1ac in ?? ()
#4  0xb4287c1c in xine_init () from /usr/lib/libxine.so.1
#5  0xffffffff in ?? ()
#6  0x087b2638 in ?? ()
#7  0x00000000 in ?? ()
Thread 2 (Thread -1296741472 (LWP 23689)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d6d816 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb429f16c in xine_event_wait () from /usr/lib/libxine.so.1
#3  0x087c64a0 in ?? ()
Thread 1 (Thread -1248790032 (LWP 23657)):
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb6d7134b in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x0804d161 in amaroK::Crash::crashHandler ()
#3  <signal handler called>
#4  0x00000000 in ?? ()
#5  0xb42aca70 in _x_rip_plugin_get_instance () from /usr/lib/libxine.so.1
#6  0x00000000 in ?? ()
#0  0xffffe410 in __kernel_vsyscall ()


==== kdBacktrace() ================

---

