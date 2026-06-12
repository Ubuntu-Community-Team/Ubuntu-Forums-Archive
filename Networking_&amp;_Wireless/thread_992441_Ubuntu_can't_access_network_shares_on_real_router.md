---
title: "Ubuntu can't access network shares on real router"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by kaweka on 2008-11-24
Ubuntu 8.10 as guest. Windows XP pro sp3 as host.
Current version of VirtualBox. Networking via NAT.

In the real world Windows works in LAN controlled by FritzBox 7270 - it's a DSL Modem with router functionality. FritzBox runs as router.
FritzBox has also USB disk connected.
This drive is set be be shared with LAN clients.
Network share protected by password.
All clients in this LAN/WLAN can exchange files only using this share.
No direct interconnections between LAN/WLAN clients are allowed.

Ubuntu has no problems to access the internet.
But it can't access the network share of FritzBox.
Share is visible from Ubuntu's file/network explorer.
Double click leads to share password query.

After having entered proper share password an error message pops up:
"user name or password not correct".

Is this an internal issue of Ubuntu or rather a deal for VirtualBox ?



The guys/girls from VirtualBox forum are suggesting trying the Host Interface networking.
Will I need a kernel recompilation for the guest linux
in order to change from NAT to Host Interface ?
In other words, will the guest linux be able to accept new
network interface (Host Interface) without my intervention
on linux side ?
I know, this change is to be made on VirtualBox.
But how about guest linux ?

---

### Post by kaweka on 2008-11-25
any ideas ?
For every hints thank you very much in advance.

---

