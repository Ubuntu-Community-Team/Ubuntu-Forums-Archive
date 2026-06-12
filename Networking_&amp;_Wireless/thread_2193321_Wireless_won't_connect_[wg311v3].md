---
title: "Wireless won't connect [wg311v3]"
date: 2013-12-12
forum: Networking &amp; Wireless
---

### Post by blackvdub97 on 2013-12-12
Hi, first off I'm new to the forums and new to Ubuntu. (I like it so far) Setting it up for my mom, cause she tends to break Windows :P

Anyway, I just installed the driver for the Netgear WG311v3 PCI card after much trouble with the Fatal: module ndiswrapper not found issue. Was able to get by that by doing this [http://askubuntu.com/questions/206082/how-do-i-compile-ndiswrapper](http://askubuntu.com/questions/206082/how-do-i-compile-ndiswrapper) and then install the driver through the gui fine. The wireless icon on the top taskbar recognizes it fine. But when I choose my network and put in my WPA key it just spins for a bit then the password window pops back up and won't connect. What do I need to do to fix this.

I am able to use my USB wifi adapter just fine, using it now.

If you need any more info let me know. I'll appreciate any help.

---

### Post by ajgreeny on 2013-12-12
Some of the Netgear adapters used to have a problem with WPA encryption, so it may be worth temporarily trying either no encryption or WEP, just to see if it is the WPA that causes the problem for you.  If you can get connected with one of those you can then search a bit further to see if you can figure out a safe answer.

Which of the WPA encryptions are you using?  I would suggest that WPA2 is the least likely to cause problems and therefore best to use.

---

### Post by blackvdub97 on 2013-12-12
OK, it did connect with encryption turned off. I was using WPA2. It connects with WPA - AES.

---

