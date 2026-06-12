---
title: "Bug Report"
date: 2009-02-05
forum: New to Ubuntu
---

### Post by POWMS on 2009-02-05
How do I go about reporting a Bug for Xububtu?

---

### Post by cardinals_fan on 2009-02-05
See the link in my sig.

---

### Post by POWMS on 2009-02-06
I got this error message after trying to turn on my panels before the desktop hung:

craig@craig-laptop:~$ xfce4-panel
craig@craig-laptop:~$ 
(xfce4-menu-plugin:5914): Gdk-WARNING **: GdkWindow 0x2800003 unexpectedly destroyed

(xfce4-places-plugin:5915): Gdk-WARNING **: GdkWindow 0x2a00003 unexpectedly destroyed
The program 'xfce4-places-plugin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 152 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
The program 'xfce4-menu-plugin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadWindow (invalid Window parameter)'.
  (Details: serial 152 error_code 3 request_code 18 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

Should I report this?

---

