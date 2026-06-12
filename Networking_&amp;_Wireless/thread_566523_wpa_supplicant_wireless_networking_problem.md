---
title: "wpa_supplicant wireless networking problem"
date: 2007-10-03
forum: Networking &amp; Wireless
---

### Post by Griffiss on 2007-10-03
HI

I have had wireless working in Feisty, but not anymore. There seems to be some issue involving wpa_supplicant.

I've reinstalled ndiswrapper, now with version 1.48, and that now seems to be fine.

**iwlist scan** gives an output that looks fine, recognising the AP.

**iwconfig** tells me the network name but says there is no encryption, although there should be.

Here is my output to ```
sudo /etc/init.d/networking restart
```

> 
Reconfiguring network interfaces...RTNETLINK answers: No such process
wpa_supplicant: cannot read contents of managed
run-parts: /etc/network/if-down.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 3843
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:11:d8:4a:2d:92
Sending on   LPF/wlan0/00:11:d8:4a:2d:92
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.0.1 port 67
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
wpa_supplicant: cannot read contents of managed
run-parts: /etc/network/if-post-down.d/wpasupplicant exited with return code 1
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Invalid argument.
wpa_supplicant: cannot read contents of managed
run-parts: /etc/network/if-pre-up.d/wpasupplicant exited with return code 1
There is already a pid file /var/run/dhclient.wlan0.pid with pid 134993416
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan0/00:11:d8:4a:2d:92
Sending on   LPF/wlan0/00:11:d8:4a:2d:92
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
wpa_supplicant: cannot read contents of managed
run-parts: /etc/network/if-up.d/wpasupplicant exited with return code 1
done.

Any help would be awesomely rewarded.

Thanks, Griff

---

### Post by moore.bryan on 2007-10-03
[I]can you post the outputs of ```
lspci
lshw -C network
iwconfig
```
[/I]

---

### Post by Griffiss on 2007-10-03
Here are the outputs:

lspci (for the device in question):

> 00:10.0 Ethernet controller: Marvell Technology Group Ltd. Marvell W8300 802.11 Adapter (rev 07)

lshw -C network (this one usually doesn't say UNCLAIMED. i.e. it still doesn't work even when UNCLAIMED doesn't appear):
> 
  *-network:1 UNCLAIMED
       description: Ethernet controller
       product: Marvell W8300 802.11 Adapter
       vendor: Marvell Technology Group Ltd.
       physical id: 10
       bus info: pci@00:10.0
       version: 07
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=32
       resources: iomemory:cb000000-cb00ffff iomemory:ca800000-ca80ffff irq:255

For iwconfig the interface isn't showing up at all now. Don't know why. It's late here and bedtime for me now. Thanks for helping

---

### Post by Griffiss on 2007-10-04
bump for cluelessness and desperation!

---

### Post by kevdog on 2007-10-04
There is no driver associated with your device.  Did you use ndiswrapper to initially install the drivers or some other method???  That is the first problem.

---

### Post by moore.bryan on 2007-10-05
> **kevdog said:**
> There is no driver associated with your device.  Did you use ndiswrapper to initially install the drivers or some other method???  That is the first problem.
*ditto... i'm a little confused by your outputs.*

---

### Post by Griffiss on 2007-10-06
Hi fellows

I had some problems with ndiswrapper in addition to the issue in the first post. It claimed my module was version 1.38, which was too old for utils version (1.9). This despite my having upgraded to 1.47 a while back. Think the problem may have been caused by upgrading something else in ubuntu?

Anyway, I reinstalled ndiswrapper with 1.48 - quite difficult as the '1.38ness' seemed to resist being cleared beforehand - then ndiswrapper looked better, no error messages with ndiswrapper -v. (kevdog - used instruction I'd got from you previously - nice one!)

Then I found someone else who had output:
```
wpa_supplicant: cannot read contents of managed
``` and used their solution, which was to delete the line 'wpa-conf Managed' from my /etc/network/interfaces file. 

Now my wireless works even better than before, always connected on startup, and doesn't drop out (yet!).

So that's great.

I have attached your reward (i think). Cheers

---

