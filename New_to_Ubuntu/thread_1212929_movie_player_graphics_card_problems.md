---
title: "movie player/ graphics card problems"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by nobodygh on 2009-07-14
Whenever I try to play a movie the movie player quits. I have this problem with both totem AND VLC, even though VLC works in X11 mode, but that doesn't really work for me. 
I run Ubuntu 9.04(Jaunty). And I have a intel graphics card, lshw gives me this:
> *-display UNCLAIMED     
       description: VGA compatible controller
       product: 82865G Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0If I run totem in terminal, I get this error:
> /var/lib/python-support/python2.6/gdata/tlslite/utils/cryptomath.py:9: DeprecationWarning: the sha module is deprecated; use the hashlib module instead
  import shaAnd upon opening a file:
> The program 'totem' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadAlloc (insufficient resources for operation)'.
  (Details: serial 82 error_code 11 request_code 132 minor_code 19)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)

---

### Post by Hospadar on 2009-07-14
What drivers are you using for your video card (if you know)?
Do you see anything in System->Administration->Hardware Drivers?

Do you have any other graphical issues?

---

