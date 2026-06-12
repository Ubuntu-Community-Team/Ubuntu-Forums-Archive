---
title: "No dhcp offers on Ubuntu 7.10, acer aspire 5520"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by Kharny on 2008-06-24
Currently trying to install ubuntu 7.10 on an acer aspire 5520.
The installation runs fine(using safe mode for monitor), but running into trouble after the first boot.

While the wired connection is recognised(eth0), it doesn't seem to get a dhcp offer for some reason.

Tried down/upping it, resetting the connection, using both network manager and command line.

Basically it just doesn't get an ip adress at all. Net worked fine on vista beforehand on same laptop, and several other machines on the same connection.

Unfortunately i don't have the option to give it a static ip, since that isn't supported by the isp.

Any insight on this?

---

### Post by wormser on 2008-06-24
It sounds like you are connecting directly to the ISP.  You should buy a cheap home router.   It will give you an added layer of security and be a local DHCP server.  Have you tried using dhclient yet?

```
sudo dhclient eth0
```

---

### Post by Kharny on 2008-06-25
A router isn't practical, as this laptop has to connect in several places. Anyway, this came out of dhclient

Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://isc.org/sw/dhcp/](http://isc.org/sw/dhcp/)

Listening on LPF/eth0/b6:a8:22:38:1b:00
Sending on   LPF/eth0/b6:a8:22:38:1b:00
Sending on   Socket/fallback
DHCPDISCOVER on Eth0 to 255:255:255:255 port 67 interval 6
DHCPDISCOVER on Eth0 to 255:255:255:255 port 67 interval 15
DHCPDISCOVER on Eth0 to 255:255:255:255 port 67 interval 7
DHCPDISCOVER on Eth0 to 255:255:255:255 port 67 interval 3
No DHCPOFFERS received.
No working leases in persistent database - sleeping.


Late reply, but work's been hell the last few days.

---

### Post by wormser on 2008-06-25
> **Kharny said:**
> A router isn't practical, as this laptop has to connect in several places. Anyway, this came out of dhclient

A router is practical for this location.  Are you sure the modem does not have a router in it?  If not then buy one.

The error message does not say much.  Who is your ISP?  What is the model of the modem?  Try unplugging the modem for 30 seconds, turn off your computer then plug the modem back in then turn your computer back on.

---

### Post by Kharny on 2008-06-25
The isp is welho in Finland, dhcp works both for the pc i work on and several others in the house. 

The modem is a motorola SB4100E, unplugging and restarting didnt do anything.

While I apreciate the advice for a router, I'm not the owner of either the laptop or the connection here.

---

### Post by ModelM on 2008-06-25
Does the ISP use MAC address filtering or registration? There is a glich in at least some Acer 5520 machines (mine, for example) which will make the MAC address different than in Windows. This might be why it worked in Windows, but not in Linux.

Another related problem which comes up on some of them is the Ethernet port being renamed at every boot (eth0, then eth1, eth2, etc). It sounds like this doesn't apply to you, but the MAC address being different might.

Anyway, check with the ISP if you can & ask about MAC address filtering.

---

### Post by Mr_FixIT on 2008-06-25
Kharny,
Take a look at the issue I am trying to solve on this thread, sounds very similar....

[http://ubuntuforums.org/showthread.php?t=838291](http://ubuntuforums.org/showthread.php?t=838291)

(BTW, I do not know how to paste links yet...sorry)

---

### Post by Kharny on 2008-06-26
Problem solved by updating my boot cd to 8.04.

Guess it was just a version/hardware recognition issue.

Thanks for the help all :D

---

