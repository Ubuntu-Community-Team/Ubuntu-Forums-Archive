---
title: "Help with making wireless work on Gutsy with Broadcom4306"
date: 2007-10-27
forum: Networking &amp; Wireless
---

### Post by puppe on 2007-10-27
**Aim:**
make the Broadcom4306 wireless card work on a Ferrari3400(AMD x64)running Gutsy.

**Description:**
- when pressing the wireless button on the laptop the correct wireless network show up in gnome-network-manager but the icon still shows an orange exclamation mark
- when running pppoeconf it can not find any network on eth1, which should be the right one
- wired network works fine even though the exclamation mark in the gnome-network-manager is still present...sometimes the exclamation mark disappear though  (?_?)

**Troubleshooting attempts:**
- tried with the restricted driver (System>Administration>Restricted Drivers Manager) without luck.
- tried fwcutter suggested by [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBroadcom) which I installed, but after rebooting it still did not working. (Perhaps there are other steps I did not do though?)
- have tried earlier with this script [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990) but that screwed up the whole network manager.

**Specs:**
sudo lshw -C network[INDENT]  *-network:0             
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:00:09.0
       logical name: eth1
       version: 03
       serial: 00:0b:6b:4b:e5:46
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.22-14-generic latency=64 link=no module=bcm43xx multicast=yes wireless=IEEE 802.11b/g
  *-network:1
       description: Ethernet interface
       product: NetXtreme BCM5788 Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 03
       serial: 00:c0:9f:5b:47:50
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.77 duplex=full firmware=5788-v3.03 latency=64 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
[/INDENT]iwconfig[INDENT]lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ppp0      no wireless extensions.
[/INDENT]uname -r[INDENT]2.6.22-14-generic
[/INDENT]I'm still searching around the web trying to get it to work but any help or hints which can put me in the right direction are greatly appreciated

---

### Post by puppe on 2007-10-28
(continuation of earlier post with same subject line)

I tried to set up wireless by following this thread
[http://ubuntuforums.org/showthread.php?t=201902](http://ubuntuforums.org/showthread.php?t=201902)
and result is that, when activating wireless (pressing the button) everything freezes for extended periods of time when trying to do anything (moving the mouse, keyword etc).

Don't know what went wrong
ndiswrapper -l gives:
[INDENT]bcmwl564 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)[/INDENT]

which is not really what was written in the tutorial/thread but otherwise I don't know.

Any help or suggestions very appreciated.

---

### Post by jmontelius on 2008-03-11
I don't think I can help you but my wireless coneection owrked out of the box. Did a clean install of Kubuntu 7.10 and after enabling propriety modules the network show up ok. Or rather it is working but the Knetworkmanager fails to show it (I can still configure it). Might not bring you closer to a solution but if others are sitting on a F3400 and are thinking about   throwing out the preintalled OS, it works ok.

---

### Post by puppe on 2008-03-12
aha, that helped.
Had not used the comp. for a while but after doing a upgrade and restarting wireless works. Thank you ubuntu :)

Still the led indicator won't work but what the heck...

I guess we can say almost [SOLVED]

---

