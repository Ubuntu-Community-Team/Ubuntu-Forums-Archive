---
title: "Why no WPA?"
date: 2007-07-26
forum: Networking &amp; Wireless
---

### Post by johann_p on 2007-07-26
OK, after failing on several other computers, I just booted the Feisty Desktop CD on a IBM/Lenovo Thinkpad T43. 
It seems to detect the WLAN card, but when I open the network settings GUI, the only option for "Password Type" I get is "WEP".

???????

It should be known by now that WEP is nearly as effective as no security at all and the only usable security is WPA. But this option is not offered.

Naturally, WLAN will not run.

At this moment, what is the average user supposed to do: since WLan does not work and WLan is the only way to connect this laptop to the internet, I do not see much choice but ejecting the CD and abort the attempt to install Ubuntu.

Do you agree?

---

### Post by aysiu on 2007-07-26
Forget about the network settings GUI. Keep it on roaming mode.

Left-click on the network manager applet and select the WPA network. You will then have the option to authenticate using WPA encryption.

---

### Post by buntunub on 2007-07-26
Did you try clicking on the Network Icon at the top of your screen first before going into the system menu?

I have found that:

1) If you dont broadcast your SSID, WPA will not work
2) Once you turn on SSID broadcast, you will then see and be able to select your network and enter in the appropriate keyring data. Works like a champ for me now like that.

Edit:

Sorry, there actually IS a way to WPA2 network without SSID Broadcasting, and that way is by following the sticky post above. Doing that however, you must disable your network manager completely and do everything manual. That worked great for me for a while, but its not as convenient as just broadcasting SSID and using network manager.

---

### Post by johann_p on 2007-07-26
> **aysiu said:**
> Forget about the network settings GUI. Keep it on roaming mode.

Left-click on the network manager applet and select the WPA network. You will then have the option to authenticate using WPA encryption.
OK I re-enabled roaming mode.
Then I clicked on the network manager applet: I get a menu with two options. The first is greyed out ("wired network"), the second is "Manual configuration" which leads me exactly to the networking settings GUI again.
In that GUI, I have three entries: 
  A minus, then "Wireless connection"
  A checked box, then "Wired connection"
  A minus, then "Modem connection"

---

### Post by johann_p on 2007-07-26
> **buntunub said:**
> 
1) If you dont broadcast your SSID, WPA will not work

I do broadcast the SSID.

> 
2) Once you turn on SSID broadcast, you will then see and be able to select your network and enter in the appropriate keyring data. Works like a champ for me now like that.

See me post above .. I do not see that and the wired network in the network settings GUI is preceded by a minus. None to see in the menu I get from the networking applet.

> 
Sorry, there actually IS a way to WPA2 network without SSID Broadcasting, and that way is by following the sticky post above. Doing that however, you must disable your network manager completely and do everything manual. That worked great for me for a while, but its not as convenient as just broadcasting SSID and using network manager.

Well that looks scary when all I want is to TEST with the install/live CD whether WLAN works on that device.

---

### Post by aysiu on 2007-07-26
When you right-click on the network manager applet, do you get an *Enable Wireless* option?

---

### Post by johann_p on 2007-07-26
OK, re-enabling the roaming mode did not make the wireless lan show up in the network applet, but after a re-boot of the CD things were as you described: I could just click on the WLAN network with the SSID i want and then I could enter WPA information.

The connection did not succeed though -- I have checked "show password" to make sure the exact characters are entered.
No idea what remains to be the problem now, but I am definitely much further and much closer to success now :)

---

### Post by wieman01 on 2007-07-27
Network Manager does work with disabled SSID broadcast as well. At least that's the case in Feisty.

---

### Post by ugm6hr on 2007-07-27
> **johann_p said:**
> OK, re-enabling the roaming mode did not make the wireless lan show up in the network applet, but after a re-boot of the CD things were as you described: I could just click on the WLAN network with the SSID i want and then I could enter WPA information.

The connection did not succeed though -- I have checked "show password" to make sure the exact characters are entered.
No idea what remains to be the problem now, but I am definitely much further and much closer to success now :)

Check your chipset in Terminal:
```
lspci
```
Look for Network / Ethernet controller.  Then search here for the output.

```
lshw -C network
```
Will give more complte info.

---

### Post by stelloscuro on 2007-12-19
Ok I have the same problem on the same computer, so I would like to carry this on

output of lspci:

00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 3 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: ATI Technologies Inc M22 [Mobility Radeon X300]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751M Gigabit Ethernet PCI Express (rev 11)
0b:00.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev 8d)
0b:02.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
 
output of lshw -C network:

 *-network DISABLED      
       description: Ethernet interface
       product: NetXtreme BCM5751M Gigabit Ethernet PCI Express
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 11
       serial: 00:16:41:57:d2:62
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=tg3 driverversion=3.77 firmware=5751m-v3.46a latency=0 module=tg3 multicast=yes
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications, Inc.
       physical id: 2
       bus info: pci@0000:0b:02.0
       logical name: wifi0
       version: 01
       serial: 00:16:cf:01:02:17
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.2 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

---

### Post by ugm6hr on 2007-12-19
> **stelloscuro said:**
> 
0b:02.0 Ethernet controller: Atheros Communications, Inc. **AR5212** 802.11abg NIC (rev 01)
 
       configuration: broadcast=yes driver=**ath_pci** ip=192.168.1.2 latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g

The bits in bold are important - your chipset is Atheros AR5212 and the driver used is madwifi (ath_pci)

Try searching for AR5212 - this might help get you started: [http://ubuntuforums.org/showpost.php?p=3972141&postcount=77](http://ubuntuforums.org/showpost.php?p=3972141&postcount=77)

---

