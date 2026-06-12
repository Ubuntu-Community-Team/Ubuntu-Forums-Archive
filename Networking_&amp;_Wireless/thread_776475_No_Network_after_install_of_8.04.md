---
title: "No Network after install of 8.04"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by Rudje65 on 2008-04-30
Yesterday i made a clean install of the 8.04 on my Acer aspire 1710
But I have no network anymore, under 7.10 worked wired and wireless perfect

Result of lspci
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
00:1f.6 Modem: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Modem Controller (rev 02)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5788 Gigabit Ethernet (rev 03)
03:01.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
03:02.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:03.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

/etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet dhcp

auto eth0

iface wlan0 inet dhcp
wpa-psk 96bb3d121a1dcb5ca81e5b75028a2399bb1c440ca8750ba0b6b1f7ccc573448e
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA2
wpa-ssid Rudje

auto wlan0

Somebody an idea to solve this ?

---

### Post by ibutho on 2008-04-30
Take a look at [http://ubuntuforums.org/showthread.php?t=734003](http://ubuntuforums.org/showthread.php?t=734003) . Hopefully that'll help.

---

### Post by Rudje65 on 2008-05-01
It didn't help and my first problem is to fix my wired network

---

### Post by agim on 2008-05-01
How did you get it working initially?

Also, post the output of this command, please.

iwconfig

---

### Post by Rudje65 on 2008-05-01
I don,t know what made it to work but this morning my wired network is ok

now i can concentrate me on my wireless 
thanks for the sugestions

---

### Post by Ayuthia on 2008-05-01
Can you post your lspci -nn?  It will provide the chipset number for your BCM4306.  This card has various chipsets.  My Dell laptop is a BCM4306 rev 03 and has a chipset of 14e4:4320 and it was able to use the b43-fwcutter method to get wireless to work.

---

