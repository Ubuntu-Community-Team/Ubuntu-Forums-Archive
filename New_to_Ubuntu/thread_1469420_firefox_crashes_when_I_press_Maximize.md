---
title: "firefox crashes when I press Maximize"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by GaaraOfDSand on 2010-05-02
I am using Xubuntu 10.04 with fluxbox (I don't know if it matters or not) each time I press the maximize button firefox crashes for some reason, if I resize it from the bottom it's ok. I ran it in the terminal and it gave me this error: 

riddlebox@BrainSlug:~$ firefox
The program 'firefox-bin' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 25788 error_code 11 request_code 53 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

I have a Nvidia FX5200 as a graphics card I had the drivers found in synaptic and then upgraded to NVIDIA-Linux-x86-173.14.25-pkg1.run and they installed normally like they did in 9.10..

This does not occur when I'm in an XFCE session


Thanks in advance for the help

EDIT: Even thunar does the same thing with the same output I even tried running it as root with the same result

---

### Post by GaaraOfDSand on 2010-05-04
Apparently conky was the culprit. It was set to dock and some applications couldn't handle it so they crashed if I set it to taskbar everything works fine. I just have to live with conky being at the bottom of applications.

---

