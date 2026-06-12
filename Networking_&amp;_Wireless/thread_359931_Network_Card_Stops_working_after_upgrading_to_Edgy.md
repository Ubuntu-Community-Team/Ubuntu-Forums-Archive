---
title: "Network Card Stops working after upgrading to Edgy"
date: 2007-02-12
forum: Networking &amp; Wireless
---

### Post by sixfooteskimo on 2007-02-12
I recently upgraded my desktop to Ubuntu Edgy from Dapper via the internet. Unfortunately once I restarted the computer and the changes took effect, the ethernet card stopped working.

Network-admin still thinks thinks there's a card there and lets me enable/disable it (but this makes no difference). The computer's definitely registering the card though, because when I swap it for a different one, the details change in device manager.

Does anyone have any thoughts? I'm relatively new to linux, so there might be some terminal command to configure network cards that I don't know about. Any help would be very much appreciated.

Sam

---

### Post by Floppyjoe on 2007-02-12
Did you have to set up your cards in a special way with Dapper(ie. ndiswrapper)?
Or did your card work out of the box?

---

### Post by sixfooteskimo on 2007-02-12
It worked straight out of the box, nothing complicated required.

---

### Post by Floppyjoe on 2007-02-12
hmmm.
Can you post the output of the following line when entered into the terminal(Applications/Accessories/terminal)?
```
iwconfig
```
Are you using network-manager to connect?
A recent Kernel Update may have broken your cards ability to function properly.

---

### Post by sixfooteskimo on 2007-02-12
it says

lo           no wireless extensions
eth0      no wireless extensions
sit0       no wireless extensions



I should say, though, that it's a wired card I'm trying to configure, not a wireless one. I may not have been clear before. Sorry.

---

### Post by sixfooteskimo on 2007-02-12
and on the network-manager thing, I don't know. Is that different from network-admin? In the past I just plugged it in to the hub, set the IP addess to DHCP in network-admin and let it work its magic.

---

### Post by Floppyjoe on 2007-02-12
Okay I was assuming it was wireless.
What happens when you enter the following command in the terminal?
```
sudo dhclient eth0
```

---

### Post by sixfooteskimo on 2007-02-12
IT WORKS!!! It gave me a whole long bit of output beginning with:

"There is already a pid file /var/run/dhclient.pid ....."

but it seemed to suggest it had connected to my hub, so I tried it and it worked!

Thank you so much for your help.
Sam

---

### Post by sixfooteskimo on 2007-02-12
I've just realised that since this computer works again, I can copy and paste the whole terminal output:

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:02:e3:16:70:34
Sending on   LPF/eth0/00:02:e3:16:70:34
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 192.168.2.1
bound to 192.168.2.8 -- renewal in 976163439 seconds.

in case it's of any interest.

Thanks again
San

---

### Post by Floppyjoe on 2007-02-12
I just don't understand why it doesn't work automatically there for you.
But your welcome.
What does your /etc/network/interfaces file look like?
```
sudo gedit /etc/network/interfaces
```
There may be something out of whack there.

---

