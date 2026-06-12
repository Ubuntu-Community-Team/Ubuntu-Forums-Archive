---
title: "Can see, but cannot connect to wireless networks with bcm4306 (powerbook g4)"
date: 2006-11-17
forum: Networking &amp; Wireless
---

### Post by blackjml on 2006-11-17
Hello,

After following the instructions in [http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174), I can see the wireless networks in my area (using 'iwlist eth0 scan' and network-manager), but I cannot connect to any of them.

I've tried reconfiguring my own network with no encryption, WEP and WPA2 -- all with no success.

The bcm43xx pages say that my card is supported. Many people have had success with this chipset. However, many people also seem to have had this problem.

I have yet to try using ndiswrapper. I'm not even sure if it's possible with a powerbook.

I've tried using wifi-radar -- same problem.

I am about to try shutting down my router and computer for fifteen minutes just in case.

I'm banging my head against a wall, and would appreciate any help I can get.

---

### Post by blackjml on 2006-11-17
I forgot to mention. syslog seems to have a bunch of useful information, which I can post on request.

---

### Post by gpierce on 2007-07-29
Did you ever get wireless up and running? I seem to be having the exact same problem.

---

### Post by kevdog on 2007-07-30
Is your router broadcasting its essid??

What does 
iwlist eth0 scan
show?

Can you post some of the errors you are getting??

---

### Post by blackfly on 2007-07-30
My Dell Inspiron with Broadcom 4318 is doing the same thing.  Don't know why.

---

### Post by carpespasm on 2007-07-30
my compaq presario 2195US has the same issue

EDIT: got it working thanks to this thread: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)

---

### Post by gpierce on 2007-07-30
> **gpierce said:**
> Did you ever get wireless up and running? I seem to be having the exact same problem.

Yes, I can see the wireless networks near me and I can connect to the un-encrypted ones but not the WPA-encrypted networks.I am running gnome on G4 Apple Powerbook. The issue seems to be related to the Power PC architecture. I read a thread in the fedora forum that the problem is "endianness." Big vs little endianness, I think. I will try to provide a link. This problem is recent. A lot of people are reporting problems with Network Manager on  PPC computers. 

Greg

---

### Post by gpierce on 2007-07-31
Here's a link to similar problem:

[http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=213088](http://bugzilla.redhat.com/bugzilla/show_bug.cgi?id=213088)

Greg

---

