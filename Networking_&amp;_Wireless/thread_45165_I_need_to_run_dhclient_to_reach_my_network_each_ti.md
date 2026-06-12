---
title: "I need to run dhclient to reach my network each time"
date: 2005-06-29
forum: Networking &amp; Wireless
---

### Post by auburn on 2005-06-29
Hi, everyone.
I'm having network issues which started with my most recent re-install. I have to call dhclient in order to get a network connection every time I reboot.
Here's the message I get from dhclient:

$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:50:70:e7:50:50
Sending on   LPF/eth0/00:50:70:e7:50:50
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.123.254
bound to 192.168.123.131 -- renewal in 3182649 seconds.

from dmesg:
eth0: VIA Rhine II at 0xec00, 00:50:70:e7:50:50, IRQ 23.
eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
(this must be from after I call dhclient and get my network working.)

I get an error while booting up, but I can't recall it (or find it in dmesg)

And this is Hoary  2.6.10-5-386. 
LIke I said, everything works fine once I call dhclient. But I'd rather it come up automatically.

Thanks everyone.

---

### Post by djg on 2005-06-29
[QUOTE=auburn]Hi, everyone.
I'm having network issues which started with my most recent re-install. I have to call dhclient in order to get a network connection every time I reboot.
Here's the message I get from dhclient:

$ sudo dhclient
Password:
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/sit0/
Sending on   LPF/sit0/
Listening on LPF/eth0/00:50:70:e7:50:50
Sending on   LPF/eth0/00:50:70:e7:50:50
Listening on LPF/lo/
Sending on   LPF/lo/
Sending on   Socket/fallback
DHCPDISCOVER on lo to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on sit0 to 255.255.255.255 port 67 interval 3
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.123.254
bound to 192.168.123.131 -- renewal in 3182649 seconds.

from dmesg:
eth0: VIA Rhine II at 0xec00, 00:50:70:e7:50:50, IRQ 23.
eth0: MII PHY found at address 1, status 0x786d advertising 05e1 Link 45e1.
(this must be from after I call dhclient and get my network working.)

I get an error while booting up, but I can't recall it (or find it in dmesg)

And this is Hoary  2.6.10-5-386. 
LIke I said, everything works fine once I call dhclient. But I'd rather it come up automatically.

Thanks everyone.[/QUOTE]
 Have you tried editing your /etc/network/interfaces config file?  Try "man interfaces" for the correct format.

---

### Post by auburn on 2005-06-29
Bingo. Thank you djg.

I commented out:

#mapping hotplug
#       script grep
#       map eth0

and added:

auto eth0
iface eth0 inet dhcp


Any idea why the hotplug method didn't work?  (I'm a newbie) What was it supposed to do?

again, thanks a lot.

---

