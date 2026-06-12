---
title: "RT2500 woes"
date: 2006-10-21
forum: Networking &amp; Wireless
---

### Post by puggers on 2006-10-21
I have an internal rt2500 chipset in my Packard Bell (](*,)) laptop. I recently installed Dapper which apparently supports it from the off, but it didn't work. I've followed the instructions on the guide [here]("https://help.ubuntu.com/community/WifiDocs/Driver/RalinkRT2500#compile") and installed the latest CVS drivers, but still it doesn't seem to come to life. I've entered the correct ESSID and WEP key into the Network Settings box, but no lights flash on my router when I click ok.
If I type in 'lshw' it comes up with: ```
*-network:0 DISABLED
             description: Wireless interface
             product: Ralink RT2500 802.11 Cardbus Reference Card
             vendor: RaLink
             physical id: 11
             bus info: pci@00:11.0
             logical name: ra0
             version: 01
             serial: 00:10:60:61:27:59
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=RT2500STA driverversion=1.1.0 CVS link=yes multicast=yes wireless=RT2500 Wireless
             resources: iomemory:44000000-44001fff

```

If I type 'ifup ra0' it displays: ```
steve@steves-ubuntu:~$ sudo ifup ra0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: Device or resource busy
SIOCSIFFLAGS: Device or resource busy
Listening on LPF/ra0/00:10:60:61:27:59
Sending on   LPF/ra0/00:10:60:61:27:59
Sending on   Socket/fallback
receive_packet failed on ra0: Network is down
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 3
send_packet: Network is down
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down
DHCPDISCOVER on ra0 to 255.255.255.255 port 67 interval 17
send_packet: Network is down
```

And when I run Wireless Assistant, which I hope to finally be able to manage my networks with, it says this: ```
steve@steves-ubuntu:~$ sudo wlassistant
Password:
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Link points to "/tmp/ksocket-root"
Link points to "/tmp/kde-root"
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  148
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
kbuildsycoca running...
Loaded application options.
DHCP Client: dhclient
All executables found.
iwconfig_status: /sbin/iwconfig
==>stderr: lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

Wireless interface(s): ra0
Permissions checked.
ifconfig_status: /sbin/ifconfig ra0
ifup: /sbin/ifconfig ra0 up
==>stderr: SIOCSIFFLAGS: Device or resource busy
scan: /sbin/iwlist ra0 scan
No networks found!
```

I've tried reinstalling the drivers a number of times, but to no avail. Is there a simple solution? I hope the code segments make some sense to someone. To make everything more complicated I'd rather not use ndiswrapper if it can be helped. Is anyone able to assist? 
Any help would be much appreciated. Thanks very much.

-Steve

---

### Post by puggers on 2006-10-22
Bump. 

Anyone?

To add to my first post, i have tried adding both pci=noacpi & pci=biosirq, to the kernel command-line thing at start up, as suggested by other sites i found with google. I also found a suggestion that I turned off PnP in the bios, but my bios doesnt seem to have that option, restrictive Packard Bell rubbish. I added the nobiospnp command too, to see if that affect anything, but it seems nothing will work! Pleae help.

-Steve

---

### Post by boz on 2006-10-27
I had problems with this driver when I had the wireless card plugged in during Dapper installation.  Go [here]("http://www.ubuntuforums.org/showthread.php?t=192588&page=5&highlight=wusb54g") and scroll down to the post made by windquest 3 posts from the bottom to see if this is your issue.  The only way I could fix it was by reinstalling Dapper :( Otherwise, it may be that you're not putting a dash (-) after every fourth character for the WEP?

Go here for better help:
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide]("https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide")
I've only been using Linux for a few months, but I do what I can.  ;)

---

### Post by keirnna on 2006-10-31
I don't know if it will help but it works out of the box for me on edgy. I am trying to get the network-manager-gnome to work. It is great normally, but I can't get my RT2500 to work with DHCP. Email me at [email]keirnna@gmail.com[/email] if there is any information you want from my system that will help.

---

