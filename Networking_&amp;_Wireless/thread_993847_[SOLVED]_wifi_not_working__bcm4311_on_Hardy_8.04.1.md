---
title: "[SOLVED] wifi not working : bcm4311 on Hardy 8.04.1"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by majikins on 2008-11-26
Hi

I've been trying to get this to work for the past few days and at my wits end so decided to throw in the towel and hope someone can help me.

The restricted drivers list b43 and wl . 
I've had very little luck with b43 as the behaviour is erratic at best - losing signal, dropped packets etc.  Just a pain in the butt.

I've disabled b43 and tried to enable wl(broadcom sta) driver. It shows enabled and in use but my wlan interface does not start up.(yes I have made sure wireless is physically enabled on the button)

inspection of dmesg gives this:
[   24.437241] wl: module license 'MIXED/Proprietary' taints kernel.
[   26.861777] udev: renamed network interface wlan0 to wlan1
[   29.952790] ADDRCONF(NETDEV_UP): wlan1: link is not ready

inspection of lshw -C network gives this:
 *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:10:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0 module=ssb

showing the b43 driver still being used as driver instead of wl.

furthur inspection of dmesg still shows references to b43:

[   28.798379] input: b43-phy0 as /devices/virtual/input/input8
[   28.935353] b43-phy0 debug: Loading firmware version 351.126 (2006-07-29 05:54:02)
[   29.942455] b43-phy0 debug: Chip initialized
[   29.942822] b43-phy0 debug: 64-bit DMA initialized
[   29.944697] Registered led device: b43-phy0:tx
[   29.944887] Registered led device: b43-phy0:rx
[   29.945025] Registered led device: b43-phy0:radio
[   29.945104] b43-phy0 ERROR: PHY transmission error
[   29.945113] b43-phy0 debug: Wireless interface started
[   29.949739] b43-phy0 debug: Adding Interface type 2
[   29.952790] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   29.995626] b43-phy0 debug: Removing Interface type 2
[   30.000714] b43-phy0 debug: Wireless interface stopped
[   30.000985] b43-phy0 debug: DMA-64 0x0200 (RX) max used slots: 0/64
[   30.001144] b43-phy0 debug: DMA-64 0x0340 (TX) max used slots: 0/128
[   30.005408] b43-phy0 debug: DMA-64 0x0300 (TX) max used slots: 0/128
[   30.005714] b43-phy0 debug: DMA-64 0x02C0 (TX) max used slots: 0/128
[   30.005926] b43-phy0 debug: DMA-64 0x0280 (TX) max used slots: 0/128
[   30.006102] b43-phy0 debug: DMA-64 0x0240 (TX) max used slots: 2/128
[   30.006276] b43-phy0 debug: DMA-64 0x0200 (TX) max used slots: 0/128

I'm now very :confused: as I have made sure that the b43 driver is disabled and unselected in restricted drivers.  

HELP pls!

also /var/log/messages comes up with sumthin weird:
Nov 26 11:20:38  dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Nov 26 11:20:38  dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Nov 26 11:20:38  dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Nov 26 11:20:38  dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.interface_mtu
Nov 26 11:24:09  kernel: [   72.518295] b43-phy0: Broadcom 4311 WLAN found
Nov 26 11:24:09  kernel: [   72.564149] b43-phy1: Broadcom 4311 WLAN found
Nov 26 11:24:09  kernel: [   72.580948] udev: renamed network interface wlan0 to wlan1
Nov 26 11:24:09  kernel: [   72.661447] input: b43-phy1 as /devices/virtual/input/input8
Nov 26 11:24:10  kernel: [   73.900821] Registered led device: b43-phy1:tx
Nov 26 11:24:10  kernel: [   73.901022] Registered led device: b43-phy1:rx
Nov 26 11:24:10  kernel: [   73.901146] Registered led device: b43-phy1:radio
Nov 26 11:24:10  kernel: [   73.910504] ADDRCONF(NETDEV_UP): wlan1: link is not ready
Nov 26 11:24:32  dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/wlan1 for sub-path wlan1.dbus.get.reason
Nov 26 11:24:37  kernel: [   75.894244] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready


what does redhat have to do with anything?

---

### Post by majikins on 2008-11-28
right updated to kernel 2.6.24.22 this morning and now MAGIC!

wl driver is loaded properly.

wicd works like a dream.

I'm so happy!

just sumthing weird - instead of wlan0 or 1, the wifi interface is listed as eth1 - just had to put that in wicd to use.

:guitar::popcorn:=D>

---

