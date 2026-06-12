---
title: "wireless hacking."
date: 2010-11-11
forum: New to Ubuntu
---

### Post by arju305 on 2010-11-11
I need to crack my wireless password (of course for learning purpose)
I need help!!!!!
These are the things i did:

******************************
With my wireless on.........
1. root@arjan:~# sudo airmon-ng stop wlan0


Interface    Chipset        Driver

eth1        Unknown         wl

************************************

2. root@arjan:~# sudo ifconfig eth1 down

**********************************
3.root@arjan:~# sudo macchanger --mac 00:11:22:33:44:55 eth1
Current MAC: 00:21:00:63:35:a6 (unknown)
ERROR: Can't change MAC: interface up or not permission: Too many open files in system
*********************************************
As my mac didnt changed. I repeated the command again.

4.root@arjan:~# sudo macchanger --mac 00:11:22:33:44:55 eth1
Current MAC: 00:11:22:33:44:55 (Cimsys Inc)
ERROR: Can't change MAC: interface up or not permission: Too many open files in system

As you can see my mac changed. But it is showing some errors (interface up??)
*********************************************************

5.root@arjan:~# sudo airmon-ng start eth1


Found 4 processes that could cause trouble.
If airodump-ng, aireplay-ng or airtun-ng stops working after
a short period of time, you may want to kill (some of) them!

PID    Name
963    NetworkManager
966    avahi-daemon
969    avahi-daemon
1097    wpa_supplicant


Interface    Chipset        Driver

eth1        Unknown         wl (monitor mode enabled)

*********************************************************

6.root@arjan:~# sudo airodump-ng eth1
ioctl(SIOCSIWMODE) failed: Invalid argument

ARP linktype is set to 1 (Ethernet) - expected ARPHRD_IEEE80211,
ARPHRD_IEEE80211_FULL or ARPHRD_IEEE80211_PRISM instead.  Make
sure RFMON is enabled: run 'airmon-ng start eth1 <#>'
Sysfs injection support was not found either.

**************

I am stuck here.
I havent patched my drivers yet. I googled it. but found nothing.
Can you help me step by step............ Please............


^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
when i run iwconfig:
root@arjan:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.457 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
when i run
root@arjan:~# sudo lshw -C network 
  *-network               
       description: Wireless interface
       product: BCM4312 802.11b/g LP-PHY
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 00:11:22:33:44:55
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 wireless=IEEE 802.11bg
       resources: irq:18 memory:99700000-99703fff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:e3:99:0d
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:46 ioport:3000(size=256) memory:93410000-93410fff memory:93400000-9340ffff memory:93420000-9343ffff
**************************


Guys help me......... I am very new to these things..............

---

### Post by bioterror on 2010-11-11
I do it usually resetting the router by pressing reset button for about ~10 seconds and then I log in with default password and username which are provided in the wlan ap's manual.

I think sniffing wep-keys and cracking wpa-keys are not for the beginners and even if I knew about these things, I would not share this information.

---

### Post by I'mGeorge on 2010-11-11
It's this tutorial; handy for you [http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/](http://ubuntulinuxhelp.com/using-ubuntu-to-crack-wep/)

---

### Post by s.fox on 2010-11-11
Closed for staff review.

**Edit:**

Thread has been reviewed.  It will remain closed.

---

