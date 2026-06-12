---
title: "VPN problem with wireless"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by sfh1975 on 2007-05-06
dear friends,
i am a complete new convert to feisty so plz bear me for stupid questions. i am trying to connect to my university vpn using the usb wireless adapter netgear ma111v2 which i am using thourgh ndiswrapper or something like that. now the problem is that i dont even see the option to create a vpn when i click on the ntework manager icon. it only says manual network configuation. a file which might be helpful reads as below:
[PHP]auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto wlan0
iface wlan0 inet dhcp

iface wlan1 inet dhcp
wireless-essid ****** (my network password)

auto wlan1

iface ath0 inet dhcp

[/PHP]

please help me with this.
i am trying to connect to this network: [http://helpdesk.ugent.be/vpn/en/linux.php](http://helpdesk.ugent.be/vpn/en/linux.php)

thanks in advance,
Faisal
Berlin

---

