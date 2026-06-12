---
title: "cannot connect to a Digicom router when using WPA2 or WEP"
date: 2013-10-25
forum: Networking &amp; Wireless
---

### Post by chhitizsubedi on 2013-10-25
I am using Ubuntu 13.04. I installad a new Digicom router and configured it. The router works fine with other devices (mobiles, windows pc) but I cannot connect to that router. I can see the SSID and i type in the password but it always fails to connect. So I tried making the wi-fi network open (i.e without password) and then I could connect to the router. The computer doesnt seem to be able to connect when using encryption with either WEP or WAP. I would be glad for some help as I cannot leave my wi-fi open to everyone.
Thanks.

---

### Post by varunendra on 2013-10-26
Welcome to the forums chhitizsubedi !

Did you try WPA or WPA2? And with TKIP or AES/CCMP?

It is highly recommended to use pure WPA2-PSK (AES/CCMP) encryption. No mixed mode, no TKIP. If that alone does not let you connect, there *may be* some tweaks that may be used to make it work. To provide us a summary of your wifi setup, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by chhitizsubedi on 2013-10-26
Thank you for the welcome!
I tried using the WPA2 with AES. I am not using any password protection right now due to above mentioned reasons.
This is the wireless script file that it generated.
```

#! /bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: anewguy, chili555, llua
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the size limit of 19.5 kB for .txt files on the Ubuntu Forums.
#
############################################################################
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.
#


FILEBASE="wireless-info"
MODMATCHES="(air|ath|carl|at7|iwl|ipw|rtl8|rt2|rt3|8192cu|rt5|rt6|rt7|rtl|r818|r871|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etork)[^[:punct:] ]*"
exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCould not write target file \"$FILEBASE.txt\", aborting.\n\n"
    exit 1
fi
printf "\n*************** info trace ***************\n"
printf "\n***** uname -a *****\n\n"
uname -a
printf "\n***** lsb_release *****\n\n"
lsb_release -idrc
printf "\n***** lspci *****\n\n"
lspci -nnk | grep -iA2 net
printf "\n***** lsusb *****\n\n"
lsusb
printf "\n***** PCMCIA Card Info *****\n\n"
pccardctl info
printf "\n***** iwconfig *****\n\n"
iwconfig
printf "\n***** rfkill *****\n\n"
rfkill list all
printf "\n***** lsmod *****\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"
printf "\n***** nm-tool *****\n"
nm-tool
printf "\n***** NetworkManager.state *****\n"
cat /var/lib/NetworkManager/NetworkManager.state
printf "\n***** NetworkManager.conf *****\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi
printf "\n***** interfaces *****\n\n"
cat /etc/network/interfaces | sed -r 's/wpa-psk [[:graph:]]+/wpa-psk <WPA key removed>/'
printf "\n***** iwlist *****\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi
printf "\n***** resolv.conf *****\n\n"
grep -v '^#' /etc/resolv.conf
printf "\n***** blacklist *****\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
	BLACKLIST=$(grep '^blacklist' $CONFFILE)
	if [ -n "$BLACKLIST" ]; then
	    printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
	fi
    fi
done
printf "\n***** modinfo *****\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done
printf "\n***** udev rules *****\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules
printf "\n***** dmesg *****\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"
printf "\n****************** done ******************\n\n"
exec 1>&3 3>&-
exec 2>&4 4>&-
sed -r -i 's/([[:alnum:]][[:alnum:]]:){5}[[:alnum:]][[:alnum:]]/<MAC address removed>/' $FILEBASE.txt
if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm -f $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi

```

This is the wireless-info.txt file:

```

*************** info trace ***************


***** uname -a *****


Linux chhitiz-Inspiron-N4030 3.8.0-31-generic #46-Ubuntu SMP Tue Sep 10 19:56:49 UTC 2013 i686 i686 i686 GNU/Linux


***** lsb_release *****


Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring


***** lspci *****


12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
	Kernel driver in use: wl
13:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Dell Device [1028:0466]
	Kernel driver in use: atl1c


***** lsusb *****


Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 005: ID 0c45:6482 Microdia 
Bus 001 Device 006: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 007: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 008: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth


***** PCMCIA Card Info *****




***** iwconfig *****


eth1      IEEE 802.11abg  ESSID:"Digicom"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC address removed>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


***** rfkill *****


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


***** lsmod *****


wl                   2902185  0 
lib80211               14040  2 wl,lib80211_crypt_tkip
cfg80211              436243  1 wl


***** nm-tool *****


NetworkManager Tool


State: connected (global)


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            atl1c
  State:             unavailable
  Default:           no
  HW Address:        <MAC address removed>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         off




- Device: eth1  [Digicom 1] ----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>


  Capabilities:
    Speed:           72 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    *Digicom:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 79


  IPv4 Settings:
    Address:         192.168.0.106
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1


    DNS:             192.168.0.1






***** NetworkManager.state *****
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


***** NetworkManager.conf *****


[main]
plugins=ifupdown,keyfile
dns=dnsmasq


no-auto-default=<MAC address removed>,


[ifupdown]
managed=false


***** interfaces *****


# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback


***** iwlist *****


eth1      Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off
                    ESSID:"Digicom"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 88ms ago
                    IE: Unknown: 000744696769636F6D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E181AFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B070300000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD9E0050F204104A0001101044000102103B0001031047001063041253101920061228008611038B0B1021001B5265616C74656B2053656D69636F6E647563746F7220436F72702E1023000752544C387878781024000D45562D323030392D30322D30361042000F3132333435363738393031323334371054000800060050F2040001101100135265616C74656B20576972656C657373204150100800020086
                    IE: Unknown: DD1E00904C336E181AFF00000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340B070300000000000000000000000000000000000000
                    IE: Unknown: DD0700E04C02022000




***** resolv.conf *****


nameserver 127.0.1.1


***** blacklist *****


[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist bcm43xx
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma


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


***** modinfo *****


filename:       /lib/modules/3.8.0-31-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     6E2531203CF49EB24353067
alias:          pci:v*d*sv*sd*bc02sc80i*
depends:        cfg80211,lib80211
vermagic:       3.8.0-31-generic SMP mod_unload modversions 686 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string




***** udev rules *****


# PCI device 0x1969:/sys/devices/pci0000:00/0000:00:1c.2/0000:13:00.0 (atl1c)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:12:00.0/bcma0:0 (bcma-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:12:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


***** dmesg *****


[   13.431634] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.481694] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   13.555171] eth1: Broadcom BCM4727 802.11 Hybrid Wireless Controller 6.20.155.1 (r326264)
[   28.087771] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[   28.087784] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[   28.087798] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[   28.087805] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[   28.087818] ERROR @wl_dev_intvar_get : error (-1)
[   28.087824] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  730.762350] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  730.762363] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  730.762377] ERROR @wl_cfg80211_get_station : Could not get rate (-1)
[  730.762383] ERROR @wl_cfg80211_get_station : Could not get rssi (-1)
[  730.762395] ERROR @wl_dev_intvar_get : error (-1)
[  730.762401] ERROR @wl_cfg80211_get_tx_power : error (-1)


****************** done ******************




```

Thank you for your response. I will appreciate any help that I can get.

---

### Post by varunendra on 2013-10-26
> **chhitizsubedi said:**
> ```

12:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller **[14e4:4727]** (rev 01)
	Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
	Kernel driver in use: **wl**

```
You are currently using the proprietary driver which is not always the best choice. The native one in your version of kernel is usually good enough to keep things nice and fast, often even better than the proprietary one. So let's try it.

Please purge the proprietary driver -
```
sudo apt-get purge bcmwl-kernel-source
```
..Then reboot and check -
```
lsmod | egrep 'wl|brcm|b43'
```
It should return only **brcmsmac** and its supporting modules in the output, and absolutely not **wl** or **b43**. If so, does it make the connectivity any better? If not, please run the script again and post back its fresh output here.

**PS:**
Oh, and I would need only the "wireless-info.txt" (or .tar.gz) file, not the script itself :)

---

### Post by chhitizsubedi on 2013-10-28
Thank you varunendra! I purged the proprietary driver and then after restart the encrypted connection could be easily connected to. Thank you again for your help.

---

### Post by varunendra on 2013-10-28
You're welcome ! :)

Since the native one is working better for you as expected, remember not to install the proprietary one suggested by "Additional Drivers" program.

---

