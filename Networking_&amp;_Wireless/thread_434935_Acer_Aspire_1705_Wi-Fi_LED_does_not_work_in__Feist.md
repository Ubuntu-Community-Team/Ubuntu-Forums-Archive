---
title: "Acer Aspire 1705 Wi-Fi LED does not work in  Feisty server setup"
date: 2007-05-06
forum: Networking &amp; Wireless
---

### Post by cendant on 2007-05-06
If I install Feisty from Alternative CD, then the red LED close to power button lights. That means wireless is on.

If I try to install from a LiveCD or server CD (I prefer installing the server and  **gnome-core** and re-compile the kernel), this LED light is not on. No wireless internet is available, although Ethernet works fine.

What is being loaded during booting so that this LED light kicks on?

thank you in advance

---

### Post by cendant on 2007-05-06
Acer Aspire 1705SMi
Pentium IV 3.06
AMBIT Wi-Fi 802.11b



These are the results when the LED is on

**# lspci**

00:0b.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV31M [GeForce FX Go5600] (rev a1)


**# dmesg | grep eth**

[   34.281260] eth0: SiS 900 PCI Fast Ethernet at 0x2000, IRQ 22, 00:c0:9f:31:91:f5.
[   47.989932] eth1: Hardware identity 8022:0000:0001:0000
[   47.990053] eth1: Station identity  001f:0006:0001:0005
[   47.990056] eth1: Firmware determined as Intersil 1.5.6
[   47.990058] eth1: Ad-hoc demo mode supported
[   47.990060] eth1: IEEE standard IBSS ad-hoc mode supported
[   47.990061] eth1: WEP supported, 104-bit key
[   47.990147] eth1: MAC address 00:02:8A:A7:5A:E3
[   47.990233] eth1: Station name "Prism  I"
[   47.990857] eth1: ready
[   47.991290] eth1: orinoco_pci at 0000:00:0b.0
[   49.858970] eth1: New link status: UNKNOWN (0008)
[   49.921787] eth1: New link status: Disconnected (0002)
[   50.241540] eth1: New link status: Connected (0001)
[   60.194725] eth0: Media Link Off
[   60.195183] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   67.081822] eth1: no IPv6 routers present


**# iwconfig**

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"CENSURE"  Nickname:"Prism  I"
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0F:CC:3B:40:8C   
          Bit Rate:11 Mb/s   Sensitivity:1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=54/92  Signal level=-41 dBm  Noise level=-141 dBm
          Rx invalid nwid:0  Rx invalid crypt:92  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0




[B]
# cat /etc/network/interfaces [/B]

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth1
iface eth1 inet dhcp
        # wireless-* options are implemented by the wireless-tools package
        wireless-mode managed
        wireless-essid any
        wireless-key1 89daee6b75f7a9911dec847586

---

### Post by cendant on 2007-05-12
Any takers?!

---

