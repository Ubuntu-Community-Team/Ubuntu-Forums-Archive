---
title: "Acer Aspire 5100: Ubuntu wont connect to wireless internet"
date: 2014-06-28
forum: Networking &amp; Wireless
---

### Post by dennis24 on 2014-06-28
I just installed Ubuntu onto my old acer aspire 5100 but when i was done and booted it up for the first time i saw that i had no internet. I think it is something wrong with the drivers because when I try to connect to wireless it dosent even give me the option to scan wireless at all. I am a very novice user to Ubuntu (and Linux for that matter) and dont know how to fix this. Any help will be well appreciated ~Thanks
PS- I can download anything needed on this computer and transfer it via USB to the Acer because i cant get any type of connection on that one

---

### Post by mörgæs on 2014-06-28
Moved to Networking. Please read the sticky notes.

---

### Post by dennis24 on 2014-06-28
sorry, i dident know i could do that, will keep that in mind (:

---

### Post by squakie on 2014-06-28
I don't know if the on-board adapter in your older laptop is connected internally to the PCI bus or the USB bus (some older laptop's built-in wireless actually were connected internally to the SB bus).

So,  please post back the output of the following:

lspci | grep Network

and 

lsusb

---

### Post by dennis24 on 2014-06-29
OK when i did the [COLOR=#000000]lspci | grep Network[/COLOR] nothing happened but for the other one i got this 

```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by squakie on 2014-06-29
Hummmmm.....that should have worked.  Try this and post the output back here:

lscpi

---

### Post by dennis24 on 2014-06-29
OK here is lscpi

```
00:00.0 Host bridge: Advanced Micro Devices, Inc. [AMD/ATI] RS480/RS482/RS485 Host Bridge (rev 10)00:01.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Bridge [int gfx]
00:04.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 1
00:05.0 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] RC4xx/RS4xx PCI Express Port 2
00:12.0 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 Serial ATA Controller (rev 80)
00:13.0 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.1 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB Host Controller (rev 80)
00:13.2 USB controller: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 USB2 Host Controller (rev 80)
00:14.0 SMBus: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 SMBus Controller (rev 83)
00:14.1 IDE interface: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 IDE Controller (rev 80)
00:14.2 Audio device: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: Advanced Micro Devices, Inc. [AMD/ATI] IXP SB4x0 PCI-PCI Bridge (rev 80)
00:18.0 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices, Inc. [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RS482M [Mobility Radeon Xpress 200]
06:01.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter (rev 10)
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:04.0 CardBus bridge: ENE Technology Inc CB-712/4 Cardbus Controller (rev 10)
06:04.1 FLASH memory: ENE Technology Inc ENE PCI Memory Stick Card Reader Controller (rev 01)
06:04.2 Unclassified device [0005]: ENE Technology Inc ENE PCI Secure Digital Card Reader Controller (rev 01)
06:04.3 FLASH memory: ENE Technology Inc FLASH memory: ENE Technology Inc: (rev 01)
06:04.4 FLASH memory: ENE Technology Inc SD/MMC Card Reader Controller (rev 01)

```

I also ran a wireless script and got this if its any help

```
[COLOR=#000000]#!/bin/bash[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# Copyright (c) 2012[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# Authors: Wild Man, Krytarik[/COLOR]
[COLOR=#000000]# Helpers: chili555[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# This script gathers the infos necessary for troubleshooting a wireless[/COLOR]
[COLOR=#000000]# connection and saves them in a text file, wrapping it in an archive if it[/COLOR]
[COLOR=#000000]# exceeds the size limit of 19.5 kB for .txt files on the Ubuntu Forums.[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]################################################## ##########################[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# This program is free software: you can redistribute it and/or modify[/COLOR]
[COLOR=#000000]# it under the terms of the GNU General Public License as published by[/COLOR]
[COLOR=#000000]# the Free Software Foundation, either version 3 of the License, or[/COLOR]
[COLOR=#000000]# (at your option) any later version.[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# This program is distributed in the hope that it will be useful,[/COLOR]
[COLOR=#000000]# but WITHOUT ANY WARRANTY; without even the implied warranty of[/COLOR]
[COLOR=#000000]# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE. See the[/COLOR]
[COLOR=#000000]# GNU General Public License for more details.[/COLOR]
[COLOR=#000000]#[/COLOR]
[COLOR=#000000]# You should have received a copy of the GNU General Public License[/COLOR]
[COLOR=#000000]# along with this program. If not, see <http://www.gnu.org/licenses/>.[/COLOR]
[COLOR=#000000]#[/COLOR]


[COLOR=#000000]FILEBASE="wireless-info"[/COLOR]
[COLOR=#000000]MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rt(2|3|5 |6|7)|rtl|r(818|871)|8192(cu|du)|ssb|wl|b43|bcma|b rcm|eth1|ndis|wlan0|firm|etwork)[^[[/COLOR]:razz:[COLOR=#000000]unct:] ]*"[/COLOR]


[COLOR=#000000]exec 3>&1 4>&2[/COLOR]
[COLOR=#000000]exec 1> $FILEBASE.txt 2> /dev/null[/COLOR]
[COLOR=#000000]if [ "$?" != "0" ]; then[/COLOR]
[COLOR=#000000]printf "\nCannot write output file, aborting.\n\n"[/COLOR]
[COLOR=#000000]exit 1[/COLOR]
[COLOR=#000000]fi[/COLOR]


[COLOR=#000000]printf "\n########## wireless info START ##########\n"[/COLOR]


[COLOR=#000000]printf "\n##### release #####\n\n"[/COLOR]
[COLOR=#000000]lsb_release -idrc[/COLOR]


[COLOR=#000000]printf "\n##### kernel #####\n\n"[/COLOR]
[COLOR=#000000]uname -a[/COLOR]


[COLOR=#000000]printf "\n##### lspci #####\n\n"[/COLOR]
[COLOR=#000000]lspci -nnk | grep -iA2 net | sed 's/^--$//'[/COLOR]


[COLOR=#000000]printf "\n##### lsusb #####\n\n"[/COLOR]
[COLOR=#000000]lsusb[/COLOR]


[COLOR=#000000]printf "\n##### PCMCIA Card Info #####\n\n"[/COLOR]
[COLOR=#000000]pccardctl info[/COLOR]


[COLOR=#000000]printf "\n##### rfkill #####\n\n"[/COLOR]
[COLOR=#000000]rfkill list all[/COLOR]


[COLOR=#000000]printf "\n##### lsmod #####\n\n"[/COLOR]
[COLOR=#000000]lsmod | egrep "(^|[[[/COLOR]:razz:[COLOR=#000000]unct:] ])${MODMATCHES}([[[/COLOR]:razz:[COLOR=#000000]unct:] ]|$)"[/COLOR]


[COLOR=#000000]printf "\n##### iw reg get #####\n\n"[/COLOR]
[COLOR=#000000]iw reg get[/COLOR]


[COLOR=#000000]printf "\n##### interfaces #####\n\n"[/COLOR]
[COLOR=#000000]sed 's/wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces[/COLOR]


[COLOR=#000000]printf "\n##### iwconfig #####\n\n"[/COLOR]
[COLOR=#000000]iwconfig[/COLOR]


[COLOR=#000000]printf "\n##### route #####\n\n"[/COLOR]
[COLOR=#000000]route -n[/COLOR]


[COLOR=#000000]printf "\n##### resolv.conf #####\n\n"[/COLOR]
[COLOR=#000000]grep -v '^#' /etc/resolv.conf[/COLOR]


[COLOR=#000000]printf "\n##### nm-tool #####\n"[/COLOR]
[COLOR=#000000]nm-tool[/COLOR]


[COLOR=#000000]printf "\n##### NetworkManager.state #####\n\n"[/COLOR]
[COLOR=#000000]cat -s /var/lib/NetworkManager/NetworkManager.state[/COLOR]


[COLOR=#000000]printf "\n##### NetworkManager.conf #####\n\n"[/COLOR]
[COLOR=#000000]grep -v '^#' /etc/NetworkManager/NetworkManager.conf[/COLOR]
[COLOR=#000000]if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then[/COLOR]
[COLOR=#000000]printf "nm-system-settings.conf (used up to 10.04):\n"[/COLOR]
[COLOR=#000000]grep -v '^#' /etc/NetworkManager/nm-system-settings.conf[/COLOR]
[COLOR=#000000]fi[/COLOR]


[COLOR=#000000]printf "\n##### iwlist #####\n\n"[/COLOR]
[COLOR=#000000]if [ -t 0 ]; then[/COLOR]
[COLOR=#000000]sudo iwlist scan || echo "Aquiring of root rights failed."[/COLOR]
[COLOR=#000000]elif [ -x /usr/bin/gksudo ]; then[/COLOR]
[COLOR=#000000]gksudo iwlist scan || echo "Aquiring of root rights failed."[/COLOR]
[COLOR=#000000]elif [ -x /usr/bin/kdesudo ]; then[/COLOR]
[COLOR=#000000]kdesudo iwlist scan || echo "Aquiring of root rights failed."[/COLOR]
[COLOR=#000000]else[/COLOR]
[COLOR=#000000]echo "No way to aquire root rights found."[/COLOR]
[COLOR=#000000]fi[/COLOR]


[COLOR=#000000]printf "\n##### iwlist channel #####\n\n"[/COLOR]
[COLOR=#000000]iwlist chan[/COLOR]


[COLOR=#000000]printf "\n##### modinfo #####\n\n"[/COLOR]
[COLOR=#000000]MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')[/COLOR]
[COLOR=#000000]for MODULE in $MODULNAMES; do[/COLOR]
[COLOR=#000000]modinfo $MODULE[/COLOR]
[COLOR=#000000]echo[/COLOR]
[COLOR=#000000]done[/COLOR]


[COLOR=#000000]printf "\n##### modules #####\n\n"[/COLOR]
[COLOR=#000000]grep -v '^#' /etc/modules[/COLOR]


[COLOR=#000000]printf "\n##### blacklist #####\n"[/COLOR]
[COLOR=#000000]for CONFFILE in /etc/modprobe.d/*.conf; do[/COLOR]
[COLOR=#000000]if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nv idia)' <<< $CONFFILE) ]]; then[/COLOR]
[COLOR=#000000]BLACKLIST=$(grep '^blacklist' $CONFFILE)[/COLOR]
[COLOR=#000000]if [ -n "$BLACKLIST" ]; then[/COLOR]
[COLOR=#000000]printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"[/COLOR]
[COLOR=#000000]fi[/COLOR]
[COLOR=#000000]fi[/COLOR]
[COLOR=#000000]done[/COLOR]


[COLOR=#000000]printf "\n##### udev rules #####\n"[/COLOR]
[COLOR=#000000]egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules[/COLOR]


[COLOR=#000000]printf "\n##### dmesg #####\n\n"[/COLOR]
[COLOR=#000000]dmesg | egrep "[[[/COLOR]:razz:[COLOR=#000000]unct:] ]${MODMATCHES}[[[/COLOR]:razz:[COLOR=#000000]unct:] ]"[/COLOR]


[COLOR=#000000]printf "\n########## wireless info END ############\n\n"[/COLOR]


[COLOR=#000000]exec 1>&3 3>&-[/COLOR]
[COLOR=#000000]exec 2>&4 4>&-[/COLOR]


[COLOR=#000000]RESULTS=$(cat -s $FILEBASE.txt)[/COLOR]
[COLOR=#000000]sed 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' <<< "$RESULTS" > $FILEBASE.txt[/COLOR]


[COLOR=#000000]if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then[/COLOR]
[COLOR=#000000]tar -czf $FILEBASE.tar.gz $FILEBASE.txt[/COLOR]
[COLOR=#000000]rm $FILEBASE.txt[/COLOR]
[COLOR=#000000]printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"[/COLOR]
[COLOR=#000000]else[/COLOR]
[COLOR=#000000]printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"[/COLOR]
[COLOR=#000000]fi[/COLOR]
```

---

### Post by dennis24 on 2014-06-29
Well for some reason i did the [COLOR=#000000]lspci | grep Network again and i got this 

```
[/COLOR]06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

[COLOR=#000000]
```[/COLOR]

---

### Post by squakie on 2014-06-29
You posted the script - you need to execute it and then post the resulting file back  - wireless-info.txt here not the script.

Since you have the Broadcom 4318, did you try (via a hardwired connection) going to additional drivers in the system setings?  Does it return anything?  Did you try enabling what it shows?

If you find an additional driver and enable it, and still have problems, run the wireless script again and post the output file back here.

---

### Post by dennis24 on 2014-06-30
I looked to see if i could even get a wired connection but still cant. As for the additional drivers in the system settings it says "No additional drivers available" and under that it said "No Proprietary drivers are in use". I also ran the wireless script again and this is the out-put&#8595;&#8595;&#8595;&#8595;

```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux dennis-Aspire-5100 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 athlon i686 GNU/Linux


##### lspci #####


06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: 8139too
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)


##### lsusb #####


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill #####


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


ssb                    51854  0 


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


No way to aquire root rights found.


##### iwlist channel #####


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512


##### modules #####


lp


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #####


[    1.985576] b43-pci-bridge 0000:06:02.0: enabling device (0004 -> 0006)
[    2.004770] ssb: Failed to switch to core 0
[    2.004789] ssb: Failed to register PCI version of SSB with error -19


########## wireless info END ############

```

---

### Post by dennis24 on 2014-06-30
also when i do "sudo iwconfig" I get

```

lo          no wireless extension
 
eth0      no wireless extension 

```

but i dont have wlan0

---

### Post by varunendra on 2014-06-30
> **dennis24 said:**
> ```

[    1.985576] b43-pci-bridge 0000:06:02.0: enabling device (0004 -> 0006)
[    2.004770] ssb: Failed to switch to core 0
[    2.004789] ssb: [COLOR="#FF0000"]Failed to register PCI version of SSB with error -19[/COLOR]

```
Usually we see a firmware error with these cards, the above one looks a bit odd. But let's try the usual fix first.

**[SIZE=3]To install the required firmware package (linux-firmware-nonfree) without internet connection[/SIZE]** please follow these steps -

**[COLOR="#FF0000"]EDIT :[/COLOR]** 11-Sep-2014 : The "linux-firmware-nonfree" package suggested below no longer installs firmware required by b43 (see this [bug report]("https://bugs.launchpad.net/bugs/1367882")).

**_To install it offline, please follow this post_ :** [http://ubuntuforums.org/showpost.php?p=13119224](http://ubuntuforums.org/showpost.php?p=13119224)


[INDENT][s]**1)** Download the "linux-firmware-nonfree" package from here : [http://packages.ubuntu.com/trusty/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/trusty/all/linux-firmware-nonfree/download)

**2)** Copy the downloaded .deb package onto your Ubuntu Desktop.

**3)** Open a terminal (Ctrl-Alt-T) and run the following commands to install it -
```
cd Desktop
sudo dpkg -i linux-firmware*.deb
```[/INDENT][/s]

Reboot after the installation is finished. If the wireless is still not working, please follow the instructions in this post to download and run 'wireless_script' (experimental version) and post back the report it generates : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

[s]**PS:**
The linux-firmware-nonfree....deb package can also be installed by simply double-clicking it, but some users sometime report problems with that method, so the above command line method is a sure-shot way to do that, without risking any possible problems.[/s] (EDIT: See the edit comment above)

---

### Post by dennis24 on 2014-06-30
[COLOR=#3E3E3E]also when i do "sudo iwconfig" I get ```

lo        no wireless extension 
eth0   no wireless extension
```
 but i dont have wlan0[/COLOR]

---

### Post by varunendra on 2014-06-30
Did you read my post above yours?

---

### Post by dennis24 on 2014-06-30
ya sorry i jut got back and am going to try it now, will post the out-come.

---

### Post by dennis24 on 2014-06-30
OK so i did exactly as said with no errors but still no luck so now here us the new wiresless-info.txt 

```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux dennis-Aspire-5100 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 athlon i686 GNU/Linux


##### lspci #####


06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: 8139too
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)


##### lsusb #####


Bus 001 Device 002: ID 154b:fa05 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill #####


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


ssb                    51854  0 


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


No way to aquire root rights found.


##### iwlist channel #####


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512


##### modules #####


lp


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #####


[    1.922715] b43-pci-bridge 0000:06:02.0: enabling device (0004 -> 0006)
[    1.940794] ssb: Failed to switch to core 0
[    1.940809] ssb: Failed to register PCI version of SSB with error -19


########## wireless info END ############



```

---

### Post by squakie on 2014-07-01
Might I suggest you see this thread:

[http://ubuntuforums.org/showthread.php?t=2160343](http://ubuntuforums.org/showthread.php?t=2160343)

---

### Post by dennis24 on 2014-07-01
Ya iv tried this one too but still havent gotten it to work. i keept running into errors during the "[COLOR=#000000][FONT=Ubuntu Mono]sudo rmmod -f b43" and the "[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe b43" commands[/FONT][/COLOR]

---

### Post by squakie on 2014-07-02
What are the error messages (perhaps a screen capture) when you try both of these?

---

### Post by varunendra on 2014-07-02
The error message "[COLOR="#FF0000"]ssb: Failed to register PCI version of SSB with error -19[/COLOR]" is still there and is troubling me. Probably this failure is why ssb didn't load "b43" later which is what we want to see with this card. But please post back the terminal outputs/errors after running the following commands -
```
modinfo b43
sudo modprobe -v b43
```

---

### Post by dennis24 on 2014-07-02
OK i did the whole b43 process over again and this is what i got
```






dennis@dennis-Aspire-5100:~$ sudo mkdir /lib/firmware/b43
[sudo] password for dennis: 
mkdir: cannot create directory &#8216;/lib/firmware/b43&#8217;: File exists
dennis@dennis-Aspire-5100:~$ sudo cp Desktop/b43/* /lib/firmware/b43
dennis@dennis-Aspire-5100:~$ sudo rmmod -f b43
rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'b43': No such file or directory
rmmod: ERROR: could not remove module b43: No such file or directory
dennis@dennis-Aspire-5100:~$ sudo rmmod -f ssb
dennis@dennis-Aspire-5100:~$  sudo modprobe b43
dennis@dennis-Aspire-5100:~$
```

---

### Post by dennis24 on 2014-07-02
As for the "modinfo b43" command this istwhat i got
```




dennis@dennis-Aspire-5100:~$ modinfo b43
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     BED87D210887FFC71A4BDE0
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)
```
But for the "sudo modprobe -v b43" command nothing happened

---

### Post by dennis24 on 2014-07-02
I re-did the b43 steps from start to finish and this is what happened
```
/



dennis@dennis-Aspire-5100:~$ sudo mkdir /lib/firmware/b43
[sudo] password for dennis: 
mkdir: cannot create directory ‘/lib/firmware/b43’: File exists
dennis@dennis-Aspire-5100:~$ sudo cp Desktop/b43/* /lib/firmware/b43
dennis@dennis-Aspire-5100:~$ sudo rmmod -f b43
rmmod: ERROR: ../libkmod/libkmod-module.c:769 kmod_module_remove_module() could not remove 'b43': No such file or directory
rmmod: ERROR: could not remove module b43: No such file or directory
dennis@dennis-Aspire-5100:~$ sudo rmmod -f ssb
dennis@dennis-Aspire-5100:~$  sudo modprobe b43
dennis@dennis-Aspire-5100:~$
```

And then here is the outcome of the "[COLOR=#000000][FONT=Ubuntu Mono]modinfo b43[/FONT][/COLOR]" command
```




dennis@dennis-Aspire-5100:~$ modinfo b43
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     BED87D210887FFC71A4BDE0
alias:          bcma:m04BFid0812rev1Dcl*
alias:          bcma:m04BFid0812rev18cl*
alias:          bcma:m04BFid0812rev17cl*
alias:          bcma:m04BFid0812rev11cl*
alias:          ssb:v4243id0812rev10*
alias:          ssb:v4243id0812rev0F*
alias:          ssb:v4243id0812rev0D*
alias:          ssb:v4243id0812rev0C*
alias:          ssb:v4243id0812rev0B*
alias:          ssb:v4243id0812rev0A*
alias:          ssb:v4243id0812rev09*
alias:          ssb:v4243id0812rev07*
alias:          ssb:v4243id0812rev06*
alias:          ssb:v4243id0812rev05*
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        77:D7:0E:1D:F4:29:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)
```

But the "[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe -v b43" command did nothing (Maybe its not supposed to.
So ya... now i dont know what to do and im still getting the same [/FONT][/COLOR][COLOR=#000000] "[/COLOR][COLOR=#FF0000]ssb: Failed to register PCI version of SSB with error -19[/COLOR][COLOR=#000000]"[/COLOR][COLOR=#000000][FONT=Ubuntu Mono] error.[/FONT][/COLOR]

---

### Post by varunendra on 2014-07-04
The "modprobe -v b43" command didn't show anything because you had already run "modprobe b43" - which does the same thing, only silently. The "-v" switch is supposed to make the actions verbose. No messages means everything happened correctly and the b43 module should have been loaded.

Can we see the following outputs after you run the command "sudo modprobe -v b43" -
```
lsmod | egrep 'ssb|b43|wl'
dmesg | egrep -i 'firmware|ssb|b43'
lspci -nnk | grep -iA2 net
```
If both the ssb and b43 modules are loaded, and there are no firmware errors, but the card still doesn't work, I wonder if there is a physical defect in the card or the pci bus itself. Can you try the "linux-firmware-nonfree" pacakge on a live session please? You'll have to manually load the b43 driver (with "sudo modprobe -v b43" command) after installing the firmware.

---

### Post by dennis24 on 2014-07-04
Ok here is the out put of the three commands 

```


dennis@dennis-Aspire-5100:~$ sudo modprobe -v b43
[sudo] password for dennis: 
insmod /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko 
dennis@dennis-Aspire-5100:~$ lsmod | egrep 'ssb|b43|wl'
b43                   356470  0 
bcma                   42043  1 b43
mac80211              545990  1 b43
cfg80211              409394  2 b43,mac80211
ssb                    51854  1 b43
dennis@dennis-Aspire-5100:~$ dmesg | egrep -i 'firmware|ssb|b43'
[    0.096740] [Firmware Bug]: ACPI: BIOS _OSI(Linux) query ignored
[    0.235102] acpi PNP0A03:00: [Firmware Info]: MMCONFIG for domain 0000 [bus 00-07] only partially covers this bridge
[    1.951251] b43-pci-bridge 0000:06:02.0: enabling device (0004 -> 0006)
[    1.971198] ssb: Failed to switch to core 0
[    1.971216] ssb: Failed to register PCI version of SSB with error -19
dennis@dennis-Aspire-5100:~$ lspci -nnk | grep -iA2 net
06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:009f]
    Kernel driver in use: 8139too
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)
dennis@dennis-Aspire-5100:~$ 

```

But im not sure what you mean when you say a "[SIZE=2][COLOR=#000000] live session". But im [/COLOR][/SIZE][COLOR=#000000]guessing[/COLOR][SIZE=2][COLOR=#000000] it means to run it off a CD or USB so  i did ever thing but nothing happened and no errors but it still doesn't work[/COLOR][/SIZE]

---

### Post by varunendra on 2014-07-04
Yes I meant a session directly run from the Live CD or DVD or USB. Did you install the firmware package on it before loading the b43 module?

If there was no ssb error, it should have loaded the "b43" module automatically. In that case, after installing the firmware package, you'll need to remove/reload the driver -
```
sudo modprobe -rv b43
sudo modprobe -v b43
```

and check -
```
dmesg | egrep 'ssb|b43'
```
Any errors? If not, does it work?

---

### Post by dennis24 on 2014-07-08
Sorry for such the delay, I had a power-outage for three days and its been kind of crazy around here lately but Im back onto this project again. 

As for the Live CD/USB idea it all went flawlessly but after i was done i still had no wireless so i did it all over again but still cant get it to work...:-|

---

### Post by varunendra on 2014-07-10
I didn't re-read the whole thread, but I have started believing that maybe your wireless card or its supporting subsystem (things on the motherboard) is broken - a possible hardware problem. If not, there is certainly something going wrong in the process we are repeating - everytime.

For now, please post back a fresh report generated by the wireless_script (experimental version), this one - [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by dennis24 on 2014-07-12
```


########## wireless info START ##########


##### release #####


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty


##### kernel #####


Linux dennis-Aspire-5100 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 athlon i686 GNU/Linux


##### lspci #####


06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: 8139too
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)


##### lsusb #####


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA Card Info #####


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill #####


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #####


ssb                    51854  0 


##### iw reg get #####


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### interfaces #####


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


##### iwconfig #####


##### route #####


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


##### resolv.conf #####


##### nm-tool #####


NetworkManager Tool


State: disconnected


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            8139too
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off


##### NetworkManager.state #####


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf #####


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### iwlist #####


No way to aquire root rights found.


##### iwlist channel #####


##### modinfo #####


filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3DE188310F77C566C2E8CB3
alias:          pci:v000014E4d00004350sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Csv*sd*bc*sc*i*
alias:          pci:v000014E4d0000432Bsv*sd*bc*sc*i*
alias:          pci:v000014E4d00004329sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004328sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004325sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004324sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D6sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004322sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004321sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004320sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004319sv*sd*bc*sc*i*
alias:          pci:v000014A4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004318sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004315sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004312sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004311sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004307sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004306sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004301sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-24-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:96:DC:92:B0:1D:75:9D:3E:85:62:EA:32:A1:C7
sig_hashalgo:   sha512


##### modules #####


lp


##### blacklist #####


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


[/etc/modprobe.d/fbdev-blacklist.conf]
blacklist arkfb
blacklist aty128fb
blacklist atyfb
blacklist radeonfb
blacklist cirrusfb
blacklist cyber2000fb
blacklist gx1fb
blacklist gxfb
blacklist kyrofb
blacklist matroxfb_base
blacklist mb862xxfb
blacklist neofb
blacklist nvidiafb
blacklist pm2fb
blacklist pm3fb
blacklist s3fb
blacklist savagefb
blacklist sisfb
blacklist tdfxfb
blacklist tridentfb
blacklist viafb
blacklist vt8623fb


##### udev rules #####


# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #####


[    1.947207] b43-pci-bridge 0000:06:02.0: enabling device (0004 -> 0006)
[    1.972787] ssb: Failed to switch to core 0
[    1.972805] ssb: Failed to register PCI version of SSB with error -19


########## wireless info END ############



```

---

### Post by varunendra on 2014-07-13
This report is from the regular script, not the newer, experimental version I suggested. Please re-read the [linked post]("http://ubuntuforums.org/showpost.php?p=13024222") carefully and try that one. The report created by it will look much different than what you have posted above (different formatting, extra info, in different sequence).

The above report only shows what we already know about the problem, I am hoping to find some clue in the extra info that the new script would provide.

In the meanwhile, please try -
```
echo "b43" | sudo tee -a /etc/modules
```
..followed by a reboot. Then check -
```
dmesg | egrep 'b43|ssb'
lsmod | egrep 'b43|ssb'
```
..and post back whatever the terminal returns.

---

### Post by dennis24 on 2014-07-13
Here is the new wireless script 
```


	======== Wireless-Info START ========


System-Info ~~~~~~~~~~~~~~~~~~~~~~~~


dennis-Aspire-5100 3.13.0-24-generic i686,  Ubuntu 14.04 LTS, trusty


CPU    : AMD Turion(tm) 64 Mobile Technology MK-36
Memory : 873 MB
Uptime : 06:44:37 up 6 min,  1 user,  load average: 0.36, 0.57, 0.37




lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


06:01.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:009f]
	Kernel driver in use: 8139too
06:02.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
06:04.0 CardBus bridge [0607]: ENE Technology Inc CB-712/4 Cardbus Controller [1524:1412] (rev 10)




lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


Bus 001 Device 002: ID 154b:fa05 PNY 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub




PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255




iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~






rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


      Interface                 Soft blocked  Hard blocked
0: acer-wireless: Wireless LAN      no            no




lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


acer_wmi               31735  0 
sparse_keymap          13708  1 acer_wmi
video                  18903  1 acer_wmi
wmi                    18673  1 acer_wmi
ssb                    51854  0 




module parameters ~~~~~~~~~~~~~~~~~~


acer_wmi      (5): brightness=-1 | ec_raw_mode=N | force_series=0 | mailled=-1 | threeg=-1
video         (3): allow_duplicates=N | brightness_switch_enabled=Y | use_native_backlight=-1
wmi           (2): debug_dump_wdg=N | debug_event=N




nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


State: disconnected
================o=======o=========o==============o=========o===========o==============o===========
 Interface & ID | Type  | Driver  | State        | Default | Speed     | Support      | HW Addr   
================o=======o=========o==============o=========o===========o==============o===========
 eth0           | Wired | 8139too | unavailable  | no      |           |              | <MAC eth0>
----------------+-------+---------+--------------+---------+-----------+--------------+-----------




NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true




NetworkManager.conf ~~~~~~~~~~~~~~~~


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false




NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~
 




interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~






Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface




iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~


(Region : "en_US.UTF-8")
country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS




iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~


           - 




iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~


No way to aquire root rights found.




blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci




modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[ssb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        




udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~


# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"




Custom files/entries ~~~~~~~~~~~~~~~


/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default


[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en




Kernel boot line ~~~~~~~~~~~~~~~~~~~


BOOT_IMAGE=/boot/vmlinuz-3.13.0-24-generic root=UUID=6ff19e83-badc-472c-a00d-f56e2b01dce1 ro quiet splash vt.handoff=7




dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~


[    0.905136] audit: initializing netlink socket (disabled)
[    1.959768] 8139cp: 8139cp: 10/100 PCI Ethernet driver v1.3 (Mar 22, 2004)
[    1.971912] b43-pci-bridge 0000:06:02.0: enabling device (0004 -> 0006)
[    1.974762] 8139too: 8139too Fast Ethernet driver 0.9.28
[    1.992811] ssb: Failed to switch to core 0
[    1.992830] ssb: Failed to register PCI version of SSB with error -19
[   21.347579] wmi: Mapper loaded
[   22.854645] acer_wmi: Acer Laptop ACPI-WMI Extras
[   22.860826] acer_wmi: Function bitmap for Communication Device: 0x21
[   22.860838] acer_wmi: Disabling ACPI video driver
[   29.352063] Bluetooth: BNEP (Ethernet Emulation) ver 1.3


	======== Done ========



```

And this is the [COLOR=#000000][FONT=Ubuntu Mono]echo "b43" | sudo tee -a /etc/modules command

```
[/FONT][/COLOR]dennis@dennis-Aspire-5100:~$ echo "b43" | sudo tee -a /etc/moduals[sudo] password for dennis: 
b43
dennis@dennis-Aspire-5100:~$ 


[COLOR=#000000][FONT=Ubuntu Mono]
```

And here is the out put of the command [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]dmesg | egrep 'b43|ssb'[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]lsmod | egrep 'b43|ssb'[/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono] after  a reboot


```
[/FONT][/COLOR]dennis@dennis-Aspire-5100:~$ dmesg | egrep 'b43|ssb'[    1.955203] b43-pci-bridge 0000:06:02.0: enabling device (0004 -> 0006)
[    1.975111] ssb: Failed to switch to core 0
[    1.975128] ssb: Failed to register PCI version of SSB with error -19
dennis@dennis-Aspire-5100:~$ lsmod | egrep 'b43|ssb'
ssb                    51854  0 
dennis@dennis-Aspire-5100:~$ 
[COLOR=#000000][FONT=Ubuntu Mono]
```[/FONT][/COLOR]

---

### Post by varunendra on 2014-07-13
Were the last two outputs from after a reboot? If not, please reboot and post them again, since the change done by "echo b43...." command will take effect after a reboot.

---

### Post by dennis24 on 2014-07-13
yes both of them were done after i reboot

---

### Post by varunendra on 2014-07-14
No b43 in the output means same possibly broken install. Did you try installing the firmware on a Live session yet? I don't think I got any confirmation about that. If it is a fresh install from a new ISO image, I have nothing more to add - the problem is a mystery that I can't solve.

If it is the same broken install, I recommend doing a fresh one - to save time and headache. Preferably using a freshly downloaded ISO - downloaded via torrent to ensure data integrity.

If it is a fresh install using the same ISO image that you originally downloaded, same recommendation as above.

The b43 module is part of the kernel. So it not loading even after adding it to the /etc/modules file indicates its absence - which further indicates a broken kernel or broken installation.

The modinfo command, when we used them, showed its presence. But the modprobe commands returned errors that it doesn't exist. It has happened throughout this thread in such a way that has made it very confusing about where we are, and how good is the installation that we are dealing with.

So it is a very very very.... extremely good idea to just do a fresh, clean install, using a new ISO image whose integrity is guaranteed (downloaded via torrent), and start from scratch - on a clean slate.

Unless your card is physically defective, this problem should have been solved with the firmware suggestion within two posts, or three at most.

---

