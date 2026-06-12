---
title: "Unable to change rmem value: please help!"
date: 2007-04-20
forum: Networking &amp; Wireless
---

### Post by jefferson7 on 2007-04-20
Hi all
I'm simply trying to change **rmem** value to a higher value.
Tried on ubuntu/kubuntu 6.06, 6.10 and 7.04 (tried on Mandriva too) without success.
I checked my current rmem by using [SpeedGuide.net]("http://www.speedguide.net") TCP analyzer tool, and I found that the default rmem value is 5888. It's very low.

This is what I done:

- added
[INDENT]sysctl -w net.core.rmem_max=511104[/INDENT]
[INDENT]sysctl -w net.core.rmem_default=511104[/INDENT]
to [FONT="Courier New"]/etc/rc.local[/FONT]. No success.


- added
[INDENT]echo 511104 > /proc/sys/net/core/rmem_default[/INDENT]
[INDENT]echo 511104 > /proc/sys/net/core/rmem_max[/INDENT]
to [FONT="Courier New"]/etc/rc.local[/FONT]. No success.


- added
[INDENT]echo "4096 511104 511104" > /proc/sys/net/ipv4/tcp_rmem[/INDENT]
[INDENT]echo "4096 16384 4194304" > /proc/sys/net/ipv4/tcp_wmem[/INDENT]
to [FONT="Courier New"]/etc/rc.local[/FONT]. No success.


- then I added
[INDENT]net.core.rmem_max=511104[/INDENT]
[INDENT]net.core.rmem_default=511104[/INDENT]
to [FONT="Courier New"]/etc/sysctl.conf[/FONT]. No success.


- and finally added
[INDENT]net.ipv4.tcp_rmem=511104[/INDENT]
[INDENT]net.ipv4.conf.default.tcp_rmem=511104[/INDENT]
to [FONT="Courier New"]/etc/sysctl.conf[/FONT]. No success.

I found these informations on this and other forums. All informations I found are concordant.

At this point, I have no more attempts :( 

**Please, help me to change rmem!**

THANK YOU

---

