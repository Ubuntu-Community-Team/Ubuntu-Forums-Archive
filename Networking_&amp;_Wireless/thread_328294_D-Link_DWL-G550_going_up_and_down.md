---
title: "D-Link DWL-G550 going up and down"
date: 2006-12-30
forum: Networking &amp; Wireless
---

### Post by jaa1180 on 2006-12-30
I bought a D-Link DWL-G550 wireless card. I has been working great, except for some reason after some time, about 10 minutes or more, the network connection is not working any more. I can restart the network services and it starts working again. 
Also, I have noticed after restarting the services the PC seems slow on responding to opening programs. I am not sure what the problems it. 

Card - D-Link AirPremier DWL-G550 Wireless PCI Adapter
No encryption (will do later) on WAP, just SSID set. 

any ideas? :confused: 

/etc/network/interfaces
```

root@server1:/home/jeff# cat /etc/network/interfaces 
auto lo
iface lo inet loopback

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

auto ath0
iface ath0 inet static
address 172.16.0.50
netmask 255.255.255.0
gateway 172.16.0.1
wireless-essid *********************************

#auto wlan0
#iface wlan0 inet dhcp

```

The essid is not real, I replaced the real SSID with stars. About the same amount of characters though. 

I have reseated the PCI card... thinking it might not be in all the way and causing communication problems. Still not working right. 

Thanks in advanced,
-Jeff

---

