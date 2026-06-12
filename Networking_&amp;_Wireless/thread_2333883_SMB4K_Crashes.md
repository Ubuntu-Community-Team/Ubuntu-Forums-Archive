---
title: "SMB4K Crashes"
date: 2016-08-14
forum: Networking &amp; Wireless
---

### Post by philipwmirabelli on 2016-08-14
Hello, I am running kubntu 16.04 1 LTS with Pasma 5.5.5 and have recently added SMB4K facility which installed ok.  I have a windows laptop that I use as a server and another pc running kubuntu 16.04 LTS with plasma 5.5.5 which runs smb4k ok and sees the windows share mount no problem.  However on the other pc running 16.04 1  when I click the windows share folder in the smb4k GUI which I have imaginatively named "workgroup", the whole programme crashes.....I get an error message from the crashed GUI which is below, it is difficult for me to understand what it is saying....... 
I did read somewhere that I may be using an old version of SMB4K I am using version 1.1.2 but I will check how to upgrade this, perhaps that will solve the issue.....any ideas?  thanks!!

```

Application: Smb4K (smb4k), signal: Segmentation fault
Using host libthread_db library "/lib/x86_64-linux-gnu/libthread_db.so.1".
[Current thread is 1 (Thread 0x7f0089f8e900 (LWP 8488))]


Thread 3 (Thread 0x7f006ffff700 (LWP 8498)):
#0  0x00007f008995ee8d in poll () at ../sysdeps/unix/syscall-template.S:84
#1  0x00007f008695439c in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f00869544ac in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f008952c2ce in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#4  0x00007f00894fa18f in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#5  0x00007f00894fa4f5 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#6  0x00007f00893e9549 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#7  0x00007f00894da223 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#8  0x00007f00893ebe3c in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007f00870406fa in start_thread (arg=0x7f006ffff700) at pthread_create.c:333
#10 0x00007f008996ab5d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109


Thread 2 (Thread 0x7f0076d88700 (LWP 8491)):
#0  0x00007f008995ee8d in poll () at ../sysdeps/unix/syscall-template.S:84
#1  0x00007f008695439c in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#2  0x00007f00869544ac in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#3  0x00007f008952c2ce in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#4  0x00007f00894fa18f in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#5  0x00007f00894fa4f5 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#6  0x00007f00893e9549 in QThread::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#7  0x00007f00894da223 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#8  0x00007f00893ebe3c in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#9  0x00007f00870406fa in start_thread (arg=0x7f0076d88700) at pthread_create.c:333
#10 0x00007f008996ab5d in clone () at ../sysdeps/unix/sysv/linux/x86_64/clone.S:109


Thread 1 (Thread 0x7f0089f8e900 (LWP 8488)):
[KCrash Handler]
#6  0x00007f0088c4ce7c in Smb4KWorkgroup::workgroupName() const () from /usr/lib/libsmb4kcore.so.4
#7  0x00007f0088c1fe86 in Smb4KScanner::lookupDomainMembers(Smb4KWorkgroup*, QWidget*) () from /usr/lib/libsmb4kcore.so.4
#8  0x00007f0088c21c88 in Smb4KScanner::slotAuthError(Smb4KLookupDomainMembersJob*) () from /usr/lib/libsmb4kcore.so.4
#9  0x00007f0089510010 in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#10 0x00007f0088c354ff in ?? () from /usr/lib/libsmb4kcore.so.4
#11 0x00007f0088c356d8 in ?? () from /usr/lib/libsmb4kcore.so.4
#12 0x00007f0089510010 in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#13 0x00007f008948f107 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#14 0x00007f008948fdb9 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#15 0x00007f0089510010 in QMetaObject::activate(QObject*, QMetaObject const*, int, void**) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#16 0x00007f00895612de in QSocketNotifier::activated(int) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#17 0x00007f008951a7bb in QSocketNotifier::event(QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#18 0x00007f008779cfdc in QApplicationPrivate::notify_helper(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#19 0x00007f00877a3f16 in QApplication::notify(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#20 0x00007f00887596aa in KApplication::notify(QObject*, QEvent*) () from /usr/lib/libkdeui.so.5
#21 0x00007f00894fb90d in QCoreApplication::notifyInternal(QObject*, QEvent*) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#22 0x00007f008952c8a2 in ?? () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#23 0x00007f00869541a7 in g_main_context_dispatch () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#24 0x00007f0086954400 in ?? () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#25 0x00007f00869544ac in g_main_context_iteration () from /lib/x86_64-linux-gnu/libglib-2.0.so.0
#26 0x00007f008952c2ae in QEventDispatcherGlib::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#27 0x00007f008784a616 in ?? () from /usr/lib/x86_64-linux-gnu/libQtGui.so.4
#28 0x00007f00894fa18f in QEventLoop::processEvents(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#29 0x00007f00894fa4f5 in QEventLoop::exec(QFlags<QEventLoop::ProcessEventsFlag>) () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#30 0x00007f00895004b9 in QCoreApplication::exec() () from /usr/lib/x86_64-linux-gnu/libQtCore.so.4
#31 0x00007f0089c39439 in kdemain () from /usr/lib/libkdeinit4_smb4k.so
#32 0x00007f0089884830 in __libc_start_main (main=0x4006d0, argc=1, argv=0x7ffc2c3b2908, init=<optimized out>, fini=<optimized out>, rtld_fini=<optimized out>, stack_end=0x7ffc2c3b28f8) at ../csu/libc-start.c:291
#33 0x00000000004006fe in _start ()
```

---

### Post by wildmanne39 on 2016-08-14
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

