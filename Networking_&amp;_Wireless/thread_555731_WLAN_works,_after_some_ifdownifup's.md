---
title: "WLAN works, after some ifdown/ifup's"
date: 2007-09-20
forum: Networking &amp; Wireless
---

### Post by Mastodront on 2007-09-20
Hi there, I hope I'm not too confusing, my English is pretty bad :)

I bought two wireless cards for me and my girlfriend a couple of weeks ago, Deltaco is the manufacturer and it's based on RTL8185.

The problem is that I can't make it work properly. 
It doesn't work with a native driver but with ndiswrapper with the WINXP-inf it seems to work fine - on my computer that's running Debian Unstable.

The girlfriends computer (tried Edgy, Feisty, Gutsy, and now trying Mint Linux 3.1) doesn't work too good though. It installs fine, and ndiswrapper says:
net8185 : driver installed
        device (10EC:8185) present (alternate driver: r818x)

The problem is that when I boot the computer, the "Link"-LED on the PC-CARD is dead. When I run "sudo ifdown wlan0" and "sudo ifup wlan0" once (sometimes a couple of times) it lights up and I get connected and everything works flawlessly (writing from the computer now).

I could live with this but my gf would be very annoyed while she don't know what a terminal - even less ifdown/ifup is. I would be very grateful if someone could help me with this, it's probably some small detail but I just can't seem to solve it.


--------------

I've read some threads on the topic on this forum and tried to put "ifdown wlan0" and "ifup wlan0" in /etc/rc.local but it doesn't help :(

---

