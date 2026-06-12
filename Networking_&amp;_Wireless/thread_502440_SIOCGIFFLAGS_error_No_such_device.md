---
title: "SIOCGIFFLAGS error: No such device"
date: 2007-07-16
forum: Networking &amp; Wireless
---

### Post by jonnymccullagh on 2007-07-16
I have a wireless network adapter which had been working fine (and the same card in another PC with Ubuntu) but I have just noticed that the network manager is no longer working. When I click on it I get an error:
SIOCGIFFLAGS error: No such device
ifconfig -a shows the device as eth0:avah rather than ath0 as it had been.
I think I may have run the Update Manager before the trouble started and I would like to go back now. Trouble is I can't remember which updates I installed to even try to remove them (Someone in another thread suggested removing the latest kernel?). Anyone got any ideas? or can I amend some file somewhere to revert the eth0:avah back to ath0 ?
Thanks in advance,
jonny


```
lspci
00:06.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

ifconfig -a
eth0:avah Link encap:Ethernet  HWaddr 00:0C:76:18:DA:0B  
          inet addr:169.254.4.224  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:19 Base address:0xd000 

more /etc/iftab
ath0 mac 00:11:50:55:30:6c arp 1
```

---

### Post by spd106 on 2007-07-16
I think that your driver has been lost or was not upgraded at the same time.

Try this command to see if the card has a working driver.
```
sudo lshw -class network
```

Then try this command to load the madwifi driver.
```
sudo modprobe ath_pci
```

Make sure that you have the correct linux-restricted -modules package installed for your kernel. The restricted drivers package should help you out, if not use Synaptic instead.

---

### Post by jonnymccullagh on 2007-07-17
Great that worked thanks spd106,
I checked Administration->Restricted Drivers Manager and got an error "You need to install linux-restricted-modules-2.6.20-16-generic for this program to work" 
So I used Synaptic and installed it.
I must have done something weird with the Update Manager to have resulted in this but it is sorted now - Thanks again spd106,
jonny

---

