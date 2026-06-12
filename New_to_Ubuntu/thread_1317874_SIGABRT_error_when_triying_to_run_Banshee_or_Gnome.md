---
title: "SIGABRT error when triying to run Banshee or Gnome-do"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by humphreybc on 2009-11-07
Hi guys,

I'm getting this error when I try to run Banshee or Gnome-do. It has something to do with the mono libraries, so I predict there is some corruption in some of my packages ... just not sure which ones to reinstall to fix it up. Could you please advise?

Banshee:
```

benjamin@benjamin-laptop:~$ banshee

** (/usr/lib/banshee-1/Banshee.exe:2522): CRITICAL **: _wapi_shm_file_open: shared file [/home/benjamin/.wapi/shared_data-benjamin-laptop-Linux-x86_64-328-12-0] open error: Input/output error

** (/usr/lib/banshee-1/Banshee.exe:2522): CRITICAL **: _wapi_shm_attach: shared file [/home/benjamin/.wapi/shared_data-benjamin-laptop-Linux-x86_64-328-12-0] open error
**
ERROR:shared.c:349:shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/banshee-1/Banshee.exe:2522): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/banshee-1/Banshee.exe:2522): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

	banshee-1 [0x47a5ef]
	/lib/libpthread.so.0 [0x7fc7ff1cc190]
	/lib/libc.so.6(gsignal+0x35) [0x7fc7febfd4b5]
	/lib/libc.so.6(abort+0x180) [0x7fc7fec00f50]
	/lib/libglib-2.0.so.0(g_assertion_message+0x120) [0x7fc7ff846540]
	/lib/libglib-2.0.so.0 [0x7fc7ff846ab0]
	banshee-1 [0x56a310]
	banshee-1 [0x557be6]
	banshee-1(mono_once+0x64) [0x5653e4]
	banshee-1 [0x557b53]
	banshee-1 [0x5692c5]
	banshee-1 [0x506dfe]
	banshee-1(mono_runtime_init+0x25) [0x50e9b5]
	banshee-1 [0x419133]
	banshee-1(mono_main+0x417) [0x461f97]
	/lib/libc.so.6(__libc_start_main+0xfd) [0x7fc7febe8abd]
	banshee-1 [0x416e19]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
0x00007fc7ff1cb090 in __read_nocancel () from /lib/libpthread.so.0
* 1 Thread 0x7fc7ffeab730 (LWP 2522)  0x00007fc7ff1cb090 in __read_nocancel ()
   from /lib/libpthread.so.0

Thread 1 (Thread 0x7fc7ffeab730 (LWP 2522)):
#0  0x00007fc7ff1cb090 in __read_nocancel () from /lib/libpthread.so.0
#1  0x000000000047a764 in ?? ()
#2  <signal handler called>
#3  0x00007fc7febfd4b5 in raise () from /lib/libc.so.6
#4  0x00007fc7fec00f50 in abort () from /lib/libc.so.6
#5  0x00007fc7ff846540 in g_assertion_message () from /lib/libglib-2.0.so.0
#6  0x00007fc7ff846ab0 in g_assertion_message_expr ()
   from /lib/libglib-2.0.so.0
#7  0x000000000056a310 in ?? ()
#8  0x0000000000557be6 in ?? ()
#9  0x00000000005653e4 in mono_once ()
#10 0x0000000000557b53 in ?? ()
#11 0x00000000005692c5 in ?? ()
#12 0x0000000000506dfe in ?? ()
#13 0x000000000050e9b5 in mono_runtime_init ()
#14 0x0000000000419133 in ?? ()
#15 0x0000000000461f97 in mono_main ()
#16 0x00007fc7febe8abd in __libc_start_main () from /lib/libc.so.6
#17 0x0000000000416e19 in ?? ()
#18 0x00007fffd0d9acc8 in ?? ()
#19 0x000000000000001c in ?? ()
#20 0x0000000000000002 in ?? ()
#21 0x00007fffd0d9b603 in ?? ()
#22 0x00007fffd0d9b60d in ?? ()
#23 0x0000000000000000 in ?? ()

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

Gnome-Do:
```

benjamin@benjamin-laptop:~$ gnome-do

** (/usr/lib/gnome-do/Do.exe:2656): CRITICAL **: _wapi_shm_file_open: shared file [/home/benjamin/.wapi/shared_data-benjamin-laptop-Linux-x86_64-328-12-0] open error: Input/output error

** (/usr/lib/gnome-do/Do.exe:2656): CRITICAL **: _wapi_shm_attach: shared file [/home/benjamin/.wapi/shared_data-benjamin-laptop-Linux-x86_64-328-12-0] open error
**
ERROR:shared.c:349:shm_semaphores_init: assertion failed: (tmp_shared != NULL)

** (/usr/lib/gnome-do/Do.exe:2656): WARNING **: Thread (nil) may have been prematurely finalized
Stacktrace:


** (/usr/lib/gnome-do/Do.exe:2656): WARNING **: Thread (nil) may have been prematurely finalized

Native stacktrace:

	/usr/bin/cli [0x47a5ef]
	/lib/libpthread.so.0 [0x7f29e007f190]
	/lib/libc.so.6(gsignal+0x35) [0x7f29dfab04b5]
	/lib/libc.so.6(abort+0x180) [0x7f29dfab3f50]
	/lib/libglib-2.0.so.0(g_assertion_message+0x120) [0x7f29e06f9540]
	/lib/libglib-2.0.so.0 [0x7f29e06f9ab0]
	/usr/bin/cli [0x56a310]
	/usr/bin/cli [0x557be6]
	/usr/bin/cli(mono_once+0x64) [0x5653e4]
	/usr/bin/cli [0x557b53]
	/usr/bin/cli [0x5692c5]
	/usr/bin/cli [0x506dfe]
	/usr/bin/cli(mono_runtime_init+0x25) [0x50e9b5]
	/usr/bin/cli [0x419133]
	/usr/bin/cli(mono_main+0x417) [0x461f97]
	/lib/libc.so.6(__libc_start_main+0xfd) [0x7f29dfa9babd]
	/usr/bin/cli [0x416e19]

Debug info from gdb:

[Thread debugging using libthread_db enabled]
0x00007f29e007e090 in __read_nocancel () from /lib/libpthread.so.0
* 1 Thread 0x7f29e0d5e730 (LWP 2656)  0x00007f29e007e090 in __read_nocancel ()
   from /lib/libpthread.so.0

Thread 1 (Thread 0x7f29e0d5e730 (LWP 2656)):
#0  0x00007f29e007e090 in __read_nocancel () from /lib/libpthread.so.0
#1  0x000000000047a764 in ?? ()
#2  <signal handler called>
#3  0x00007f29dfab04b5 in raise () from /lib/libc.so.6
#4  0x00007f29dfab3f50 in abort () from /lib/libc.so.6
#5  0x00007f29e06f9540 in g_assertion_message () from /lib/libglib-2.0.so.0
#6  0x00007f29e06f9ab0 in g_assertion_message_expr ()
   from /lib/libglib-2.0.so.0
#7  0x000000000056a310 in ?? ()
#8  0x0000000000557be6 in ?? ()
#9  0x00000000005653e4 in mono_once ()
#10 0x0000000000557b53 in ?? ()
#11 0x00000000005692c5 in ?? ()
#12 0x0000000000506dfe in ?? ()
#13 0x000000000050e9b5 in mono_runtime_init ()
#14 0x0000000000419133 in ?? ()
#15 0x0000000000461f97 in mono_main ()
#16 0x00007f29dfa9babd in __libc_start_main () from /lib/libc.so.6
#17 0x0000000000416e19 in ?? ()
#18 0x00007fff535e3f58 in ?? ()
#19 0x000000000000001c in ?? ()
#20 0x0000000000000002 in ?? ()
#21 0x00007fff535e567f in ?? ()
#22 0x00007fff535e568c in ?? ()
#23 0x0000000000000000 in ?? ()

=================================================================
Got a SIGABRT while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

Aborted

```

---

### Post by directhex on 2009-11-07
kill all Mono apps, and run "rm -r /home/benjamin/.wapi"

---

### Post by humphreybc on 2009-11-07
> **directhex said:**
> kill all Mono apps, and run "rm -r /home/benjamin/.wapi"

Wow, fancy that, worked a charm! Learn something new every day huh. One more problem that I now know how to fix myself :)

Thanks!

---

### Post by avdzm on 2009-11-29
thanks directhex,
that worked for me too,
my laptop failed with the hibernation and i got this error afterwards.

---

### Post by vjcamarena on 2009-11-29
Wow, thanks, directhex... this fixed my problems too!

I'm loving this community!

---

### Post by Pifilatakanemu on 2009-12-15
worked fo me too, thanks a lot.

---

### Post by Machiavelli on 2010-03-09
> **directhex said:**
> kill all Mono apps, and run "rm -r /home/benjamin/.wapi"

wow, thank you! I really like Banshee as a musicplayer and diden't whant to go with something else, thanks for helping out!

---

### Post by ntt2k on 2010-03-22
one more stupid question, can you show me the command how to identify all currently running app associate with mono library? so i can kill them ...

---

### Post by maxdbh on 2010-03-31
Wow thanks!!!!

Je suis tombé par hasard sur cette page suite au meme problème et grace à vous tout marche à merveille.

---

