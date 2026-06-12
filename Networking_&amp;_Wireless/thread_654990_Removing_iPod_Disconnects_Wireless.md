---
title: "Removing iPod Disconnects Wireless"
date: 2007-12-31
forum: Networking &amp; Wireless
---

### Post by CanofAltoids on 2007-12-31
Hello,

After managing to get my wireless working in Gutsy by installing ndiswrapper, I've noticed that every time I unplug my ipod, my connection dies.  I'm using the win98 Realtek 8187 driver with ndiswrapper.  Whether I remove the ipod softly with "eject /dev/sde" or just unplug it from the USB cable, I find that my connection immediately stops working.  Any way to fix this?  Thanks.

---

### Post by CanofAltoids on 2008-01-01
Ehm... bump.  Now, it seems that it's disconnecting my wireless connection when I plug it in, as well?  What's going on here?

It's getting extremely tedious having to restart my computer every time I unplug my iPod, so any help would be greatly appreciated.

---

### Post by FRuMMaGe on 2008-01-15
I have the same problem.

I havn't found a solution yet, but I wrote a VERY short bash script to restart networking for you quickly.

I have it shortcutted to my gnome bar aswell so all i have to do is click it.

Just put the following into a text document:
```
sudo /etc/init.d/networking restart
```
Now save it as "restnet.sh" without the quotes.

Now navigate to the directory where you put it in the terminal and type "chmod +x restnet.sh"

Now just make a launcher that runs a terminal application with the command "sh /PATH/TO/SCRIPT.sh"

Obviously replace PATHTOSCRIPT with the path to the script.

Hope I helped!

---

### Post by CanofAltoids on 2008-01-19
Well, I've already done something similar to that (using the same command), and here is the output:
```

 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.wlan0.pid with pid 8751
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:15:8a:02:05:16
Sending on   LPF/wlan0/00:15:8a:02:05:16
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/wlan0/00:15:8a:02:05:16
Sending on   LPF/wlan0/00:15:8a:02:05:16
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

However, when I try the command before I unplug my iPod (or any other USB device), it works fine and resets my connection successfully.  Why doesn't this work after I unplug it?

---

