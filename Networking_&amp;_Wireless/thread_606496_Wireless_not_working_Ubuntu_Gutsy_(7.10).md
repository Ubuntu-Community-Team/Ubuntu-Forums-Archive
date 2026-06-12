---
title: "Wireless not working Ubuntu Gutsy (7.10)"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by JMC8501 on 2007-11-08
Hi,

I've always had problems with wireless on my laptop in the Ubuntu OS. I've recently upgraded to Ubuntu Gutsy Gibbon, but wireless is still not working. My wireless card is not the source of the problem. This is the problem:

I've never been able to get Network Manager to work. Neither the applet nor in terminal have ever gotten me results. However, the applet under the name "Network-Monitor" has always been around. This, I believe, is linked to "Network" under System->Administrator->Network. Sometimes this will show wireless networks, other times it will not, but there is no clear way to update which networks it sees, etc... Yet, using this I am able to connect to some wireless networks, but only the unprotected kind.

I tried installing other programs, most recently the much hailed "WICD," but this was also a disappointment. The applet also failed to work, and when I tried to connect to a network with WPA security, it absolutely failed to connect. In fact, I never could connect to any network using WICD. 

Please help me as I am new to Linux and am in need of guidance.

---

### Post by Waistless on 2007-11-08
In your wireless settings in the router for the network you're connecting to (assuming you're trying to get it working with a home network), is there a setting for the network mode with options such as G-Only or B-Only or Mixed? If you do make sure it's set to Mixed, Ubuntu seems to have problems with this sort of security.

Only thing I could think of, i'm not a network whiz :(


Hope it works, doing that solved my problems with wireless :)

---

