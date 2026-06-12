---
title: "Multiple wireless &amp; wired NIC setup headaches"
date: 2007-09-04
forum: Networking &amp; Wireless
---

### Post by darkwyrm on 2007-09-04
I'm having a problem setting up a server which sits between two different wireless networks. There are 2 D-Link DWL-G510s in the machine and with the Network Manager applet, I can connect easily to either network. Or at least I used to, anyways. After following the HOWTO on WPA and looking at the section on tweaking /etc/network/interfaces and wpa_supplicant.conf and playing with it for a while, nothing works now. :( Up to now, I only needed access to the one wireless network and the wired and easily had them set up with the Network Manager. Now I need access to all three networks.

One wireless network is WPA-PSK with a 192.168.0.x / 255.255.255.0 netmask and has Internet access. The other one is currently also WPA-PSK, but 172.16.0.x addresses and the same netmask, and it purposely does NOT have Internet access. The wired network is a 10.0.0.x network and is just used for network printing. I can easily ignore that one and let it do nothing, but it would be nice to have working.

Where should I go to get this working? I'm quite technical, but just not all that experienced with Ubuntu, and networking in particular.

---

### Post by darkwyrm on 2007-09-05
It seems silly replying to my own post, but I did manage to get the networking going with kwlan, so I know this can be done. Does anyone know how I could do something like what I described above using interfaces?

---

