---
title: "Getting ENV 2 to get mounted?"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by Kafubie on 2010-05-17
I connected the phone through USB.
It didn't recognize it.

I did lsusb, I got
Bus 002 Device 003: ID 1004:6000 LG Electronics, Inc. VX4400/VX6000 Cellphone

So it recognizes....  How would I be able to get pictures and poo off of my phone on ubuntu 10.04?

---

### Post by Peter09 on 2010-05-18
Hi,
might be worth telling us what version of Ubuntu you are using.
 
Does your phone pop up with a box asking how it should present itself - normally you have options for storage, modem etc.

---

### Post by Kafubie on 2010-05-18
> **Peter09 said:**
> Hi,
might be worth telling us what version of Ubuntu you are using.
 
Does your phone pop up with a box asking how it should present itself - normally you have options for storage, modem etc.

I have 10.04.
The phone doesn't present it's self.
Never gave me a option too anyways.
Maybe the phone is just incompatible. :(

---

### Post by Kafubie on 2010-05-18
bump

---

### Post by Kafubie on 2010-05-19
I'm just going to bump this everyday.

---

### Post by Peter09 on 2010-05-20
What model of phone is it?

---

### Post by Programmer210 on 2010-07-23
> **Kafubie said:**
> I have 10.04.
The phone doesn't present it's self.
Never gave me a option too anyways.
Maybe the phone is just incompatible. :(

I'm having the same problem. I'm running an up-to-date 10.04, 64 bit. When I plug in a normal USB stick, it is recognized fine, and Nautilus pops up. When I plug in my LG Keybo (9100, Env2) from Koodo (part of Telus), there is activity seen in /var/log/syslog, but it is not recognized as a USB storage device. The phone asks if I want it to go into USB storage mode, and I say "yes". That triggers /var/syslog activity too. However, the last entry I see says "waiting for device to settle".

If I turn off the "usb mass storage" in the phone, and run BitPim as root, it can communicate with the phone, and get various stuff from it, but it won't get images. I'm left with taking out the microSD card, and plugging it into a stack of 2 adapters into a USB port, in order to get pictures and movies from it. I'd rather not have to do that. I can provide syslog output if required.

As a separate issue, which is not my concern right now, I've tried the uddev stuff that the BitPim docs talk about, and it doesn't work for me.

---

### Post by science.copperfield on 2010-12-12
Bump!

---

### Post by llamabr on 2010-12-12
My father in law has the env touch.  The software in it is designed only to be used with some app that comes with the phone in the box, and runs on windows.  I spent a few hours trying to hack my way into it, then ultimately just took the sd card out and plugged it in.  so much easier.

I believe you'll fail any other way.  The hardware you bought was specifically designed to keep you from doing what you want to do.

---

### Post by sandyd on 2010-12-12
nope, I never got the env2 to mount.

I eventually transfered the files through bluetooth.

my cousin has the LG Keybo 2 (its called differently in different regions, LG Keybo 1 = ENV2), and that mounted perfectly 10 days ago. However, that may not be the case since I use a different linux setup (gentoo). I used udisks to mount it though KDE's solid interface. Both the phone's memory and the SD card shows up perfectly without fiddling (after changing it to mass storage mode)

---

