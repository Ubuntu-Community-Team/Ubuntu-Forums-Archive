---
title: "wireless network on eee pc ?"
date: 2008-10-22
forum: Networking &amp; Wireless
---

### Post by sohlinux on 2008-10-22
Hi,

Just bought a new laptop, its a "eee pc 904hd", installed ubuntu-8.04.1-desktop but I cannot see the wireless network.

how can I get this wireless network up and running?

Thanks
Tom :)

---

### Post by camoanimal on 2008-10-22
First off, is your wireless card active (i.e. It is recognized by Ubuntu)?  If it is then you could try typing in the SSID or 'name' of you router.  It should search and connect to the router.  If it still does not recognize the router, or card, then you may need to try reinstalling the drivers for that wireless card.

---

### Post by sohlinux on 2008-10-22
> **camoanimal said:**
> First off, is your wireless card active (i.e. It is recognized by Ubuntu)?  If it is then you could try typing in the SSID or 'name' of you router.  It should search and connect to the router.  If it still does not recognize the router, or card, then you may need to try reinstalling the drivers for that wireless card.

All I can see in the network settings is a point to point connection.

inside the p2p properties it shows the following . 

under general tab. connection type. 

serial modem, pppoe modem and gprs/umts

and there is a tab for modem ports, dial type and volume

I havnt a clue where to find the wireless connections?

if the wireless card is not being recognised then how do I install a driver for it?

Thanks
Tom

---

### Post by sethvath on 2008-10-22
In terminal:

lspci <-- look at the very bottom for the wireless card
ifconfig 
iwconfig

copy and paste what you see here.

---

### Post by sohlinux on 2008-10-22
> **sethvath said:**
> In terminal:

lspci <-- look at the very bottom for the wireless card
ifconfig 
iwconfig

copy and paste what you see here.

this is what it says...........

john@john-laptop:~$ lspci

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1c.1 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 2 (rev 04)
00:1c.3 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 4 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
03:00.0 Ethernet controller: Attansic Technology Corp. Unknown device 1026 (rev b0)





john@john-laptop:~$ ifconfig

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1650 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1650 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:83076 (81.1 KB)  TX bytes:83076 (81.1 KB)

john@john-laptop:~$ iwconfig

lo        no wireless extensions.

---

### Post by sethvath on 2008-10-22
Someone has posted on how to get Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01) working with madwifi. You may want to follow the instructions on post #3 and #6. I've never used madwifi, only wicd so I cant comment which is better. 

[http://ubuntuforums.org/showthread.php?t=902860](http://ubuntuforums.org/showthread.php?t=902860)

---

### Post by sohlinux on 2008-10-23
thanks for the info :)

---

