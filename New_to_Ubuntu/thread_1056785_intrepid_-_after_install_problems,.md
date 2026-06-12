---
title: "intrepid - after install problems,"
date: 2009-02-01
forum: New to Ubuntu
---

### Post by Sceiron on 2009-02-01
I decided to move from 8.04 to 8.10 yesterday. But not without problems.
I performed a so called 'clean install'.

Nautilus-open-terminal wont work
I have it installed, but it not available when i right click my desktop?
Is it not working in intrepid?

EDIT: After reinstalling, rebooting open-terminal is working again!!! Juhu, so only one problem left :)

Kopete
I installed kopete, added MSN account, and logged on, but when i press 
Settings -> Configure it tries to open the configure menu, but it crashes with following message: A Fatal Error Occurred

```
Application: Kopete (kopete), signal SIGABRT
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread 0xb59056c0 (LWP 14139)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0xb804e430 in __kernel_vsyscall ()
#7  0xb6400880 in raise () from /lib/tls/i686/cmov/libc.so.6
#8  0xb6402248 in abort () from /lib/tls/i686/cmov/libc.so.6
#9  0xb7483795 in qt_message_output () from /usr/lib/libQtCore.so.4
#10 0xb7483872 in qFatal () from /usr/lib/libQtCore.so.4
#11 0xb74838cc in qt_assert_x () from /usr/lib/libQtCore.so.4
#12 0xb377bbfa in ?? () from /usr/lib/libkopete_videodevice.so.4
#13 0xb3792a04 in Kopete::AV::VideoDevicePool::getFrame ()
   from /usr/lib/libkopete_videodevice.so.4
#14 0xb37b6cdb in ?? () from /usr/lib/kde4/kcm_kopete_avdeviceconfig.so
#15 0xb37b694b in ?? () from /usr/lib/kde4/kcm_kopete_avdeviceconfig.so
#16 0xb7590a60 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#17 0xb75917e2 in QMetaObject::activate () from /usr/lib/libQtCore.so.4
#18 0xb75cb7a7 in QTimer::timeout () from /usr/lib/libQtCore.so.4
#19 0xb759740e in QTimer::timerEvent () from /usr/lib/libQtCore.so.4
#20 0xb758b53f in QObject::event () from /usr/lib/libQtCore.so.4
#21 0xb6a5d8ec in QApplicationPrivate::notify_helper ()
   from /usr/lib/libQtGui.so.4
#22 0xb6a6572e in QApplication::notify () from /usr/lib/libQtGui.so.4
#23 0xb7abbb2d in KApplication::notify () from /usr/lib/libkdeui.so.5
#24 0xb757be61 in QCoreApplication::notifyInternal ()
   from /usr/lib/libQtCore.so.4
#25 0xb75a9d81 in ?? () from /usr/lib/libQtCore.so.4
#26 0xb75a6520 in ?? () from /usr/lib/libQtCore.so.4
#27 0xb5f5e6f8 in g_main_context_dispatch () from /usr/lib/libglib-2.0.so.0
#28 0xb5f61da3 in ?? () from /usr/lib/libglib-2.0.so.0
#29 0xb5f61f61 in g_main_context_iteration () from /usr/lib/libglib-2.0.so.0
#30 0xb75a6478 in QEventDispatcherGlib::processEvents ()
   from /usr/lib/libQtCore.so.4
#31 0xb6af7ea5 in ?? () from /usr/lib/libQtGui.so.4
#32 0xb757a52a in QEventLoop::processEvents () from /usr/lib/libQtCore.so.4
#33 0xb757a6ea in QEventLoop::exec () from /usr/lib/libQtCore.so.4
#34 0xb757cda5 in QCoreApplication::exec () from /usr/lib/libQtCore.so.4
#35 0xb6a5d767 in QApplication::exec () from /usr/lib/libQtGui.so.4
#36 0x0808aa6f in _start ()
#0  0xb804e430 in __kernel_vsyscall ()

```

Anyone got any pointers on this problem? 
Using gimp or amsn isn't something i want, so dont suggest it..

For the record: amarok and koversation runs smooth.
Any help would be great!

---

### Post by halovivek on 2009-02-02
reinstall the kopte again. it will fine.

---

### Post by Sceiron on 2009-02-02
No, that doesn't help.

```

ASSERT failure in QVector<T>::operator[]: "index out of range", file /usr/include/qt4/QtCore/qvector.h, line 325
KCrash: Application 'kopete' crashing...
sock_file=/home/user/.kde/socket-bosshaug/kdeinit4__0

```

CLI output when it crashes....

what is this qt4 thing, seems lik one some value/string is out of range...
Have tried to install both with apt-get and aptitude, but same result.

How to solve this?

EDIT:
Solved:
did some googlin, and found this to be a video device problem.
So i plugged in my web-cam and launched kopete again and then its suddenly working...
Strange thing...but i belive maybe my tv-card was causing confusion to kopete in some strange way.

---

### Post by oldos2er on 2009-02-02
nautilus-open-terminal only works from within Nautilus itself, not on the desktop.

Edit: I take that back, you should have an 'Open in Terminal' entry in your desktop menu. If you haven't already done so, log out, log back in, and you should see it.

---

