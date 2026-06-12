---
title: "AP Found but no IP address"
date: 2005-11-27
forum: Networking &amp; Wireless
---

### Post by Super King on 2005-11-27
Hi all,

Installed my D-Link DWL-520 card into my desktop, and it was recognized in Device Manager, but Wireless connection did not show up in Sys-Admin-Networking. Installed the drivers from the included CD via ndiswrapper, verified they were installed correctly (got the "drivers present, hardware present" message), and got the Wireless connection to show up in Sys-Admin-Networking. I can see one access point, and I configure it (no WEP key, uses DHCP), but that's as far as I get. No IP address according to ifconfig. 

I'm unsure of what step to take next. There's always installing different drivers (from the ndiswrapper wiki page), but that doesn't seem like it'd help, as the card is already recognized and can see

---

### Post by tehwa on 2005-11-27
The GUI won't offer much feedback, which is a bit sad. What's it say when you make a DHCP request using command ```
sudo ifup ath0
``` (replace 'ath0' with 'wlan0' if that's what it has called it).

If it says it is already configured, run```
sudo ifdown ath0
sudo ifup ath0
```
Also, it's worthwhile posting the contents of the config file located at: ```
/etc/network/interfaces
```
The GUI in Administration -> Networking really needs to give more feedback...

---

### Post by Super King on 2005-11-27
```
sudo ifup wlan0
```

It says, "ifup: interface wlan0 already configured" so I ran the next two commands you gave.

```
sudo ifdown wlan0
sudo ifup wlan0
```

> root@hawker:/home/brandon # ifdown wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:05:5d:96:84:79
Sending on   LPF/wlan0/00:05:5d:96:84:79
Sending on   Socket/fallback
root@hawker:/home/brandon # ifup wlan0
Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:05:5d:96:84:79
Sending on   LPF/wlan0/00:05:5d:96:84:79
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 5
-------------------

It keeps on sending the DHCPDiscover packet 'till I kill it.

Oh, and my /etc/network/interfaces file shows...(I edited out the comments)

> auto lo
iface lo inet loopback


mapping hotplug
            script grep
            map eth0

iface wlan0 inet dhcp
wireless-essid AP350Netbar

auto wlan0

---

### Post by wbiggers on 2005-12-03
Super King - I found that my router didn't like to give ubuntu DHCP information.  In specific, I had lots of trouble with DNS servers.  Try making the connection a static IP address (if you know what sub-net the router is running).

I found that the gui for networking was a good place to set the initial information for the wireless card.  On item you may need to do after putting in the wireless info in the gui is use the command line to set the channel.  The command is

sudo iwconfig wlan0 channel ???

If you don't know what channel the Access Point (AP) is running, try entering the command 'iwlist scan'.  It should tell you all the wireless networks your card is detecting, whether or not they are encrypted, and what channel they are operating on.

---

