---
title: "need gnome-network-admin deb package for ubuntu 10.04 (for dial-up modem access)"
date: 2010-06-04
forum: New to Ubuntu
---

### Post by hanzj on 2010-06-04
Hello,
We are using Dial-up internet access for now. Ubuntu does not come out-of-the-box with phone-modem capabilities, and the help file said that I need "gnome-network-admin" package. Where can I get it?

Also, could anyone confirm what other packages I need to download and install to make the gnome-network-admin package work?

Can someone who is on a recently fresh-install of Ubuntu 10.04 tell me what ALL other packages apt-get or synaptic tells you to get? Thank you.


Thanks.

---

### Post by cariboo on 2010-06-04
The best place to look for packages, is [packages.ubuntu.com]("http://packages.ubuntu.com/").

---

### Post by hanzj on 2010-06-04
I did see that page, but the thing is I need to know all this because I'll be without internet access when I try to  get the modem issue working. That is why I would like to know what deb packages I need while I'm away from that computeur.

---

### Post by lkraemer on 2010-06-05
Hanzj,
There are a couple of questions you need to answer first:
1.  Are you planning on using the INTERNAL Win-Modem, or 
    an EXTERNAL Serial US Robotics Hardware Modem?  If
    you are going to try the Internal Win-Modem, you will
    need to start at [www.linmodems.org](www.linmodems.org) and contact Marvin
    and those folks for his script, and support for what
    that script reports.  Your EMAILS MUST BE in PLAIN TEXT,
    or they will be rejected.......Using a Winmodem will
    take several days and be a journey you may not want to
    attempt, it's up to you..........

2.  Are you going to use a Serial Port on your computer, or do
    you only have USB ports and will be using a USB to Serial
    converter to connect to the External Modem?

3.  Do you have access to the Internet via another computer running
    M$ using an established Dialup account?

If you don't have a Dialup account, Look for one that works well
with Linux.  Copper.net seems to work fine, as I have used it for
several years now.  Search forum for "Linux ISP's"

You ONLY need to download and install the following:
1. wvdial & dependencies......

You need to download wvdial and the following dependencies for 10.04.

wvdial & dependencies:
libuniconf4.6
libwvstreams4.6-extras
libwvstreams4.6-base

Located at:
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)
Select 10.04 -> Communications Programs -> wvdial 1.60.3
Download these with XP, then copy the *.deb files to USB Flash Drive,
& then to Ubuntu subdirectory /var/cache/apt/archives & then install
using Synaptic Package Manager.....ie.
```

sudo cp ~/Downloads/mydebs/*.deb /var/cache/apt/archives

```
OR you can go to SYSTEM -> ADMINISTRATION -> SOFTWARE SOURCES
and check the box for installable from CDROM/DVD.........then
insert your LiveCD and install from the CDR.

2. Gnome-PPP
   But wait until you have wvdial working before trying anything with
   Gnome-PPP.

Once this is done you will need to configure wvdial, add your specific
information to the configuration file, and then attempt a dialout.
More later.......

lk

---

