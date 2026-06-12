---
title: "can't get 10.4 to install"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by hemidood on 2010-06-13
Hello all, I'm brand new to this forum and Ubuntu in general. Here's my problem, I downloaded 10.4 burned ISO to a DVD, everything looks good. When I reboot it starts to install but after a minute of the scrolling dots, screen goes blank and then nothing, except for the screen gets activated then goes off every few seconds. Bear in mind that if you offer a solution that involves adding command lines please tell me exactly how to do that. 1 more thing is my machine is a 64 bit intel system, the download for 64 bit shows AMD, should I attempt to install that versus 32?
 
TIA Bill

---

### Post by apjone on 2010-06-13
Best off trying the 32bit install for now, 64-bit can sometimes be a bit troublesome.

---

### Post by bruno9779 on 2010-06-13
If your machine is 64 bit, you should install a 64 bit distro. AMD64 is the standard label for this.

Nonetheless, you can install 32 bit OS on 64 bit system.

I would try to install the alternate iso:

[http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-amd64.iso.torrent](http://releases.ubuntu.com/10.04/ubuntu-10.04-alternate-amd64.iso.torrent)

from canonical website:

> Alternate installer details

The text-based alternate installer can be downloaded from the complete list of download locations below. This installation CD is suited for computers unable to run the graphical desktop based installation, either because their computer does not meet the minimum requirements for the live cd or because their computer requires configuration after the installation is complete in order to use the desktop.

---

### Post by bruno9779 on 2010-06-13
BTW, I have found only the .torrent link

---

### Post by Sef on 2010-06-13
> Best off trying the 32bit install for now, 64-bit can sometimes be a bit troublesome.


So can the 32-bit.  I would suspect failure to check the download or a bad burn, or possible the OP needs to use the alternate cd.

> Bear in mind that if you offer a solution that involves adding command lines please tell me exactly how to do that. 1 more thing is my machine is a 64 bit intel system, the download for 64 bit shows AMD, should I attempt to install that versus 32?

A few questions:

1) How did you download: from Ubuntu's servers or via a torrent?

2) If from Ubuntu's servers, did you md5sum the download?

3) What are your system specs, including your graphics card?

And a comment:

4) The alternate cd is very easy to use.  The only hard part for someone new is if you will manually partition, but there are options for a full disk install.

---

### Post by hemidood on 2010-06-13
Downloaded from Ubuntu's site, you got me with the md5sum, system: Asus P6T Deluxe V2, 6 gig ram, Intel i7 overclocked to 4.43, ATI 5850 video card, 2 drives a 160 gig ssd, and 1 terrabyte standard drive the one I want to install to.

---

### Post by hemidood on 2010-06-13
The alternate cd install did it I got it to install, thanks for all of your help.

---

