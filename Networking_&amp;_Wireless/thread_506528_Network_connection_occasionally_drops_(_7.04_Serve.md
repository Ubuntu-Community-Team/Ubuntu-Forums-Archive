---
title: "Network connection occasionally drops ( 7.04 Server - RTL8169 - NETDEV WATCHDOG )"
date: 2007-07-21
forum: Networking &amp; Wireless
---

### Post by herbstr2408 on 2007-07-21
Hi guys,

I have an Aopen mini pc running Ubuntu 7.04 Server edition. The problem I have with it is that every now and then the "wired" network connection drops. It happens about 2-3 times a day.

The box is connected to a Netgear ProSafe VPN Firewall (FVS114) which in turn is connected to an ADSL modem on the internet port. No other devices are connected to the Netgear firewall.

To get the network connection back up again I have to either reboot the box, or simply switch off/on the netgear firewall.

I set up the box to act as a wireless access point using hostapd. bridge-utils and madwifi drivers for the wireless part.

The only unusual thing(s) I notice when the connection drops is the following error message in

**_/var/log/dmesg_**
[COLOR="SeaGreen"][ 3222.550627] NETDEV WATCHDOG: eth0: transmit timed out
[ 3234.548124] NETDEV WATCHDOG: eth0: transmit timed out
[ 3246.545620] NETDEV WATCHDOG: eth0: transmit timed out[/COLOR]

**_/var/log/messages_**
[COLOR="SeaGreen"]Jul 20 02:09:57 bonsai kernel: [ 3318.530599] NETDEV WATCHDOG: eth0: transmit timed out
Jul 20 02:10:09 bonsai kernel: [ 3330.528097] NETDEV WATCHDOG: eth0: transmit timed out[/COLOR]

and on the firewall side the led's are flickering like mad on the port the server is connected to. 

I'm not sure why this is happening suddenly. I had the box running on 6.06 for the past year or so without a problem, although it was connected to a netgear switch and not to the firewall directly.


_**Below more info about the system:**_
Ubuntu 7.04 Server (Kernel Version 2.6.20-16-server)

**# lspci -v**
[COLOR="SeaGreen"]01:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8169 Gigabit Ethernet (rev 10)
        Subsystem: AOPEN Inc. Unknown device 0589
        Flags: bus master, 66MHz, medium devsel, latency 32, IRQ 18
        I/O ports at d000 [size=256]
        Memory at d0030000 (32-bit, non-prefetchable) [size=256]
        [virtual] Expansion ROM at 20000000 [disabled] [size=128K]
        Capabilities: [dc] Power Management version 2[/COLOR]

**# ethtool -i eth0**
[COLOR="SeaGreen"]driver: r8169
version: 2.2LK
firmware-version: 
bus-info: 0000:01:06.0[/COLOR]

**# mii-diag eth0**
 [COLOR="SeaGreen"]Basic registers of MII PHY #32:  0100 794d 001c c910 0de1 0020 0004 2001.
 Basic mode control register 0x0100: Auto-negotiation disabled, with
 Speed fixed at 10 mbps, full-duplex.
 You have link beat, and everything is working OK.
 Your link partner is generating 10baseT link beat  (no autonegotiation).
   End of basic transceiver information.[/COLOR]

**# brctl show**
[COLOR="SeaGreen"]bridge name     bridge id               STP enabled     interfaces
br0             8000.00018062417b       no              eth0
                                                        ath0[/COLOR]

**/etc/network/interfaces**
[COLOR="SeaGreen"]auto ath0
iface ath0 inet manual
        pre-up wlanconfig ath0 destroy
        pre-up wlanconfig ath0 create wlandev wifi0 wlanmode ap
        post-down wlanconfig ath0 destroy
        wireless-mode master

auto br0
iface br0 inet static
        address 192.168.0.1
        network 192.168.0.0
        netmask 255.255.255.0
        broadcast 192.168.0.255
        gateway 192.168.0.254
        bridge_ports eth0 ath0
        bridge_stp off[/COLOR]

I would really appreciate if somebody has an idea on how to fix this as it is driving me mad.

I tried a few things, like using a different port on the firewall, forcing the interface to 10Mbit FD & HD. Even disabled acpi by editing grub and added the following parameters **acpi=off noapci** Nothing seems to help. I cannot reproduce the problem either. The connection sometimes drops even if there is no load on the interface.

BR // Rupert

---

### Post by herbstr2408 on 2007-07-22
I tried now a different network card (usb) and have exactly the same problem. After a while the lan connection just drops and I have to restart the firewall.

The usb card I use now:

[COLOR="SeaGreen"]pegasus 5-2:1.0: setup Pegasus II specific registers
pegasus 5-2:1.0: eth1, ELECOM USB Ethernet LD-USB20, 00:90:fe:66:d5:b2[/COLOR]

[B]# ethtool -i eth1
[/B][COLOR="SeaGreen"]driver: pegasus
version: v0.6.14 (2006/09/27)
firmware-version: 
bus-info: usb-0000:00:1d.7-2[/COLOR]

I don't think its a driver problem, which I guess leaves either a problem with the current version of the kernel, or the Netgear firewall, maybe a combination of both ?!?

PS: I upgraded the firewall with the latest firmware (v1.1_10) a couple of days ago...didn't help though.

Rupert

---

