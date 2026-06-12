---
title: "What, no wireless card!?"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by mr love and justice on 2006-11-06
I upgraded to edgy last night and Ubuntu seems to have forgotten that my computer comes with a wireless card. It's a Dell Truemobile, and I had it running perfectly in dapper with the help of ndiswrapper. In fact, the windows driver is still installed, but eth1 just won't show up in Network Settings. I have a networking icon in my top panel left over from dapper and when I open up eth1's Connection Properties dialog, then hit Configure, edgy tells me that 'The interface does not exist.' Arg. 

Ideas?

MLaJ

---

### Post by mr love and justice on 2006-11-06
More info on this issue:

I looked up the card in the device manager and it's sitting quite happily under my 82801 PCI bridge. Yet when I run

```
 sudo ifup eth1 
```

you can see what kind of stuff gets burped up:

```

Error for wireless request "Set Encode" (8B2A) :
    SET failed on device eth1 ; No such device.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device eth1 ; No such device.
There is already a pid file /var/run/dhclient.eth1.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
```

Definitely out of my depth on this one..

---

### Post by mr love and justice on 2006-11-06
Ok, got it fixed by reading through "Broadcom 4306 With Ndiswrapper 54 Mbps" in the FAQ forums. Just had to run 

```
sudo modprobe ndiswrapper
``` and it took off on its own

now i just have to reinstall my VPN client with the new kernel source..

---

