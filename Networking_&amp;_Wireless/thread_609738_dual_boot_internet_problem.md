---
title: "dual boot internet problem"
date: 2007-11-11
forum: Networking &amp; Wireless
---

### Post by westcoasteagles on 2007-11-11
Hi.

Managed to get internet connection with 7.10 installed on a drive by itself, however, when I installed it on a dual boot machine with XP, I can't get an internet connection. It is on the same machine that I managed to get the connection when the OS was installed by itself. And XP can get connected on the dual boot drive - but 7.10 can't.

This is the result of doing an ifconfig...

sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:40:F4:5F:C4:15  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:5 Base address:0xee00 

 Any ideas?

---

### Post by ParanoiaPersonified on 2007-11-11
What ethernet adapter are you using? There is a [known issue]("http://ubuntuforums.org/showthread.php?t=538448") with certain Realtek adapters to do with WakeOnLan.

---

### Post by rpinwelly on 2007-11-11
I have pretty much the same problem, but with 7.04 (and with a live CD of 7.10). I posted on this in the thread [http://ubuntuforums.org/showthread.php?t=607276](http://ubuntuforums.org/showthread.php?t=607276).  Oddly enough, the internet connection originally worked jsut fine, but then it just got lost.

Haven't got a solution yet ... and being a total Linux newbie, I don't really know where to start... :-) any help with this would be greatly appreciated!

---

### Post by westcoasteagles on 2007-11-12
Hey ParanoiaPersonified!

Good work! Solved the problem. :guitar:

Thanks very much! :)

---

