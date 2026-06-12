---
title: "Pulling my hair out trying to get wireless to work"
date: 2007-03-26
forum: Networking &amp; Wireless
---

### Post by cknight on 2007-03-26
Hi folks,

I'm using a Netgear WG311T pci card to connect to my router.  This combination worked out of the box using broadcast SSID and no encryption.  I'm now trying to create a more secure network and am failing miserably.   Here are the scenarios:

Disabling SSID broadcasting works so long as I don't also try getting encryption to work.  
I can get 64 bit WEP to occasionally work, but only if I enable SSID broadcasting
After getting 64-bit WEP to occasionally work, I changed the router to 128-bit (without changing anything on my Kubuntu wireless settings) WEP encryption and it just wouldn't connect.

What gives?  Can anyone help?

Here's some info:
lspci gives:
```
01:0a.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
```

```
cknight@cknight-desktop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp
wireless-essid mySSID
wireless-key s:wepkey

auto wlan0
iface wlan0 inet dhcp

```

---

### Post by Floppyjoe on 2007-03-26
I usually add the following lines to get my connection to work:
```
wireless-channel 7
wireless-mode managed 
```
Where I would substitute the channel of your router for 7
This may or may not help you.

---

