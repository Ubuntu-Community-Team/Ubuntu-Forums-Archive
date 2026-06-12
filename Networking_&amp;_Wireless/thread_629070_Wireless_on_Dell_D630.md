---
title: "Wireless on Dell D630"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by Kleenux on 2007-12-01
I installed Ubuntu 7.10 Server on my Dell D630.

For some reasons the Wireless connection is not appearing in Network.

# iwconfig
[FONT="Courier New"]
lo        no wireless extensions.

eth0      no wireless extensions.
[/FONT]

# lspci
[FONT="Courier New"]
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
[/FONT]

# cat /etc/network/interfaces
[FONT="Courier New"]
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
[/FONT]


I guess it should be easily fixed... since there no much info on that in the forums for the D630. Maybe because I installed Server (then Desktop with apt-get)?

Note: the restricted drivers screen from System/Admin errors "need to install linux-restricted-modules-2.6.22-14-server" which is not available... (known problem) But maybe related?


Thank you for your help - I'm not used to wireless on Linux.

---

### Post by Kleenux on 2007-12-02
anybody?

---

### Post by registering on 2007-12-03
I don't know, but it may be because you used Server and not Desktop, like you said. I used Desktop and my wireless is extremely flaky; even my wired is not working well. After many attempts at fixing I'm downgrading to Feisty and see if things behave better. I have a D630 also. Good luck.

---

### Post by Kleenux on 2007-12-04
> **registering said:**
> I don't know, but it may be because you used Server and not Desktop, like you said. I used Desktop and my wireless is extremely flaky; even my wired is not working well. After many attempts at fixing I'm downgrading to Feisty and see if things behave better. I have a D630 also. Good luck.

Thanks :( 
Yes I'm using Server and "restricted drivers" was seemingly forgotten from the server distro...

Is there maybe a simple module available to get wireless working?

---

