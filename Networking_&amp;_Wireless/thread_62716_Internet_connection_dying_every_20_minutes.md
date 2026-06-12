---
title: "Internet connection dying every 20 minutes"
date: 2005-09-05
forum: Networking &amp; Wireless
---

### Post by Tewmas on 2005-09-05
I've recently installed Ubuntu for the first time. I've got almost everything I need up and running through tutorials and some googling, but one problem remains: My internet connection goes down every 20 minutes.

I'm suspecting that there's something supposed to be done every 20 minutes to keep it alive, but I don't know what. I've tried Google but I'm lost to find out what to search for.

RIght now I'm doing...
```
sudo /etc/init.d/networking restart
``` 
...every 20 minutes to reconnect to the internet. It's getting kinda annoying so I'm hoping someone here recognize the problem.

My setup:

- Ubuntu Hoary 5.04 AMD64
- nForce 3 integrated network card
- Dynamic IP (DHCP)
- vDSL (from the ISP Bredbandsbolaget if anyone know of them)
- Connected to the modem through a switch

I'm grateful for any tips or pointers!

---

### Post by s_p_a_r_k_y on 2005-09-05
seems weird that your ISP would be giving you a 20 minute dhcp lease...from the console 
```
sudo dhclient eth0
```
and see how many seconds are in your lease

---

### Post by Tewmas on 2005-09-05
This is what I got from your command s_p_a_r_k_y:
> sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:11:09:04:c9:e3
Sending on   LPF/eth0/00:11:09:04:c9:e3
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 83.226.151.2
bound to 83.226.151.*** -- renewal in 1494 seconds.Tried running it several times and I ended up with values from 1300 to 1800 seconds.

---

### Post by s_p_a_r_k_y on 2005-09-05
who's your ISP? There is no reason for them to be giving out such short lease times. Usual lease times range from 1 day to 6 months. If you want a quick and dirty solution you could have something like this
```


#!/bin/bash
while [ 1 ]; do
   dhclient eth0
   sleep 1200
done
exit 0


```
and run that as root. It will refresh dhcp every 20 minutes for you...
to run it in the background
```
 sudo dhcp_refresh_script & 
```
thats if you save it as dhcp_refresh_script

---

### Post by dolny on 2005-10-02
[QUOTE=s_p_a_r_k_y]seems weird that your ISP would be giving you a 20 minute dhcp lease...from the console 
```
sudo dhclient eth0
```
and see how many seconds are in your lease[/QUOTE]

I have a similar problem with my cable modem (Breezy 5.10 but I had it on Hoary too). My connection also dies :(

```
mrplant@milkshake:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/eth0/00:10:95:8d:e4:f0
Sending on   LPF/eth0/00:10:95:8d:e4:f0
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 213.156.96.1
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 213.156.96.1
bound to 213.156.101.2 -- renewal in 4449 seconds.
mrplant@milkshake:~$                       
```

---

