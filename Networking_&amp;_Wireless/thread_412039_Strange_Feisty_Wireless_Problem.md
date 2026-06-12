---
title: "Strange Feisty Wireless Problem"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by Ice2097 on 2007-04-17
So I installed Ubuntu 6.10 on an old laptop (Vaio PCG-f490) with a MN-720 PCMCIA wireless card in it. Internet didnt work at first, but after going through a ndiswrapper installation procedure, the card worked fine. I then upgraded to Ubuntu 7.04, and now I'm having a really strange problem: on boot, the card is powered on, and in Ubuntu it can detect and display all the wireless networks around me, but when I try to connect to one it always times out (neither of the gray "connection dots" turn green). The only way (that I have found) that I can get it to connect is to try to connect to a password protected network (with a random password) which gets one of the "connection dots" to turn green and then switch to my unprotected network, which will then connects fine.
Any ideas why this is happening? :confused:
Thanks

---

### Post by H.E. Pennypacker on 2007-04-17
Can you please try connecting to the Internet using Wicd Manager?  Sometimes, Ubuntu's default programs can be at fault.  You may be able to get it working using third-party software such as Wicd Manager.

[http://compwiz18.blackhole.cx/wicd/wb/](http://compwiz18.blackhole.cx/wicd/wb/)

---

### Post by RDAC on 2007-04-17
Did you try disabling then re-enabling wireless? If you did, sounds like we might have the same issue. Please let me know if the above solution (Wicd) solves your issue.

---

### Post by Ice2097 on 2007-04-17
Yeah, disabling and re-enabling wireless did nothing for me.
The Wicd program works great so far (I'll let you know if I have any problems).
Thanks!

---

