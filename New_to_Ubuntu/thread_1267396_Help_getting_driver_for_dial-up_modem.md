---
title: "Help getting driver for dial-up modem"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by coldReactive on 2009-09-15
The modem is **56K ITU v.92-ready Fax/Modem**, which is not supported by Ubuntu by default. Is there ANY DEB package for this? The computer this is on has no Internet otherwise, and currently has Windows installed, but would love to migrate it to ubuntu.

The computer itself is a eMachines T5026. The ethernet is obviously supported.

---

### Post by Whiffle on 2009-09-15
You're gonna need more information.  ITU v.92 is the standard, 56K is the speed, and its a Fax/Modem.  It doesn't really tell us anything about the hardware.  Can you get some lspci and lshw output for it using a live cd?

---

### Post by coldReactive on 2009-09-15
> **Whiffle said:**
> You're gonna need more information.  ITU v.92 is the standard, 56K is the speed, and its a Fax/Modem.  It doesn't really tell us anything about the hardware.  Can you get some lspci and lshw output for it using a live cd?

It'll have to be some other time, the computer is being used by someone else now, so I'll have to wait until they're gone, which won't be for several days. I'll reply back then.

---

### Post by corncob on 2009-09-15
When I had dial up I used to connect with gnome-ppp.  You can download and install it in Synaptic.  I used a US Robotics hardware modem at the time.  It doesn't recognize win modems

---

### Post by Whiffle on 2009-09-15
Yeah a hardware modem is really the way to go with linux.  If you've got a Goodwill Computerworks near you they probably have one.  I bought one for a project off ebay for $10, and its been working flawlessly for over a year, and was MUCH easier to setup than any winmodem.

---

### Post by coldReactive on 2009-09-15
> **Whiffle said:**
> Yeah a hardware modem is really the way to go with linux.  If you've got a Goodwill Computerworks near you they probably have one.  I bought one for a project off ebay for $10, and its been working flawlessly for over a year, and was MUCH easier to setup than any winmodem.

The modem is internal actually, and we have no Goodwill Computerworks, just goodwills. But yeah, when I get the time, I'll get the output of that.

---

### Post by corncob on 2009-09-16
An internal modem can still be a hardware modem.  Give gnome-ppp a try when you get your computer back.  Maybe you'll luck out.

---

### Post by coldReactive on 2009-09-16
Here's the computer's lshw and lspci

---

### Post by Whiffle on 2009-09-16
Search for HSF and conexant and you'll find all the information you want on that thing.  Its a winmodem.

---

### Post by coldReactive on 2009-09-16
> **Whiffle said:**
> Search for HSF and conexant and you'll find all the information you want on that thing.  Its a winmodem.

It's unfortunate that when I do the update manager, my kernel will be upgraded, so what two drivers should I download: [http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php](http://www.linuxant.com/drivers/hsf/full/downloads-ubuntu-x86.php)

---

### Post by cariboo on 2009-09-16
Have a look [here]("https://help.ubuntu.com/community/DialupModemHowto"), it helped me setup an intel modem for a fax server.

---

### Post by rob86 on 2009-09-16
It took me days to get my dial up modem working on Ubuntu. I had to install drivers, and do some weird stuff I don't remember, like editing a conf and adding lines that didn't make sense to me. I did get it working though, miraculously.

If you get frustrated and desperate, check out PuppyLinux. I'm not saying switch to it from Ubuntu (they're not in the same league..puppy linux is a light weight OS), but the dialup support on that is excellent, and  I wonder if you could somehow get it's dialer from it. I don't know how it works. What took me days in Ubuntu, searching for drivers, editing confs, downloading wvdial, gnome ppp, and other stuff, took me an entire 10 secods on Puppy Linux. I booted up the live cd, It said something along the liens of, "Hey, you have a dialup modem, want to set it up?" and I said sure. and It was like, this is your initialization code, want to connect? and It connected. I didn't even need to download drivers. Don't get me wrong, Ubuntu's great, but I wish it had PuppyLinux's dialup support.. :)

---

