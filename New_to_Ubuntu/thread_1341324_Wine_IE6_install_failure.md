---
title: "Wine IE6 install failure"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by K7AAY on 2009-11-29
Following the install directions to add IE6 to Wine 1.01 in Karmic Koala at 
[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)
fail with this error message. 


[INDENT]The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
  (Details: serial 10945 error_code 1 request_code 0 minor_code 0)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)[/INDENT]

Are there alternate instructions which work?

---

### Post by Sir Jasper on 2009-11-29
Hi,

In case it may help, I use Wine 1.0.1 and I installed Internet Explorer 6 using Wine-Doors. It works well.

My regards

---

### Post by K7AAY on 2009-11-29
> **Sir Jasper said:**
> Hi,

In case it may help, I use Wine 1.0.1 and I installed Internet Explorer 6 using Wine-Doors. It works well.

My regards

Wine-Doors is gacked. Adding the link to Software Sources results in a 404 message regarding the .tar.gz file from Wine-Doors following the instructions in [https://launchpad.net/~wine-doors-dev-team/+archive/ppa](https://launchpad.net/~wine-doors-dev-team/+archive/ppa)

How did you install Wine-Doors?

---

### Post by Sir Jasper on 2009-11-29
Hi,

It was in Synaptic Package Manager 8.10. I have just looked and it is still in 9.04.

My regards

---

### Post by K7AAY on 2009-11-29
> **Sir Jasper said:**
> Hi,

It was in Synaptic Package Manager 8.10. I have just looked and it is still in 9.04.

My regards

Sadly, missing from 9.10

Any other ideas?

---

### Post by SunnyRabbiera on 2009-11-29
Try playonlinux, great for those insane folk who want IE in Linux.
Playonlinux even does IE7

[http://www.playonlinux.com/en/](http://www.playonlinux.com/en/)

They have a version for Ubuntu in the download section

---

### Post by Sir Jasper on 2009-11-29
Hi,

I assume you could use a live CD (8.10 or 9.04) if you have one.

If not, I have no other ideas, - so try Sunny´s suggestion.

My regards

---

### Post by toagathonen on 2010-01-22
> **K7AAY said:**
> Following the install directions to add IE6 to Wine 1.01 in Karmic Koala at 
[http://www.tatanka.com.br/ies4linux/page/Installation](http://www.tatanka.com.br/ies4linux/page/Installation)
fail with this error message. 
 
[INDENT]The program 'ies4linux-gtk.py' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadRequest (invalid request code or no such operation)'.
(Details: serial 10945 error_code 1 request_code 0 minor_code 0)
(Note to programmers: normally, X errors are reported asynchronously;
that is, you will receive the error a while after causing it.
To debug your program, run it with the --sync command line
option to change this behavior. You can then get a meaningful
backtrace from your debugger if you break on the gdk_x_error() function.)
[/INDENT]Are there alternate instructions which work?
I got exactly the same error message using Wine 1.1.36 in Ubuntu 9.10.
 
Is there an alternate solution for this case?  Or should I change to Ubuntu 9.04 and use wine 1.0.1?

---

