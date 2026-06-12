---
title: "[SOLVED] Trouble Installing ndiswrapper"
date: 2007-07-22
forum: Networking &amp; Wireless
---

### Post by Azslande on 2007-07-22
I am trying to install ndiswrapper and I am running into a problem. I am following the method described here [at this postt=197102]("http://ubuntuforums.org/showthread.php?t=197102"). I get everything going then the install just kinda stalls out. I get to the following and it never progresses.

```
Starting ndiswrapper install...
If you have any package managers open (i.e. Adept or Synaptic or apt-get),
Please close them now.
Pausing for 10 seconds - please read the message.
Feisty release detected.
Installing ndiswrapper-1.9...

```

Any ideas?

Currently I am hooked up via an ethernet cable. The card IS plugged in. It is a Linksys WPC54GS, and I am using a Dell Inspiron 2200. lspci outputs the following.

```
03:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

---

### Post by Azslande on 2007-07-22
Nevermind... For some reason, I exited the Terminal this time and Synaptic popped open. I ran the terminal again, closed Synaptic and it followed through.

---

