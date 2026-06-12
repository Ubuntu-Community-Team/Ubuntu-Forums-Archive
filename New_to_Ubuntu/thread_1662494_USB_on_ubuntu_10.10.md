---
title: "USB on ubuntu 10.10"
date: 2011-01-08
forum: New to Ubuntu
---

### Post by daveboy23 on 2011-01-08
hi, i've searched a couple of places already and couldn't find an answer (this is my way of saying sorry if this thread already exist and solved).

i just installed ubuntu 10.10 (and updated everything) and for some reason the memory sticks (AKA USB) are not working.
can anyone tell me how to solve this?
btw - in other threads i found they talked about a floppy being in the way (or something) - i don't have that, it's a laptop (toshiba satellite A215-S4807)

thanks everyone

---

### Post by khelben1979 on 2011-01-08
> **daveboy23 said:**
> i just installed ubuntu 10.10 (and updated everything) and for some reason the memory sticks (AKA USB) are not working.
can anyone tell me how to solve this?

```
lsusb
``` from a terminal will tell us if the USB devices gets detected. Let us know what happens with that.

Are you using [GNOME]("http://en.wikipedia.org/wiki/GNOME") as desktop?

---

### Post by daveboy23 on 2011-01-09
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

this is what i get when i connect the USB stick.  and yes, i am using Gnome

---

### Post by NickJones on 2011-01-09
I know it may seems simple, but have you tried different USBs and different USB ports?

---

### Post by daveboy23 on 2011-01-09
yap, tried diff ports and diff USB's

---

### Post by khelben1979 on 2011-01-09
Now we know that your Ubuntu stick gets detected by the system. From the looks of it, I think your USB stick does not mount by itself and this the problem.

To solve the problem, you haveto mount it manually. To be able to do that, you need to know which device name that the usb stick gets once connected physically to your PC.

Try the instructions provided by [this webpage]("http://linuxhelp.blogspot.com/2007/03/steps-to-manually-mount-usb-flash-drive.html").

---

### Post by daveboy23 on 2011-01-09
this is a problem though - the same stick is used on another computer of mine with ubuntu and it does autoload there (the computer with the 32bit OS doesn't autoload it, while the 64bit OS does)

that is the only diff i could think of between the 2 computers
is there a way to cause it to autoload? as this computer is left for my girlfriend and she's not so tech-oriented

thanks guys

---

### Post by amjjawad on 2011-01-09
> **daveboy23 said:**
> i just installed ubuntu 10.10 [COLOR=Red]**(and updated everything) **[/COLOR]and for some reason the memory sticks (AKA USB) are not working.

If I remember correctly, I have read some where here that update should not be made "IF" Ubuntu is installed on USB Drive. Perhaps I'm confusing this with another issue but that's what I'm sure I read it some where.

---

### Post by khelben1979 on 2011-01-09
How about creating a script from the webpage I mentioned? Then she just needs to run that script. That's how I did myself a long time ago.

---

### Post by daveboy23 on 2011-01-09
well, i thought of something more elegant then a script - like an actual fix.  let's be real here - if these stupid small bugs are going around it's going to be very hard to tell people how ubuntu is better then windows.  yes, her computer is faster and everything is fine, but if i can't connect any USB sticks to it we're going to have to go back to windows...

isn't there any fix that can solve this once and for all?

---

### Post by khelben1979 on 2011-01-09
An actual fix would be to install KDE and use that instead of GNOME. That's where the problem is.

Another fix is to configure GNOME so that the USB memory automounts or find out if there are any missing packages in the Ubuntu system which is the reason to why GNOME behaves this way.

It's very bad that Ubuntu 10.10 behaves this way, but from my experience, problems like these can sometimes get solved by installing packages which are needed for additional functions to the Ubuntu system. It should work by default.

---

### Post by daveboy23 on 2011-01-10
thank you very much for answering me.  tried KDE and it works great.

too bad these little bugs are still present in ubuntu at least the OS saves itself by having such a great community.

thank you so much again

---

### Post by khelben1979 on 2011-01-10
You're welcome! :)

---

### Post by amjjawad on 2011-01-10
> **daveboy23 said:**
> too bad these little bugs are still present in ubuntu at least the OS saves itself by having such a great community.


NO OS is perfect. Sad but true.

I always avoid 10.10 and prefer 10.04. At least, it's LTS.

Good job you managed to fix it ;)

---

### Post by daveboy23 on 2011-01-13
yeah, but i don't deserve any respect for it.

basically, re-install the entire system, or use KDE.

not the best solved but solved to me.

thanks everyone for helping

---

### Post by amjjawad on 2011-01-14
> **daveboy23 said:**
> yeah, but i don't deserve any respect for it.

basically, re-install the entire system, or use KDE.

not the best solved but solved to me.

thanks everyone for helping

**"I did not fail, I found 10,000 ways that did not work".**

In your case, it did work so don't underestimate yourself :)

---

