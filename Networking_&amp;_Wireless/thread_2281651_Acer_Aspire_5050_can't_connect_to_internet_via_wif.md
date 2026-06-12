---
title: "Acer Aspire 5050 can't connect to internet via wifi"
date: 2015-06-08
forum: Networking &amp; Wireless
---

### Post by jamzinbc on 2015-06-08
Hi just wondering if you could direct me to the Wild Man's guide to solving the 5050 wifi problem.  thanks,

James

---

### Post by wildmanne39 on 2015-06-08
Hi, I moved your post to its own thread so you will be able to get the help you need.

Please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by jamzinbc on 2015-06-08
Thank you so kindly for the advice. I ran the wireless-info script and here is what it says. Can anybody make sense out of it?

```


########## wireless info START ##########


Report from: 08 Jun 2015 20:03 PDT -0700


Booted last: 08 Jun 2015 12:58 PDT -0700


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid


##### kernel ############################


Linux 3.19.0-18-generic #18-Ubuntu SMP Tue May 19 18:31:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME Flashback (Metacity)


##### lspci #############################


08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:010f]
	Kernel driver in use: 8139too


08:04.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:ff96] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0418]


##### lsusb #############################


Bus 001 Device 003: ID 04e8:6864 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
video                  20480  1 acer_wmi
wmi                    20480  1 acer_wmi
b43                   421888  0 
bcma                   57344  1 b43
mac80211              724992  1 b43
cfg80211              540672  2 b43,mac80211
ssb                    65536  1 b43


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth2      Link encap:Ethernet  HWaddr <MAC 'eth2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.144  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::ac71:2fff:fe30:545e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:691 errors:0 dropped:0 overruns:0 frame:0
          TX packets:837 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:388824 (388.8 KB)  TX bytes:128205 (128.2 KB)


##### iwconfig ##########################


eth2      no wireless extensions.


usb0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    1024   0        0 usb0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     0      0        0 usb0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       605     1  0 19:59 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         usb0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'usb0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.2/usb1/1-5/1-5:1.0/net/usb0
GENERAL.IP-IFACE:                       usb0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       00e8d339-d345-4b0b-a1e2-ece45eabfa7e
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   00e8d339-d345-4b0b-a1e2-ece45eabfa7e | Wired connection 2
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.42.144/24, gw = 192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.144
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1433822436
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = james-desktop
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         ip = fe80::ac71:2fff:fe30:545e/64, gw = ::


GENERAL.DEVICE:                         eth2
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
GENERAL.DRIVER:                         8139too
GENERAL.DRIVER-VERSION:                 0.9.28
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth2' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:08:02.0/net/eth2
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/bondaygee.com]] (600 root)
[connection] id=bondaygee.com | type=wifi
[wifi] ssid=bondaygee.com | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Vancouver (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20), (N/A)
	(2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
	(5735 - 5835 @ 40), (3, 20), (N/A), NO-IR


##### iwlist channels ###################


eth2      no frequency information.


usb0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth2      Interface doesn't support scanning.


usb0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[b43]
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     25A88E97301A6821E663814
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
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


[bcma]
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-18-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     45659D6D4B015B51A3FF148
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-18-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.19.0-18-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-18-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        F1:A2:A3:18:F7:05:DD:CD:A4:68:5A:32:12:11:6C:13:D2:FD:23:66
sig_hashalgo:   sha512


##### module parameters #################


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


ndiswrapper
b43


##### modprobe options ##################


[/etc/modprobe.d/asus_nb_wmi.conf]
options asus_nb_wmi wapf=1


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
blacklist ideapad-laptop
blacklist ideapad-laptop


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


rfkill unblock wifi
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x8086:0x1503 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


##### dmesg #############################


[   35.351208] 8139too 0000:08:02.0 eth2: link down


########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-06-09
The pci id is not being read correctly, is this a desktop? if so can you try a different pci slot and see if that corrects the readying?
You have a broadcom driver installed but from what I can tell your device is an atheros?
Thanks

---

### Post by jamzinbc on 2015-06-09
This is an Acer Aspire 5050 laptop. The wifi is built in and i can't get it to work. Maybe the physical switch isn't even turned on.  That switch kinda broke, but a few years back I found a way to make it turn on upon booting with some linux code.

Currently I'm tethering my Samsung Galaxy S3 for internet usuage.

I'm not sure what to do from here.  The Thread Titles said the Acer 5050 Wifi issues were solved but the solutions don't seem to work for me.  Should uninstall those broadcam drivers?  Would they conflict?

---

### Post by wildmanne39 on 2015-06-09
When a thread is marked solved it is just for the person that started the thread  so the same solution does not work for everyone.

How old is this laptop?

I am guessing it is an  atheros device based on the pci id and research but it is not being recognized properly so I am a little puzzled here.

Why is the broadcom driver installed was it just a shot in the dark?
Thanks

---

### Post by jamzinbc on 2015-06-09
Yeah everything has been a shot in the dark for me since I'm barely familiar with ubuntu, though I find it fun searching for the codes.  

We had this laptop for about five years.  I had ubuntu on it just a few years ago.  The monitor got busted.  I left  it a few years.  Then for fun, unattached the monitor, plugged an external, boosted the ram and installed the new ubuntu.  I remember saying "yeah hoo I fixed the wifi just a few years ago". I had to find a way to make it turn on I believe since the switch maybe activated or not I don't know

It's fun to try and figure out anyways.

---

### Post by wildmanne39 on 2015-06-09
Before I try experimenting can you boot into an older kernel and see if the wireless works there? and run the script from there maybe it will show the actual device PCI ID. I believe it uses the ath9k driver but I am not sure.
Thanks

---

### Post by jamzinbc on 2015-06-09
So I rebooted, held down shift key and chose a version of ubuntu with an earlier number.  I ran that wireless info script again and here's result.  Wireless didn't work either.  So I plugged in my Samsung S3 again.

```
#!/bin/bash#
# Copyright (c) 2012
#
# Authors: Wild Man, Krytarik
# Helpers: chili555
#
# This script gathers the infos necessary for troubleshooting a wireless
# connection and saves them in a text file, wrapping it in an archive if it
# exceeds the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.
#
##############################################################################
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


SCRIPTDATE="2015-05-21 11:10 +0200"
FILEBASE="wireless-info"
OUTPUTDIR="$PWD"
OUTPUTDIRFB="/tmp"


MODMATCHES="(air|ar5|at7|ath[^3]?|b43|bcma|brcm|carl|ipw|iwl|ndis|r(818|8192[eu]|871|92su)|rt[23567]|rtl|ssb|wl|(cfg|mac)80211)"
LSMODMATCHES="(wmi|(dell|ideapad)[-_]laptop)"
DMESGMATCHES="(wlan[0-9]|eth[1-9]|firmware|[nN]etwork)"
NMPROFMATCHES="\(\[connection\]\|id=\|type=\|permissions=\|autoconnect=\|\[802-11-wireless\]\|\[wifi\]\|ssid=\|bssid=\|mac-address\(-blacklist\)\?=\|mtu=\|\[802-1x\]\|[[:graph:]]*ca-certs\?=\|\[ipv[46]\]\|method=\)"


DMESGEXCL="apparmor|(cfg|mac)80211"
MODINFOEXCL="alias"
MODPROBEXCL="(alsa-base|blacklist-(firewire|framebuffer|modem|oss|watchdog)|fglrx|nvidia|fbdev|bumblebee)"
PMUTILSEXCL="/etc/pm/(power.d/(95hdparm-apm|intel-audio-powersave|sata_alpm)|sleep.d/(10_grub-common|10_unattended-upgrades.*|novatel_3g.*))"


NETMGRNAMES=("NetworkManager" "Wicd" "ConnMan")
NETMGRPATHS=("/usr/sbin/NetworkManager" "/usr/sbin/wicd" "/usr/sbin/connmand")


export LANG="en_US.UTF-8"
export LANGUAGE="en_US:en"
export LC_ALL="en_US.UTF-8"


if [ -t 0 ]; then
    DIALOGAPP="terminal"
    DIALOGBREAK=" "
    TERMOUT="yes"
elif [ -x /usr/bin/zenity ]; then
    DIALOGAPP="zenity"
    DIALOGBREAK="\n"
elif [ -x /usr/bin/kdialog ]; then
    DIALOGAPP="kdialog"
    DIALOGBREAK="\n"
else
    exit 1
fi


if [ -t 0 ]; then
    SUDO="sudo"
elif [ -x /usr/bin/pkexec ]; then
    SUDO="pkexec"
elif [ -x /usr/bin/gksudo ]; then
    SUDO="gksudo"
    GKSUDO="yes"
elif [ -x /usr/bin/kdesudo ]; then
    SUDO="kdesudo"
    KDESUDO="yes"
    KDESUDOCMT=" needs administrative privileges. Please enter your password."
fi


dialog_info () {
    case $DIALOGAPP in
	terminal)
	    printf "%b\n" "$1"
	    ;;
	zenity)
	    zenity --info --text="$1"
	    ;;
	kdialog)
	    kdialog --msgbox "$1"
	    ;;
    esac
}


dialog_error () {
    case $DIALOGAPP in
	terminal)
	    printf "%b\n" "$1" >&2
	    ;;
	zenity)
	    zenity --error --text="$1"
	    ;;
	kdialog)
	    kdialog --error "$1"
	    ;;
    esac
}


dialog_question () {
    case $DIALOGAPP in
	terminal)
	    local INPUT
	    read -r -p "$1 [Y/n]: " INPUT
	    echo "${INPUT,,}"
	    ;;
	zenity)
	    zenity --question --text="$1" || echo "no"
	    ;;
	kdialog)
	    kdialog --yesno "$1" || echo "no"
	    ;;
    esac
}


exec 3>&1 4>&2
exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
    dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\",${DIALOGBREAK}trying in \"$OUTPUTDIRFB\" instead.${TERMOUT+\n}"
    OUTPUTDIR="$OUTPUTDIRFB"
    exec 1> "$OUTPUTDIR/$FILEBASE.txt" || {
	dialog_error "${TERMOUT+\n}Cannot write output file in \"$OUTPUTDIR\" either, aborting.${TERMOUT+\n}"
	exit 1
    }
}
exec 2>&1


printf "\n########## wireless info START ##########\n\n"
REPORTDATE=$(date +"%d %b %Y %H:%M %Z %z")
SCRIPTDATE=$(date -u -d "$SCRIPTDATE" +"%d %b %Y %H:%M %Z %z")
LASTBOOTDT=$(last -FRn 1 reboot | sed -n 's/.*system boot[ ]\+\(.\+\) - .*$/\1/p')
LASTBOOTDT=$(date -d "$LASTBOOTDT" +"%d %b %Y %H:%M %Z %z")
printf "Report from: %s\n\n" "$REPORTDATE"
printf "Booted last: %s\n\n" "$LASTBOOTDT"
printf "Script from: %s\n" "$SCRIPTDATE"


printf "\n##### release ###########################\n\n"
lsb_release -idrc


printf "\n##### kernel ############################\n\n"
uname -srvmpio
echo
sed 's/root=[^ ]*//;s/[ ]\+/, /g;s/^BOOT_IMAGE=[^ ]*/Parameters:/' /proc/cmdline


printf "\n##### desktop ###########################\n\n"
if [ -n "$DESKTOP_SESSION" ]; then
    DESKTOP="$DESKTOP_SESSION"
else
    DESKTOP=$(sed -n 's/^Session=\(.\+\)$/\1/p' "$HOME/.dmrc")
    DESKDMRC=" (from ~/.dmrc)"
fi
if [ -n "$DESKTOP" ]; then
    if [ -f "/usr/share/xsessions/$DESKTOP.desktop" ]; then
	DESKTOP=$(sed -n 's/^Name=\(.\+\)$/\1/p' "/usr/share/xsessions/$DESKTOP.desktop")
    fi
    echo "${DESKTOP/ Session/}${DESKDMRC}"
else
    printf "\nCould not be determined.\n"
fi


printf "\n##### lspci #############################\n\n"
lspci -nnk | grep -iA 2 '^[^[:space:]].*net' | sed '/^--$/d;/^[^[:space:]]/ i\\'


printf "\n##### lsusb #############################\n\n"
lsusb


printf "\n##### PCMCIA card info ##################\n\n"
if [ -x /sbin/pccardctl ]; then
    pccardctl info
else
    echo "'pccardctl' is not installed (package \"pcmciautils\")."
fi


printf "\n##### rfkill ############################\n\n"
rfkill list all


printf "\n##### lsmod #############################\n\n"
LSMOD=$(lsmod | egrep "(^|[[:punct:] ])($MODMATCHES|$LSMODMATCHES)[^[:punct:] ]*([[:punct:] ]|$)")
echo "$LSMOD"


printf "\n##### interfaces ########################\n\n"
sed '/^#/d;s/^wpa-psk [[:graph:]]\+/wpa-psk <WPA key removed>/' /etc/network/interfaces


printf "\n##### ifconfig ##########################\n\n"
ifconfig -a | sed '/^lo /,/^$/d'


printf "\n##### iwconfig ##########################\n\n"
iwconfig


printf "\n##### route #############################\n\n"
route -n


printf "\n##### resolv.conf #######################\n\n"
grep -v '^#' /etc/resolv.conf


printf "\n##### network managers ##################\n\n"
printf "Installed:\n\n"
for NETMGRNR in "${!NETMGRPATHS[@]}"; do
    if [ -f "${NETMGRPATHS[$NETMGRNR]}" ]; then
	NETMGRINST+=("${NETMGRNAMES[$NETMGRNR]}")
    fi
done
printf "\t%s\n" "${NETMGRINST[@]:-None found.}"
NETMGRMATCHES=${NETMGRPATHS[@]/#*\//|}
NETMGRMATCHES=${NETMGRMATCHES// |/|}
NETMGRMATCHES="(${NETMGRMATCHES#|})"
printf "\nRunning:\n\n"
ps -ef | egrep "( |/)$NETMGRMATCHES($| )" || printf "\tNone found.\n"


printf "\n##### NetworkManager info ###############\n\n"
if [ -x /usr/bin/nm-tool ]; then
    nm-tool
elif [ -x /usr/bin/nmcli ]; then
    nmcli -f all device show | sed '/^GENERAL.DEVICE:[ ]\+lo$/,/^$/d; /^AP\[[0-9]\+\]\./d'
    echo
    nmcli -f SSID,BSSID,MODE,CHAN,FREQ,RATE,SIGNAL,BARS,SECURITY,ACTIVE,IN-USE device wifi list
else
    echo "NetworkManager is not installed (package \"network-manager\")."
fi


printf "\n##### NetworkManager.state ##############\n\n"
cat -s /var/lib/NetworkManager/NetworkManager.state


printf "\n##### NetworkManager.conf ###############\n\n"
grep -v '^#' /etc/NetworkManager/NetworkManager.conf
if [ -f /etc/NetworkManager/nm-system-settings.conf ]; then
    printf "\nnm-system-settings.conf (used up to Ubuntu 10.04):\n\n"
    grep -v '^#' /etc/NetworkManager/nm-system-settings.conf
fi


printf "\n##### NetworkManager profiles ###########\n\n"
if [ -d /etc/NetworkManager/system-connections ]; then
    if [ -n "$SUDO" ]; then
	trap "" 2 3
	NMPROFILES=$(find /etc/NetworkManager/system-connections -maxdepth 1 -type f -exec $SUDO${GKSUDO+ -D grep --}${KDESUDO+ -d --comment "<b>grep</b>$KDESUDOCMT" --} grep -vH '^$' {} +) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
	trap 2 3
	if [ "$SUDOSUCCESS" = "yes" ]; then
	    ORIGIFS="$IFS"
	    IFS=$'\n'
	    for NMWLPRFFILE in $(sed -n 's/^\(.\+\):type=\(802-11-wireless\|wifi\).*$/\1/p' <<< "$NMPROFILES"); do
		NMWLPRFFLPERMS=$(stat -c "%a %U" "$NMWLPRFFILE")
		NMWLPROFILE=($(sed -n "s;^$NMWLPRFFILE:\($NMPROFMATCHES.*\)$;\1 |;p" <<< "$NMPROFILES"))
		NMWLPROFSOUT+="[[$NMWLPRFFILE]] ($NMWLPRFFLPERMS)"$'\n'"${NMWLPROFILE[@]}"$'\n\n'
	    done
	    IFS="$ORIGIFS"
	    sed 's# | \[#\n\[#g;s#\] |#\]#g;s/ |$//' <<< "$NMWLPROFSOUT" | sed '/^\[[^]]*\]$/d'
	else
	    printf "\nAcquisition of admin privileges failed.\n"
	fi
    else
	echo "No way to acquire admin privileges found."
    fi
else
    echo "No NetworkManager profiles found."
fi


printf "\n##### iw reg get ########################\n\n"
if [ -x /sbin/iw ]; then
    if IWREGGET=$(iw reg get 2>&1) && [ -f /etc/timezone ]; then
	REGION=$(cat /etc/timezone)
	printf "Region: %s (based on set time zone)\n\n" "$REGION"
    fi
    echo "$IWREGGET"
else
    echo "'iw' is not installed (package \"iw\")."
fi


printf "\n##### iwlist channels ###################\n\n"
if [ -x /sbin/iwlist ]; then
    iwlist chan
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi


printf "\n##### iwlist scan #######################\n\n"
if [ -x /sbin/iwlist ]; then
    if [ -n "$SUDO" ]; then
	trap "" 2 3
	IWLISTSCAN=$($SUDO${KDESUDO+ -d} iwlist scan) && SUDOSUCCESS="yes" || SUDOSUCCESS="no"
	trap 2 3
	if [ "$SUDOSUCCESS" = "yes" ]; then
	    if [[ $IWLISTSCAN = *Frequency:* ]]; then
		printf "Channel occupancy:\n\n"
		grep '^[ ]*Frequency:' <<< "$IWLISTSCAN" | sort | uniq -c | sed 's/^[ ]\+\([ ][0-9]\+\)[ ]\+/     \1   APs on   /'
		echo
	    fi
	    grep -v '^[ ]*IE: Unknown:' <<< "$IWLISTSCAN"
	else
	    printf "\nAcquisition of admin privileges failed.\n"
	fi
    else
	echo "No way to acquire admin privileges found."
    fi
else
    echo "'iwlist' is not installed (package \"wireless-tools\")."
fi


printf "\n##### module infos ######################\n\n"
MODULES=$(egrep -o "^$MODMATCHES[^ ]*" <<< "$LSMOD")
for MODULE in $MODULES; do
    MODINFO=$(modinfo $MODULE | egrep -v "^$MODINFOEXCL:")
    printf "[%s]\n%s\n\n" "$MODULE" "$MODINFO"
done


printf "\n##### module parameters #################\n\n"
for MODULE in $MODULES; do
    if [ -d /sys/module/$MODULE/parameters ]; then
	MODPARAMS=$(grep -H '^[[:graph:]]' /sys/module/$MODULE/parameters/* | sed 's#^.*/##;s/:/: /')
	printf "[%s]\n%s\n\n" "$MODULE" "$MODPARAMS"
    fi
done


printf "\n##### /etc/modules ######################\n\n"
grep -v '^#' /etc/modules


printf "\n##### modprobe options ##################\n\n"
for MODPROBEFILE in $(find /etc/modprobe.{conf,d} -name "*.conf" -regextype posix-egrep -not -regex ".*$MODPROBEXCL.*" 2> /dev/null | sort); do
    MODPROBEOPTS=$(egrep -v '^(#|$)' $MODPROBEFILE)
    if [ -n "$MODPROBEOPTS" ]; then
	printf "[%s]\n%s\n\n" "$MODPROBEFILE" "$MODPROBEOPTS"
    fi
done


printf "\n##### rc.local ##########################\n\n"
grep -v '^#' /etc/rc.local


printf "\n##### pm-utils ##########################\n\n"
for PMUTILSFILE in $(find /etc/pm/*.d \( -type f -o -type l \) -regextype posix-egrep -not -regex "$PMUTILSEXCL" | sort); do
    PMUTFLCONT=$(egrep -v '^(#|$)' $PMUTILSFILE)
    if [ -n "$PMUTFLCONT" ]; then
	PMUTFLPERMS=$(stat -c "%a %U" $PMUTILSFILE)
	printf "[%s] (%s)\n%s\n\n" "$PMUTILSFILE" "$PMUTFLPERMS" "$PMUTFLCONT"
    fi
done


printf "\n##### udev rules ########################\n\n"
for UDEVRLFILE in /etc/udev/rules.d/*net*.rules; do
    UDEVRULES=$(grep -B1 '^[^#]' $UDEVRLFILE | egrep -v '^(--)?$')
    if [ -n "$UDEVRULES" ]; then
	printf "[%s]\n%s\n\n" "$UDEVRLFILE" "$UDEVRULES"
    fi
done


printf "\n##### dmesg #############################\n\n"
dmesg | tail -n 100 | egrep "[[:punct:] ]($MODMATCHES|$DMESGMATCHES)[^[:punct:] ]*[[:punct:] ]" | egrep -v "$DMESGEXCL" | uniq -cf 2 | sed 's/^[ ]\+1[ ]\+//;s/^[ ]\+\([0-9]\+\)[ ]\+\(.\+\)$/\2 (repeated \1 times)/'


printf "\n########## wireless info END ############\n\n"


exec 2>&4 4>&-
exec 1>&3 3>&-


##### MAC address masking #####


RESULTS=$(cat -s "$OUTPUTDIR/$FILEBASE.txt")$'\n'


ORIGIFS="$IFS"
IFS=$'\n'


IFACESRAW=$(sed -n '/^##### ifconfig #####/,/^##### /p' <<< "$RESULTS")
IFACESIDS=($(sed -n "s/^\([^ ]\+\)[ ]\+.*HWaddr.*/'\1' [IF]/p" <<< "$IFACESRAW"))
IFACESMACS=($(sed -n 's/^[^ ]\+[ ]\+.*HWaddr \([^ ]\+\)[ ]*/\1/p' <<< "$IFACESRAW"))


WLAPSIWLRAW=$(sed -n '/^##### iwlist scan #####/,/^##### /p' <<< "$RESULTS")
WLAPSIWLIDS=($(sed -n "/^[ ]*Cell [0-9]\+/,/^[ ]*ESSID:/ {/^[ ]*Cell [0-9]\+/h;/^[ ]*ESSID:/ {H;g;s/^[ ]*Cell 0\?\([0-9]\+\).*ESSID:\"\(.*\)\"$/'\2' [AC\1]/p}}" <<< "$WLAPSIWLRAW"))
WLAPSIWLMACS=($(sed -n 's/^[ ]*Cell [0-9]\+.*Address: \([^ ]\+\)/\1/p' <<< "$WLAPSIWLRAW"))


WLAPSNMRAW=$(sed -n '/^##### NetworkManager info #####/,/^##### / {/^[ ]*Wireless Access Points/,/^$/ {/Wireless Access Points/d;s/^[ ]\+\*\?//;s/:[ ]\+/\t/;p}; /^SSID[ ]\+BSSID[ ]\+/,/^$/ {/^SSID[ ]\{2,\}BSSID[ ]\{2,\}/d;s/[ ]\{2,\}/\t/;p}}' <<< "$RESULTS")
WLAPSNMIDS=($(awk -F '\t' '{printf "'\''%s'\'' [AN%d]\n", $1, NR}' <<< "$WLAPSNMRAW"))
WLAPSNMMACS=($(grep -o '\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}' <<< "$WLAPSNMRAW"))


IFS="$ORIGIFS"


for IFACENR in "${!IFACESMACS[@]}"; do
    MACMASKSED+="s;${IFACESMACS[$IFACENR]};<MAC ${IFACESIDS[$IFACENR]-address}>;I;"
done


for WLAPIWLNR in "${!WLAPSIWLMACS[@]}"; do
    MACMASKSED+="s;${WLAPSIWLMACS[$WLAPIWLNR]};<MAC ${WLAPSIWLIDS[$WLAPIWLNR]-address}>;I;"
done


for WLAPNMNR in "${!WLAPSNMMACS[@]}"; do
    MACMASKSED+="s;${WLAPSNMMACS[$WLAPNMNR]};<MAC ${WLAPSNMIDS[$WLAPNMNR]-address}>;I;"
done


sed "$MACMASKSED/\([[:alnum:]]\{2\}:\)\{6,\}/! s/\([[:alnum:]]\{2\}:\)\{5\}[[:alnum:]]\{2\}/<MAC address>/" <<< "$RESULTS" > "$OUTPUTDIR/$FILEBASE.txt"


##### The End #####


dialog_info "${TERMOUT+\n}Results saved in \"$OUTPUTDIR/$FILEBASE.txt\".${TERMOUT+\n}"


if (( $(stat -c %s "$OUTPUTDIR/$FILEBASE.txt") > 19968 )); then
    tar -czf "$OUTPUTDIR/$FILEBASE.tar.gz" -C "$OUTPUTDIR" "$FILEBASE.txt" && \
	dialog_info "Results also archived in \"$OUTPUTDIR/$FILEBASE.tar.gz\",${DIALOGBREAK}as they exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums.${TERMOUT+\n}" || \
	dialog_error "Results exceed the 19.5 kB size limit for \".txt\" attachments${DIALOGBREAK}on the Ubuntu Forums, but archive could not be created.${TERMOUT+\n}"
fi


if [ -x /usr/bin/pastebinit ] && ping -nc 3 -w 6 -i 0.2 paste.ubuntu.com > /dev/null 2>&1; then
    PASTEBIN=$(dialog_question "Do you also want to post them${DIALOGBREAK}to your default 'pastebinit' provider?")
    if [[ ! $PASTEBIN =~ ^no?$ ]]; then
	PASTERESULT=$(pastebinit -i "$OUTPUTDIR/$FILEBASE.txt" -f text 2>&1) && PASTESUCCESS="yes"
	if [ "$PASTESUCCESS" = "yes" ]; then
	    dialog_info "${TERMOUT+\n}Pastebin successful:\n\n${PASTERESULT}${TERMOUT+\n}"
	else
	    if [ -n "$PASTERESULT" ]; then
		dialog_error "${TERMOUT+\n}Pastebin failed, error message is:\n\n${PASTERESULT}${TERMOUT+\n}"
	    else
		dialog_error "${TERMOUT+\n}Pastebin failed, no error message given.${TERMOUT+\n}"
	    fi
	fi
    else
	echo
    fi
fi
```

---

### Post by wildmanne39 on 2015-06-09
That is the actual script, we need to see the file created by running the script like in the previous post.
Thanks

---

### Post by jamzinbc on 2015-06-09
Hopefully I have copied and pasted the correct one this time:

```


########## wireless info START ##########


Report from: 09 Jun 2015 19:58 PDT -0700


Booted last: 09 Jun 2015 07:08 PDT -0700


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid


##### kernel ############################


Linux 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


GNOME Flashback (Metacity)


##### lspci #############################


08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:010f]
	Kernel driver in use: 8139too


08:04.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:ff96] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0418]


##### lsusb #############################


Bus 001 Device 008: ID 04e8:6864 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
video                  20480  1 acer_wmi
wmi                    20480  1 acer_wmi
b43                   421888  0 
bcma                   57344  1 b43
mac80211              720896  1 b43
cfg80211              540672  2 b43,mac80211
ssb                    65536  1 b43


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth2      Link encap:Ethernet  HWaddr <MAC 'eth2' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


usb0      Link encap:Ethernet  HWaddr <MAC 'usb0' [IF]>  
          inet addr:192.168.42.242  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::a888:d4ff:fe3c:3323/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1792 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1810 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:983974 (983.9 KB)  TX bytes:304838 (304.8 KB)


##### iwconfig ##########################


eth2      no wireless extensions.


usb0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    1024   0        0 usb0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     0      0        0 usb0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       557     1  0 14:09 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         usb0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         <MAC 'usb0' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.2/usb1/1-5/1-5:1.0/net/usb0
GENERAL.IP-IFACE:                       usb0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       e85d27a1-3c7e-442f-ba88-d16952810eff
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/2
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{4}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   e85d27a1-3c7e-442f-ba88-d16952810eff | Wired connection 2
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.42.242/24, gw = 192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.242
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1433908069
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = james-desktop
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         ip = fe80::a888:d4ff:fe3c:3323/64, gw = ::


GENERAL.DEVICE:                         eth2
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
GENERAL.DRIVER:                         8139too
GENERAL.DRIVER-VERSION:                 0.9.28
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'eth2' [IF]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:08:02.0/net/eth2
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off


##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/bondaygee.com]] (600 root)
[connection] id=bondaygee.com | type=wifi
[wifi] ssid=bondaygee.com | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/Vancouver (based on set time zone)


country 00: DFS-UNSET
	(2402 - 2472 @ 40), (3, 20), (N/A)
	(2457 - 2482 @ 40), (3, 20), (N/A), NO-IR
	(2474 - 2494 @ 20), (3, 20), (N/A), NO-OFDM, NO-IR
	(5170 - 5250 @ 40), (3, 20), (N/A), NO-IR
	(5735 - 5835 @ 40), (3, 20), (N/A), NO-IR


##### iwlist channels ###################


eth2      no frequency information.


usb0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth2      Interface doesn't support scanning.


usb0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


[b43]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     25A88E97301A6821E663814
depends:        bcma,ssb,mac80211,cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
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


[bcma]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     F17244FFF75F9BDF92327ED
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512


[mac80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F518BE1BD732F328C9E430B
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/3.19.0-15-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     268045EBCFAFDADD136DCF6
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


[ssb]
filename:       /lib/modules/3.19.0-15-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     551AE4C23939F7FBED9DA61
depends:        
intree:         Y
vermagic:       3.19.0-15-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        9E:64:80:70:92:F3:A6:A8:F6:6F:3B:7E:A4:CB:37:67:FD:FA:E0:8A
sig_hashalgo:   sha512


##### module parameters #################


[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2


[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


ndiswrapper
b43


##### modprobe options ##################


[/etc/modprobe.d/asus_nb_wmi.conf]
options asus_nb_wmi wapf=1


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
blacklist ideapad-laptop
blacklist ideapad-laptop


[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


##### rc.local ##########################


rfkill unblock wifi
exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x0032 (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x8086:0x1503 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# PCI device 0x10ec:0x8139 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth2' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth2"
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth3"


##### dmesg #############################


[   36.518449] 8139too 0000:08:02.0 eth2: link down


########## wireless info END ############



```

---

### Post by wildmanne39 on 2015-06-10
We are going to remove b43 and ndiswrapper from ```
/etc/modules
```
do:
```
sudo gedit /etc/modules
```
remove ndiswrapper and b43 then save the file and reboot.

Then post the output of:
```
lspci -nn | grep -e 0200 -e 0280
```
Thanks

---

### Post by jamzinbc on 2015-06-11
Thank you for trying to help.  I should point out. I'm getting an internet error upon booting up that says: usr/sbin/ModemManager.  I think it failed to load.

"Modem Manager crashed with SIGSEGIV IN g_main_context_dispatch()"

A few more lines were in the error report.

I will try the above recommendations now.

Ok file saved now for reboot.  And here's the result.  Any clues?

08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
08:04.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:ff96] (rev 01)

---

### Post by chili555 on 2015-06-11
>  I'm getting an internet error upon booting up that says: usr/sbin/ModemManager. I think it failed to load.

"Modem Manager crashed with SIGSEGIV IN g_main_context_dispatch()"

A few more lines were in the error report.In case this is somehow related to your built-in wireless, Wild Man asks that you remove the USB modem and reboot. Then run:```
lspci -nn | grep Atheros
```Does your device identify itself as 168c:ff96, which is wrong, or does it identify as 168c:0032 which we believe is correct?

---

### Post by jamzinbc on 2015-06-11
Response to code:
08:04.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:ff96] (rev 01)

---

### Post by wildmanne39 on 2015-06-11
The only thing that I can think of that might help is resetting the bios to default and possibly the cmos, maybe chili555 will have another idea he is the best at wireless issues.
Thanks for posting chili555.

---

### Post by jamzinbc on 2015-06-11
Well I did a bios restore defaults.  And here's the error message I get upon booting up. I took a snapshot with my camera is this provides any clues:

[https://drive.google.com/file/d/0B3f1SrP-3AFdQmNhdVczRmVmUkE/view?usp=sharing](https://drive.google.com/file/d/0B3f1SrP-3AFdQmNhdVczRmVmUkE/view?usp=sharing)

---

### Post by wildmanne39 on 2015-06-11
So did it actually boot all the way?
Where it says see load modules service you should look there and see what it says.

---

### Post by jamzinbc on 2015-06-11
After that screen it just turned to the purple ubuntu color.  Actually to be honest after the Bios Restore, it didn't boot up.  It froze during the bootup process with a purple screen.  Then I unplugged and removed battery. Rebooted again and then I saw those messages and photographed them. That's all it said....before it switched to the purple ubuntu screen.

I'm using this Acer 5050 to write all the messages. So it does eventually boot all the way and seems to work pretty good.

---

### Post by wildmanne39 on 2015-06-11
What does this tell us now:
```
lspci -nn | grep -e 0200 -e 0280
```
Thanks

---

### Post by jamzinbc on 2015-06-11
Code entered: lspci -nn | grep -e 0200 -e 0280
Response:
08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
08:04.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:ff96] (rev 01)

---

### Post by wildmanne39 on 2015-06-11
It did not change anything but for the heck of it do:
```
sudo modprobe ath9k
```
Does wireless come on? and run a post a new file from the script please.
Thanks

---

### Post by jamzinbc on 2015-06-11
Did the sudomod probe.  Didn't see anything happen.  Rebooted and got stuck in a BusyBox Inintrafs menu:  [https://drive.google.com/file/d/0B3f1SrP-3AFdOUoyeFVXRG9nX3c/view?usp=sharing](https://drive.google.com/file/d/0B3f1SrP-3AFdOUoyeFVXRG9nX3c/view?usp=sharing)

Killed power restarted. Tried sudo modprobe ath9k again and ran that script:

Here's that wireless script again:

```

```

########## wireless info START ##########


Report from: 11 Jun 2015 19:41 PDT -0700


Booted last: 11 Jun 2015 12:32 PDT -0700


Script from: 21 May 2015 09:10 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 15.04
Release:	15.04
Codename:	vivid


##### kernel ############################


Linux 3.19.0-18-generic #18-Ubuntu SMP Tue May 19 18:31:35 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


GNOME Flashback (Metacity)


##### lspci #############################




08:02.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8100/8101L/8139 PCI Fast Ethernet Adapter [10ec:8139] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:010f]
	Kernel driver in use: 8139too


08:04.0 Ethernet controller [0200]: Qualcomm Atheros Device [168c:ff96] (rev 01)
	Subsystem: AMBIT Microsystem Corp. Device [1468:0418]


##### lsusb #############################


Bus 001 Device 004: ID 04e8:6864 Samsung Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 1532:001c Razer USA, Ltd RZ01-0036 Optical Gaming Mouse [Abyssus]
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255


##### rfkill ############################


0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath9k                 147456  0 
ath9k_common           32768  1 ath9k
ath9k_hw              458752  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              724992  1 ath9k
cfg80211              540672  4 ath,ath9k_common,ath9k,mac80211
acer_wmi               20480  0 
sparse_keymap          16384  1 acer_wmi
video                  20480  1 acer_wmi
wmi                    20480  1 acer_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth2      Link encap:Ethernet  HWaddr 00:16:36:ab:5a:50  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)


usb0      Link encap:Ethernet  HWaddr 72:20:98:d8:ab:e8  
          inet addr:192.168.42.206  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::7020:98ff:fed8:abe8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31072 errors:3 dropped:0 overruns:0 frame:3
          TX packets:15589 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:39783995 (39.7 MB)  TX bytes:4208209 (4.2 MB)




##### iwconfig ##########################


eth2      no wireless extensions.


usb0      no wireless extensions.


lo        no wireless extensions.




##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    1024   0        0 usb0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     0      0        0 usb0


##### resolv.conf #######################


nameserver 127.0.1.1


##### network managers ##################


Installed:


	NetworkManager


Running:


root       564     1  0 19:32 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         usb0
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         SAMSUNG
GENERAL.PRODUCT:                        SAMSUNG_Android
GENERAL.DRIVER:                         rndis_host
GENERAL.DRIVER-VERSION:                 22-Aug-2005
GENERAL.FIRMWARE-VERSION:               RNDIS device
GENERAL.HWADDR:                         72:20:98:D8:AB:E8
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:13.2/usb1/1-5/1-5:1.0/net/usb0
GENERAL.IP-IFACE:                       usb0
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-UUID:                       a25f2532-01c0-4d8e-a95c-c40648f57288
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   a25f2532-01c0-4d8e-a95c-c40648f57288 | Wired connection 2
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         ip = 192.168.42.206/24, gw = 192.168.42.129
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.42.129
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 192.168.42.129
DHCP4.OPTION[5]:                        ip_address = 192.168.42.206
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 192.168.42.129
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 192.168.42.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 3150
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 192.168.42.129
DHCP4.OPTION[16]:                       dhcp_renewal_time = 1800
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       requested_routers = 1
DHCP4.OPTION[19]:                       expiry = 1434080137
DHCP4.OPTION[20]:                       requested_wpad = 1
DHCP4.OPTION[21]:                       host_name = james-desktop
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[24]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[25]:                       network_number = 192.168.42.0
DHCP4.OPTION[26]:                       requested_domain_search = 1
DHCP4.OPTION[27]:                       requested_ntp_servers = 1
DHCP4.OPTION[28]:                       next_server = 192.168.42.129
DHCP4.OPTION[29]:                       vendor_encapsulated_options = ANDROID_METERED
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 3600
IP6.ADDRESS[1]:                         ip = fe80::7020:98ff:fed8:abe8/64, gw = ::


GENERAL.DEVICE:                         eth2
GENERAL.TYPE:                           ethernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL-8100/8101L/8139 PCI Fast Ethernet Adapter
GENERAL.DRIVER:                         8139too
GENERAL.DRIVER-VERSION:                 0.9.28
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         00:16:36:AB:5A:50
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:14.4/0000:08:02.0/net/eth2
GENERAL.IP-IFACE:                       
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 
WIRED-PROPERTIES.CARRIER:               off






##### NetworkManager.state ##############


[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


##### NetworkManager.conf ###############


[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


[ifupdown]
managed=false


##### NetworkManager profiles ###########

---

### Post by wildmanne39 on 2015-06-12
That did not help either, you may have a corrupt install, if you reformatted your ubuntu partition and reinstalled ubuntu it might help, that is the only thing I can suggest and that is a long shot. I wonder if you are having some kind of hardware issue because of the errors you are getting. I know that a hard reboot like you are doing will corrupt files and cause hard drive failure.

---

### Post by jamzinbc on 2015-06-12
I was thinking of maybe of reinstalling with Lubuntu instead.  That's a lighter version right? I actually quite enjoy installing operating systems! It's fun!

---

### Post by wildmanne39 on 2015-06-12
Yes lubuntu is much lighter then ubuntu.

---

### Post by chili555 on 2015-06-12
> **jamzinbc said:**
> I was thinking of maybe of reinstalling with Lubuntu instead.  That's a lighter version right? I actually quite enjoy installing operating systems! It's fun!I doubt it will fix this:```
08:04.0 Ethernet controller [0200]: Qualcomm Atheros Device [[COLOR="#FF0000"]168c:ff96[/COLOR]] (rev 01)
Subsystem: AMBIT Microsystem Corp. Device [1468:0418]

```In any case, good luck.

---

### Post by jamzinbc on 2015-06-16
Yes and thanks for the advice.  I wonder why it worked on Ubuntu 12 but not this version.  Hard to say.  It might be an actual physical problem like the wifi switch being permanently in the off position. I can't access it any more.  Anyways thanks for trying.

I have no idea what that code jargon means above.  I'm curious though as to what it means.

08:04.0 Ethernet controller [0200]: Qualcomm Atheros Device [[COLOR=#FF0000]168c:ff96[/COLOR]] (rev 01)
Subsystem: AMBIT Microsystem Corp. Device [1468:0418]

Another Question:

After a fresh installation of Lubuntu, what kind of sudo code should a person input into a terminal to try and activate this Atheros Wifi hardware? I was trying random things before.

---

### Post by chili555 on 2015-06-16
Drivers meet up with hardware and work together based on the pci.id, usb.id, etc. The driver has coded in it the devices it will claim and work with. The driver we think is supposed to work with your device is ath9k. Here is its modinfo:```
$ modinfo ath9k
filename:       /lib/modules/3.19.0-16-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     6D1C555B730584789ECF3D1
alias:          pci:v0000168Cd00000036sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv00001043sd000085F2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00004026bc*sc*i*
alias:          pci:v0000168Cd00000036sv000017AAsd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E081bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E07Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A120bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd000028A2bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002810bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Fsd00007202bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002182bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002130bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000692bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000832bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000612bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000652bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000642bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003027bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Ebc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Dbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000144Dsd0000411Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001028sd0000020Cbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd00002005bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd0000217Fbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000103Csd000018E3bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000213Abc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000682bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd000006A2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000662bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000672bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000622bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd00003028bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E069bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd0000302Bbc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003026bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003025bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd0000218Abc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd000028A1bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002812bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001B9Asd00002811bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00006671bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000842bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd000006B2bc*sc*i*
alias:          pci:v0000168Cd00000036sv000011ADsd00000632bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000185Fsd0000A119bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000105Bsd0000E068bc*sc*i*
alias:          pci:v0000168Cd00000036sv00001A3Bsd00002176bc*sc*i*
alias:          pci:v0000168Cd00000036sv0000168Csd00003028bc*sc*i*
alias:          pci:v0000168Cd00000037sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000034sv*sd*bc*sc*i*
alias:          pci:v0000168Cd00000030sv00001A56sd00002003bc*sc*i*
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
alias:          pci:v0000[COLOR="#FF0000"]168C[/COLOR]d0000[COLOR="#FF0000"]0032[/COLOR]sv00001043sd0000850Dbc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C01bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00001C00bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F95bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001195bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001F86bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00001186bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001B9Asd00002000bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000144Fsd00007197bc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Fbc*sc*i*
alias:          pci:v0000168Cd00000032sv0000105Bsd0000E04Ebc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006628bc*sc*i*
alias:          pci:v0000168Cd00000032sv000011ADsd00006627bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001C56sd00004001bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002100bc*sc*i*
alias:          pci:v0000168Cd00000032sv00001A3Bsd00002C97bc*sc*i*
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
alias:          pci:v0000168Cd00000030sv00001A56sd00002001bc*sc*i*
alias:          pci:v0000168Cd00000030sv00001A56sd00002000bc*sc*i*
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
alias:          platform:qca953x_wmac
alias:          platform:qca955x_wmac
alias:          platform:ar934x_wmac
alias:          platform:ar933x_wmac
alias:          platform:ath9k
depends:        ath9k_hw,mac80211,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       3.19.0-16-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        CB:FB:67:D2:A3:78:D1:85:C4:A0:6F:9F:73:60:5E:84:9D:86:18:5D
sig_hashalgo:   sha512
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)
```As an example, 168c:0032 under several subsystems is listed; I've highlighted one. However, 168c:ff96 is not. Therefore, the driver doesn't claim the device and work with it.

When we google 168c:ff96, we see no driver as appropriate for it and a few posts about "...my wireless isn't working, what shall I do?"

I wonder if the device is somehow defective and doesn't any longer correctly advertise it's pci.id. As it stands now, no driver claims it.

---

