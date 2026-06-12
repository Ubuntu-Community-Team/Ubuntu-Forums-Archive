---
title: "D-Link DWL-G520 problems"
date: 2005-05-14
forum: Networking &amp; Wireless
---

### Post by rjanik on 2005-05-14
This is a bit of a two part problem.  

1) I installed the DWL-G520 card but Ubuntu did not recognize it (according to the Ubuntu wiki this card is suposed to be auto detected by the OS).  Is there something I didnt do?  

2) In order to remedy the problem I installed ndiswrapper and used the provided driver (followed the instructions on the Ubuntu wiki).  I got the computer connected to the network and I saved the session.  But now the computer takes for ever to boot up.  

I would prefer not to have to use ndiswrapper but if I must is there a way to ensure that the modual loads into the kernal at boot up with out this extremely long boot time.  Any help would be greatly appreciated.

---

### Post by FreeEagle on 2005-05-21
i hope this will help you to figure out how to make it work..
 
[http://www.wearablelinux.org/modules.php?name=Forums&file=viewtopic&t=15#192](http://www.wearablelinux.org/modules.php?name=Forums&file=viewtopic&t=15#192)

FreeEagle

---

### Post by kleeman on 2005-05-21
What does your /etc/network/interfaces have in it? You may need to disable sections which automatically bring up the wired (an unconnected) interfaces.

---

### Post by NateC on 2005-05-21
I use that card.. auto-detected for me... you have to enable it in the system > Administration > networking.

---

