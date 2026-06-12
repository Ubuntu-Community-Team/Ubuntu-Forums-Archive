---
title: "Hardy wireless adapter names wrong?"
date: 2008-06-01
forum: Networking &amp; Wireless
---

### Post by metrorat on 2008-06-01
Hi all... Have a bit of an issue with my wireless adapter in Hardy. While the internet and network are actually working I think it is causing other issues on login related to a persistent gnome-settings-daemon error. It seems that Hardy is calling my wireless adaptor wmaster0. ```
sudo lshw -C network
``` outputs  ```
*-network               
       description: Ethernet interface
       product: NetLink BCM5789 Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 21
       serial: 00:0f:b0:ee:b8:c2
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.86 firmware=5789-v3.49a latency=0 link=no module=tg3 multicast=yes port=twisted pair
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wmaster0
       version: 02
       serial: 00:13:02:07:c2:a6
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwl3945 ip=192.168.1.101 latency=0 module=iwl3945 multicast=yes wireless=IEEE 802.11g

```

I upgraded to Hardy from Gutsy and to that from Feisty.  i originally set up my manual network config in Feisty (after much wailing and gnashing of teeth).  And it seems like the configuration has been carried over from upgrade to upgrade including the wireless adapter name eth1.  So when I click on my wireless monitor icon in the taskbar and select configuration I can't configure eth1, instead getting the message:

```
The interface does not exist
Check that it is correctly typed and that it is correctly supported by your system.
```

The adapter wmaster0 is not listed in the drop down menu. Listed are:
eth1
eth0:avahi
lo

I'm guessing that Hardy has used a different naming convention for the wireless adapter but I don't understand why its still working as eth1.

content of /etc/network/interfaces is:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

```

No mention of wmaster0. 

Running ifconfig gives:
```
eth0      Link encap:Ethernet  HWaddr 00:0f:b0:ee:b8:c2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

eth1      Link encap:Ethernet  HWaddr 00:13:02:07:c2:a6  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe07:c2a6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9697 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6524089 (6.2 MB)  TX bytes:1251538 (1.1 MB)

eth0:avahi Link encap:Ethernet  HWaddr 00:0f:b0:ee:b8:c2  
          inet addr:169.254.10.228  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:235 errors:0 dropped:0 overruns:0 frame:0
          TX packets:235 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:22685 (22.1 KB)  TX bytes:22685 (22.1 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-13-02-07-C2-A6-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

No idea what the crack is with all of this.  Can anyone help? I get boot warnings about eth1 'no such device' and have a suspicion that this discrepancy is responsible for my gsd error.

Cheers folks

---

### Post by spd106 on 2008-06-01
You may still have the card set to eth1 in the /etc/iftab. I believe that wireless interfaces are supposed to named wlan0 these days. hal should be managing the interface names, so you shouldn't need anything in the /etc/iftab any more.

The wmaster0 interface is a consequence of the move to the new mac80211 wireless stack and is actually a good sign, but it doesn't work with any of the configuration tools and should just be ignored.

---

### Post by metrorat on 2008-06-03
Hi - cheers for the reply. Actually I don't have anything in etc/iftab in terms of adaptor names. Just the following:
```

# This file is no longer used and has been automatically replaced.
# See /etc/udev/rules.d/70-persistent-net.rules for more information.
#

# This file assigns persistent names to network interfaces.
# See iftab(5) for syntax.

##eth0 mac 00:0f:b0:ee:b8:c2 arp 1
```

/etc/udev/rules.d/70-persistent-net.rules contains:
```

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# Converted from /etc/iftab on upgrade
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:0f:b0:ee:b8:c2", ATTRS{type}=="1", NAME="eth0"


# PCI device 0x8086:0x4222 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:13:02:07:c2:a6", ATTR{type}=="1", NAME="eth1"
```

Looks like the contents of /etc/iftab have been moved to this file. I'll try editing it to read wlan0 for eth1 and see what happens (don't worry I'll back it up).

---

### Post by chili555 on 2008-06-03
I wouldn't worry too much about eth1 vs. wlan0. Mine, also using a 3945ABG, is exactly the same:```
chili@LAPTOP60:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:19:d2:c2:1b:8d  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2484 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2139 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2359319 (2.2 MB)  TX bytes:338655 (330.7 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:184 errors:0 dropped:0 overruns:0 frame:0
          TX packets:184 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10060 (9.8 KB)  TX bytes:10060 (9.8 KB)

wmaster0  Link encap:UNSPEC  HWaddr 00-19-D2-C2-1B-8D-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
```Except for the desktop icon issue, you are connecting fine.

Are you using Network Manager or configuring your interfaces manually? If manually, please notice that eth1 does *not* appear in your *interfaces* file. That may be at the root of your desktop icon issue. I'd suggest amending it to:```
auto lo
iface lo inet loopback

#auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp
```

---

### Post by metrorat on 2008-06-03
Well... that didn't work.  I also edited /etc/network/interfaces and replaced all eth1 entries with wlan0. Wireless failed on reboot.

In the network manager I ditched my old saved location (based on eth1) and tried to create a new one based on wlan0 (which was apparently detected).  Entered all the same info as before (WEP key etc). Restarted networking daemons - nothing. Rebooted - nothing. When I clicked on the network icon in the taskbar I got an error message: 'Please contact your system administrator. Device does not exist'

Any suggestions?

---

### Post by metrorat on 2008-06-03
Hi Chill... thanks. I clicked on to that myself yesterday and managed to get rid of the gsd error.  I also had to edit my /etc/hosts file.

I had previously had to edit it to get samba to work in Feisty from Linux to Linux.linksys.net. But this also seems to have been causing problems with gsd in Hardy - don't ask me why.

The reason I was looking to sort out the wireless naming issue is because of boot messages telling me wlan0 is being renamed to eth1 and then that eth1 does not exist.

---

