---
title: "Banshee crashes in 10s"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by ozbolt on 2009-02-02
and if i run it with terminal this is most of what gets shown:

Well I tried to reinstall banshee and mono (at least what I've found in synaptic, but still the same.
Any idea please?

And another thing: Is there a txt file that texts all podcasts feeds becouse I don't wanna spend another 10 minutes searching it again and again.

LP, Ožbolt 


```
0xb7f85430 in __kernel_vsyscall ()
  21 Thread 0xb73a1b90 (LWP 9217)  0xb7f85430 in __kernel_vsyscall ()
  20 Thread 0xb737db90 (LWP 9218)  0xb7f85430 in __kernel_vsyscall ()
  19 Thread 0xb5fa6b90 (LWP 9219)  0xb7f85430 in __kernel_vsyscall ()
  18 Thread 0xb420bb90 (LWP 9222)  0xb7f85430 in __kernel_vsyscall ()
  17 Thread 0xb4106b90 (LWP 9223)  0xb7f85430 in __kernel_vsyscall ()
  16 Thread 0xb4001b90 (LWP 9224)  0xb7f85430 in __kernel_vsyscall ()
  15 Thread 0xb3268b90 (LWP 9227)  0xb7f85430 in __kernel_vsyscall ()
  14 Thread 0xb337db90 (LWP 9228)  0xb7f85430 in __kernel_vsyscall ()
  13 Thread 0xb302cb90 (LWP 9230)  0xb7f85430 in __kernel_vsyscall ()
  12 Thread 0xb2f27b90 (LWP 9231)  0xb7f85430 in __kernel_vsyscall ()
  11 Thread 0xb2e22b90 (LWP 9232)  0xb7f85430 in __kernel_vsyscall ()
  10 Thread 0xb2d1db90 (LWP 9233)  0xb7f85430 in __kernel_vsyscall ()
  9 Thread 0xb2bd9b90 (LWP 9234)  0xb7f85430 in __kernel_vsyscall ()
  8 Thread 0xb2ab1b90 (LWP 9236)  0xb7f85430 in __kernel_vsyscall ()
  7 Thread 0xb29acb90 (LWP 9237)  0xb7f85430 in __kernel_vsyscall ()
  6 Thread 0xb28a1b90 (LWP 9238)  0xb7f85430 in __kernel_vsyscall ()
  5 Thread 0xb282fb90 (LWP 9239)  0xb7f85430 in __kernel_vsyscall ()
  4 Thread 0xb271ab90 (LWP 9240)  0xb7f85430 in __kernel_vsyscall ()
  3 Thread 0xb2615b90 (LWP 9241)  0xb7f85430 in __kernel_vsyscall ()
  2 Thread 0xb23ffb90 (LWP 9242)  0xb7f85430 in __kernel_vsyscall ()
  1 Thread 0xb7cc36d0 (LWP 9216)  0xb7f85430 in __kernel_vsyscall ()

Thread 21 (Thread 0xb73a1b90 (LWP 9217)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e80906 in nanosleep () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08110fc8 in ?? ()
#3  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#4  0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 20 (Thread 0xb737db90 (LWP 9218)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d075 in pthread_cond_wait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x081143b7 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080b5c1a in ?? ()
#7  0x080d5f74 in ?? ()
#8  0x081279de in ?? ()
#9  0x0813ff75 in ?? ()
#10 0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#11 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 19 (Thread 0xb5fa6b90 (LWP 9219)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x08116a2c in ?? ()
#5  0x0812962a in ?? ()
#6  0x080d3013 in ?? ()
#7  0xb5dc30fa in ?? ()
#8  0xb5fb6fa3 in ?? ()
#9  0xb5fb5d40 in ?? ()
#10 0xb7916411 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 18 (Thread 0xb420bb90 (LWP 9222)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x08114432 in ?? ()
#4  0x08129a75 in ?? ()
#5  0x080d4bd9 in ?? ()
#6  0xb423c28f in ?? ()
#7  0xb423bf0f in ?? ()
#8  0xb423bc17 in ?? ()
#9  0xb423ba06 in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea71 in ?? ()
#12 0x080d8ff3 in ?? ()
#13 0x080d9420 in ?? ()
#14 0x080d5f74 in ?? ()
#15 0x081279de in ?? ()
#16 0x0813ff75 in ?? ()
#17 0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 17 (Thread 0xb4106b90 (LWP 9223)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x08114432 in ?? ()
#4  0x08129a75 in ?? ()
#5  0x080d4bd9 in ?? ()
#6  0xb423c28f in ?? ()
#7  0xb423bf0f in ?? ()
#8  0xb423bc17 in ?? ()
#9  0xb423ba06 in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea71 in ?? ()
#12 0x080d8ff3 in ?? ()
#13 0x080d9420 in ?? ()
#14 0x080d5f74 in ?? ()
#15 0x081279de in ?? ()
#16 0x0813ff75 in ?? ()
#17 0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 16 (Thread 0xb4001b90 (LWP 9224)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x08114432 in ?? ()
#4  0x08129a75 in ?? ()
#5  0x080d4bd9 in ?? ()
#6  0xb423c28f in ?? ()
#7  0xb423bf0f in ?? ()
#8  0xb423bc17 in ?? ()
#9  0xb423ba06 in ?? ()
#10 0x0809e8e3 in mono_runtime_invoke_array ()
#11 0x0809ea71 in ?? ()
#12 0x080d8ff3 in ?? ()
#13 0x080d9420 in ?? ()
#14 0x080d5f74 in ?? ()
#15 0x081279de in ?? ()
#16 0x0813ff75 in ?? ()
#17 0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#18 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 15 (Thread 0xb3268b90 (LWP 9227)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d945e in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 14 (Thread 0xb337db90 (LWP 9228)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7dc8c01 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7f0298b in g_spawn_sync () from /usr/lib/libglib-2.0.so.0
#3  0xb7f02d3c in g_spawn_command_line_sync () from /usr/lib/libglib-2.0.so.0
#4  0x0817b565 in ?? ()
#5  0x0807f78b in ?? ()
#6  <signal handler called>
#7  0xb7d662c3 in strlen () from /lib/tls/i686/cmov/libc.so.6
#8  0x0809ca2a in mono_string_new ()
#9  0x0809cab3 in mono_string_new_wrapper ()
#10 0xb4d38f97 in ?? ()
#11 0xb2726d6b in ?? ()
#12 0xb2726453 in ?? ()
#13 0x080c65c8 in ?? ()
#14 0xb4cc99da in ?? ()
#15 0xb27269c3 in ?? ()
#16 0xb272693b in ?? ()
#17 0xb27267b7 in ?? ()
#18 0xb27265ba in ?? ()
#19 0xb272652c in ?? ()
#20 0xb2c1339c in ?? ()
#21 0xb2c12cf0 in ?? ()
#22 0xb2c1232e in ?? ()
#23 0xb326e1dc in ?? ()
#24 0xb347533d in ?? ()
#25 0xb347531c in ?? ()
#26 0xb3474fd0 in ?? ()
#27 0xb7916411 in ?? ()
#28 0x08098c55 in mono_runtime_delegate_invoke ()
#29 0x080d5fdf in ?? ()
#30 0x081279de in ?? ()
#31 0x0813ff75 in ?? ()
#32 0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#33 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 13 (Thread 0xb302cb90 (LWP 9230)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d945e in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 12 (Thread 0xb2f27b90 (LWP 9231)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d945e in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 11 (Thread 0xb2e22b90 (LWP 9232)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d945e in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 10 (Thread 0xb2d1db90 (LWP 9233)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d945e in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 9 (Thread 0xb2bd9b90 (LWP 9234)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7dd0fb6 in epoll_wait () from /lib/tls/i686/cmov/libc.so.6
#2  0x080d8a02 in ?? ()
#3  0x080d5f74 in ?? ()
#4  0x081279de in ?? ()
#5  0x0813ff75 in ?? ()
#6  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 8 (Thread 0xb2ab1b90 (LWP 9236)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7dc5f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb2c0fb81 in ?? ()
#3  0xb2c0fb2d in ?? ()
#4  0x0a6d3e52 in ?? ()
#5  0xb2ac9a4d in avahi_simple_poll_run () from /usr/lib/libavahi-common.so.3
#6  0xb2aca320 in avahi_simple_poll_iterate ()
   from /usr/lib/libavahi-common.so.3
#7  0xb2aca370 in avahi_simple_poll_loop () from /usr/lib/libavahi-common.so.3
#8  0xb2c0faeb in ?? ()
#9  0xb2c0fa22 in ?? ()
#10 0xb7916411 in ?? ()
#11 0x08098c55 in mono_runtime_delegate_invoke ()
#12 0x080d5fdf in ?? ()
#13 0x081279de in ?? ()
#14 0x0813ff75 in ?? ()
#15 0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#16 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 7 (Thread 0xb29acb90 (LWP 9237)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e80328 in accept () from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08124909 in ?? ()
#3  0x080ddb1b in ?? ()
#4  0xb2c11c9a in ?? ()
#5  0xb2c11ab7 in ?? ()
#6  0xb2c11926 in ?? ()
#7  0xb7916411 in ?? ()
#8  0x08098c55 in mono_runtime_delegate_invoke ()
#9  0x080d5fdf in ?? ()
#10 0x081279de in ?? ()
#11 0x0813ff75 in ?? ()
#12 0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#13 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 6 (Thread 0xb28a1b90 (LWP 9238)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7dc5f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eccc32 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7ecd2c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb625c8b0 in ?? () from /usr/lib/libORBit-2.so.0
#5  0xb7ef402f in ?? () from /usr/lib/libglib-2.0.so.0
#6  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#7  0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 5 (Thread 0xb282fb90 (LWP 9239)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d92fd in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 4 (Thread 0xb271ab90 (LWP 9240)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d92fd in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xb2615b90 (LWP 9241)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d945e in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 2 (Thread 0xb23ffb90 (LWP 9242)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7e7d3a2 in pthread_cond_timedwait@@GLIBC_2.3.2 ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0x08114368 in ?? ()
#3  0x081169ec in ?? ()
#4  0x0812944c in ?? ()
#5  0x080d92fd in ?? ()
#6  0x080d5f74 in ?? ()
#7  0x081279de in ?? ()
#8  0x0813ff75 in ?? ()
#9  0xb7e7950f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#10 0xb7dd07ee in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 1 (Thread 0xb7cc36d0 (LWP 9216)):
#0  0xb7f85430 in __kernel_vsyscall ()
#1  0xb7dc5f77 in poll () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7eccc32 in ?? () from /usr/lib/libglib-2.0.so.0
#3  0xb7ecd2c2 in g_main_loop_run () from /usr/lib/libglib-2.0.so.0
#4  0xb69893a9 in gtk_main () from /usr/lib/libgtk-x11-2.0.so.0
#5  0xb3554ee6 in ?? ()
#6  0xb3554eb0 in ?? ()
#7  0xb3554c53 in ?? ()
#8  0xb6db056d in ?? ()
#9  0xb6db0453 in ?? ()
#10 0xb6db035a in ?? ()
#11 0xb791447c in ?? ()
#12 0xb79081c3 in ?? ()
#13 0x0809cb76 in mono_runtime_exec_main ()
#14 0x0809d19b in mono_runtime_run_main ()
#15 0x0805af2e in mono_main ()
#16 0x0805a432 in ?? ()
#17 0xb7d05685 in __libc_start_main () from /lib/tls/i686/cmov/libc.so.6
#18 0x0805a371 in ?? ()
#0  0xb7f85430 in __kernel_vsyscall ()


=================================================================
Got a SIGSEGV while executing native code. This usually indicates
a fatal error in the mono runtime or one of the native libraries 
used by your application.
=================================================================

```

---

### Post by directhex on 2009-02-02
You've missed out the first part of the output, which should include a managed stack trace

---

