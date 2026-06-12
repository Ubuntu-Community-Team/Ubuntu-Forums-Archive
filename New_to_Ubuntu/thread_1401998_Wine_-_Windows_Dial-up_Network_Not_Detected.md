---
title: "Wine - Windows Dial-up Network Not Detected"
date: 2010-02-08
forum: New to Ubuntu
---

### Post by bi11 on 2010-02-08
Day 2 with my reconfigured Ubuntu computer. Installed Wine, downloaded a VPN program that has to have Windows, but the install fails saying "Windows dial-up Networking Not Detected (have Firefox connection).  HELP!

---

### Post by cariboo on 2010-02-08
Why are you trying to setup a dial up connection in Wine, that won't work. Have a look at this [how to]("https://help.ubuntu.com/community/DialupModemHowto").

---

### Post by DaveInPhx on 2010-02-09
I set the PC up for Bill, using Hardy as the install OS due to problems with the onboard video card, (now partially resolved).

The problem he has is that while running in Ubuntu, the PC access the network and internet via the external router, and obtains it's IP address from there.  After installing Wine, which he needs for a proprietary application, the application is not detecting a network interface and is prompting for a dial-up connection - he doesn't need dial-up, he already has a broadband connection available and working under Linux.

This is a bit beyond me too, so I suggested that he ask here for help. Meanwhile I'm scouring the web trying to find answers for this.  We already checked /etc/hosts and it contains the default loopback address.

---

