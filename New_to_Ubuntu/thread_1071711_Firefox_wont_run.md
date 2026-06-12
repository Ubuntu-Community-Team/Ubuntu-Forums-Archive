---
title: "Firefox wont run"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by Ducatiboy Stu on 2009-02-16
For some reason Firefox has stopped working on me.

It stopped after I did a recent update. I uninstalled it, re-installed it, evn installed FIrefox 2 and went to an older kernel version , but it still wont run..


```
ncts@ncts:~$ firefox --sync
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
** Message: GetValue variable 1 (1)
** Message: GetValue variable 2 (2)
The program 'firefox' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 14952 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb7f3d767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb7f3d81e]
#2 /usr/lib/libX11.so.6 [0xb6a92518]
#3 /usr/lib/libX11.so.6(XFreeCursor+0x25) [0xb6a6e8f5]
#4 /usr/lib/libqt-mt.so.3(_ZN11QCursorDataD1Ev+0x3f) [0xb4eaa389]
#5 /usr/lib/libqt-mt.so.3(_ZN7QCursorD1Ev+0x5a) [0xb4eaa58e]
#6 /usr/lib/libqt-mt.so.3 [0xb4eaa5d5]
#7 /lib/tls/i686/cmov/libc.so.6(exit+0xd4) [0xb7cdc084]
#8 /usr/lib/libgdk-x11-2.0.so.0 [0xb6678637]
#9 /usr/lib/libbonoboui-2.so.0 [0xb62aa665]
#10 /usr/lib/libX11.so.6(_XError+0xfe) [0xb6a8b73e]
#11 /usr/lib/libX11.so.6 [0xb6a92e5c]
#12 /usr/lib/libX11.so.6(_XReply+0x15a) [0xb6a9321a]
#13 /usr/lib/libX11.so.6(XSync+0x6a) [0xb6a8724a]
#14 /usr/lib/libX11.so.6 [0xb6a873c5]
#15 /usr/lib/libX11.so.6 [0xb6a9357d]
#16 /usr/lib/libX11.so.6(XCreatePixmap+0x8d) [0xb6a69e2d]
#17 /usr/lib/libgdk-x11-2.0.so.0(gdk_pixmap_new+0x13c) [0xb66799dc]
#18 /usr/lib/xulrunner-1.9.0.6/libxul.so [0xb77e6d28]
#19 /usr/lib/xulrunner-1.9.0.6/libxul.so [0xb77e96fc]
Killed
ncts@ncts:~$ 

```

---

### Post by Ducatiboy Stu on 2009-02-17
?

---

### Post by gackt on 2009-02-20
before someone post a very complicated answer, why dont we try to reinstall it? with purge if needed.

---

### Post by kellemes on 2009-02-20
Have you tried using a new profile?
```
firefox -profilemanager
```
Create new profile and run firefox using this profile..
If this works, your old profile is sick.
You can delete it or simply don't use it.

---

