---
title: "Hardy Heron not using iftab"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by spawnywhippet on 2008-06-04
I have been struggling for weeks and weeks trying to get wireless working on IBM Thinkpad T42. It has the High Rate wireless card with the latest firmware. It can see my networks, but only offers WEP or LEAP connectivity. I followed the Ndiswrapper Howto ([http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)) which worked with a previous laptop with Cisco card, but for some reason, this machine did not have an iftab file, which I need to edit in order to rename the WLAN connection from 'wifi0' to 'wlan0'. I manually created one with the correct entries, but Ubuntu just ignores it. Any ideas on how to make Ubuntu read the file on boot?


my /etc/iftab contains the following:

#This file assigns persistent names to network interfaces.
#See iftab(5) for syntax.

eth0 mac 00:0d:60:75:b6:fc arp 1
wlan0 mac 00:05:3c:06:c2:d2 arp 1



andy@ubuntu-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth2
       version: 03
       serial: 00:0d:60:75:b6:fc
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A ip=192.168.1.116 latency=64 mingnt=255 module=e1000 multicast=yes
  *-network:1
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:3c:06:c2:d2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b

---

### Post by jetsam on 2008-06-04
Ubuntu used to use iftab, but the functionality of iftab has been moved to **/etc/udev/rules.d/70-persistent-net.rules**.  It should be relatively straight forward to modify this file and change your interface names.  Make sure you comment out any old or missing interfaces which may be reserving the names you want to use (eth0, wlan0).  

Maybe make a backup first.  You can post the file here if you have trouble with the modifications.

**Added**: Oh, and you'll need to reconfigure networking for your new interface names after you change the names in the file and reboot.

---

### Post by spawnywhippet on 2008-06-04
Thanks for your help, I've had a look at the file and there appears to be no reference to 'wifi0', my wireless current card. How do I edit this so wifi0 becomes wlan0?

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x101e (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:60:fb:b5:4e", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14b9:0xa504 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:8a:5d:dc:18", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x101e (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:60:5f:4e:d3", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14b9:0xa504 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:8a:5d:d3:a5", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x8086:0x101e (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:60:75:b6:fe", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x1260:0x3873 (hostap_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:05:3c:06:c2:d4", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

---

### Post by jetsam on 2008-06-04
I think I'd try this:

```
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

[COLOR="Red"]# PCI device 0x8086:0x101e (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:60:75:b6:fc", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"[/COLOR]

[COLOR="Red"]# Prism 2.5 Wavelan chipset Wireless interface (Hand Tweaked)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:05:3c:06:c2:d2", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"[/COLOR]

# PCI device 0x8086:0x101e (e1000)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:60:fb:b5:4e", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14b9:0xa504 (ndiswrapper)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:8a:5d:dc:18", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:0x101e (e1000)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:60:5f:4e:d3", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# PCI device 0x14b9:0xa504 (ndiswrapper)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:8a:5d:d3:a5", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x8086:0x101e (e1000)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:60:75:b6:fe", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"

# PCI device 0x1260:0x3873 (hostap_pci)
[COLOR="Red"]#[/COLOR]SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:05:3c:06:c2:d4", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
```

Changes in red.  I commented the whole file, but moved eth2 to the top and renamed it, then changed your mac address to what lshw reports.  I put your mac address into the new wlan0 entry.  

Do make a backup before you modify:
```
sudo cp /etc/udev/rules.d/70-persistent-net.rules ~/Desktop/70-persistent-net.rules.bak
```

You might need the services of someone who knows wireless well.  I am far from that.  I think that file will get your interface names the way you want them, though.

---

### Post by spawnywhippet on 2008-06-04
Thanks for the assistance, after a bit of modification, it worked on the LAN card, but not on the wireless. It seems that ndiswrapper is still bound to the old a504 card that failed as it keeps repopulating entries in the 70-persistent-net-generator.rules. I am lost here, I thought I had uninstalled the neta504 drivers...
.

andy@ubuntu-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network:0             
       description: Ethernet interface
       product: 82540EP Gigabit Ethernet Controller (Mobile)
       vendor: Intel Corporation
       physical id: 1
       bus info: pci@0000:02:01.0
       logical name: eth0
       version: 03
       serial: 00:0d:60:75:b6:fe
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 driverversion=7.3.20-k2-NAPI firmware=N/A latency=64 mingnt=255 module=e1000 multicast=yes
  *-network:1
       description: Wireless interface
       product: Prism 2.5 Wavelan chipset
       vendor: Intersil Corporation
       physical id: 2
       bus info: pci@0000:02:02.0
       logical name: wifi0
       version: 01
       serial: 00:05:3c:06:c2:d4
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical wireless ethernet physical
       configuration: broadcast=yes driver=hostap firmware=1.4.9 latency=64 module=hostap_pci multicast=yes wireless=IEEE 802.11b



# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x101e (e1000)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:0d:60:75:b6:fe", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# Prism 2.5 Wavelan chipset Wireless interface (Hand Tweaked)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}==" 00:05:3c:06:c2:d4", ATTR{type}=="1", KERNEL=="wifi*", NAME="wlan0"

# PCI device 0x14b9:0xa504 (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:02:8a:5d:dc:18", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# PCI device 0x1260:0x3873 (hostap_pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:05:3c:06:c2:d4", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"

---

### Post by jetsam on 2008-06-05
...out of my depths now, too.  I just don't use wireless, so I don't know it at all.

Your mac addresses keep changing!

---

### Post by Kralizec on 2008-06-18
I don't have a Prism-based wireless card myself. However after reading through a few posts, I found one that looked promising: [http://ph.ubuntuforums.com/showthread.php?t=606861]("http://ph.ubuntuforums.com/showthread.php?t=606861"), post #7 in particular. I hope this helps.

---

