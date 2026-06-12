---
title: "Kdenlive"
date: 2009-03-06
forum: New to Ubuntu
---

### Post by quietbear on 2009-03-06
First of all, is there a single program for linux that works right every time?  By that I mean, something that will work the same way every time you use it, and one that doesnt crash all the time?

Kino keeps crashing all the time so I switched to Kdenlive.

I like it better, besides the fact it keeps crashing.  Other than that it is great, if it actually worked, I would be really pleased with it!

Here is the thing that pops up:

Oh wait, never mind!  Well, I was going to, but I guess when the report comes up, I click copy, it did, and now there is nothing in the clipboard.  So, no report!

I cannot believe this.  I have always heard how LInux is better than windows, and to be honest, my system has never run worse in its life, it has never crashed more than it has now.

I think it is time for me to switch back to reliable operating system that has programs that work.

I dont really know what to say now, I cant tell you all what the report says, it wont let me copy paste it, no other video editing software can go more than 30 minutes without crashing, what should I do?

---

### Post by quietbear on 2009-03-06
A Fatal Error Occurred
The application Kdenlive (kdenlive) crashed and caused the signal 11 (SIGSEGV).
Please help us improve the software you use by filing a report at [http://bugs.kde.org](http://bugs.kde.org). Useful details include how to reproduce the error, documents that were loaded, etc.

I would post the rest of the report, but your own forum will not let me:

> You have included 10 images in your message. You are limited to using 8 images so please go back and correct the problem and then continue again.

Images include use of smilies, the BB code [img] tag and HTML <img> tags. The use of these is all subject to them being enabled by the administrator.

Even though there is not a single BBcode in it.

> Application: Kdenlive (kdenlive), signal SIGSEGV
[Current thread is 0 (LWP 7974)]

Thread 4 (Thread 0xb08fdb90 (LWP 7985)):
#0  0xb7f27430 in __kernel_vsyscall ()
#1  0xb6802df1 in select () from /lib/tls/i686/cmov/libc.so.6
#2  0xb7498150 in ?? () from /usr/lib/libQtCore.so.4
#3  0xb73c86ae in ?? () from /usr/lib/libQtCore.so.4
#4  0xb671250f in start_thread () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xb680aa0e in clone () from /lib/tls/i686/cmov/libc.so.6

Thread 3 (Thread 0xa2d30b90 (LWP 8106)):
#0  0xb7f27430 in __kernel_vsyscall ()
#1  0xb67163a2 in pthread_cond_timedwait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6818c14 in pthread_cond_timedwait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb7eeeba9 in mlt_consumer_get_frame () from /usr/lib/libmlt.so.1
#4  0xb67139de in pthread_mutex_lock () from /lib/tls/i686/cmov/libpthread.so.0
#5  0xe8758bff in ?? ()

Thread 2 (Thread 0xb267db90 (LWP 8107)):
#0  0xb7f27430 in __kernel_vsyscall ()
#1  0xb6716075 in pthread_cond_wait@@GLIBC_2.3.2 () from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb6818bbd in pthread_cond_wait () from /lib/tls/i686/cmov/libc.so.6
#3  0xb35f5d2c in ?? () from /usr/lib/mlt/libmltsdl.so
Backtrace stopped: previous frame inner to this frame (corrupt stack?)

Thread 1 (Thread 0xb5e536c0 (LWP 7974)):
[KCrash Handler]
#6  0x080c02a6 in QBasicAtomicInt::ref ()
#7  0x080c2235 in QList<CommentedTime>::QList ()
#8  0x0816bc6c in DocClipBase::commentedSnapMarkers ()
#9  0x081c77de in ClipItem::paint ()
#10 0xb713d7ed in ?? () from /usr/lib/libQtGui.so.4
#11 0xb71404ea in ?? () from /usr/lib/libQtGui.so.4
#12 0xb7141681 in QGraphicsScene::drawItems () from /usr/lib/libQtGui.so.4


That is part of it, if I put more in your forum wont let me post.  Man linux just keeps on getting better huh?
Of course it did it again, so here is the report.

---

