---
title: "No networks are listed"
date: 2014-02-04
forum: Networking &amp; Wireless
---

### Post by HJQG3wT on 2014-02-04
I just bought this wireless card from thinkpenguin. 
[https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-pci-card](https://www.thinkpenguin.com/gnu-linux/penguin-wireless-n-pci-card)

When I try to connect, no networks are listed.
```

 adam@fornax:~$ lspci00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200/2nd Generation Core Processor Family PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:16.0 Communication controller: Intel Corporation 6 Series/C200 Series Chipset Family MEI Controller #1 (rev 04)
00:19.0 Ethernet controller: Intel Corporation 82579V Gigabit Network Connection (rev 05)
00:1a.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #2 (rev 05)
00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05)
00:1c.0 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 1 (rev b5)
00:1c.1 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 2 (rev b5)
00:1c.3 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 4 (rev b5)
00:1c.4 PCI bridge: Intel Corporation 6 Series/C200 Series Chipset Family PCI Express Root Port 5 (rev b5)
00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev b5)
00:1d.0 USB controller: Intel Corporation 6 Series/C200 Series Chipset Family USB Enhanced Host Controller #1 (rev 05)
00:1f.0 ISA bridge: Intel Corporation Z68 Express Chipset Family LPC Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 6 Series/C200 Series Chipset Family SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 6 Series/C200 Series Chipset Family SMBus Controller (rev 05)
03:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
04:00.0 SATA controller: JMicron Technology Corp. JMB362 SATA Controller (rev 10)
05:00.0 USB controller: ASMedia Technology Inc. ASM1042 SuperSpeed USB Host Controller
06:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 01)
07:00.0 Network controller: Qualcomm Atheros AR922X Wireless Network Adapter (rev 01)


```


```

adam@fornax:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr c8:60:00:c0:be:f6  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 Memory:f7c00000-f7c20000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:349 errors:0 dropped:0 overruns:0 frame:0
          TX packets:349 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:144356 (144.3 KB)  TX bytes:144356 (144.3 KB)


```

---

### Post by varunendra on 2014-02-06
Hmm.. so sorry to see that no network cards work well for you, at least not out-of-box. Are we in for another joy ride?

First off, please always use 'Code' tags for posting outputs, see the "Using Code Tags" link in my signature to see why and how.

Next, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

---

### Post by HJQG3wT on 2014-02-12
Thanks for responding, Varun. Cards from ThinkPenguin are supposed to run out-of-the-box, so I'm thinking in all the previous attempts, I messed something up. Here's the script output:

```



*************** info trace ***************


***** uname -a *****


Linux fornax 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
07:00.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01)
    Subsystem: D-Link System Inc DWA-552 802.11n Xtreme N Desktop Adapter (rev A2) [1186:3a7a]


***** lsusb *****


Bus 002 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 046d:081b Logitech, Inc. Webcam C310
Bus 002 Device 003: ID 08bb:2902 Texas Instruments PCM2902 Audio Codec
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


ath9k                 155779  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444732  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              597268  1 ath9k
cfg80211              480503  3 ath,ath9k,mac80211


***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


#for wake-on-lan
ethernet-wol g


***** iwlist *****




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     9960BB0B644BE14E4A2F42B
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,ath9k_common,mac80211,ath,cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           enable_diversity:Enable Antenna diversity for AR9565 (int)


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     2DB88A2876852DC1D8C5A1D
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     57A1E15BE088B8A5C4BE74F
depends:        ath
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-15-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A890CDBC88E6EF28CD751DD
depends:        cfg80211
intree:         Y
vermagic:       3.11.0-15-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.6/0000:06:00.0/0000:07:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x1814:0x5392 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# PCI device 0x168c:0x0029 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


***** dmesg *****


[    8.103237] ath9k 0000:07:00.0: enabling device (0000 -> 0002)
[    9.667587] ath: phy0: Bad EEPROM checksum 0x38fa or revision 0x000e
[    9.667605] ath: phy0: Unable to initialize hardware; initialization status: -22
[    9.667622] ath9k 0000:07:00.0: Failed to initialize device
[    9.686619] ath9k: probe of 0000:07:00.0 failed with error -22


****************** done ******************



```

---

### Post by varunendra on 2014-02-12
> **HJQG3wT said:**
> ```

[    8.103237] ath9k 0000:07:00.0: enabling device (0000 -> 0002)
[    9.667587] ath: phy0: [COLOR="#FF0000"]Bad EEPROM checksum 0x38fa or revision 0x000e[/COLOR]
[    9.667605] ath: phy0: [COLOR="#FF0000"]Unable to initialize hardware; initialization status: -22[/COLOR]
[    9.667622] ath9k 0000:07:00.0: Failed to initialize device
[    9.686619] ath9k: probe of 0000:07:00.0 failed with error -22

```

I don't like above messages, but let's try a newer driver before we come to a conclusion. Accordingly, please check which backport modules are available for your installation (you may have to enable "Unsupported Updates" under "Updates" tab in "Software Properties" (Alt-F2 > software-properties-gtk)) :
```
sudo apt-get update
sudo apt-cache show linux-backports-modules* | grep Package
```

I am considering to install the version from kernel 3.12, as originally suggested by dr. chili555 here : [http://askubuntu.com/a/392791](http://askubuntu.com/a/392791)

---

### Post by HJQG3wT on 2014-02-12
```

adam@fornax:~$ sudo apt-cache show linux-backports-modules* | grep Package
E: No packages found

```

Also, I wrote to thinkPenguin. Their response:

> 
[FONT=arial]Have you tried:[/FONT]

[FONT=arial]sudo iwconfig[/FONT]

[FONT=arial]if it sees wlan[X] in the list like wlan0 then run:[/FONT]

[FONT=arial]sudo ifconfig wlan[x] up[/FONT]
[FONT=arial]sudo iwlist wlan[x] scanning[/FONT]

[FONT=arial]While this shouldn't be necessary I have encountered cards that wouldn't[/FONT]
[FONT=arial]scan initially. After forcing them once they work as expected. What this[/FONT]
[FONT=arial]command does is force the scanning to commence immediately. Disabling the[/FONT]
[FONT=arial]networking and wireless from the network applet (right click the applet)[/FONT]
[FONT=arial]should also have the same effect of forcing the wireless card to scan the[/FONT]
[FONT=arial]network for wireless access points. I [/FONT][FONT=arial]think[/FONT][FONT=arial] the reason it doesn't[/FONT]
[FONT=arial]sometimes scan initially is that the network applet is set to scan[/FONT]
[FONT=arial]automatically but won't scan more than a certain number of time repeatedly[/FONT]
[FONT=arial]and if it thinks its been scanned recently then it just doesn't.[/FONT]

[FONT=arial]Beyond that what distribution and version are you using? I'm assuming for[/FONT]
[FONT=arial]the moment there isn't a problem here or with the card being defective.[/FONT]

[FONT=arial]Some other things that may help to identify the problem is checking the[/FONT]
[FONT=arial]BIOS and making sure plug-n-play are enabled. Then booting from a live CD.[/FONT]
[FONT=arial]Sometimes people have blacklisted drivers/modules in an effort to get[/FONT]
[FONT=arial]other devices working. Particularly those who have touched NDISWrapper.[/FONT]
[FONT=arial]That could also leave one with a card that doesn't work.[/FONT]

[FONT=arial]There may not be a whole lot more to really investigate. The cards have[/FONT]
[FONT=arial]native support in the mainline kernel and don't require any firmware. As[/FONT]
[FONT=arial]long as there isn't an issue with the system specifically and the version[/FONT]
[FONT=arial]of the distribution is remotely recent this card should work out of the[/FONT]
[FONT=arial]box.[/FONT]

[FONT=arial]We can expedite another card if it appears to be defective. We'll give you[/FONT]
[FONT=arial]an RMA # and then you just need to get us a tracking number when[/FONT]
[FONT=arial]returning. At which point we can ship another card out right away. No need[/FONT]
[FONT=arial]to wait. Otherwise we can ship a new card when it is received.[/FONT]

[FONT=arial]What I might also suggest is exchanging it for a different model. We can[/FONT]
[FONT=arial]refund the difference if there is a price discrepancy between the two. The[/FONT]
[FONT=arial]reason to switch models is it'll ensure any issue pertaining to a card[/FONT]
[FONT=arial]being problematic in a given system isn't duplicated twice. While not that[/FONT]
[FONT=arial]common I have seen that in some circumstances. Mostly with mini itx boards[/FONT]
[FONT=arial]and PCIe x16 slots where the motherboard manufacturers are designing[/FONT]
[FONT=arial]essentially non-standard slots PCIe slots that only work with graphics[/FONT]
[FONT=arial]cards. They'll usually explicitly state this in documentations/manuals[/FONT]
[FONT=arial]even, but most people aren't aware of that.[/FONT]


---

### Post by varunendra on 2014-02-12
> **HJQG3wT said:**
> ```

adam@fornax:~$ sudo apt-cache show linux-backports-modules* | grep Package
E: **[COLOR="#FF0000"]No packages found[/COLOR]**

```

Similar situation, my similar guess and a similar solution.. please try this : [http://ubuntuforums.org/showthread.php?t=2204912&p=12927696#post12927696](http://ubuntuforums.org/showthread.php?t=2204912&p=12927696#post12927696)

Replace the "make defconfig-wifi" with "**make defconfig-ath9k**" command, rest would be the same.

And it's good to see that thinkPenguin is being so co-operative here. Maybe you should give them link to this thread as reference to what you are trying. See if they can help with it or suggest a replacement themselves. They sound honest.

---

### Post by HJQG3wT on 2014-02-13
Ok did that. No obvious change. I'm sending the link for this thread to ThinkPenguin in case they have anything to add.


I ran the script again too:
```



*************** info trace ***************


***** uname -a *****


Linux fornax 3.11.0-15-generic #25-Ubuntu SMP Thu Jan 30 17:22:01 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux


***** lsb_release *****


Distributor ID:    Ubuntu
Description:    Ubuntu 13.10
Release:    13.10
Codename:    saucy


***** lspci *****


00:19.0 Ethernet controller [0200]: Intel Corporation 82579V Gigabit Network Connection [8086:1503] (rev 05)
    Subsystem: ASUSTeK Computer Inc. P8P67 Deluxe Motherboard [1043:849c]
    Kernel driver in use: e1000e
--
07:00.0 Network controller [0280]: Qualcomm Atheros AR922X Wireless Network Adapter [168c:0029] (rev 01)
    Subsystem: D-Link System Inc DWA-552 802.11n Xtreme N Desktop Adapter (rev A2) [1186:3a7a]


***** lsusb *****


Bus 002 Device 006: ID 0cf3:3005 Atheros Communications, Inc. AR3011 Bluetooth
Bus 002 Device 005: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 002 Device 004: ID 046d:081b Logitech, Inc. Webcam C310
Bus 002 Device 003: ID 08bb:2902 Texas Instruments PCM2902 Audio Codec
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


***** PCMCIA Card Info *****




***** iwconfig *****




***** rfkill *****


0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


***** lsmod *****


ath9k                 101498  0 
ath9k_common           13792  1 ath9k
ath9k_hw              428205  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              515529  1 ath9k
cfg80211              478869  3 ath,ath9k,mac80211
compat                 13385  5 cfg80211,ath9k_common,ath9k,mac80211,ath9k_hw


***** nm-tool *****


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


#for wake-on-lan
ethernet-wol g


***** iwlist *****




***** resolv.conf *****




***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac


[/etc/modprobe.d/libpisock9.conf]
blacklist visor


***** modinfo *****


filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     6D837567F66C87252B5746B
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv000010CFsd00001783bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000064bc*sc*i*
alias:          pci:v0000168Cd00000034sv000014CDsd00000063bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000103Csd00001864bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006641bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006631bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001043sd0000850Ebc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002110bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001969sd00000091bc*sc*i*
alias:          pci:v0000168Cd00000034sv000017AAsd00003214bc*sc*i*
alias:          pci:v0000168Cd00000034sv0000168Csd00003117bc*sc*i*
alias:          pci:v0000168Cd00000034sv000011ADsd00006661bc*sc*i*
alias:          pci:v0000168Cd00000034sv00001A3Bsd00002116bc*sc*i*
alias:          pci:v0000168Cd00000033sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003219bc*sc*i*
alias:          pci:v0000168Cd00000032sv000017AAsd00003218bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C708bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C680bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000C706bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd0000410Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004106bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Dsd00004105bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000185Fsd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003122bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000168Csd00003119bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E075bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002152bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd0000126Abc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002126bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001237bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002086bc*sc*i*
alias:          pci:v0000168Cd00000030sv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Esv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Dsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Csv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv*sd*bc*sc*i*
alias:          pci:v0000168Cd0000002Bsv00001A3Bsd00002C37bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd00001536bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv000010CFsd0000147Cbc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000185Fsd0000309Dbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A32sd00000306bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006642bc*sc*i*
alias:          pci:v0000168Cd0000002Asv000011ADsd00006632bc*sc*i*
alias:          pci:v0000168Cd0000002Asv0000105Bsd0000E01Fbc*sc*i*
alias:          pci:v0000168Cd0000002Asv00001A3Bsd00001C71bc*sc*i*
alias:          pci:v0000168Cd0000002Asv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000029sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000027sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000024sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000023sv*sd*bc*sc*i*
depends:        ath9k_hw,mac80211,compat,ath9k_common,cfg80211,ath
vermagic:       3.11.0-15-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)


filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_common.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     B65D5C15D1E4C019C588B60
depends:        compat,ath,ath9k_hw
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
version:        backported from Linux (v3.12.8-0-g97f15f1) using backports v3.12.8-1-0-geb41fad
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     48190E60BAAA01309886B35
depends:        compat,ath
vermagic:       3.11.0-15-generic SMP mod_unload modversions 


filename:       /lib/modules/3.11.0-15-generic/updates/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     A6709A1820CCCB16F734445
depends:        cfg80211
vermagic:       3.11.0-15-generic SMP mod_unload modversions 




***** udev rules *****


# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x168c:/sys/devices/pci0000:00/0000:00:1c.6/0000:06:00.0/0000:07:00.0 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x1814:0x5392 (rt2800pci)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"


# PCI device 0x168c:0x0029 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"


***** dmesg *****


[    8.087215] ath9k 0000:07:00.0: enabling device (0000 -> 0002)
[    9.652110] ath: phy0: Bad EEPROM checksum 0x38fa or revision 0x000e
[    9.652128] ath: phy0: Unable to initialize hardware; initialization status: -22
[    9.652146] ath9k 0000:07:00.0: Failed to initialize device
[    9.668036] ath9k: probe of 0000:07:00.0 failed with error -22


****************** done ******************

```

---

### Post by varunendra on 2014-02-13
No further suggestions from me. Let's see what ThinkPenguin's reply is.

Based on what I could find on the net, the above error messages don't seem to necessarily mean that the hardware faulty (a few worked despite those messages initially), but for now, I've already tried what I thought to be most trusted version of the driver, and don't know of anything else that we can try with as much confidence.

---

