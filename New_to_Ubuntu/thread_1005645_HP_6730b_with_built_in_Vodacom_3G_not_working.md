---
title: "HP 6730b with built in Vodacom 3G not working"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by Meezy on 2008-12-08
Hi All,

):P

I am a newbie to ubuntu, I installed ubuntu 8.10 Intrepid on my HP 6730b and can't get my Vodacom 3G card working.  Could someone please help, I don't know where to start.  I have these modems in my Windows device list:

Agere Systems HDA Modem
HP un2400 Mobile Broadband Module Modem

Thanks in advance.

Meezy

---

### Post by el Buffo on 2008-12-10
> **Meezy said:**
> 
I am a newbie to ubuntu, I installed ubuntu 8.10 Intrepid on my HP 6730b and can't get my Vodacom 3G card working.  Could someone please help, I don't know where to start.  I have these modems in my Windows device list:

Agere Systems HDA Modem
HP un2400 Mobile Broadband Module Modem


Same Problem here. The "HP un2400" is not visible by lsusb etc. The same thing on Windows. HP Connection Tool shows the card as "powered off". On Windows the Card (un2400) must be enabled by HP Connection Tool. After that the card is recognized by Windows and visible in Device Manager as USB Devise.

It seems the card is "powered off" and must be enabled first. Don't know how to enable under Linux.

Any Ideas?

EDIT: "modprobe hp-wmi" does the trick! The card is now visible by lsusb. Going to test...

Greetings!
el Buffo

---

### Post by el Buffo on 2008-12-11
The card is visible, but i can't use it.
Seems there is no driver for the Qualcomm Gobi working on the Card.
I've tested with "modprobe usbserial vendor=0x03f0 product=0x201d" but it will not work.

Any idea?

---

### Post by Meezy on 2008-12-12
Hi el Buffo,

I don't have a clue, I found some sites which I am going to have a look into more detail.   [https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262498](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/262498)

I don't know if it's going to work, but I'll see what happens.

Thanks for the response, I almost thought that I was alone out there!

I'll keep you posted on my findings


I can now see the card when I use lsusb, unfortunately it still doesn't work.  Is there no one from ubuntu we can chat to about this.

---

### Post by el Buffo on 2008-12-18
Hallo Meezy,
today i tried to modify option.c to recognize the un2400.
[http://ubuntuforums.org/showthread.php?p=6393445#post6393445](http://ubuntuforums.org/showthread.php?p=6393445#post6393445)

But i'm not a driver developer ;)

Greetings!
el Buffo

---

