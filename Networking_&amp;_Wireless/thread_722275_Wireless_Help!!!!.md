---
title: "Wireless Help!!!!"
date: 2008-03-12
forum: Networking &amp; Wireless
---

### Post by fatalflight on 2008-03-12
Need Help, can someone guide me through installing Network Manager step by step, ive just installed the latest Ubuntu Distro and cant figure it out, (BTW im a mega linux n00b, dont know owt)

---

### Post by rustybronco on 2008-03-12
Kevdog's finest...
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by prshah on 2008-03-12
> **fatalflight said:**
> Need Help, can someone guide me through installing Network Manager step by step, ive just installed the latest Ubuntu Distro and cant figure it out, (BTW im a mega linux n00b, dont know owt)

What version of Ubuntu, and what network card? Most network cards are working out of the box with Ubuntu now.

Version:
```
uname -a
```

What network card?
```
lspci | grep -i network 
```

and do you want to connect to a network, or just the Internet?

---

### Post by prshah on 2008-03-12
> **rustybronco said:**
> Kevdog's finest...
[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

You may NOT need ndiswrapper... better to try the other small steps before this big one.

---

### Post by rustybronco on 2008-03-12
> **fatalflight said:**
> Need Help, can someone guide me through installing Network Manager step by stepas was asked...
I don't know what methods or even if he did try to use the built in drivers.

I give people some credit due.

---

### Post by fatalflight on 2008-03-12
> **prshah said:**
> What version of Ubuntu, and what network card? Most network cards are working out of the box with Ubuntu now.

Version:
```
uname -a
```

What network card?
```
lspci | grep -i network 
```

and do you want to connect to a network, or just the Internet?

I need to connect to my DRAYTEK VIGOR 3800G router for internet access, ive tried connecting using the in built network thing on ubuntu but it doesnt work, ive read posts about NetworkManager and no one gives a clear guide, stage by stage of how to get it From downloading it all the way to finishing install and it working. I know so little about how linux works that until I start getting use to it I need some basic tutorials on the basics. If anyone knows of a guide of installing NetworkManager from start to finish I would be grateful as anything.:popcorn::popcorn:

Intel Wireless 2200BG (802.11 b/g) or Broadcom 802.11/b/g WiFi card

Im not 100% which, Id say its the broadcom most likely but slim chance its the Intel.

---

### Post by rustybronco on 2008-03-12
> **fatalflight said:**
> ive read posts about NetworkManager and no one gives a clear guide, stage by stage of how to get it From downloading it all the way to finishing install and it working. I know so little about how linux works that until I start getting use to it **I need some basic tutorials on the basics.** If anyone knows of a guide of installing NetworkManager from start to finish I would be grateful as anything.:popcorn::popcorn:

Intel Wireless 2200BG (802.11 b/g) or Broadcom 802.11/b/g WiFi card

Im not 100% which, Id say its the broadcom most likely but slim chance its the Intel.applications>accessories>terminal then type in **lspci | grep -i network** cut and past the output of what you get back here.

did you have a look at Kevdog's guide yet?

basics...[https://help.ubuntu.com/](https://help.ubuntu.com/) choose your required version at the top. 6.06, 7.04, 7.10 ect.

Welcome and don't be afraid to ask questions.

---

### Post by prshah on 2008-03-12
Fine, let's take it step by step:

Step 1: What is your ubuntu version.

a) Click on (Top left hand corner) Applications-Accessories->Terminal.
    OR if you dont have "Applications"
b) press "ctrl+spacebar" and type using the keyboard "konsole" then press enter
    OR if nothing shows up when pressing Ctrl+Spacebar,
press Alt+F2 and type in "gnome-terminal" and press enter.

At this point a (black) new window will come up.

In that window, type ```
uname -a
``` and tell us what it replies.

Then in the same window type ```
 lspci | grep -i network
``` "|" on your keyboard may be a vertical line with a break in the middle sort of like:

> 
|
|


or it may just be a vertical line, usually with the "\" key.

then tell us what it says.

After this we will have some definite information to go on and we can then clear your problem up fast.

---

### Post by fatalflight on 2008-03-12
Okay,

first line responds:

Linux laptop1 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT i6
86 GNU/Linux

2nd line responds:
06:05.0 Network Controller: Braodcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Contoller (rev 02)

thats what i get, so yes it is broadcom. Ive recently installed all the WLAN related software and they connect to my router but dont excahnge info or anything like that (doesnt even register as having signal) and ive got NetworkManager now (idiot moment)

Also, id like to say thanks to everyone trying to help me, really grateful!!!:KS:KS

---

### Post by fatalflight on 2008-03-13
Hi, ive been doing more reasearch and i found this by accident but luck, I havent tried it yet but im posting its link to help anyone searching for the same thing I am. It may help it may not!

[http://en.opensuse.org/Ndiswrapper_howto](http://en.opensuse.org/Ndiswrapper_howto)

:guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar::guitar:

---

### Post by prshah on 2008-03-13
> **fatalflight said:**
> Okay,

first line responds:

Linux laptop1 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT i6
86 GNU/Linux

2nd line responds:
06:05.0 Network Controller: Braodcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Contoller (rev 02)

thats what i get, so yes it is broadcom. Ive recently installed all the WLAN related software and they connect to my router but dont excahnge info or anything like that (doesnt even register as having signal) and ive got NetworkManager now (idiot moment)

Also, id like to say thanks to everyone trying to help me, really grateful!!!:KS:KS

Is your problem solved now? if not, now on to the next step.. post the results of ```
cat /proc/net/wireless
```

---

### Post by fatalflight on 2008-03-14
Ibter-| sta-|    Quality         |   Discarded packets                | Missed | WE
 face | tus | link level noise |  nwid  crypt  frag  retry  misc  | beacon | 22
  eth1: 0000  0. -256. -256.           0       0      0        0        0            0

---

