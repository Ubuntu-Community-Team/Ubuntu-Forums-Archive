---
title: "installed Broadcom drivers but can't make it start on boot"
date: 2014-04-29
forum: Networking &amp; Wireless
---

### Post by cocolopez on 2014-04-29
after struggling with the driver in lubuntu 14.04 manage to install it, fix de network manager problem, but I need to enter the command:

sudo modprobe -r b43 ssb wl brcmfmac brcmsmac bcma
sudo modprobe wl

every time I boot. I try to put the command in autostart but no luck.

I no it must be really simple but I'm really new at this.

thanks in advance.

---

### Post by Hadaka on 2014-04-29
hi,please open a terminal, ctrl/alt/t then COPY  and paste in
this command.,

```
lspci -n | grep 0280 | awk '{print $3}'
```
post the output
thanks.

---

### Post by cocolopez on 2014-04-29
It came out this:

14e4:4315

---

### Post by Hadaka on 2014-04-29
hi, please open a terminal ctrl/alt/t then COPY and paste
one line at a time.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then do..
```
sudo apt-get update
sudo su
apt-get install linux-firmware-nonfree
echo b43 >> /etc/modules
exit 0
```
thanks.

---

### Post by cocolopez on 2014-04-29
i don't actually understand what you just make do.
but it's fixed.
Thanks a lot!

---

### Post by Hadaka on 2014-04-29
Glad that worked for you !!

---

### Post by gulmer on 2014-04-30
I have an PowerPc PowerBook G4 with Lubuntu and also have wifi problems. lspci -nn | grep 0280 results; 0001:10:12:.0 Network controller [2080]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 3) I tried the codes you suggested and had no results, no wifi. Maybe you could help me.

---

### Post by Hadaka on 2014-04-30
Hi Gulmer, you have a different pci-id you should really open 
a new thread with your info..pci-id 4320. But since you are here
lets take a quick look, if it looks like it is going to get involved,
then we'll open a new thread, please post the outout of,,
```
lspci -nnk | egrep '0200|0280'
lsmod
rfkill list all
cat /etc/modules
cat /etc/network/interfaces
```
thanks.

---

### Post by gulmer on 2014-04-30
mauri@mauri-laptop:~$ lspci -nnk | egrep '0200|0280'
0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
0002:20:0f.0 Ethernet controller [0200]: Apple Inc. UniNorth 2 GMAC (Sun GEM) [106b:0032] (rev 80)
mauri@mauri-laptop:~$ lsmod
Module                  Size  Used by
nls_iso8859_1           3477  1 
usb_storage            48091  1 
btusb                  21455  0 
joydev                 10216  0 
arc4                    1872  2 
b43                   375232  0 
rfcomm                 59701  8 
bnep                   15645  2 
bcma                   44450  1 b43
bluetooth             360512  22 bnep,btusb,rfcomm
mac80211              570770  1 b43
rtc_generic             1187  0 
mac_hid                 3597  0 
appletouch              9847  0 
parport_pc             36057  0 
cfg80211              424569  2 b43,mac80211
ppdev                   9199  0 
lp                      8879  0 
parport                36819  3 lp,ppdev,parport_pc
snd_powermac           65375  0 
uio_pdrv_genirq         3754  0 
snd_pcm                94024  1 snd_powermac
snd_page_alloc          7356  1 snd_pcm
uio                     9785  1 uio_pdrv_genirq
snd_seq_midi            5892  0 
snd_seq_midi_event      6943  1 snd_seq_midi
snd_rawmidi            22228  1 snd_seq_midi
snd_seq                62457  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device          6906  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              22194  2 snd_pcm,snd_seq
snd                    64958  7 snd_timer,snd_pcm,snd_seq,snd_rawmidi,snd_seq_device,snd_powermac,snd_seq_midi
soundcore               1096  1 snd
apm_emu                 1404  0 
apm_emulation           6981  1 apm_emu
hid_generic              928  0 
usbhid                 46826  0 
hid                    92208  2 hid_generic,usbhid
nouveau              1085947  2 
firewire_ohci          34367  0 
ttm                    77426  1 nouveau
firewire_core          63034  1 firewire_ohci
sungem                 29310  0 
drm_kms_helper         43579  1 nouveau
sungem_phy             11874  1 sungem
crc_itu_t               1471  1 firewire_core
ssb                    57500  1 b43
drm                   270767  4 ttm,drm_kms_helper,nouveau
uninorth_agp            7396  1 
mauri@mauri-laptop:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
mauri@mauri-laptop:~$ cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

apm_emu
snd-powermac
therm_adt746x
mauri@mauri-laptop:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback
mauri@mauri-laptop:~$

---

### Post by Hadaka on 2014-04-30
Hi, let's give this a try...
please open a terminal ctrl/alt/t
then we need to edit one file...please do..
```
gksudo gedit /etc/modules
```
Place a # in front of every item currently listed
and add lp and b43..........make it look like this,,
that's an L "lp" b43
```
#apm_emu
#snd-powermac
#therm_adt746x
lp
b43
```
then save and close gedit.
then do..from a wired connection connected to the internet
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-firmware-nonfree  
```
boot
thanks.
** If your ethernet (hard wired)becomes disabeled from this then just
re-edit /etc/modules and remove the #.....

---

### Post by gulmer on 2014-04-30
Looks like there maybe another problem, after the code for gedit, password and nothing came up, no list.

---

### Post by gulmer on 2014-04-30
no gedit was installed when Lubuntu was installed.so I went to synaptics and installed gedit.

---

### Post by gulmer on 2014-04-30
Got gedit to work and made the changes you suggested and put in the rest of the codes, rebooted and still have the wired connection but no wifi or even a icon for wireless network searching. Now what?

---

### Post by Hadaka on 2014-04-30
ok.try this..
```
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
```
then.
```
sudo modprobe -rf b43
sudo modprobe b43
```
anything?

---

### Post by gulmer on 2014-04-30
sudo rm /etc/modprobe.d/blacklist-bcm43.conf results; cannot remove  no such file or directory. sudo modprobe -rf b43 result; nothing came up  sudo modprobe b43 result; nothing came up.

---

### Post by gulmer on 2014-04-30
Should I remove the firmware-b43-installer and b43-fwcutter in synaptics?

---

### Post by Hadaka on 2014-04-30
Hi, well its being stubborn, dont worry about the fwcutter,b43 stuff
all that and the kitchen sink is in the nonfree driver,,,since this is an
older aapl machine,..im wondering if your ram is lacking..how much
ram does the thing have..also...you should be able to toggle the "airport"
switch for the wireless as well ,and i "think" you may have a bios like area
to turn wireless on and off,,check that as well.
also please post..
```
if config

```

---

### Post by gulmer on 2014-04-30
if config resuts; >

---

### Post by Hadaka on 2014-04-30
lets also run Varun's script file see what pops up.
follow the link..follow the directions...thanks.

[http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385)

---

### Post by gulmer on 2014-04-30
I installed WIFI Radar and it shows my network but still not connecting, trying to get IP Address right now.

---

### Post by gulmer on 2014-04-30
resuts of script;#!/bin/bash
#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
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
MODMATCHES="(air|ar5|ath|carl|at7|iwl|ipw|rt(2|3|5|6|7)|rtl|r(818|871)|8192(cu|du)|ssb|wl|b43|bcma|brcm|eth1|ndis|wlan0|firm|etork)[^[:punct:] ]*"

exec 3>&1 4>&2
exec 1> $FILEBASE.txt 2> /dev/null
if [ "$?" != "0" ]; then
    printf "\nCannot write output file, aborting.\n\n"
    exit 1
fi

printf "\n########## wireless info START ##########\n"

printf "\n##### release #####\n\n"
lsb_release -idrc

printf "\n##### kernel #####\n\n"
uname -a

printf "\n##### lspci #####\n\n"
lspci -nnk | grep -iA2 net | sed 's/^--$//'

printf "\n##### lsusb #####\n\n"
lsusb

printf "\n##### PCMCIA Card Info #####\n\n"
pccardctl info

printf "\n##### rfkill #####\n\n"
rfkill list all

printf "\n##### iw reg get #####\n\n"
iw reg get

printf "\n##### interfaces #####\n\n"
sed 's/wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces

printf "\n##### iwconfig #####\n\n"
iwconfig

printf "\n##### route #####\n\n"
route -n

printf "\n##### resolv.conf #####\n\n"
grep -v '^#' /etc/resolv.conf

printf "\n##### nm-tool #####\n"
nm-tool

printf "\n##### NetworkManager.state #####\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state

printf "\n##### NetworkManager.conf #####\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "nm-system-settings.conf (used up to 10.04):\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi

printf "\n##### iwlist #####\n\n"
if [ -t 0 ]; then
    sudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/gksudo ]; then
    gksudo iwlist scan || echo "Aquiring of root rights failed."
elif [ -x /usr/bin/kdesudo ]; then
    kdesudo iwlist scan || echo "Aquiring of root rights failed."
else
    echo "No way to aquire root rights found."
fi

printf "\n##### iwlist channel #####\n\n"
iwlist chan

printf "\n##### lsmod #####\n\n"
lsmod | egrep "(^|[[:punct:] ])${MODMATCHES}([[:punct:] ]|$)"

printf "\n##### modinfo #####\n\n"
MODULNAMES=$(lsmod | egrep "^$MODMATCHES" | awk '{print $1}')
for MODULE in $MODULNAMES; do
    modinfo $MODULE
    echo
done

printf "\n##### modules #####\n\n"
grep -v '^#' /etc/modules

printf "\n##### blacklist #####\n"
for CONFFILE in /etc/modprobe.d/*.conf; do
    if [[ -n $(egrep -v '/etc/modprobe.d/(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia)' <<< $CONFFILE) ]]; then
	BLACKLIST=$(grep '^blacklist' $CONFFILE)
	if [ -n "$BLACKLIST" ]; then
	    printf "\n[%s]\n%s\n" $CONFFILE "$BLACKLIST"
	fi
    fi
done

printf "\n##### udev rules #####\n"
egrep '^(#.*device|[^#]|$)' /etc/udev/rules.d/70-persistent-net.rules

printf "\n##### dmesg #####\n\n"
dmesg | egrep "[[:punct:] ]${MODMATCHES}[[:punct:] ]"

printf "\n########## wireless info END ############\n\n"

exec 1>&3 3>&-
exec 2>&4 4>&-

RESULTS=$(cat -s $FILEBASE.txt)
sed 's/\([[:alnum:]][[:alnum:]]:\)\{5\}[[:alnum:]][[:alnum:]]/<MAC address removed>/' <<< "$RESULTS" > $FILEBASE.txt

if [ $(stat -c %s $FILEBASE.txt) -gt 19968 ]; then
    tar -czf $FILEBASE.tar.gz $FILEBASE.txt
    rm $FILEBASE.txt
    printf "\nResults archived in \"%s.tar.gz\", as they exceed the 19.5 kB size limit for .txt files on the Ubuntu Forums.\n\n" "$FILEBASE"
else
    printf "\nResults saved in \"%s.txt\".\n\n" "$FILEBASE"
fi

---

### Post by Hadaka on 2014-04-30
Hi, you psted the actual script for the script file..please re-read
the instructions and you will see it puts a .txt file in your home directory...run that 
to issue all the comands and then post the output of that...please re read the instructions
thanks.

---

### Post by gulmer on 2014-04-30
########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux mauri-laptop 3.13.0-24-powerpc-smp #46-Ubuntu SMP Thu Apr 10 19:09:05 UTC 2014 ppc ppc ppc GNU/Linux

##### lspci #####

0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Apple Inc. AirPort Extreme [106b:004e]
	Kernel driver in use: b43-pci-bridge

0002:20:0f.0 Ethernet controller [0200]: Apple Inc. UniNorth 2 GMAC (Sun GEM) [106b:0032] (rev 80)
	Kernel driver in use: gem

##### lsusb #####

Bus 001 Device 002: ID 148f:3070 Ralink Technology, Corp. RT2870/RT3070 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1267:004d Logic3 / SpectraVideo plc 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:030a Apple, Inc. Internal Trackpad
Bus 002 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy1: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

---

### Post by gulmer on 2014-04-30
##### iwconfig #####

wlan1     IEEE 802.11bg  ESSID:"Ghost Kitty"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            gem
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.113
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             198.60.22.2
    DNS:             198.60.22.22
    DNS:             192.168.1.1

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

---

### Post by gulmer on 2014-04-30
Wireless Access Points 
    Ghost Kitty:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 94 WPA2
    HOTMAMAS:        Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    MickandJune:     Infra, <MAC address removed>, Freq 2417 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    KPNetwork:       Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    Petersen_Guest1: Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2
    tl000000:        Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    JercsHome:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 10 WPA2
    Ghost Kitty-guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100
    xfinitywifi:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 40
    medialink_016BA8:Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 20
    dlink:           Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    JETPACK:         Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 10 WPA WPA2
    my room:         Infra, <MAC address removed>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17
    linksys:         Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA
    HOME-81E2:       Infra, <MAC address removed>, Freq 2437 MHz, Rate 54 Mb/s, Strength 7 WPA WPA2

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    Ghost Kitty:     Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 85 WPA2
    Ghost Kitty-guest: Infra, <MAC address removed>, Freq 2412 MHz, Rate 54 Mb/s, Strength 89

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

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"Ghost Kitty"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005b24c8de8
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 000B47686F7374204B69747479
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD840050F204104A0001101044000102103B00010310470010239C738B7CA60619B839F6466C8208C310210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B73797320453235303010080002228C103C0001031049000600372A000120
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=66/70  Signal level=-44 dBm  
                    Encryption key:off
                    ESSID:"Ghost Kitty-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005b24c9ab1
                    Extra: Last beacon: 40ms ago
                    IE: Unknown: 001147686F7374204B697474792D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

---

### Post by gulmer on 2014-04-30
Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Petersen_Guest1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 28976ms ago
                    IE: Unknown: 000F506574657273656E5F477565737431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F1100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

wlan0     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-34 dBm  
                    Encryption key:on
                    ESSID:"Ghost Kitty"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005b262626f
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000B47686F7374204B69747479
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD840050F204104A0001101044000102103B00010310470010239C738B7CA60619B839F6466C8208C310210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B73797320453235303010080002228C103C0001031049000600372A000120
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-24 dBm  
                    Encryption key:off
                    ESSID:"Ghost Kitty-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005b25eba9c
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 001147686F7374204B697474792D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 03 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:on
                    ESSID:"KPNetwork"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 00094B504E6574776F726B
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B071700000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD880050F204104A0001101044000102103B0001031047001008082236A4CF108E54ED7C4934915F4B1021000D4E4554474541522C20496E632E1023000A574E44523337303076331024000A574E44523337303076331042000230311054000800060050F2040001101100094B504E657467656172100800020004103C0001031049000600372A000120
                    IE: Unknown: DD090010180204F02C0000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 04 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"Petersen_Guest1"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000F506574657273656E5F477565737431
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFE181BFFFF000001000000000000000000000000000000000000
                    IE: Unknown: 3D160B0F1100000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180200F02C0000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

---

### Post by gulmer on 2014-04-30
Cell 05 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=22/70  Signal level=-88 dBm  
                    Encryption key:off
                    ESSID:"medialink_016BA8"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000005b3150146
                    Extra: Last beacon: 884ms ago
                    IE: Unknown: 00106D656469616C696E6B5F303136424138
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706434E20010D14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: DD270050F204104A0001101044000101104700102880288028801880A880C83A35016BA8103C000101
                    IE: Unknown: 050400010006
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A6E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: 3D1606000000000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05000011127A
                    IE: Unknown: DD1E00904C336E1117FF000000010000000000000000000000000C0000000000
                    IE: Unknown: DD1A00904C3406000000000000000000000000000000000000000000
                    IE: Unknown: DD07000C4304000000
          Cell 06 - Address: <MAC address removed>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:off
                    ESSID:"my room"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000001336421988d
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 00076D7920726F6F6D
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 2D1A0C1103FF00000000000000000000000000000000000000000000
                    IE: Unknown: 32043048606C
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 07 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"HOTMAMAS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000133659fb3ef
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 0008484F544D414D4153
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030042127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
                    IE: Unknown: DD870050F204104A0001101044000102103B000103104700102880288028801880A880F8EDA582DEA010210005415252495310230006544738363247102400065254323836301042000831323334353637381054000800060050F204000110110012415252495320544738363220526F7574657210080002210C103C0001011049000600372A000120
          Cell 08 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:""
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000133659f3d46
                    Extra: Last beacon: 1320ms ago
                    IE: Unknown: 0000
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 32040C183060
                    IE: Unknown: 0706555320010B14
                    IE: Unknown: 33082001020304050607
                    IE: Unknown: 33082105060708090A0B
                    IE: Unknown: 050400010000
                    IE: Unknown: 2A0104
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 7F0101
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030042127A
                    IE: Unknown: DD07000C4303000000
          Cell 09 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:off
                    ESSID:"xfinitywifi"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000133659fdc9d
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 000B7866696E69747977696669
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0104
                    IE: Unknown: 32040C183060
                    IE: Unknown: 2D1A0C0017FFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601000700000000000000000000000000000000000000
                    IE: Unknown: 3E0100
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
                    IE: Unknown: 0B05030042127A
                    IE: Unknown: 7F0101
                    IE: Unknown: DD07000C4303000000
                    IE: Unknown: 0706555320010B10
          Cell 10 - Address: <MAC address removed>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=14/70  Signal level=-96 dBm  
                    Encryption key:on
                    ESSID:"JercsHome"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000005b0ecdac3
                    Extra: Last beacon: 48ms ago
                    IE: Unknown: 00094A65726373486F6D65
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030106
                    IE: Unknown: 0706555320010B1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 2D1AAD511BFFFFFF0000000000000000000000000000000000000000
                    IE: Unknown: 33027E95
                    IE: Unknown: 3D1606001100000000000000000000000000000000000000
                    IE: Unknown: 46050200010000
                    IE: Unknown: DD180050F2020101010003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0700039301750320
                    IE: Unknown: DD0E0017F2070001010620C9D01D4565
                    IE: Unknown: DD0B0017F20100010100000007

---

### Post by gulmer on 2014-04-30
##### iwlist channel #####

wlan1     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz
wlan0     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### lsmod #####

rt2800usb              18303  0 
rt2x00usb              12253  1 rt2800usb
rt2800lib              81126  1 rt2800usb
rt2x00lib              48723  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt               1463  1 rt2800lib
b43                   375232  0 
bcma                   44450  1 b43
mac80211              570770  4 b43,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              424569  3 b43,mac80211,rt2x00lib
ssb                    57500  1 b43

##### modinfo #####

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/net/wireless/rt2x00/rt2800usb.ko
license:        GPL
firmware:       rt2870.bin
description:    Ralink RT2800 USB Wireless LAN driver.
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     DA14F8D6EA2B8FF7B32CA13
alias:          usb:vF201p5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0254d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApF511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApD522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApC522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p006Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0069d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p004Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v08B9p1197d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18E8p6259d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB29d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB24d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v05A6p0101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9032d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0169d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0168d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0615d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0605d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp094Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148FpF101d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v06F8pE036d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0010d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0602d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p0600d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A1d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0150d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0148d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p012Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3401d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3400d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3399d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3340d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3322d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3262d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17A7d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1790d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1760d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p166Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E0Bp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C08d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3074d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3073d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20F4p724Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C21d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0241d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v057Cp8501d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5372d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp5370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2182d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2181d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2180d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2126d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p2104d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp23F6d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1800d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04DAp1801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A42d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C23d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C22d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C20d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3365d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3329d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A32d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v043Ep7A12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3421d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p006Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p006Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0067d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3573d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED19d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9019d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0846p9012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p016Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p003Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp094Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0021d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0020d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7733d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148FpF301d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp1103d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17ADd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p17BCd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p7733d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0284d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0930p0A07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0068d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0066d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0065d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0062d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0041d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0170d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0079d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0944d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9801d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v167Bp4001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p179Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0764d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0761d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0744d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3572d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0165d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0050d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp8070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3370d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p20DDd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp945Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p343Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p341Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3418d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0586p3416d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p5257d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0283d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0282d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v5A57p0280d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0025d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0CDEp0022d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep3013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v157Ep300Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0324d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0323d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0313d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0302d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v177Fp0153d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0006d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApB522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083ApA618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap8522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7522d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7512d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap7511d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v083Ap6618d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0060d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p005Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0051d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0048d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0047d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0042d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0040d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p003Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0039d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p002Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DF6p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v129Bp1828d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04E8p2018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v148Fp2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1A32p0304d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pED06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019pAB25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2019p5201d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0471p200Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0011d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp000Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1D4Dp0002d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v20B8p8888d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1B75p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p899Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p871Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p870Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p822Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p821Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p6899d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3871d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3822d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3821d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0DB0p3820d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v100Dp9031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0166d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0164d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0163d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0789p0162d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0078d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0077d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1737p0070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13B1p0031d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0948d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0947d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v04BBp0945d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0018d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0017d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0013d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p000Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0009d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0003d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0E66p0001d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1044p800Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15A9p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9709d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9708d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9707d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9706d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9705d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9703d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9702d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1740p9701d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp14A9d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v203Dp1480d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7722d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7718d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7717d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p7711d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v7392p4085d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0FE9pB307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07FAp7712d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v2001p3C1Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C17d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C16d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C15d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C13d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C11d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ed*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C0Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07D1p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v18C5p0012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp003Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07AAp002Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01A8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01EEd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p01A2d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p016Fd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p015Dd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p0158d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0411p00E8d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp935Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Bd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp825Ad*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp815Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp805Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v050Dp8053d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3321d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3307d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3305d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3273d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v13D3p3247d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1761p0B05d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1784d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1742d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1732d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v0B05p1731d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1690p0740d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v15C5p0008d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C2Cd*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C28d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C27d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C25d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C23d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C12d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C07d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v14B2p3C06d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2870d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v8516p2070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2310d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2210d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1EDAp2012d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v1482p3C09d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3072d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3071d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p3070d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2770d*dc*dsc*dp*ic*isc*ip*in*
alias:          usb:v07B8p2870d*dc*dsc*dp*ic*isc*ip*in*

---

### Post by gulmer on 2014-04-30
depends:        rt2x00lib,rt2x00usb,rt2800lib
intree:         Y
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/net/wireless/rt2x00/rt2x00usb.ko
license:        GPL
description:    rt2x00 usb library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     71807644F8032549D8EEE1E
depends:        rt2x00lib,mac80211
intree:         Y
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/net/wireless/rt2x00/rt2800lib.ko
license:        GPL
description:    Ralink RT2800 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com), Bartlomiej Zolnierkiewicz
srcversion:     7B08D09B1EA44369AFEDD87
depends:        rt2x00lib,mac80211,crc-ccitt
intree:         Y
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/net/wireless/rt2x00/rt2x00lib.ko
license:        GPL
description:    rt2x00 library
version:        2.3.0
author:         [http://rt2x00.serialmonkey.com](http://rt2x00.serialmonkey.com)
srcversion:     A3877FC563539F5625D49FE
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     217DD8BEC7FF87080BDE4B1
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
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
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

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     1D811BE4D53D78885E5638B
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3188E13D66C5770F3BCBE8C
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
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
sig_hashalgo:   sha512

##### modules #####

lp
b43

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

[/etc/modprobe.d/blacklist.local.conf]
blacklist snd-aoa-codec-tas
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-i2sbus
blacklist snd-aoa-soundbus
blacklist snd-aoa

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

# PCI device 0x106b:0x0032 (gem)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4320 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    3.488258] b43-pci-bridge 0001:10:12.0: enabling device (0004 -> 0006)
[    3.488304] ssb: Found chip with id 0x4306, rev 0x03 and package 0x00
[    3.488313] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    3.488320] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    3.488326] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    3.488333] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    3.488340] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    3.512768] ssb: Sonics Silicon Backplane found on PCI device 0001:10:12.0
[   18.831672] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   18.854800] b43-phy0: Found PHY: Analog 2, Type 2 (G), Revision 2
[   21.128758] ieee80211 phy1: rt2x00_set_rt: Info - RT chipset 3070, rev 0201 detected
[   21.283800] ieee80211 phy1: rt2x00_set_rf: Info - RF chipset 0005 detected
[   23.965365] systemd-udevd[317]: renamed network interface wlan0 to rename3
[   24.425182] systemd-udevd[325]: renamed network interface wlan1 to wlan0
[   25.814856] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   25.903563] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   25.907333] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   25.959525] ieee80211 phy1: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2870.bin'
[   25.975426] ieee80211 phy1: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.29
[   26.444495] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   26.445533] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready

########## wireless info END ############
Is this what you wanted?

---

### Post by Hadaka on 2014-04-30
yes ! that is what i needed, ok remove the usb wifi dongle and leave it
out untill we get your internal wifi card going. so..remove the usb dongle
boot...
*if it does not connect...please run the wireless script again.
we may end up running that script a couple more times...so be patient
thanks.

---

### Post by gulmer on 2014-04-30
Supper time, will have to resume in the am. Thanks for all your patience and help.

---

### Post by gulmer on 2014-05-01
Script without usb dongle; 
########## wireless info START ##########

##### release #####

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04 LTS
Release:	14.04
Codename:	trusty

##### kernel #####

Linux mauri-laptop 3.13.0-24-powerpc-smp #46-Ubuntu SMP Thu Apr 10 19:09:05 UTC 2014 ppc ppc ppc GNU/Linux

##### lspci #####

0001:10:12.0 Network controller [0280]: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller [14e4:4320] (rev 03)
	Subsystem: Apple Inc. AirPort Extreme [106b:004e]
	Kernel driver in use: b43-pci-bridge

0002:20:0f.0 Ethernet controller [0200]: Apple Inc. UniNorth 2 GMAC (Sun GEM) [106b:0032] (rev 80)
	Kernel driver in use: gem

##### lsusb #####

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1267:004d Logic3 / SpectraVideo plc 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 003: ID 05ac:030a Apple, Inc. Internal Trackpad
Bus 002 Device 004: ID 05ac:8205 Apple, Inc. Bluetooth HCI
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA Card Info #####

##### rfkill #####

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no

##### iw reg get #####

##### interfaces #####

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

##### iwconfig #####

wlan1     IEEE 802.11bg  ESSID:"Ghost Kitty"  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            gem
  State:             connected
  Default:           yes
  HW Address:        <MAC address removed>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.113
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             198.60.22.2
    DNS:             198.60.22.22
    DNS:             192.168.1.1

- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            b43
  State:             disconnected
  Default:           no
  HW Address:        <MAC address removed>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

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

wlan1     Scan completed :
          Cell 01 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:on
                    ESSID:"Ghost Kitty"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000143f29ea15
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 000B47686F7374204B69747479
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD840050F204104A0001101044000102103B00010310470010239C738B7CA60619B839F6466C8208C310210005436973636F1023000D4C696E6B7379732045323530301024000776312E302E30311042000234321054000800060050F20400011011000D4C696E6B73797320453235303010080002228C103C0001031049000600372A000120
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
          Cell 02 - Address: <MAC address removed>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=65/70  Signal level=-45 dBm  
                    Encryption key:off
                    ESSID:"Ghost Kitty-guest"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000143f28cf51
                    Extra: Last beacon: 44ms ago
                    IE: Unknown: 001147686F7374204B697474792D6775657374
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1AFC181BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601001300000000000000000000000000000000000000
                    IE: Unknown: 4A0E14000A002C01C800140005001900
                    IE: Unknown: 7F0101
                    IE: Unknown: DD090010180201F0040000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00

##### iwlist channel #####

wlan1     14 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Channel 14 : 2.484 GHz

##### lsmod #####

b43                   375232  0 
bcma                   44450  1 b43
mac80211              570770  1 b43
cfg80211              424569  2 b43,mac80211
ssb                    57500  1 b43

##### modinfo #####

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     217DD8BEC7FF87080BDE4B1
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
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
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

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     1D811BE4D53D78885E5638B
alias:          pci:v000014E4d00004727sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004365sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004359sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004358sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004357sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004353sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004331sv*sd*bc*sc*i*
alias:          pci:v000014E4d0000A8D8sv*sd*bc*sc*i*
alias:          pci:v000014E4d00004313sv*sd*bc*sc*i*
alias:          pci:v000014E4d00000576sv*sd*bc*sc*i*
depends:        
intree:         Y
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
sig_hashalgo:   sha512

filename:       /lib/modules/3.13.0-24-powerpc-smp/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     3188E13D66C5770F3BCBE8C
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
vermagic:       3.13.0-24-powerpc-smp SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        <MAC address removed>:29:4B:64:FA:24:73:89:82:A7:5E:A3:55:68:38
sig_hashalgo:   sha512

##### modules #####

lp
b43

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

[/etc/modprobe.d/blacklist.local.conf]
blacklist snd-aoa-codec-tas
blacklist snd-aoa-fabric-layout
blacklist snd-aoa-i2sbus
blacklist snd-aoa-soundbus
blacklist snd-aoa

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

# PCI device 0x106b:0x0032 (gem)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x14e4:0x4320 (b43)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address removed>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #####

[    0.000000] PMU driver v2 initialized for Core99, firmware: 0c
[    3.525703] b43-pci-bridge 0001:10:12.0: enabling device (0004 -> 0006)
[    3.525753] ssb: Found chip with id 0x4306, rev 0x03 and package 0x00
[    3.525762] ssb: Core 0 found: ChipCommon (cc 0x800, rev 0x04, vendor 0x4243)
[    3.525769] ssb: Core 1 found: IEEE 802.11 (cc 0x812, rev 0x05, vendor 0x4243)
[    3.525775] ssb: Core 2 found: PCMCIA (cc 0x80D, rev 0x02, vendor 0x4243)
[    3.525781] ssb: Core 3 found: V90 (cc 0x807, rev 0x02, vendor 0x4243)
[    3.525788] ssb: Core 4 found: PCI (cc 0x804, rev 0x09, vendor 0x4243)
[    3.536401] ssb: Sonics Silicon Backplane found on PCI device 0001:10:12.0
[   18.786196] b43-phy0: Broadcom 4306 WLAN found (core revision 5)
[   18.810111] b43-phy0: Found PHY: Analog 2, Type 2 (G), Revision 2
[   24.489776] systemd-udevd[312]: renamed network interface wlan0 to wlan1
[   26.982141] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   27.119144] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
[   27.122565] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready

########## wireless info END ############

---

### Post by Hadaka on 2014-05-01
nothing is really jumping out as to why this isnt working
unless im just not seeing it. the only minor thing i saw was
a space in your router ssid name  "ghost kitty" so ya might
want to do an underscore or no space. I sent a note to our
local wireless expert to have  look at this as well...dont
give up just yet.
thanks.

---

### Post by gulmer on 2014-05-01
Thanks for your persistence.

---

### Post by Hadaka on 2014-05-01
ok..let's do this..disconnect the ethernet cable
boot...see if it connects. *If no connection wireless
then run the wireless script again...plug back in and
post it.
thanks.

---

### Post by gulmer on 2014-05-01
OK, here's what I decided to do, I'm installing 12.04 right now which maybe easier to get wifi to work and yes that's like starting all over again, but 12.04 is stable. I guess I'll have to go through all the same processes, maybe not.

---

### Post by Hadaka on 2014-05-01
ok...If you have problems please post a new thread
and make refrence to this one, good luck !!

---

### Post by Matthias_Holder on 2014-05-02
Hi, 

I am facing a similar issue with a broadcom 4313 wifi module (Asus eee PC 1018P). I am desperately trying to install but Lubuntu 14.04 proves to be a nightmare in this respect, as there is no GUI Interface that would easily let me select another driver. I have already installed the b43 drivers but can't select them.

Also, as I tried the commands you (Hadaka) suggested in post #4, now wl is gone and rfkill list says the wifi card is soft blocked. Before that I was able to see my wifi networks and could connect to them, although it would not let me connect. In this scenario, wl was installed. So I'm reckoning that b43 might solve my problem but I just don't know how to activate it.

The query in #2 you asked cocolopez to run, prompts the following: 14e4:4727

Hope you can help.

Cheers,
Matthias

---

### Post by Matthias_Holder on 2014-05-02
Hi,

Wifi is now working fine and I somehow managed to solve the issue on my own. I uninstalled ndiswrapper and everything b43 related.

However, the only way for me to get to work my wifi is by running the following commands

```

sudo modprobe -r b43
sudo modprobe -r wl
sudo modprobe wl
```

After doing this, nm-applet is starting to establish a connection right away.

So, what I do not understand is the following: How can b43 still be sticking around although I uninstalled it? Secondly, how can I stop it from loading on startup, so I don't need to perform above commands?

Another thing I observed and may help in solving this issue. While booting, the following line appears:

```
b43.allhwsupport=1
```

---

### Post by Hadaka on 2014-05-02
Hi Mattahis_Holder,please start a new thread as your card and
error are not related to this SOLVED thread. Please do no post
on solved thread...
thanks

---

### Post by Matthias_Holder on 2014-05-02
Sorry about this. I did as suggested and opened a new thread.

---

