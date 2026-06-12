---
title: "Massive problems installing Ubuntu Netbook Edition on Asus PX1001"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by md328 on 2010-10-15
Hey guys,

I just bought a Asus px 1001 netbook and am trying to install Ubuntu Netbook Edition 10.10 I have a  4G sandisk USB disk with (U3 Cruzar on it) that I'm trying to turn into a live USB. 

So far I've used the starup disk creator in Linux Mint (my desktop computer) which didn't seem to work at all. I've trtied using my roommates laptop which is running ubuntu to do the same thing. after I booted it up it gave me an error "system configuration could not be loaded" or and said something about syslinux (I am not a huge techie, so I have no clue what that could mean).  Next I tried using Unetbootin to create a live usb. Everything seemed to go fine as far as the unetbootin creation of the iso image. When I try to boot from the usb now, it seems to be doing something, then takes me to a Unetbootin screen that only gives me the options of Default and Back. If I hit default, it give me message "no init found. try passing init=bootarg

Busybox v1.15.3 (ubuntu 1:1. 15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of bulit-in commands.

(initramfs)" then it has a blinking cursor right next to this.

It seems like it does a little more when I hit Back, but it ultimately gives me the same message

Ok...so what the hell is going on?

---

### Post by viralmeme on 2010-10-15
> **md328 said:**
> I just bought a Asus px 1001 netbook and am trying to install Ubuntu Netbook Edition 10.10 I have a  4G sandisk USB disk with (U3 Cruzar on it
That maybe the problem, U3 is stored in a hidden partition flagged as a CD so as the U3 will load itself when you insert the USB device. Fire-up Qparted and delete the hidden partition.

---

### Post by md328 on 2010-10-15
Yeah I figured that is what it was, and I actually had another blank partition 2 gig flash disk that I used unetbootin on. Same thing happened when I tried to boot from it.  I'm not sure if would actually be the computer. Asus is notorious for using express gate which makes installing any distro a nightmare.  but this particular model doesn't seem to have anything like that.  I'm wondering if the may be some kind of encryption in the bios that prevents the usb drives from booting up properly?

Another option I do have is to break down and buy an external dvd-rom drive and install the liveDVD of ubuntu netbook that way. I tested it out and it does work on all the other computers in our place.  Obviously I would love to save the 40 or 50 some odd bucks on a dvd rom drive, so if anyone has any suggestions and a linux noob could comprehend, I would greatly appreciate it. 

Oh btw thanks viralmeme

---

### Post by md328 on 2010-10-16
SOLVED. Found this guide: [http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/](http://trentscott.com/2010/10/07/fixing-usb-install-issues-with-ubuntu-10-10-maverick-meerkat/)  Worked like a charm.

---

