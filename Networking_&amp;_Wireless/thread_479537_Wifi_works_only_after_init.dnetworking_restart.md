---
title: "Wifi works only after init.d/networking restart"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by andb on 2007-06-20
What I would like to know is how to set up wifi networking to work on booting without my nasty hack.

I have an Atheros card in my 6.10 Edgy workstation. When the machine boots, the card is recognized but doesnt actually connect to the network. It seems to be stuck at the encryption level. My hack of a fix was to throw a script into /etc/rc2.d/ to restart networking. Nothing special, /etc/rc2.d/S99network is just a restart:
```
/etc/init.d/network restart
```
Now it works on booting. It seems to me that something is being started too early, since everything works once its up and running. I'd like to understand better what is really happening here so that I can make it work right, instead of just having work right now. Thanks for any advice or references to material that will help to sort this out.


```
$lspci | grep Ethernet
00:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
```

by the way, if I switch from static to DHCP, the client does not receive a response, until the networking restart command is issued.
```
$cat /etc/network/interfaces
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

auto ath0
#iface ath0 inet dhcp

iface ath0 inet static
address 192.168.1.52
gateway 192.168.1.11
dns-nameservers 192.168.1.11
netmask 255.255.255.0

wpa-driver madwifi
wpa-ssid dd-wrt
wpa-ap-scan 1
wpa-proto WPA
pa-pairwise TKIP 
wpa-group TKIP
wpa-key-mgmt WPA-PSK
wpa-psk myKeyIsHere
```

---

### Post by moron on 2007-06-22
For what it is worth, I'm experiencing the exact same behaviour under Feisty.

---

### Post by kevdog on 2007-06-22
Im not sure of the root cause either, however it seems your type of hack has been employed elsewhere:
[http://ubuntuforums.org/showthread.php?t=318539](http://ubuntuforums.org/showthread.php?t=318539)

Sorry that doesnt help you much, but many many other people have also noticed this behaivor

---

### Post by PReDiToR on 2008-02-12
Find a file called 'rc.local'. Try 'sudo updatedb', then 'locate rc.local'. It should be in '/etc' somewhere depending on your version.
If you don't have one, this hack won't work for you.

'cd' to the location of the file, then 'sudo vi  rc.local'. 

Go down until you get to 'exit 0' and press 'insert'

Type 'ifdown eth1', press return then type 'ifup eth1'.
Press 'Escape' then ':wq' (colon, w then q).

Reboot and your WiFi should come up on boot. It did for me on gOS 2 beta (Gutsy based I believe).

As a (primarily) openSUSE user I was looking for sysconfig, and am having great fun with Ubuntu.

---

