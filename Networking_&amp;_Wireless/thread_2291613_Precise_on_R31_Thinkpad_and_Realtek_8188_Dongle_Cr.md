---
title: "Precise on R31 Thinkpad and Realtek 8188 Dongle Crashes Attempting To Go Online"
date: 2015-08-21
forum: Networking &amp; Wireless
---

### Post by JGreenidge on 2015-08-21
Greetings:

I tried my best to follow the canceled topic line:  Networking & Wireless > RealTek RTL-8188CUs working well-how to

I am reviving a R31 Thinkpad with Ubuntu 12.04 since Thinkpad sites say that’s the best Ubuntu version to efficiently run on this machine. To network I'm using a Realtek 802.11n dongle with mini-CD containing RTL8188 CU and RTL8188 EU folders. After repeated failed attempts at using the CD's software I tapped the advice to try scripts and drivers on-line and found in the canceled topic the closest remedy, [https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/Tjeremiah](https://code.google.com/p/realtek-8188cus-wireless-drivers-3444749-ubuntu-1304/Tjeremiah) as mentioned the canceled topic.

The R31 at last logs on the web via wifi and even the clock and weather apps update real-time as normal as does software update. But if I attempt to use a browser or access the web via CLI the system crashes. The particulars of my system as follows:


```

########## wireless info START ##########

Report from: 18 Aug 2015 04:22 EDT -0400

Booted last: 18 Aug 2015 03:54 EDT -0400

Script from: 14 Jul 2015 17:04 UTC +0000

##### release ###########################

Distributor ID:	Debian
Description:	Ubuntu
Release:	12.04.5 LTS
Codename:	Precise Pangolin

##### kernel ############################

Linux 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 i686 i686 i386 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

default

##### lspci #############################

01:08.0 Ethernet controller [0200]: Intel Corporation 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller [8086:1031] (rev 42)
Subsystem: IBM Device [1014:1031]
Kernel driver in use: e100

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0bda:0179 Realtek Semiconductor Corp. 

##### PCMCIA card info ##################

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth1 Link encap:Ethernet HWaddr <MAC 'eth1' [IF]> 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

irda0 Link encap:IrLAP HWaddr <MAC 'irda0' [IF]> 
NOARP MTU:2048 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:8 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wlan0 Link encap:Ethernet HWaddr <MAC 'wlan0' [IF]> 
inet addr:192.168.1.170 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:936 errors:0 dropped:108 overruns:0 frame:0
TX packets:427 errors:0 dropped:1 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:379495 (379.4 KB) TX bytes:57922 (57.9 KB)

##### iwconfig ##########################

lo no wireless extensions.

eth1 no wireless extensions.

irda0 no wireless extensions.

wlan0 IEEE 802.11bgn ESSID:"FiOS-XU1SQ" Nickname:"<WIFI@REALTEK>"
Mode:Managed Frequency:2.462 GHz Access Point: <MAC 'FiOS-XU1SQ' [AC1]> 
Bit Rate:72.2 Mb/s Sensitivity:0/0 
Retry:off RTS thr:off Fragment thr:off
Power Management:off
Link Quality=51/100 Signal level=-56 dBm Noise level=0 dBm
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

##### route #############################

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 wlan0
169.254.0.0 0.0.0.0 255.255.0.0 U 1000 0 0 wlan0
192.168.1.0 0.0.0.0 255.255.255.0 U 2 0 0 wlan0

##### resolv.conf #######################

grep: /etc/resolv.conf: No such file or directory

##### network managers ##################

Installed:

NetworkManager

Running:

root 684 1 0 03:54 ? 00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
Type: Wired
Driver: e100
State: unavailable
Default: no
HW Address: <MAC 'eth1' [IF]>

Capabilities:
Carrier Detect: yes

Wired Properties
Carrier: off

- Device: wlan0 [FiOS-XU1SQ 1] ------------------------------------------------
Type: 802.11 WiFi
Driver: r8188eu
State: connected
Default: yes
HW Address: <MAC 'wlan0' [IF]>

Capabilities:
Speed: 72 Mb/s

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points (* = current AP)
Parker: Infra, <MAC 'Parker' [AC6]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 0 WPA WPA2
L5E02: Infra, <MAC 'L5E02' [AC4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 0 WEP
*FiOS-XU1SQ: Infra, <MAC 'FiOS-XU1SQ' [AC1]>, Freq 2462 MHz, Rate 16 Mb/s, Strength 57 WPA2
TG1672GF2: Infra, <MAC 'TG1672GF2' [AN4]>, Freq 2462 MHz, Rate 44 Mb/s, Strength 0 WPA2
FiOS-DMJCP: Infra, <MAC 'FiOS-DMJCP' [AC2]>, Freq 2412 MHz, Rate 16 Mb/s, Strength 0 WPA2
TG1672GB2: Infra, <MAC 'TG1672GB2' [AN6]>, Freq 2412 MHz, Rate 44 Mb/s, Strength 0 WPA2
3FHB9: Infra, <MAC '3FHB9' [AN7]>, Freq 2437 MHz, Rate 2 Mb/s, Strength 0 WPA2

IPv4 Settings:
Address: 192.168.1.170
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1

DNS: 192.168.1.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

no-auto-default=<MAC 'eth1' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/FiOS-XU1SQ 1]] (600 root)
[connection] id=FiOS-XU1SQ 1 | type=802-11-wireless
[802-11-wireless] ssid=FiOS-XU1SQ | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/FiOS-XU1SQ]] (600 root)
[connection] id=FiOS-XU1SQ | type=802-11-wireless
[802-11-wireless] ssid=FiOS-XU1SQ | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

nl80211 not found.

##### iwlist channels ###################

lo no frequency information.

eth1 no frequency information.

irda0 no frequency information.

wlan0 13 channels in total; available frequencies :
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
Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo Interface doesn't support scanning.

eth1 Interface doesn't support scanning.

irda0 Interface doesn't support scanning.

Channel occupancy:

4 APs on Frequency:2.412 GHz (Channel 1)
2 APs on Frequency:2.462 GHz (Channel 11)

wlan0 Scan completed :
Cell 01 - Address: <MAC 'FiOS-XU1SQ' [AC1]>
ESSID:"FiOS-XU1SQ"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.462 GHz (Channel 11)
Encryption key:on
Bit Rates:144 Mb/s
Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Quality=0/100 Signal level=2/100 
Cell 02 - Address: <MAC 'FiOS-DMJCP' [AC2]>
ESSID:"FiOS-DMJCP"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.412 GHz (Channel 1)
Encryption key:on
Bit Rates:144 Mb/s
Extra:rsn_ie =30140100000fac040100000fac040100000fac020c00
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Quality:0 Signal level:0 Noise level:0
Cell 03 - Address: <MAC 'BNYJK' [AC3]>
ESSID:"BNYJK"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.412 GHz (Channel 1)
Encryption key:on
Bit Rates:130 Mb/s
Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Quality:0 Signal level:0 Noise level:0
Cell 04 - Address: <MAC 'L5E02' [AC4]>
ESSID:"L5E02"
Protocol:IEEE 802.11bg
Mode:Master
Frequency:2.412 GHz (Channel 1)
Encryption key:on
Bit Rates:54 Mb/s
Quality:0 Signal level:0 Noise level:0
Cell 05 - Address: <MAC 'TG1672G42' [AC5]>
ESSID:"TG1672G42"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.412 GHz (Channel 1)
Encryption key:on
Bit Rates:300 Mb/s
Extra:rsn_ie =30140100000fac040100000fac040100000fac020000
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : CCMP
Pairwise Ciphers (1) : CCMP
Authentication Suites (1) : PSK
Quality:0 Signal level:0 Noise level:0
Cell 06 - Address: <MAC 'Parker' [AC6]>
ESSID:"Parker"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.462 GHz (Channel 11)
Encryption key:on
Bit Rates:144 Mb/s
Extra:wpa_ie =dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Extra:rsn_ie =30180100000fac020200000fac04000fac020100000fac020c00
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Quality:0 Signal level:0 Noise level:0

##### module infos ######################

##### module parameters #################

##### /etc/modules ######################

lp
r8168
r8168

##### modprobe options ##################

[/etc/modprobe.d/50-8188eu.conf]
blacklist r8188eu

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
blacklist r8169

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/power.d/00-jupiter-cpu] (755 root)
JUPITER_PATH="/usr/lib/jupiter/scripts"
JUPITER_KERNEL="/usr/lib/jupiter/kernel"
JUPITER_HW="/usr/lib/jupiter/vendors"
JUPITER_VAR="/var/jupiter"
DEFAULT_MODE="high"
VENDOR=$(dmidecode -s system-manufacturer)
AC_DEVICE=$(ls /sys/class/power_supply | grep "ADP\|AC")
ACPI_AC_PROC=/sys/class/power_supply/$AC_DEVICE/online
function save_ac_state {
if [ ! -d "$JUPITER_VAR" ]; then
mkdir $JUPITER_VAR 2>/dev/null
fi
}
function set_cpu {
if [ -e "$ACPI_AC_PROC" ]; then
if [ "$(cat $ACPI_AC_PROC)" = "1" ]; then
if [ -e "$JUPITER_VAR/power" ]; then
RESTORE_MODE=$(cat $JUPITER_VAR/power)
else
RESTORE_MODE=$DEFAULT_MODE
fi
$JUPITER_PATH/cpu-control $RESTORE_MODE
$JUPITER_KERNEL/power
if [ -e "$JUPITER_HW/$VENDOR/power" ]; then
"$JUPITER_HW/$VENDOR/power"
fi
else
if [ -e "$JUPITER_VAR/battery" ]; then
RESTORE_MODE=$(cat $JUPITER_VAR/battery)
else
RESTORE_MODE="powersave"
fi
$JUPITER_PATH/cpu-control $RESTORE_MODE
$JUPITER_KERNEL/battery
if [ -e "$JUPITER_HW/$VENDOR/battery" ]; then
"$JUPITER_HW/$VENDOR/battery" 
fi
fi
else
if [ -e "$JUPITER_VAR/power" ]; then
RESTORE_MODE=$(cat $JUPITER_VAR/power)
else
RESTORE_MODE=$DEFAULT_MODE
fi
$JUPITER_PATH/cpu-control $RESTORE_MODE
$JUPITER_KERNEL/power
if [ -e "$JUPITER_HW/$VENDOR/power" ]; then
"$JUPITER_HW/$VENDOR/power"
fi
fi
}
case "$1" in
*) set_cpu
;;
esac

[/etc/pm/power.d/.svn/all-wcprops] (644 root)
K 25
svn:wc:ra_dav:version-url
V 56
/svnroot/jupiter/!svn/ver/228/jupiter-current/pm/power.d
END
00-jupiter-cpu
K 25
svn:wc:ra_dav:version-url
V 71
/svnroot/jupiter/!svn/ver/228/jupiter-current/pm/power.d/00-jupiter-cpu
END

[/etc/pm/power.d/.svn/entries] (644 root)
10
dir
229
[https://jupiter.svn.sourceforge.net/svn](https://jupiter.svn.sourceforge.net/svn) ... pm/power.d
[https://jupiter.svn.sourceforge.net/svnroot/jupiter](https://jupiter.svn.sourceforge.net/svnroot/jupiter)
2012-08-06T23:39:27.703920Z
228
fewt
88dc9430-8cf2-4ce5-b1bb-985ca465ea57

00-jupiter-cpu
file
2012-08-08T11:01:54.013128Z
c0c4896a4d88780d239a3e13d93ece53
2012-08-06T23:39:27.703920Z
228
fewt
has-props
1650


[/etc/pm/power.d/.svn/prop-base/00-jupiter-cpu.svn-base] (644 root)
K 14
svn:executable
V 1
*
END

[/etc/pm/power.d/.svn/text-base/00-jupiter-cpu.svn-base] (644 root)
JUPITER_PATH="/usr/lib/jupiter/scripts"
JUPITER_KERNEL="/usr/lib/jupiter/kernel"
JUPITER_HW="/usr/lib/jupiter/vendors"
JUPITER_VAR="/var/jupiter"
DEFAULT_MODE="high"
VENDOR=$(dmidecode -s system-manufacturer)
AC_DEVICE=$(ls /sys/class/power_supply | grep "ADP\|AC")
ACPI_AC_PROC=/sys/class/power_supply/$AC_DEVICE/online
function save_ac_state {
if [ ! -d "$JUPITER_VAR" ]; then
mkdir $JUPITER_VAR 2>/dev/null
fi
}
function set_cpu {
if [ -e "$ACPI_AC_PROC" ]; then
if [ "$(cat $ACPI_AC_PROC)" = "1" ]; then
if [ -e "$JUPITER_VAR/power" ]; then
RESTORE_MODE=$(cat $JUPITER_VAR/power)
else
RESTORE_MODE=$DEFAULT_MODE
fi
$JUPITER_PATH/cpu-control $RESTORE_MODE
$JUPITER_KERNEL/power
if [ -e "$JUPITER_HW/$VENDOR/power" ]; then
"$JUPITER_HW/$VENDOR/power"
fi
else
if [ -e "$JUPITER_VAR/battery" ]; then
RESTORE_MODE=$(cat $JUPITER_VAR/battery)
else
RESTORE_MODE="powersave"
fi
$JUPITER_PATH/cpu-control $RESTORE_MODE
$JUPITER_KERNEL/battery
if [ -e "$JUPITER_HW/$VENDOR/battery" ]; then
"$JUPITER_HW/$VENDOR/battery" 
fi
fi
else
if [ -e "$JUPITER_VAR/power" ]; then
RESTORE_MODE=$(cat $JUPITER_VAR/power)
else
RESTORE_MODE=$DEFAULT_MODE
fi
$JUPITER_PATH/cpu-control $RESTORE_MODE
$JUPITER_KERNEL/power
if [ -e "$JUPITER_HW/$VENDOR/power" ]; then
"$JUPITER_HW/$VENDOR/power"
fi
fi
}
case "$1" in
*) set_cpu
;;
esac

[/etc/pm/sleep.d/00-jupiter-restore] (755 root)
JUPITER_PATH="/usr/lib/jupiter/scripts"
JUPITER_VAR="/var/jupiter"
if [ ! -d "$JUPITER_VAR" ]; then
mkdir -p $JUPITER_VAR >/dev/null 2>&1 || true
chown -R root:jupiter $JUPITER_VAR >/dev/null 2>&1 || true
chmod 775 $JUPITER_VAR >/dev/null 2>&1 || true
chmod ug+s $JUPITER_VAR >/dev/null 2>&1 || true
setfacl -Rm g:jupiter:rwX,d:g:jupiter:rwX . >/dev/null 2>&1 || true
fi
case "$1" in
hibernate|suspend|sleep)
;;
thaw|resume)
USER=$(who | sed -n '/ (:0[\.0]*)$\| :0 /{s/ .*//p;q}')
if [ -e "$JUPITER_VAR/bt_saved" ]; then
sudo $JUPITER_PATH/bluetooth restore 2>/dev/null &
fi
if [ -e "$JUPITER_VAR/wifi_saved" ]; then
sudo $JUPITER_PATH/wifi restore silent 2>/dev/null
fi
if [ -e "$JUPITER_VAR/touchpad_saved" ]; then
su $USER -l -c "DISPLAY=:0.0 $JUPITER_PATH/touchpad restore silent" 2>/dev/null &
fi
;;
*) exit $NA
;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
# USB device 0x0bda:0x0179 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[ 24.851684] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[ 25.111584] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[ 26.018993] udevd[346]: renamed network interface eth0 to eth1
[ 29.316781] ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 29.667053] ADDRCONF(NETDEV_UP): eth1: link is not ready (repeated 2 times)
[ 34.864655] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 45.632045] wlan0: no IPv6 routers present

########## wireless info END ############

```

I am a non-techie playing it by ear and anything I learn about Linux is a welcome education. Your assistance would be must appreciated and any needed info will be forwarded ASAP.

Thank you!

Jim in NYC

---

### Post by chili555 on 2015-08-21
> grep: /etc/resolv.conf: No such file or directoryUh oh!!!

Please see post #6 here for a discussion of the remedy. I suspect that this may fix your issue, but if not, we'll dig deeper.

[http://ubuntuforums.org/showthread.php?t=2068299](http://ubuntuforums.org/showthread.php?t=2068299)

---

### Post by JGreenidge on 2015-08-22
> **chili555 said:**
> Uh oh!!!

Please see post #6 here for a discussion of the remedy. I suspect that this may fix your issue, but if not, we'll dig deeper.

[http://ubuntuforums.org/showthread.php?t=2068299](http://ubuntuforums.org/showthread.php?t=2068299)

Thank you! I'll check this out!

Jim in NYC

---

### Post by JGreenidge on 2015-08-31
> **chili555 said:**
> Uh oh!!!

Please see post #6 here for a discussion of the remedy. I suspect that this may fix your issue, but if not, we'll dig deeper.

[http://ubuntuforums.org/showthread.php?t=2068299](http://ubuntuforums.org/showthread.php?t=2068299)

Thank for the lead!

I mugged thru and gleaned what I can on the passage:

> 
Code:
nm-tool | grep -i dns
to see what DNS servers you are using."

Running the command you posted I get this result : DNS: 10.0.0.1 

Running this command " cat /run/resolvconf/resolv.conf " I get this output :
" cat: /run/resolvconf/resolv.conf: No such file or directory "

"Alternatively, you can manually create that file in the /etc directory with :
Code:
echo "nameserver xx.xx.xx.xx | sudo tee /etc/resolv.conf
echo "nameserver yy.yy.yy.yy | sudo tee -a /etc/resolv.conf
where xx... and yy... are your preferred primary and secondary DNS servers"

Tried running the above command with this input : echo "nameserver 10.0.0.1 | sudo tee /etc/resolv.conf" but it didn't do anything, then while looking at the command I see that you had only one " so I searched the internet and found that the other " had to be placed right after the IP address so I used the command "echo "nameserver 10.0.0.1" | sudo tee /etc/resolv.conf and that did it.

Problem solved my friend, no more errors when I run conky THANK YOUUUUUUUU !!!!!!!!

When I run " sudo cat /etc/resolv.conf " I get " nameserver 10.0.0.1 "



When I did the echo "nameserver 10.0.0.1 | sudo tee /etc/resolv.conf, my system actually started downloading full web pages for about three minutes then ceased, though the weather and Software Update Managers (monitoring and alerting that there are updates) continue to function normally. No further combinations of !0.xx.xx.xx seems to work.It's frustrating that there is such a seeming minor hang-up. Are there any further command line downloads I can do to diagnosis further?

Thanks for any hints!

Jim in NYC

---

### Post by chili555 on 2015-09-01
According to your wireless_info:> wlan0 Link encap:Ethernet HWaddr <MAC 'wlan0' [IF]> 
inet addr:192.168.1.170 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::<IP6 'wlan0' [IF]>/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:936 errors:0 dropped:108 overruns:0 frame:0
TX packets:427 errors:0 dropped:1 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:379495 (379.4 KB) TX bytes:57922 (57.9 KB)You are in the network of 192.168.1.1. I suggest you overwrite the setting you had previously:```
sudo -i
echo  "nameserver 192.168.1.1"  >  /etc/resolv.conf
exit
```Test:```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.google.com
```Better? It might take a reboot.

---

### Post by JGreenidge on 2015-09-02
> **chili555 said:**
> According to your wireless_info:You are in the network of 192.168.1.1. I suggest you overwrite the setting you had previously:```
sudo -i
echo  "nameserver 192.168.1.1"  >  /etc/resolv.conf
exit
```Test:```
ping -c3 192.168.1.1
ping -c3 8.8.8.8
ping -c3 www.google.com
```Better? It might take a reboot.

I'll get to work on this Chili, but first let me say that selfless guys like you are absolute bricks and life savers. I've previously spun my problems at Linux sites where they thumb their nose up at helping you out once they learn you're also appealing for help on other sites, as though they have some exclusive service contract helping just you out and to heck with cross-pollinating remedies with the greater Linux community, as though we couldn't do with a little team brainstorming to solve common problems for the Linux community as a whole. Thanks for your unselfish ego-free devotion!

Jim in NYC

---

### Post by chili555 on 2015-09-02
>  at Linux sites where they thumb their nose up at helping you When I started in Linux, way back when, that was my experience exactly. I always wondered why people join a forum and reply to posts to tell you *why they aren't going to answer!!!* I also vowed to not be that guy.

You just gave me the biggest paycheck this year. I enjoy doing what I do and your kind words make it much more than worthwhile. Thank you very much.

---

### Post by JGreenidge on 2015-09-03
> **chili555 said:**
> When I started in Linux, way back when, that was my experience exactly. I always wondered why people join a forum and reply to posts to tell you *why they aren't going to answer!!!* I also vowed to not be that guy.

You just gave me the biggest paycheck this year. I enjoy doing what I do and your kind words make it much more than worthwhile. Thank you very much.

Hey, your good Linux Samaritan more than deserve accolades! I hope other users appreciate that! I only regret that no Linux site seems to have a database off all discovered solutions to such problems which one can readily tap instead of this agony of treasure hunting like this. That's where your help shines!

```
jwg@q ~ $ sudo -i
[sudo] password for jwg: 
q ~ # echo  "nameserver 192.168.1.1"  >  /etc/resolv.conf
q ~ # exit
logout
jwg@q ~ $ ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=4.51 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=3.86 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=2.70 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 2.709/3.694/4.513/0.747 ms
jwg@q ~ $ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=58 time=59.3 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=58 time=10.3 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=58 time=9.44 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 9.449/26.393/59.360/23.314 ms
jwg@q ~ $ ping -c3 www.google.com
PING www.google.com (173.194.43.82) 56(84) bytes of data.
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=1 ttl=55 time=75.9 ms
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=2 ttl=55 time=24.6 ms
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=3 ttl=55 time=23.5 ms

--- www.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 23.584/41.392/75.976/24.458 ms
jwg@q ~ $

```
==========================================================================


Okay, I performed the operations you cited above and for several moments the ping route seemed to've worked with Opera doing some low-level page searching but then the works crashed when I moved up with Firefox or tried a Software Manager update operation. I was unable to repeat an even partially successful process again and often received a screen readout of:

```

jwg@q ~ $ sudo -i
[sudo] password for jwg: 
q ~ # echo  "nameserver 192.168.1.1"  >  /etc/resolv.conf
q ~ # exit
logout
jwg@q ~ $ test:
No command 'test:' found, did you mean:
 Command 'testr' from package 'testrepository' (universe)
 Command 'test' from package 'coreutils' (main)
test:: command not found
jwg@q ~ $  ping -c3 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_req=1 ttl=64 time=4.20 ms
64 bytes from 192.168.1.1: icmp_req=2 ttl=64 time=3.19 ms
64 bytes from 192.168.1.1: icmp_req=3 ttl=64 time=6.48 ms

--- 192.168.1.1 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 3.192/4.624/6.481/1.376 ms
jwg@q ~ $ ping -c3 8.8.8.8
PING 8.8.8.8 (8.8.8.8) 56(84) bytes of data.
64 bytes from 8.8.8.8: icmp_req=1 ttl=58 time=21.8 ms
64 bytes from 8.8.8.8: icmp_req=2 ttl=58 time=10.0 ms
64 bytes from 8.8.8.8: icmp_req=3 ttl=58 time=9.69 ms

--- 8.8.8.8 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 9.695/13.886/21.883/5.656 ms
jwg@q ~ $ ping -c3 www.google.com
PING www.google.com (63.117.14.23) 56(84) bytes of data.
64 bytes from 23.14.117.63.piscataway.google-ggc.verizon.com (63.117.14.23): icmp_req=2 ttl=59 time=11.8 ms
64 bytes from 23.14.117.63.piscataway.google-ggc.verizon.com (63.117.14.23): icmp_req=3 ttl=59 time=12.3 ms

--- www.google.com ping statistics ---
3 packets transmitted, 2 received, 33% packet loss, time 2008ms
rtt min/avg/max/mdev = 11.886/12.109/12.332/0.223 ms
```

============================================================================

My maybe simplistic non-techie view of this is that some kind of bad up/download data handling bug is in the works and ends up corrupting whatever routine is involved. I'm wondering is it creating a data file with bad permissions or can't be found for future access? Maybe a new nameserver address or name might do it, though when I first availed "10.0.0.1" instead of 192.168.1.1 in a previous remedy recommendation did work temporarily even though it looks apparent that it's no where a similar address. I am gleaning topics on dropped Realtek wifi links but I'm nonplussed over which of dozens and dozens solutions fits my shoe here. I'm wondering whether it might be limitations of the R31 laptop itself as well. Would a total wifi system purge and reinstall help and how would I do it? Should I repeat another diagnostic nm-tool "dump" via:

```
jwg@q ~ $ nm-tool | grep -i dns
    DNS:             192.168.1.1
jwg@q ~ $ 

jwg@q ~ $ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:00:E2:82:0C:20

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [FiOS-XU1SQ 1] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8188eu
  State:             connected
  Default:           yes
  HW Address:        00:65:0E:01:98:D7

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    TG1672G42:       Infra, 8C:09:F4:D0:94:40, Freq 2412 MHz, Rate 44 Mb/s, Strength 0 WPA2
    FiOS-DMJCP:      Infra, C8:A7:0A:A7:09:F2, Freq 2462 MHz, Rate 16 Mb/s, Strength 0 WPA2
    FiOS-DMJCP_2GEXT:Infra, A0:63:91:2D:29:10, Freq 2462 MHz, Rate 44 Mb/s, Strength 0 WPA2
    L5E02:           Infra, 00:26:62:F0:C3:6C, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WEP
    *FiOS-XU1SQ:     Infra, C8:A7:0A:BE:16:1A, Freq 2462 MHz, Rate 16 Mb/s, Strength 100 WPA2
    BNYJK:           Infra, 18:1B:EB:A7:72:CD, Freq 2412 MHz, Rate 2 Mb/s, Strength 0 WPA2

  IPv4 Settings:
    Address:         192.168.1.170
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


cat /run/resolvconf/resolv.conf
nm-tool | grep -i dns
sudo ln -st /etc /run/resovconf/resolv.conf
echo "nameserver 10.0.0.0" | sudo tee /etc/resolv.conf
echo "nameserver 10.0.0.0" | sudo tee -a /etc/resolv.conf
```

Thanks for any hints!

Jim in NYC

---

### Post by chili555 on 2015-09-03
> echo "nameserver 10.0.0.0" | sudo tee /etc/resolv.conf10.0.0.0 has nothing whatever to do with your network; nothing. I don't understand why you insist on undoing a successful result:> PING [www.google.com](www.google.com) (173.194.43.82) 56(84) bytes of data.
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=1 ttl=55 time=75.9 ms
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=2 ttl=55 time=24.6 ms
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=3 ttl=55 time=23.5 msIf you can reach Google, your network is operating correctly.> I was unable to repeat an even partially successful process again and often received a screen readout of:Of what? I see no screenshot or image.> it might be limitations of the R31 laptop itselfNot at all likely.> but then the works crashed when I moved up with Firefox or tried a Software Manager update operation. What crashed? What happened?

We will have to start again later.

---

### Post by chili555 on 2015-09-04
In an ideal, default install, /etc/resolv.conf is used to resolve (get it!!) names, which the internet can't use, into numbers, which it can. It does so by giving a nameserver address to which the system can refer to look up the number associated with any name. For example, you look for Google, and the nameserver replies that it can be found at 173.194.43.82. You can see the process when you ping:> [COLOR="#FF0000"]PING [www.google.com](www.google.com) (173.194.43.82) 56(84) bytes of data.[/COLOR]
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=1 ttl=55 time=75.9 ms
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=2 ttl=55 time=24.6 ms
64 bytes from yyz08s09-in-f18.1e100.net (173.194.43.82): icmp_req=3 ttl=55 time=23.5 msIn recent Ubuntu versions, we use dnsmasq. That means that we will keep a local directory of often used addresses. For example, I visit ubuntuforums.org a zillion times a day. My system keeps the numeric address on file so I am not slowed down a few milliseconds asking the lookup service for the data. I already have it. Please see:```
man dnsmasq
```> Dnsmasq  accepts  DNS  queries  and  either  answers them from a small, local, cache or forwards them to a  real,  recursive,  DNS  server. 

To do this, /etc/resolv.conf is actually a symbolic link to /run/resolvconf/resolv.conf.```
ls -al /etc/resolv.conf
lrwxrwxrwx 1 root root 29 Apr 29 12:03 /etc/resolv.conf -> ../run/resolvconf/resolv.conf

```However, in your case, the link was missing entirely:> ##### resolv.conf #######################

grep: /etc/resolv.conf: No such file or directory
At this point, we don't know whether /run/resolvconf/resolv.conf is missing or faulty. We don't know whether dnsmasq is working or not. We haven't gotten that far yet.

We do know that if we place a known working DNS nameserver into a new file /etc/resolv.conf, that name resolution will then be possible. How do we know a known working DNS nameserver? We know the address the ethernet uses:> IPv4 Settings:
Address: 192.168.1.170
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1

[COLOR="#FF0000"]DNS: 192.168.1.1[/COLOR]We then asked /etc/resolv.conf to use the same number and it worked. You pinged [www.google.com](www.google.com) and it resolved to 173.194.43.82 and you got ping returns. 

We can certainly sort out dnsmasq and the needed symbolic link, but for now, you are able to resolve and reach the outside world. I suggest we troubleshoot what happens after that. What crashed?> but then the works crashed when I moved up with Firefox or tried a Software Manager update operation.What exactly happened or didn't?

Are you still able to ping Google?

---

### Post by JGreenidge on 2015-09-05
> **chili555 said:**
> 

Are you still able to ping Google?

Yes, and I don't know what to add but that on boot-up and I command-line:

```
jwg@q ~ $ ping -c3 [www.google.com](www.google.com)
PING [www.google.com](www.google.com) (63.117.14.26) 56(84) bytes of data.
64 bytes from 26.14.117.63.piscataway.google-ggc.verizon.com (63.117.14.26): icmp_req=1 ttl=59 time=12.3 ms
64 bytes from 26.14.117.63.piscataway.google-ggc.verizon.com (63.117.14.26): icmp_req=2 ttl=59 time=16.7 ms
64 bytes from 26.14.117.63.piscataway.google-ggc.verizon.com (63.117.14.26): icmp_req=3 ttl=59 time=13.4 ms

--- [www.google.com](www.google.com) ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2002ms
rtt min/avg/max/mdev = 12.338/14.166/16.744/1.880 ms
jwg@q ~ $ 
jwg@q ~ $ nm-tool

NetworkManager Tool

State: connected (global)

- Device: eth1 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        00:00:E2:82:0C:20

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [FiOS-XU1SQ 1] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8188eu
  State:             connected
  Default:           yes
  HW Address:        00:65:0E:01:98:D7

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    FiOS-DMJCP:      Infra, C8:A7:0A:A7:09:F2, Freq 2412 MHz, Rate 16 Mb/s, Strength 0 WPA2
    BNYJK:           Infra, 18:1B:EB:A7:72:CD, Freq 2412 MHz, Rate 2 Mb/s, Strength 0 WPA2
    FiOS-DMJCP_2GEXT:Infra, A0:63:91:2D:29:10, Freq 2412 MHz, Rate 44 Mb/s, Strength 0 WPA2
    TG1672G42:       Infra, 8C:09:F4:D0:94:40, Freq 2412 MHz, Rate 44 Mb/s, Strength 0 WPA2
    TG1672GB2:       Infra, 40:70:09:4D:4F:B0, Freq 2412 MHz, Rate 44 Mb/s, Strength 0 WPA2
    L5E02:           Infra, 00:26:62:F0:C3:6C, Freq 2437 MHz, Rate 54 Mb/s, Strength 0 WEP
    *FiOS-XU1SQ:     Infra, C8:A7:0A:BE:16:1A, Freq 2462 MHz, Rate 16 Mb/s, Strength 100 WPA2
    6Q28R:           Infra, 00:7F:28:E4:E1:0E, Freq 2462 MHz, Rate 2 Mb/s, Strength 0 WPA2

  IPv4 Settings:
    Address:         192.168.1.170
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


jwg@q ~ $ 

jwg@q ~ $ dmesg|tail
[   38.129546] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[   38.129559] watchdog: failed to be enabled on some cpus
[   38.922397] init: plymouth-stop pre-start process (1297) terminated with status 1
[  532.470766] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[  532.470780] watchdog: failed to be enabled on some cpus
[  557.276267] Bluetooth: RFCOMM TTY layer initialized
[  557.276295] Bluetooth: RFCOMM socket layer initialized
[  557.276300] Bluetooth: RFCOMM ver 1.11
[  713.297405] atkbd serio0: Unknown key released (translated set 2, code 0xe0 on isa0060/serio0).
[  713.297419] atkbd serio0: Use 'setkeycodes e060 <keycode>' to make it known.
jwg@q ~ $ 

```

So Google is indeed pinged and as long as I leave things alone regarding network the menu bar does update weather and time and the Software Manager seem to update in background but soon as I load up a browser, within seconds of a window appearing the entire system freezes, cursor arrow and all. I think ideally I should run a full wifi diagnostics script like I previously had (wget -N -t 5 -T 10 [https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info](https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info) && \ chmod +x wireless-info && \ .wireless-info )    but lost to see what's the prelude that's tripping up these browsers so, so for now I'm trying to backtrace sites to find that script.

Jim in NYC

---

### Post by chili555 on 2015-09-05
I highly suspect the problem is not DNS but either Firefox or the wireless driver.

Does Firefox operate as expected with ethernet?

Are there any clues as to the crash here?```
dmesg | grep -e wlan -e r8188
```

---

### Post by JGreenidge on 2015-09-06
> **chili555 said:**
> I highly suspect the problem is not DNS but either Firefox or the wireless driver.

Does Firefox operate as expected with ethernet?

Are there any clues as to the crash here?```
dmesg | grep -e wlan -e r8188
```

jwg@q ~ $ dmesg | grep -e r8188
[  172.049976] usbcore: registered new interface driver r8188eu
jwg@q ~ $ 

No cable ethernet issues at all.  But with the wifi it's a total absolute freeze-crash once the browser starts poking into the net, give or take one or two minutes downloading any pages. With Firefox and Opera if I config them to not access home pages or Speed Dial at the get-go on boot-up nothing happens, only when they start accessing/downloading pages. It's puzzling to me that the system taps the web for weather app and software manager updates without any problem. I agree that it's driver thing somehow, so to double-chreck I'm still seeking the wifi set-up diagnostics script and looking to experiment with the much lighter Gnome browser to see if there's any difference.

Thanks for the assist!

Jim in NYC.

---

### Post by JGreenidge on 2015-09-07
Aplogies correction on last command line:

```
jwg@q ~ $ dmesg | grep -e wlan -e r8188
[   23.957839] usbcore: registered new interface driver r8188eu
[   28.095265] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.123669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.858366] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
jwg@q ~ $ dmesg | grep -e wlan -e r8188
[   23.957839] usbcore: registered new interface driver r8188eu
[   28.095265] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.123669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.858366] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  164.095641] udevd[542]: renamed network interface wlan0 to wlan1
[  165.457831] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  165.461311] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  169.377129] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
jwg@q ~ $ dmesg | grep -e wlan -e r8188
[   23.957839] usbcore: registered new interface driver r8188eu
[   28.095265] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   28.123669] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   33.858366] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  164.095641] udevd[542]: renamed network interface wlan0 to wlan1
[  165.457831] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  165.461311] ADDRCONF(NETDEV_UP): wlan1: link is not ready
[  169.377129] ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
jwg@q ~ $
```

---

### Post by chili555 on 2015-09-07
Why do we see wlan0 and wlan1? And by ?, I actually mean ????????

Is there an internal wireless that's conflicting with the USB dongle? We should either troubleshoot the internal and get it going properly and then set aside the USB, or else, we should blacklist the internal.

May we know more details?```
lspci -nn | grep 0280
```Why did you feel you needed a USB wireless instead of the internal?

In your original post, we see wlan0 and no sign of wlan1.  :confused:

---

### Post by JGreenidge on 2015-09-07
> **chili555 said:**
> Why do we see wlan0 and wlan1? And by ?, I actually mean ????????

Is there an internal wireless that's conflicting with the USB dongle? We should either troubleshoot the internal and get it going properly and then set aside the USB, or else, we should blacklist the internal.

May we know more details?```
lspci -nn | grep 0280
```Why did you feel you needed a USB wireless instead of the internal?

In your original post, we see wlan0 and no sign of wlan1.  :confused:

Thanks for your your patience!

There's no readout of lspci -nn | grep 0280 at all. Just an empty new line.

The old Thinkpad R31 didn't have an internal modem and Thinkpad.com says they weren't configured for any outside a "card slot" and I see no indication of any. As for the wlan0 and wlan1 thing I've totally no clue at all. I just copied and pasted all the results of the line commands I'm given. Lenovo.com folks with older machines are also very interested how this plays out but can offer no clues for upgrading such an old machine so, though some recommend trying the dongle out with a clean Mint install and see if there's any "network handling" difference from a Ubuntu Precise install. So I'm also web-hunting for any wifi diagnosis scripts or apps.

Thanks for your efforts!

Jim in NYC
.

---

### Post by chili555 on 2015-09-08
Let's have a look at:```
sudo lshw -C network
cat /etc/udev/rules.d/70-persistent-net.rules
```Aside from the rename to wlan1, we see nothing suspicious; we see nothing indicating a crash. 

Please detach the ethernet, get a wireless connection and run:```
dmesg
```Note the timestamp at the last line. Jot it down for future reference. Now run:```
firefox www.google.com
```Let is crash and then run again:```
dmesg
```Post all the lines *after* the timestamp you wrote down so we can see what happens...or not.

Here is a sample timestamp from my machine for example:```
<snip>
[223005.630045] wlan0: associate with xx:d7:19:41:54:xx (try 1/3)
[223005.633681] wlan0: RX AssocResp from xx:d7:19:41:54:xx (capab=0x1411 status=0 aid=2)
[COLOR="#FF0000"][223005.639465][/COLOR] wlan0: associated
```Yes; this machine has been booted up for 10+ days.

---

### Post by JGreenidge on 2015-09-08
This is the 1st raw output to rush to you -- I'll repeat it to find the time stamp shortly. Thanks!

Jim in NYC

```

==================================================================

jwg@q ~ $ sudo lshw -C network
[sudo] password for jwg: 
  *-network               
       description: Ethernet interface
       product: 82801CAM (ICH3) PRO/100 VE (LOM) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth1
       version: 42
       serial: 00:00:e2:82:0c:20
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 multicast=yes port=MII speed=10Mbit/s
       resources: irq:11 memory:80100000-80100fff ioport:7000(size=64)
  *-network
       description: Wireless interface
       physical id: 2
       bus info: usb@2:1
       logical name: wlan0
       serial: 00:65:0e:01:98:d7
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=r8188eu ip=192.168.1.170 multicast=yes wireless=IEEE 802.11bgn



jwg@q ~ $ cat /etc/udev/rules.d/70-persistent-net.rules
# This file was automatically generated by the /lib/udev/write_net_rules
# program, run by the persistent-net-generator.rules rules file.
#
# You can modify it, as long as you keep each rule on a single
# line, and change only the value of the NAME= key.

# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:16:d3:34:9c:1a", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (iwl3945)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:19:d2:75:d6:5f", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:1e.0/0000:01:08.0 (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:e2:82:0c:20", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

# USB device 0x0bda:0x0179 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:65:0e:01:98:d7", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

# USB device 0x0bda:0x0179 (usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:e0:4c:81:88:02", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan2"
jwg@q ~ $ 


jwg@q ~ $ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000002f7d0000 - 000000002f7e0000 (reserved)
[    0.000000]  BIOS-e820: 000000002f7e0000 - 000000002f7e8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f7e8000 - 000000002f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002f800000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: IBM 26563CF/26563CF, BIOS 1FETE8WW (3.080) 04/11/2003
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x2f7d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000002f7d0000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002f400000 page 2M
[    0.000000]  002f400000 - 002f7d0000 page 4k
[    0.000000] kernel direct mapping tables up to 2f7d0000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 2d6d1000 - 2e463000
[    0.000000] ACPI: RSDP 000fe030 00014 (v00 IBM   )
[    0.000000] ACPI: RSDT 2f7e0000 0002C (v01 IBM    Cnote2   00003080 IBM  00000001)
[    0.000000] ACPI: FACP 2f7e0054 00074 (v01 IBM    Cnote2   00003080 IBM  00000001)
[    0.000000] ACPI: DSDT 2f7e00cc 05C71 (v01   IBM    CNOTE2 00003080 MSFT 0100000C)
[    0.000000] ACPI: FACS 2f7e8000 00040
[    0.000000] ACPI: BOOT 2f7e002c 00028 (v01 IBM    Cnote2   00003080 IBM  00000001)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2f7d0000
[    0.000000]   low ram: 0 - 2f7d0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002f7d0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002f7d0
[    0.000000] On node 0 totalpages: 194399
[    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map ef1df200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1488 pages used for memmap
[    0.000000]   Normal zone: 188928 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xf108
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 30000000:cfff0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @eec00000 s31616 r0 d21632 u4194304
[    0.000000] pcpu-alloc: s31616 r0 d21632 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192879
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=4abe85b2-7e14-4b8d-a514-bdd0188c32e4 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3111936 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 743672k/778048k available (5627k kernel code, 33924k reserved, 2764k data, 712k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xeffd0000 - 0xff7fe000   ( 248 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xef7d0000   ( 759 MB)
[    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
[    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=ee808000 soft=ee80a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1129.781 MHz processor.
[    0.004005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2259.56 BogoMIPS (lpj=4519124)
[    0.004018] pid_max: default: 32768 minimum: 301
[    0.004077] Security Framework initialized
[    0.004134] AppArmor: AppArmor initialized
[    0.004139] Yama: becoming mindful.
[    0.004292] Mount-cache hash table entries: 512
[    0.004624] Initializing cgroup subsys cpuacct
[    0.004641] Initializing cgroup subsys memory
[    0.004661] Initializing cgroup subsys devices
[    0.004668] Initializing cgroup subsys freezer
[    0.004674] Initializing cgroup subsys blkio
[    0.004692] Initializing cgroup subsys perf_event
[    0.008074] mce: CPU supports 5 MCE banks
[    0.008195] SMP alternatives: switching to UP code
[    0.020317] Freeing SMP alternatives: 24k freed
[    0.020359] ACPI: Core revision 20110623
[    0.025600] ACPI: setting ELCR to 0200 (from 0800)
[    0.028044] ftrace: allocating 25954 entries in 51 pages
[    0.036305] weird, boot CPU (#0) not listed by the BIOS.
[    0.036318] SMP motherboard not detected.
[    0.036323] Local APIC not detected. Using dummy APIC emulation.
[    0.036328] SMP disabled
[    0.036333] Performance Events: 
[    0.036340] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.036344] no hardware sampling interrupt available.
[    0.036352] p6 PMU driver.
[    0.036364] ... version:                0
[    0.036368] ... bit width:              32
[    0.036372] ... generic registers:      2
[    0.036377] ... value mask:             00000000ffffffff
[    0.036381] ... max period:             000000007fffffff
[    0.036385] ... fixed-purpose events:   0
[    0.036389] ... event mask:             0000000000000003
[    0.037054] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[    0.037260] Brought up 1 CPUs
[    0.037269] Total of 1 processors activated (2259.56 BogoMIPS).
[    0.037922] devtmpfs: initialized
[    0.038270] EVM: security.selinux
[    0.038275] EVM: security.SMACK64
[    0.038279] EVM: security.capability
[    0.038449] PM: Registering ACPI NVS region at 2f7e8000 (98304 bytes)
[    0.042281] print_constraints: dummy: 
[    0.042335] RTC time: 12:54:24, date: 09/08/15
[    0.042455] NET: Registered protocol family 16
[    0.042791] EISA bus registered
[    0.042898] ACPI: bus type pci registered
[    0.044617] PCI: PCI BIOS revision 2.10 entry at 0xf0200, last bus=1
[    0.044622] PCI: Using configuration type 1 for base access
[    0.048120] bio: create slab <bio-0> at 0
[    0.048425] ACPI: Added _OSI(Module Device)
[    0.048433] ACPI: Added _OSI(Processor Device)
[    0.048438] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.048444] ACPI: Added _OSI(Processor Aggregator Device)
[    0.050030] ACPI: EC: Look up EC in DSDT
[    0.055786] ACPI: Interpreter enabled
[    0.055804] ACPI: (supports S0 S1 S3 S4 S5)
[    0.055861] ACPI: Using PIC for interrupt routing
[    0.088596] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.088920] ACPI: No dock devices found.
[    0.088927] HEST: Table not found.
[    0.088938] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.089176] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.089594] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.089602] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.089610] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.089617] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
[    0.089624] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
[    0.089631] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000dffff] (ignored)
[    0.089639] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff] (ignored)
[    0.089646] pci_root PNP0A03:00: host bridge window [mem 0x000e4000-0x000e7fff] (ignored)
[    0.089653] pci_root PNP0A03:00: host bridge window [mem 0x000e8000-0x000ebfff] (ignored)
[    0.089660] pci_root PNP0A03:00: host bridge window [mem 0x000ec000-0x000effff] (ignored)
[    0.089667] pci_root PNP0A03:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
[    0.089674] pci_root PNP0A03:00: host bridge window [mem 0x2f800000-0xffdfffff] (ignored)
[    0.089701] pci 0000:00:00.0: [8086:3575] type 0 class 0x000600
[    0.089773] pci 0000:00:02.0: [8086:3577] type 0 class 0x000300
[    0.089790] pci 0000:00:02.0: reg 10: [mem 0x98000000-0x9fffffff pref]
[    0.089801] pci 0000:00:02.0: reg 14: [mem 0x90100000-0x9017ffff]
[    0.089842] pci 0000:00:02.0: supports D1
[    0.089861] pci 0000:00:02.1: [8086:3577] type 0 class 0x000380
[    0.089876] pci 0000:00:02.1: reg 10: [mem 0x88000000-0x8fffffff pref]
[    0.089887] pci 0000:00:02.1: reg 14: [mem 0x80200000-0x8027ffff]
[    0.089927] pci 0000:00:02.1: supports D1
[    0.089981] pci 0000:00:1d.0: [8086:2482] type 0 class 0x000c03
[    0.090028] pci 0000:00:1d.0: reg 20: [io  0xa4a0-0xa4bf]
[    0.090071] pci 0000:00:1d.1: [8086:2484] type 0 class 0x000c03
[    0.090117] pci 0000:00:1d.1: reg 20: [io  0xa4e0-0xa4ff]
[    0.090160] pci 0000:00:1d.2: [8086:2487] type 0 class 0x000c03
[    0.090206] pci 0000:00:1d.2: reg 20: [io  0xa800-0xa81f]
[    0.090264] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.090316] pci 0000:00:1f.0: [8086:248c] type 0 class 0x000601
[    0.090387] pci 0000:00:1f.0: quirk: [io  0xf100-0xf17f] claimed by ICH4 ACPI/GPIO/TCO
[    0.090397] pci 0000:00:1f.0: quirk: [io  0xf200-0xf23f] claimed by ICH4 GPIO
[    0.090422] pci 0000:00:1f.1: [8086:248a] type 0 class 0x000101
[    0.090442] pci 0000:00:1f.1: reg 10: [io  0xa830-0xa837]
[    0.090456] pci 0000:00:1f.1: reg 14: [io  0xa848-0xa84b]
[    0.090469] pci 0000:00:1f.1: reg 18: [io  0xa860-0xa867]
[    0.090483] pci 0000:00:1f.1: reg 1c: [io  0xa878-0xa87b]
[    0.090496] pci 0000:00:1f.1: reg 20: [io  0xa890-0xa89f]
[    0.090510] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.090548] pci 0000:00:1f.3: [8086:2483] type 0 class 0x000c05
[    0.090594] pci 0000:00:1f.3: reg 20: [io  0x8000-0x801f]
[    0.090638] pci 0000:00:1f.5: [8086:2485] type 0 class 0x000401
[    0.090656] pci 0000:00:1f.5: reg 10: [io  0x9800-0x98ff]
[    0.090670] pci 0000:00:1f.5: reg 14: [io  0x9c00-0x9c3f]
[    0.090733] pci 0000:00:1f.6: [8086:2486] type 0 class 0x000703
[    0.090751] pci 0000:00:1f.6: reg 10: [io  0xa000-0xa0ff]
[    0.090765] pci 0000:00:1f.6: reg 14: [io  0xa400-0xa47f]
[    0.090857] pci 0000:01:08.0: [8086:1031] type 0 class 0x000200
[    0.090877] pci 0000:01:08.0: reg 10: [mem 0x80100000-0x80100fff]
[    0.090891] pci 0000:01:08.0: reg 14: [io  0x7000-0x703f]
[    0.090950] pci 0000:01:08.0: supports D1 D2
[    0.090956] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.090965] pci 0000:01:08.0: PME# disabled
[    0.090989] pci 0000:01:09.0: [104c:ac50] type 2 class 0x000607
[    0.091010] pci 0000:01:09.0: reg 10: [mem 0x38000000-0x38000fff]
[    0.091040] pci 0000:01:09.0: supports D1 D2
[    0.091046] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.091054] pci 0000:01:09.0: PME# disabled
[    0.091088] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.091099] pci 0000:00:1e.0:   bridge window [io  0x7000-0x7fff]
[    0.091108] pci 0000:00:1e.0:   bridge window [mem 0x80100000-0x801fffff]
[    0.091117] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.091125] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.091170] pci_bus 0000:02: [bus 02-05] partially hidden behind transparent bridge 0000:01 [bus 01-01]
[    0.091185] pci_bus 0000:00: on NUMA node 0
[    0.091197] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.091296] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.091458]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.097679] ACPI: PCI Interrupt Link [PILA] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.097893] ACPI: PCI Interrupt Link [PILB] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.098102] ACPI: PCI Interrupt Link [PILC] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.098310] ACPI: PCI Interrupt Link [PILD] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.098518] ACPI: PCI Interrupt Link [PILE] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.098726] ACPI: PCI Interrupt Link [PILF] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.098901] ACPI: PCI Interrupt Link [PILG] (IRQs 3 4 5 6 7 9 11 12 14 15) *0, disabled.
[    0.099076] ACPI: PCI Interrupt Link [PILH] (IRQs 3 4 5 6 7 9 11 12 14 15) *0, disabled.
[    0.099440] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.099462] vgaarb: loaded
[    0.099467] vgaarb: bridge control possible 0000:00:02.0
[    0.099819] i2c-core: driver [aat2870] using legacy suspend method
[    0.099825] i2c-core: driver [aat2870] using legacy resume method
[    0.100127] SCSI subsystem initialized
[    0.100325] libata version 3.00 loaded.
[    0.100482] usbcore: registered new interface driver usbfs
[    0.100517] usbcore: registered new interface driver hub
[    0.100600] usbcore: registered new device driver usb
[    0.100882] PCI: Using ACPI for IRQ routing
[    0.100896] PCI: pci_cache_line_size set to 32 bytes
[    0.101000] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.101007] reserve RAM buffer: 000000002f7d0000 - 000000002fffffff 
[    0.101314] NetLabel: Initializing
[    0.101320] NetLabel:  domain hash size = 128
[    0.101324] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.101354] NetLabel:  unlabeled traffic allowed by default
[    0.101569] Switching to clocksource pit
[    0.125546] AppArmor: AppArmor Filesystem Enabled
[    0.125679] pnp: PnP ACPI init
[    0.125744] ACPI: bus type pnp registered
[    0.126114] pnp 00:00: [bus 00-ff]
[    0.126125] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.126133] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.126139] pnp 00:00: [io  0x0d00-0xffff window]
[    0.126164] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.126170] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.126177] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.126184] pnp 00:00: [mem 0x000c8000-0x000dffff window]
[    0.126190] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.126197] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.126203] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.126210] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.126217] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.126223] pnp 00:00: [mem 0x2f800000-0xffdfffff window]
[    0.126494] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.127085] pnp 00:01: [io  0x0000-0x000f]
[    0.127092] pnp 00:01: [io  0x0081-0x008f]
[    0.127098] pnp 00:01: [io  0x0094-0x009f]
[    0.127104] pnp 00:01: [io  0x00c0-0x00df]
[    0.127111] pnp 00:01: [dma 4]
[    0.127215] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.127277] pnp 00:02: [io  0x0061]
[    0.127354] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.127397] pnp 00:03: [io  0x00f0-0x00ff]
[    0.127408] pnp 00:03: [irq 13]
[    0.127483] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.127524] pnp 00:04: [io  0x0070-0x0073]
[    0.127531] pnp 00:04: [irq 8]
[    0.127610] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.130295] pnp 00:05: [io  0x0060]
[    0.130301] pnp 00:05: [io  0x0064]
[    0.130308] pnp 00:05: [irq 1]
[    0.130446] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.133507] pnp 00:06: [io  0x03bc-0x03bf]
[    0.133515] pnp 00:06: [irq 7]
[    0.133660] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.136524] pnp 00:07: [io  0x03f0-0x03f5]
[    0.136531] pnp 00:07: [io  0x03f7]
[    0.136537] pnp 00:07: [irq 6]
[    0.136544] pnp 00:07: [dma 2]
[    0.136658] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.136862] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (disabled)
[    0.137105] pnp 00:09: Plug and Play ACPI device, IDs IBM0071 PNP0511 (disabled)
[    0.137149] pnp 00:0a: [irq 12]
[    0.137232] pnp 00:0a: Plug and Play ACPI device, IDs IBM3780 PNP0f13 (active)
[    0.145456] pnp 00:0b: [io  0xf100-0xf16f]
[    0.145463] pnp 00:0b: [io  0xf178-0xf17f]
[    0.145469] pnp 00:0b: [io  0xf200-0xf23f]
[    0.145475] pnp 00:0b: [io  0x002e-0x002f]
[    0.145487] pnp 00:0b: [io  0x0380-0x038f]
[    0.145493] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.145499] pnp 00:0b: [io  0x0580-0x0587]
[    0.145505] pnp 00:0b: [mem 0x00000000-0x000009ff]
[    0.145511] pnp 00:0b: [mem 0x00000f00-0x00000fff]
[    0.145518] pnp 00:0b: [mem 0xfff80000-0xffffffff]
[    0.145524] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.145530] pnp 00:0b: [mem 0xfff00000-0xfff7ffff]
[    0.145536] pnp 00:0b: [mem 0x00100000-0x00ffffff]
[    0.145542] pnp 00:0b: [mem 0x01000000-0x2f7fffff]
[    0.145549] pnp 00:0b: [mem 0xfebffc00-0xfebfffff]
[    0.145593] pnp 00:0b: disabling [io  0xf100-0xf16f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf100-0xf17f]
[    0.145603] pnp 00:0b: disabling [io  0xf178-0xf17f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf100-0xf17f]
[    0.145760] system 00:0b: [io  0xf200-0xf23f] has been reserved
[    0.145769] system 00:0b: [io  0x0380-0x038f] has been reserved
[    0.145777] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.145785] system 00:0b: [io  0x0580-0x0587] has been reserved
[    0.145793] system 00:0b: [mem 0x00000000-0x000009ff] could not be reserved
[    0.145802] system 00:0b: [mem 0x00000f00-0x00000fff] could not be reserved
[    0.145811] system 00:0b: [mem 0xfff80000-0xffffffff] could not be reserved
[    0.145820] system 00:0b: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.145828] system 00:0b: [mem 0xfff00000-0xfff7ffff] has been reserved
[    0.145836] system 00:0b: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.145844] system 00:0b: [mem 0x01000000-0x2f7fffff] could not be reserved
[    0.145853] system 00:0b: [mem 0xfebffc00-0xfebfffff] has been reserved
[    0.145862] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.148655] pnp: PnP ACPI: found 12 devices
[    0.148661] ACPI: ACPI bus type pnp unregistered
[    0.148671] PnPBIOS: Disabled by ACPI PNP
[    0.188692] Switching to clocksource acpi_pm
[    0.188772] PCI: max bus depth: 2 pci_try_num: 3
[    0.188834] pci 0000:00:1f.1: BAR 5: assigned [mem 0x30000000-0x300003ff]
[    0.188850] pci 0000:00:1f.1: BAR 5: set to [mem 0x30000000-0x300003ff] (PCI address [0x30000000-0x300003ff])
[    0.188861] pci 0000:00:1e.0: BAR 15: assigned [mem 0x34000000-0x37ffffff pref]
[    0.188873] pci 0000:01:09.0: BAR 16: assigned [mem 0x3c000000-0x3fffffff]
[    0.188881] pci 0000:01:09.0: BAR 15: assigned [mem 0x34000000-0x37ffffff pref]
[    0.188889] pci 0000:01:09.0: BAR 14: assigned [io  0x7400-0x74ff]
[    0.188897] pci 0000:01:09.0: BAR 13: assigned [io  0x7800-0x78ff]
[    0.188904] pci 0000:01:09.0: CardBus bridge to [bus 02-05]
[    0.188911] pci 0000:01:09.0:   bridge window [io  0x7800-0x78ff]
[    0.188920] pci 0000:01:09.0:   bridge window [io  0x7400-0x74ff]
[    0.188928] pci 0000:01:09.0:   bridge window [mem 0x34000000-0x37ffffff pref]
[    0.188937] pci 0000:01:09.0:   bridge window [mem 0x3c000000-0x3fffffff]
[    0.188946] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.188954] pci 0000:00:1e.0:   bridge window [io  0x7000-0x7fff]
[    0.188963] pci 0000:00:1e.0:   bridge window [mem 0x80100000-0x801fffff]
[    0.188972] pci 0000:00:1e.0:   bridge window [mem 0x34000000-0x37ffffff pref]
[    0.189001] pci 0000:00:1e.0: setting latency timer to 64
[    0.189408] ACPI: PCI Interrupt Link [PILB] enabled at IRQ 11
[    0.189417] PCI: setting IRQ 11 as level-triggered
[    0.189428] pci 0000:01:09.0: PCI INT A -> Link[PILB] -> GSI 11 (level, low) -> IRQ 11
[    0.189442] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.189449] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.189457] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.189463] pci_bus 0000:01: resource 1 [mem 0x80100000-0x801fffff]
[    0.189470] pci_bus 0000:01: resource 2 [mem 0x34000000-0x37ffffff pref]
[    0.189477] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.189483] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
[    0.189490] pci_bus 0000:02: resource 0 [io  0x7800-0x78ff]
[    0.189496] pci_bus 0000:02: resource 1 [io  0x7400-0x74ff]
[    0.189503] pci_bus 0000:02: resource 2 [mem 0x34000000-0x37ffffff pref]
[    0.189509] pci_bus 0000:02: resource 3 [mem 0x3c000000-0x3fffffff]
[    0.189655] NET: Registered protocol family 2
[    0.189846] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.190684] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.196167] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.198911] TCP: Hash tables configured (established 131072 bind 65536)
[    0.198922] TCP reno registered
[    0.198945] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.199044] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.199479] NET: Registered protocol family 1
[    0.199553] pci 0000:00:02.0: Boot video device
[    0.200112] ACPI: PCI Interrupt Link [PILA] enabled at IRQ 11
[    0.200131] pci 0000:00:1d.0: PCI INT A -> Link[PILA] -> GSI 11 (level, low) -> IRQ 11
[    0.200163] pci 0000:00:1d.0: PCI INT A disabled
[    0.200461] ACPI: PCI Interrupt Link [PILD] enabled at IRQ 11
[    0.200471] pci 0000:00:1d.1: PCI INT B -> Link[PILD] -> GSI 11 (level, low) -> IRQ 11
[    0.200492] pci 0000:00:1d.1: PCI INT B disabled
[    0.200750] ACPI: PCI Interrupt Link [PILC] enabled at IRQ 11
[    0.200759] pci 0000:00:1d.2: PCI INT C -> Link[PILC] -> GSI 11 (level, low) -> IRQ 11
[    0.200779] pci 0000:00:1d.2: PCI INT C disabled
[    0.200848] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    0.200868] PCI: CLS 32 bytes, default 32
[    0.201071] Simple Boot Flag at 0x41 set to 0x1
[    0.201952] audit: initializing netlink socket (disabled)
[    0.201988] type=2000 audit(1441716864.196:1): initialized
[    0.250233] Trying to unpack rootfs image as initramfs...
[    0.320881] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.360621] VFS: Disk quotas dquot_6.5.2
[    0.360826] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.368917] fuse init (API version 7.17)
[    0.369348] msgmni has been set to 1452
[    0.377408] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.384503] io scheduler noop registered
[    0.384518] io scheduler deadline registered
[    0.384594] io scheduler cfq registered (default)
[    0.385062] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.385149] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.389301] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.400713] ACPI: AC Adapter [AC] (on-line)
[    0.404691] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.404714] ACPI: Sleep Button [SLPB]
[    0.404900] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.405121] ACPI: Lid Switch [LID]
[    0.405261] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.405274] ACPI: Power Button [PWRF]
[    0.413456] Marking TSC unstable due to TSC halts in idle
[    0.413480] ACPI: acpi_idle registered with cpuidle
[    0.480410] thermal LNXTHERM:00: registered as thermal_zone0
[    0.480424] ACPI: Thermal Zone [THR1] (67 C)
[    0.508577] thermal LNXTHERM:01: registered as thermal_zone1
[    0.508589] ACPI: Thermal Zone [THR2] (40 C)
[    0.508745] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.508790] ACPI: Battery Slot [BAT0] (battery present)
[    0.509021] ERST: Table is not found!
[    0.509028] GHES: HEST is not enabled!
[    0.509342] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.525384] isapnp: Scanning for PnP cards...
[    0.531883] serial 00:08: [io  0x03f8-0x03ff]
[    0.531974] serial 00:08: [irq 3]
[    0.532735] serial 00:08: activated
[    0.553238] 00:08: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A
[    0.636883] serial 0000:00:1f.6: PCI INT B -> Link[PILB] -> GSI 11 (level, low) -> IRQ 11
[    0.636925] serial 0000:00:1f.6: PCI INT B disabled
[    0.637160] ACPI: Battery Slot [BAT0] (battery present)
[    0.637426] Linux agpgart interface v0.103
[    0.637576] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    0.637621] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.638010] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.638409] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0x98000000
[    0.646300] brd: module loaded
[    0.653169] loop: module loaded
[    0.653668] ata_piix 0000:00:1f.1: version 2.13
[    0.653705] ata_piix 0000:00:1f.1: can't derive routing for PCI INT A
[    0.653810] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.654765] scsi0 : ata_piix
[    0.660509] scsi1 : ata_piix
[    0.662288] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xa890 irq 14
[    0.662298] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xa898 irq 15
[    0.663804] Fixed MDIO Bus: probed
[    0.663868] tun: Universal TUN/TAP device driver, 1.6
[    0.663873] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.664360] PPP generic driver version 2.4.2
[    0.664673] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.664733] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.664770] uhci_hcd: USB Universal Host Controller Interface driver
[    0.664877] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[PILA] -> GSI 11 (level, low) -> IRQ 11
[    0.664903] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.664910] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.665034] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.665087] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000a4a0
[    0.665502] hub 1-0:1.0: USB hub found
[    0.665516] hub 1-0:1.0: 2 ports detected
[    0.665698] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[PILD] -> GSI 11 (level, low) -> IRQ 11
[    0.665720] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.665727] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.665871] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    0.665912] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000a4e0
[    0.666278] hub 2-0:1.0: USB hub found
[    0.666291] hub 2-0:1.0: 2 ports detected
[    0.666463] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[PILC] -> GSI 11 (level, low) -> IRQ 11
[    0.666485] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.666492] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.666639] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    0.666682] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000a800
[    0.667069] hub 3-0:1.0: USB hub found
[    0.667082] hub 3-0:1.0: 2 ports detected
[    0.667395] usbcore: registered new interface driver libusual
[    0.667539] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.669815] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.669843] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.672976] mousedev: PS/2 mouse device common for all mice
[    0.673437] rtc_cmos 00:04: RTC can wake from S4
[    0.673666] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.673702] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    0.673938] device-mapper: uevent: version 1.0.3
[    0.676328] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.676510] EISA: Probing bus 0 at eisa.0
[    0.676556] Cannot allocate resource for EISA slot 7
[    0.676562] Cannot allocate resource for EISA slot 8
[    0.676567] EISA: Detected 0 cards.
[    0.676597] cpufreq-nforce2: No nForce2 chipset.
[    0.676702] cpuidle: using governor ladder
[    0.676841] cpuidle: using governor menu
[    0.676847] EFI Variables Facility v0.08 2004-May-17
[    0.677594] TCP cubic registered
[    0.678033] NET: Registered protocol family 10
[    0.679636] NET: Registered protocol family 17
[    0.679703] Registering the dns_resolver key type
[    0.679782] Using IPI No-Shortcut mode
[    0.682975] PM: Hibernation image not present or could not be loaded.
[    0.683025] registered taskstats version 1
[    0.824411] ata2.01: NODEV after polling detection
[    0.824616] ata1.00: ATA-5: IC25N020ATCS04-0, CA2OA71A, max UDMA/100
[    0.824625] ata1.00: 39070080 sectors, multi 16: LBA 
[    0.827925] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.833527] ata2.00: ATAPI: UJDA745 DVD/CDRW, 1.00, max UDMA/33
[    0.833993] ata1.00: configured for UDMA/100
[    0.957114] ata2.00: configured for UDMA/33
[    1.100081] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    1.156080] isapnp: No Plug & Play device found
[    1.156582] scsi 0:0:0:0: Direct-Access     ATA      IC25N020ATCS04-0 CA2O PQ: 0 ANSI: 5
[    1.157075] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.157592] sd 0:0:0:0: [sda] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.157737] sd 0:0:0:0: [sda] Write Protect is off
[    1.157745] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.157803] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.161001] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[    1.165549] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.165565] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.166023] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.166420] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.217561]  sda: sda1 sda2 sda3
[    1.218756] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.626417] Freeing initrd memory: 13896k freed
[    1.695092]   Magic number: 15:780:935
[    1.695360] rtc_cmos 00:04: setting system clock to 2015-09-08 12:54:25 UTC (1441716865)
[    1.695415] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.695420] EDD information not available.
[    1.695837] Freeing unused kernel memory: 712k freed
[    1.698051] Write protecting the kernel text: 5628k
[    1.698159] Write protecting the kernel read-only data: 2324k
[    1.763374] udevd[86]: starting version 175
[    2.277777] Floppy drive(s): fd0 is 1.44M
[    2.302838] FDC 0 is a National Semiconductor PC87306
[    2.447795] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.447806] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.505062] ACPI: PCI Interrupt Link [PILE] enabled at IRQ 11
[    2.505085] e100 0000:01:08.0: PCI INT A -> Link[PILE] -> GSI 11 (level, low) -> IRQ 11
[    2.593336] e100 0000:01:08.0: PME# disabled
[    2.594752] e100 0000:01:08.0: eth0: addr 0x80100000, irq 11, MAC addr 00:00:e2:82:0c:20
[    2.832542] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   19.174228] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   19.395595] udevd[320]: starting version 175
[   19.569796] Adding 8188k swap on /dev/sda3.  Priority:-1 extents:1 across:8188k 
[   19.787723] lp: driver loaded but no devices found
[   19.924983] ------------[ cut here ]------------
[   19.925020] WARNING: at /build/buildd/linux-3.2.0/fs/proc/generic.c:808 remove_proc_entry+0x1ad/0x200()
[   19.925027] Hardware name: 26563CF
[   19.925031] name 'r8168'
[   19.925035] Modules linked in: r8168(O+) lp parport e100 floppy
[   19.925054] Pid: 331, comm: modprobe Tainted: G           O 3.2.0-23-generic #36-Ubuntu
[   19.925060] Call Trace:
[   19.925080]  [<c104b182>] warn_slowpath_common+0x72/0xa0
[   19.925089]  [<c118624d>] ? remove_proc_entry+0x1ad/0x200
[   19.925096]  [<c118624d>] ? remove_proc_entry+0x1ad/0x200
[   19.925105]  [<c104b253>] warn_slowpath_fmt+0x33/0x40
[   19.925113]  [<c118624d>] remove_proc_entry+0x1ad/0x200
[   19.925122]  [<efff8000>] ? 0xefff7fff
[   19.925146]  [<efff8013>] rtl8168_init_module+0x13/0x1000 [r8168]
[   19.925155]  [<c1001125>] do_one_initcall+0x35/0x170
[   19.925162]  [<efff8000>] ? 0xefff7fff
[   19.925173]  [<c108651d>] sys_init_module+0xad/0x210
[   19.925188]  [<c1130df3>] ? sys_close+0x73/0xc0
[   19.925200]  [<c1576ed4>] syscall_call+0x7/0xb
[   19.925212]  [<c1570000>] ? encode+0x26/0x2b
[   19.925218] ---[ end trace f7bc2cdf902f6683 ]---
[   20.148779] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   20.800386] [Firmware Bug]: ACPI(VGA0) defines _DOD but not _DOS
[   20.834724] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input4
[   20.835147] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[   21.186201] [drm] Initialized drm 1.1.0 20060810
[   21.448951] Bluetooth: Core ver 2.16
[   21.449027] NET: Registered protocol family 31
[   21.449033] Bluetooth: HCI device and connection manager initialized
[   21.449042] Bluetooth: HCI socket layer initialized
[   21.449047] Bluetooth: L2CAP socket layer initialized
[   21.449062] Bluetooth: SCO socket layer initialized
[   21.588102] ppdev: user-space parallel port driver
[   21.593978] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.593989] Bluetooth: BNEP filters: protocol multicast
[   21.619200] parport_pc 00:06: reported by Plug and Play ACPI
[   21.619256] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   21.717986] lp0: using parport0 (interrupt-driven).
[   21.817019] Non-volatile memory driver v1.3
[   22.045590] i915 0000:00:02.0: PCI INT A -> Link[PILA] -> GSI 11 (level, low) -> IRQ 11
[   22.045606] i915 0000:00:02.0: setting latency timer to 64
[   22.120846] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   22.120857] [drm] Driver supports precise vblank timestamp query.
[   22.128782] irda_init()
[   22.128829] NET: Registered protocol family 23
[   22.136164] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   22.149041] intel_rng: FWH not detected
[   22.171510] nsc-ircc 00:09: [io  0x02f8-0x02ff]
[   22.171628] nsc-ircc 00:09: [irq 4]
[   22.171637] nsc-ircc 00:09: [dma 1]
[   22.179352] nsc-ircc 00:09: activated
[   22.179371] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 4 ; dma 1.
[   22.187340] nsc-ircc, chip->init
[   22.187360] nsc-ircc, Found chip at base=0x02e
[   22.187387] nsc-ircc, driver loaded (Dag Brattli)
[   22.205735] IrDA: Registered device irda0
[   22.205746] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   22.459323] [drm] initialized overlay support
[   22.673536] psmouse serio1: hgpk: ID: 10 00 64
[   22.890655] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[   22.988599] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   23.002061] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input5
[   23.157707] EEPROM ID = 0x8129
[   23.262367] usbcore: registered new interface driver r8188eu
[   23.318171] fbcon: inteldrmfb (fb0) is primary device
[   23.320465] Console: switching to colour frame buffer device 128x48
[   23.320547] fb0: inteldrmfb frame buffer device
[   23.320552] drm: registered panic notifier
[   23.320628] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   23.320900] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.551203] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   23.551215] thinkpad_acpi: http://ibm-acpi.sf.net/
[   23.551221] thinkpad_acpi: ThinkPad BIOS 1FETE8WW (3.080), EC unknown
[   23.551226] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
[   23.551231] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[   23.554029] yenta_cardbus 0000:01:09.0: CardBus bridge found [1014:1017]
[   23.554054] yenta_cardbus 0000:01:09.0: Using CSCINT to route CSC interrupts to PCI
[   23.554060] yenta_cardbus 0000:01:09.0: Routing CardBus interrupts to PCI
[   23.554069] yenta_cardbus 0000:01:09.0: TI: mfunc 0x01111c02, devctl 0x64
[   23.565716] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   23.592166] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   23.593451] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   23.797412] yenta_cardbus 0000:01:09.0: ISA IRQ mask 0x0438, PCI irq 11
[   23.797423] yenta_cardbus 0000:01:09.0: Socket status: 30000006
[   23.797432] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   23.797455] yenta_cardbus 0000:01:09.0: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[   23.797465] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: excluding 0x7000-0x703f 0x7400-0x74ff
[   23.824674] snd_intel8x0 0000:00:1f.5: PCI INT B -> Link[PILB] -> GSI 11 (level, low) -> IRQ 11
[   23.824714] snd_intel8x0 0000:00:1f.5: setting latency timer to 64
[   23.846737]  0x7800-0x78ff
[   23.922438] yenta_cardbus 0000:01:09.0: pcmcia: parent PCI bridge window: [mem 0x80100000-0x801fffff]
[   23.922452] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80100000-0x801fffff: excluding 0x80100000-0x8010ffff
[   23.922479] yenta_cardbus 0000:01:09.0: pcmcia: parent PCI bridge window: [mem 0x34000000-0x37ffffff pref]
[   23.922487] pcmcia_socket pcmcia_socket0: cs: memory probe 0x34000000-0x37ffffff: excluding 0x34000000-0x37ffffff
[   24.106782] udevd[343]: renamed network interface eth0 to eth1
[   24.303153] init: failsafe main process (623) killed by TERM signal
[   24.549463] intel8x0_measure_ac97_clock: measured 165455 usecs (7946 samples)
[   24.549474] intel8x0: clocking to 48000
[   25.847834] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377 0x380-0x38f
[   25.854687] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   25.855402] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   25.856004] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   25.897048] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xf0000-0xfffff
[   25.897120] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   25.897184] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   25.897249] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   26.108341] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1
[   27.544538] MAC Address = 00:65:0e:01:98:d7
[   27.582316] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.608602] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.757540] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   27.766490] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   29.451566] init: lightdm main process (996) killed by TERM signal
[   32.361019] R8188EU: INFO assoc success
[   32.361601] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   36.859098] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[   36.859111] watchdog: failed to be enabled on some cpus
[   37.747260] init: plymouth-stop pre-start process (1300) terminated with status 1
[   81.359717] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[   81.359734] watchdog: failed to be enabled on some cpus
[  104.602804] Bluetooth: RFCOMM TTY layer initialized
[  104.602827] Bluetooth: RFCOMM socket layer initialized
[  104.602832] Bluetooth: RFCOMM ver 1.11
jwg@q ~ $ 


======================================= AFTER FIREFOX - GOGGLE CRASH ======================================

jwg@q ~ $ dmesg
[    0.000000] Initializing cgroup subsys cpuset
[    0.000000] Initializing cgroup subsys cpu
[    0.000000] Linux version 3.2.0-23-generic (buildd@palmer) (gcc version 4.6.3 (Ubuntu/Linaro 4.6.3-1ubuntu4) ) #36-Ubuntu SMP Tue Apr 10 20:41:14 UTC 2012 (Ubuntu 3.2.0-23.36-generic 3.2.14)
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   NSC Geode by NSC
[    0.000000]   Cyrix CyrixInstead
[    0.000000]   Centaur CentaurHauls
[    0.000000]   Transmeta GenuineTMx86
[    0.000000]   Transmeta TransmetaCPU
[    0.000000]   UMC UMC UMC UMC
[    0.000000] BIOS-provided physical RAM map:
[    0.000000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[    0.000000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[    0.000000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[    0.000000]  BIOS-e820: 0000000000100000 - 000000002f7d0000 (usable)
[    0.000000]  BIOS-e820: 000000002f7d0000 - 000000002f7e0000 (reserved)
[    0.000000]  BIOS-e820: 000000002f7e0000 - 000000002f7e8000 (ACPI data)
[    0.000000]  BIOS-e820: 000000002f7e8000 - 000000002f800000 (ACPI NVS)
[    0.000000]  BIOS-e820: 000000002f800000 - 0000000030000000 (reserved)
[    0.000000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[    0.000000] Notice: NX (Execute Disable) protection missing in CPU!
[    0.000000] NX (Execute Disable) protection: approximated by x86 segment limits
[    0.000000] DMI 2.3 present.
[    0.000000] DMI: IBM 26563CF/26563CF, BIOS 1FETE8WW (3.080) 04/11/2003
[    0.000000] e820 update range: 0000000000000000 - 0000000000010000 (usable) ==> (reserved)
[    0.000000] e820 remove range: 00000000000a0000 - 0000000000100000 (usable)
[    0.000000] last_pfn = 0x2f7d0 max_arch_pfn = 0x100000
[    0.000000] MTRR default type: uncachable
[    0.000000] MTRR fixed ranges enabled:
[    0.000000]   00000-9FFFF write-back
[    0.000000]   A0000-BFFFF uncachable
[    0.000000]   C0000-CBFFF write-protect
[    0.000000]   CC000-EFFFF uncachable
[    0.000000]   F0000-FFFFF write-protect
[    0.000000] MTRR variable ranges enabled:
[    0.000000]   0 base 000000000 mask FE0000000 write-back
[    0.000000]   1 base 020000000 mask FF0000000 write-back
[    0.000000]   2 disabled
[    0.000000]   3 disabled
[    0.000000]   4 disabled
[    0.000000]   5 disabled
[    0.000000]   6 disabled
[    0.000000]   7 disabled
[    0.000000] PAT not supported by CPU.
[    0.000000] initial memory mapped : 0 - 01c00000
[    0.000000] Base memory trampoline at [c009b000] 9b000 size 16384
[    0.000000] init_memory_mapping: 0000000000000000-000000002f7d0000
[    0.000000]  0000000000 - 0000400000 page 4k
[    0.000000]  0000400000 - 002f400000 page 2M
[    0.000000]  002f400000 - 002f7d0000 page 4k
[    0.000000] kernel direct mapping tables up to 2f7d0000 @ 1bfb000-1c00000
[    0.000000] RAMDISK: 2d6d1000 - 2e463000
[    0.000000] ACPI: RSDP 000fe030 00014 (v00 IBM   )
[    0.000000] ACPI: RSDT 2f7e0000 0002C (v01 IBM    Cnote2   00003080 IBM  00000001)
[    0.000000] ACPI: FACP 2f7e0054 00074 (v01 IBM    Cnote2   00003080 IBM  00000001)
[    0.000000] ACPI: DSDT 2f7e00cc 05C71 (v01   IBM    CNOTE2 00003080 MSFT 0100000C)
[    0.000000] ACPI: FACS 2f7e8000 00040
[    0.000000] ACPI: BOOT 2f7e002c 00028 (v01 IBM    Cnote2   00003080 IBM  00000001)
[    0.000000] 0MB HIGHMEM available.
[    0.000000] 759MB LOWMEM available.
[    0.000000]   mapped low ram: 0 - 2f7d0000
[    0.000000]   low ram: 0 - 2f7d0000
[    0.000000] Zone PFN ranges:
[    0.000000]   DMA      0x00000010 -> 0x00001000
[    0.000000]   Normal   0x00001000 -> 0x0002f7d0
[    0.000000]   HighMem  empty
[    0.000000] Movable zone start PFN for each node
[    0.000000] early_node_map[2] active PFN ranges
[    0.000000]     0: 0x00000010 -> 0x0000009f
[    0.000000]     0: 0x00000100 -> 0x0002f7d0
[    0.000000] On node 0 totalpages: 194399
[    0.000000] free_area_init_node: node 0, pgdat c18258c0, node_mem_map ef1df200
[    0.000000]   DMA zone: 32 pages used for memmap
[    0.000000]   DMA zone: 0 pages reserved
[    0.000000]   DMA zone: 3951 pages, LIFO batch:0
[    0.000000]   Normal zone: 1488 pages used for memmap
[    0.000000]   Normal zone: 188928 pages, LIFO batch:31
[    0.000000] Using APIC driver default
[    0.000000] ACPI: PM-Timer IO Port: 0xf108
[    0.000000] SMP: Allowing 1 CPUs, 0 hotplug CPUs
[    0.000000] Local APIC disabled by BIOS -- you can enable it with "lapic"
[    0.000000] APIC: disable apic facility
[    0.000000] APIC: switched to apic NOOP
[    0.000000] nr_irqs_gsi: 16
[    0.000000] PM: Registered nosave memory: 000000000009f000 - 00000000000a0000
[    0.000000] PM: Registered nosave memory: 00000000000a0000 - 00000000000f0000
[    0.000000] PM: Registered nosave memory: 00000000000f0000 - 0000000000100000
[    0.000000] Allocating PCI resources starting at 30000000 (gap: 30000000:cfff0000)
[    0.000000] Booting paravirtualized kernel on bare hardware
[    0.000000] setup_percpu: NR_CPUS:8 nr_cpumask_bits:8 nr_cpu_ids:1 nr_node_ids:1
[    0.000000] PERCPU: Embedded 13 pages/cpu @eec00000 s31616 r0 d21632 u4194304
[    0.000000] pcpu-alloc: s31616 r0 d21632 u4194304 alloc=1*4194304
[    0.000000] pcpu-alloc: [0] 0 
[    0.000000] Built 1 zonelists in Zone order, mobility grouping on.  Total pages: 192879
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.2.0-23-generic root=UUID=4abe85b2-7e14-4b8d-a514-bdd0188c32e4 ro quiet splash vt.handoff=7
[    0.000000] PID hash table entries: 4096 (order: 2, 16384 bytes)
[    0.000000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[    0.000000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[    0.000000] Initializing CPU#0
[    0.000000] allocated 3111936 bytes of page_cgroup
[    0.000000] please try 'cgroup_disable=memory' option if you don't want memory cgroups
[    0.000000] Initializing HighMem for node 0 (00000000:00000000)
[    0.000000] Memory: 743672k/778048k available (5627k kernel code, 33924k reserved, 2764k data, 712k init, 0k highmem)
[    0.000000] virtual kernel memory layout:
[    0.000000]     fixmap  : 0xfff16000 - 0xfffff000   ( 932 kB)
[    0.000000]     pkmap   : 0xff800000 - 0xffc00000   (4096 kB)
[    0.000000]     vmalloc : 0xeffd0000 - 0xff7fe000   ( 248 MB)
[    0.000000]     lowmem  : 0xc0000000 - 0xef7d0000   ( 759 MB)
[    0.000000]       .init : 0xc1833000 - 0xc18e5000   ( 712 kB)
[    0.000000]       .data : 0xc157ef84 - 0xc1832080   (2764 kB)
[    0.000000]       .text : 0xc1000000 - 0xc157ef84   (5627 kB)
[    0.000000] Checking if this processor honours the WP bit even in supervisor mode...Ok.
[    0.000000] SLUB: Genslabs=15, HWalign=32, Order=0-3, MinObjects=0, CPUs=1, Nodes=1
[    0.000000] Hierarchical RCU implementation.
[    0.000000] 	RCU dyntick-idle grace-period acceleration is enabled.
[    0.000000] NR_IRQS:2304 nr_irqs:256 16
[    0.000000] CPU 0 irqstacks, hard=ee808000 soft=ee80a000
[    0.000000] vt handoff: transparent VT on vt#7
[    0.000000] Console: colour dummy device 80x25
[    0.000000] console [tty0] enabled
[    0.000000] Fast TSC calibration using PIT
[    0.000000] Detected 1129.763 MHz processor.
[    0.008005] Calibrating delay loop (skipped), value calculated using timer frequency.. 2259.52 BogoMIPS (lpj=4519052)
[    0.008017] pid_max: default: 32768 minimum: 301
[    0.008075] Security Framework initialized
[    0.008131] AppArmor: AppArmor initialized
[    0.008137] Yama: becoming mindful.
[    0.008289] Mount-cache hash table entries: 512
[    0.008626] Initializing cgroup subsys cpuacct
[    0.008642] Initializing cgroup subsys memory
[    0.008663] Initializing cgroup subsys devices
[    0.008671] Initializing cgroup subsys freezer
[    0.008677] Initializing cgroup subsys blkio
[    0.008694] Initializing cgroup subsys perf_event
[    0.012083] mce: CPU supports 5 MCE banks
[    0.012204] SMP alternatives: switching to UP code
[    0.024337] Freeing SMP alternatives: 24k freed
[    0.024380] ACPI: Core revision 20110623
[    0.029613] ACPI: setting ELCR to 0200 (from 0800)
[    0.032046] ftrace: allocating 25954 entries in 51 pages
[    0.044286] weird, boot CPU (#0) not listed by the BIOS.
[    0.044300] SMP motherboard not detected.
[    0.044305] Local APIC not detected. Using dummy APIC emulation.
[    0.044309] SMP disabled
[    0.044315] Performance Events: 
[    0.044321] no APIC, boot with the "lapic" boot parameter to force-enable it.
[    0.044326] no hardware sampling interrupt available.
[    0.044334] p6 PMU driver.
[    0.044345] ... version:                0
[    0.044349] ... bit width:              32
[    0.044353] ... generic registers:      2
[    0.044358] ... value mask:             00000000ffffffff
[    0.044362] ... max period:             000000007fffffff
[    0.044367] ... fixed-purpose events:   0
[    0.044371] ... event mask:             0000000000000003
[    0.045067] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[    0.045330] Brought up 1 CPUs
[    0.045340] Total of 1 processors activated (2259.52 BogoMIPS).
[    0.046071] devtmpfs: initialized
[    0.046419] EVM: security.selinux
[    0.046424] EVM: security.SMACK64
[    0.046428] EVM: security.capability
[    0.046595] PM: Registering ACPI NVS region at 2f7e8000 (98304 bytes)
[    0.050417] print_constraints: dummy: 
[    0.050473] RTC time: 13:17:13, date: 09/08/15
[    0.050596] NET: Registered protocol family 16
[    0.050932] EISA bus registered
[    0.051038] ACPI: bus type pci registered
[    0.052752] PCI: PCI BIOS revision 2.10 entry at 0xf0200, last bus=1
[    0.052758] PCI: Using configuration type 1 for base access
[    0.056251] bio: create slab <bio-0> at 0
[    0.056546] ACPI: Added _OSI(Module Device)
[    0.056554] ACPI: Added _OSI(Processor Device)
[    0.056560] ACPI: Added _OSI(3.0 _SCP Extensions)
[    0.056566] ACPI: Added _OSI(Processor Aggregator Device)
[    0.058151] ACPI: EC: Look up EC in DSDT
[    0.063904] ACPI: Interpreter enabled
[    0.063922] ACPI: (supports S0 S1 S3 S4 S5)
[    0.064027] ACPI: Using PIC for interrupt routing
[    0.096579] ACPI: EC: GPE = 0x1d, I/O: command/status = 0x66, data = 0x62
[    0.096894] ACPI: No dock devices found.
[    0.096901] HEST: Table not found.
[    0.096913] PCI: Ignoring host bridge windows from ACPI; if necessary, use "pci=use_crs" and report a bug
[    0.097153] ACPI: PCI Root Bridge [PCI0] (domain 0000 [bus 00-ff])
[    0.097572] pci_root PNP0A03:00: host bridge window [io  0x0000-0x0cf7] (ignored)
[    0.097580] pci_root PNP0A03:00: host bridge window [io  0x0d00-0xffff] (ignored)
[    0.097588] pci_root PNP0A03:00: host bridge window [mem 0x000a0000-0x000bffff] (ignored)
[    0.097595] pci_root PNP0A03:00: host bridge window [mem 0x000c0000-0x000c3fff] (ignored)
[    0.097602] pci_root PNP0A03:00: host bridge window [mem 0x000c4000-0x000c7fff] (ignored)
[    0.097609] pci_root PNP0A03:00: host bridge window [mem 0x000c8000-0x000dffff] (ignored)
[    0.097617] pci_root PNP0A03:00: host bridge window [mem 0x000e0000-0x000e3fff] (ignored)
[    0.097624] pci_root PNP0A03:00: host bridge window [mem 0x000e4000-0x000e7fff] (ignored)
[    0.097631] pci_root PNP0A03:00: host bridge window [mem 0x000e8000-0x000ebfff] (ignored)
[    0.097638] pci_root PNP0A03:00: host bridge window [mem 0x000ec000-0x000effff] (ignored)
[    0.097645] pci_root PNP0A03:00: host bridge window [mem 0x000f0000-0x000fffff] (ignored)
[    0.097652] pci_root PNP0A03:00: host bridge window [mem 0x2f800000-0xffdfffff] (ignored)
[    0.097680] pci 0000:00:00.0: [8086:3575] type 0 class 0x000600
[    0.097750] pci 0000:00:02.0: [8086:3577] type 0 class 0x000300
[    0.097767] pci 0000:00:02.0: reg 10: [mem 0x98000000-0x9fffffff pref]
[    0.097778] pci 0000:00:02.0: reg 14: [mem 0x90100000-0x9017ffff]
[    0.097819] pci 0000:00:02.0: supports D1
[    0.097838] pci 0000:00:02.1: [8086:3577] type 0 class 0x000380
[    0.097853] pci 0000:00:02.1: reg 10: [mem 0x88000000-0x8fffffff pref]
[    0.097865] pci 0000:00:02.1: reg 14: [mem 0x80200000-0x8027ffff]
[    0.097905] pci 0000:00:02.1: supports D1
[    0.097959] pci 0000:00:1d.0: [8086:2482] type 0 class 0x000c03
[    0.098005] pci 0000:00:1d.0: reg 20: [io  0xa4a0-0xa4bf]
[    0.098048] pci 0000:00:1d.1: [8086:2484] type 0 class 0x000c03
[    0.098095] pci 0000:00:1d.1: reg 20: [io  0xa4e0-0xa4ff]
[    0.098137] pci 0000:00:1d.2: [8086:2487] type 0 class 0x000c03
[    0.098183] pci 0000:00:1d.2: reg 20: [io  0xa800-0xa81f]
[    0.098241] pci 0000:00:1e.0: [8086:2448] type 1 class 0x000604
[    0.098294] pci 0000:00:1f.0: [8086:248c] type 0 class 0x000601
[    0.098366] pci 0000:00:1f.0: quirk: [io  0xf100-0xf17f] claimed by ICH4 ACPI/GPIO/TCO
[    0.098376] pci 0000:00:1f.0: quirk: [io  0xf200-0xf23f] claimed by ICH4 GPIO
[    0.098401] pci 0000:00:1f.1: [8086:248a] type 0 class 0x000101
[    0.098420] pci 0000:00:1f.1: reg 10: [io  0xa830-0xa837]
[    0.098434] pci 0000:00:1f.1: reg 14: [io  0xa848-0xa84b]
[    0.098448] pci 0000:00:1f.1: reg 18: [io  0xa860-0xa867]
[    0.098461] pci 0000:00:1f.1: reg 1c: [io  0xa878-0xa87b]
[    0.098475] pci 0000:00:1f.1: reg 20: [io  0xa890-0xa89f]
[    0.098488] pci 0000:00:1f.1: reg 24: [mem 0x00000000-0x000003ff]
[    0.098526] pci 0000:00:1f.3: [8086:2483] type 0 class 0x000c05
[    0.098573] pci 0000:00:1f.3: reg 20: [io  0x8000-0x801f]
[    0.098616] pci 0000:00:1f.5: [8086:2485] type 0 class 0x000401
[    0.098634] pci 0000:00:1f.5: reg 10: [io  0x9800-0x98ff]
[    0.098648] pci 0000:00:1f.5: reg 14: [io  0x9c00-0x9c3f]
[    0.098711] pci 0000:00:1f.6: [8086:2486] type 0 class 0x000703
[    0.098729] pci 0000:00:1f.6: reg 10: [io  0xa000-0xa0ff]
[    0.098743] pci 0000:00:1f.6: reg 14: [io  0xa400-0xa47f]
[    0.098835] pci 0000:01:08.0: [8086:1031] type 0 class 0x000200
[    0.098855] pci 0000:01:08.0: reg 10: [mem 0x80100000-0x80100fff]
[    0.098869] pci 0000:01:08.0: reg 14: [io  0x7000-0x703f]
[    0.098928] pci 0000:01:08.0: supports D1 D2
[    0.098934] pci 0000:01:08.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.098943] pci 0000:01:08.0: PME# disabled
[    0.098967] pci 0000:01:09.0: [104c:ac50] type 2 class 0x000607
[    0.098988] pci 0000:01:09.0: reg 10: [mem 0x00000000-0x00000fff]
[    0.099018] pci 0000:01:09.0: supports D1 D2
[    0.099023] pci 0000:01:09.0: PME# supported from D0 D1 D2 D3hot D3cold
[    0.099031] pci 0000:01:09.0: PME# disabled
[    0.099066] pci 0000:00:1e.0: PCI bridge to [bus 01-01] (subtractive decode)
[    0.099077] pci 0000:00:1e.0:   bridge window [io  0x7000-0x7fff]
[    0.099086] pci 0000:00:1e.0:   bridge window [mem 0x80100000-0x801fffff]
[    0.099096] pci 0000:00:1e.0:   bridge window [io  0x0000-0xffff] (subtractive decode)
[    0.099104] pci 0000:00:1e.0:   bridge window [mem 0x00000000-0xffffffff] (subtractive decode)
[    0.099148] pci_bus 0000:02: [bus 02-05] partially hidden behind transparent bridge 0000:01 [bus 01-01]
[    0.099164] pci_bus 0000:00: on NUMA node 0
[    0.099177] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[    0.099275] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCI1._PRT]
[    0.099436]  pci0000:00: Unable to request _OSC control (_OSC support mask: 0x1e)
[    0.105699] ACPI: PCI Interrupt Link [PILA] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.105916] ACPI: PCI Interrupt Link [PILB] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.106124] ACPI: PCI Interrupt Link [PILC] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.106333] ACPI: PCI Interrupt Link [PILD] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.106541] ACPI: PCI Interrupt Link [PILE] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.106749] ACPI: PCI Interrupt Link [PILF] (IRQs 3 4 5 6 7 9 *11 12 14 15)
[    0.106925] ACPI: PCI Interrupt Link [PILG] (IRQs 3 4 5 6 7 9 11 12 14 15) *0, disabled.
[    0.107100] ACPI: PCI Interrupt Link [PILH] (IRQs 3 4 5 6 7 9 11 12 14 15) *0, disabled.
[    0.107468] vgaarb: device added: PCI:0000:00:02.0,decodes=io+mem,owns=io+mem,locks=none
[    0.107491] vgaarb: loaded
[    0.107495] vgaarb: bridge control possible 0000:00:02.0
[    0.107848] i2c-core: driver [aat2870] using legacy suspend method
[    0.107854] i2c-core: driver [aat2870] using legacy resume method
[    0.108162] SCSI subsystem initialized
[    0.108359] libata version 3.00 loaded.
[    0.108515] usbcore: registered new interface driver usbfs
[    0.108549] usbcore: registered new interface driver hub
[    0.108632] usbcore: registered new device driver usb
[    0.108914] PCI: Using ACPI for IRQ routing
[    0.108929] PCI: pci_cache_line_size set to 32 bytes
[    0.109031] reserve RAM buffer: 000000000009fc00 - 000000000009ffff 
[    0.109038] reserve RAM buffer: 000000002f7d0000 - 000000002fffffff 
[    0.109347] NetLabel: Initializing
[    0.109353] NetLabel:  domain hash size = 128
[    0.109357] NetLabel:  protocols = UNLABELED CIPSOv4
[    0.109388] NetLabel:  unlabeled traffic allowed by default
[    0.109603] Switching to clocksource pit
[    0.133459] AppArmor: AppArmor Filesystem Enabled
[    0.133593] pnp: PnP ACPI init
[    0.133658] ACPI: bus type pnp registered
[    0.134029] pnp 00:00: [bus 00-ff]
[    0.134040] pnp 00:00: [io  0x0cf8-0x0cff]
[    0.134048] pnp 00:00: [io  0x0000-0x0cf7 window]
[    0.134054] pnp 00:00: [io  0x0d00-0xffff window]
[    0.134077] pnp 00:00: [mem 0x000a0000-0x000bffff window]
[    0.134084] pnp 00:00: [mem 0x000c0000-0x000c3fff window]
[    0.134091] pnp 00:00: [mem 0x000c4000-0x000c7fff window]
[    0.134097] pnp 00:00: [mem 0x000c8000-0x000dffff window]
[    0.134104] pnp 00:00: [mem 0x000e0000-0x000e3fff window]
[    0.134110] pnp 00:00: [mem 0x000e4000-0x000e7fff window]
[    0.134117] pnp 00:00: [mem 0x000e8000-0x000ebfff window]
[    0.134124] pnp 00:00: [mem 0x000ec000-0x000effff window]
[    0.134130] pnp 00:00: [mem 0x000f0000-0x000fffff window]
[    0.134137] pnp 00:00: [mem 0x2f800000-0xffdfffff window]
[    0.134323] pnp 00:00: Plug and Play ACPI device, IDs PNP0a03 (active)
[    0.134991] pnp 00:01: [io  0x0000-0x000f]
[    0.134999] pnp 00:01: [io  0x0081-0x008f]
[    0.135005] pnp 00:01: [io  0x0094-0x009f]
[    0.135010] pnp 00:01: [io  0x00c0-0x00df]
[    0.135017] pnp 00:01: [dma 4]
[    0.135130] pnp 00:01: Plug and Play ACPI device, IDs PNP0200 (active)
[    0.135194] pnp 00:02: [io  0x0061]
[    0.135273] pnp 00:02: Plug and Play ACPI device, IDs PNP0800 (active)
[    0.135317] pnp 00:03: [io  0x00f0-0x00ff]
[    0.135328] pnp 00:03: [irq 13]
[    0.135403] pnp 00:03: Plug and Play ACPI device, IDs PNP0c04 (active)
[    0.135445] pnp 00:04: [io  0x0070-0x0073]
[    0.135451] pnp 00:04: [irq 8]
[    0.135531] pnp 00:04: Plug and Play ACPI device, IDs PNP0b00 (active)
[    0.138265] pnp 00:05: [io  0x0060]
[    0.138272] pnp 00:05: [io  0x0064]
[    0.138278] pnp 00:05: [irq 1]
[    0.138418] pnp 00:05: Plug and Play ACPI device, IDs PNP0303 (active)
[    0.141476] pnp 00:06: [io  0x03bc-0x03bf]
[    0.141483] pnp 00:06: [irq 7]
[    0.141626] pnp 00:06: Plug and Play ACPI device, IDs PNP0400 (active)
[    0.144494] pnp 00:07: [io  0x03f0-0x03f5]
[    0.144501] pnp 00:07: [io  0x03f7]
[    0.144508] pnp 00:07: [irq 6]
[    0.144514] pnp 00:07: [dma 2]
[    0.144628] pnp 00:07: Plug and Play ACPI device, IDs PNP0700 (active)
[    0.144828] pnp 00:08: Plug and Play ACPI device, IDs PNP0501 (disabled)
[    0.145068] pnp 00:09: Plug and Play ACPI device, IDs IBM0071 PNP0511 (disabled)
[    0.145111] pnp 00:0a: [irq 12]
[    0.145193] pnp 00:0a: Plug and Play ACPI device, IDs IBM3780 PNP0f13 (active)
[    0.153522] pnp 00:0b: [io  0xf100-0xf16f]
[    0.153530] pnp 00:0b: [io  0xf178-0xf17f]
[    0.153536] pnp 00:0b: [io  0xf200-0xf23f]
[    0.153542] pnp 00:0b: [io  0x002e-0x002f]
[    0.153555] pnp 00:0b: [io  0x0380-0x038f]
[    0.153561] pnp 00:0b: [io  0x04d0-0x04d1]
[    0.153567] pnp 00:0b: [io  0x0580-0x0587]
[    0.153574] pnp 00:0b: [mem 0x00000000-0x000009ff]
[    0.153580] pnp 00:0b: [mem 0x00000f00-0x00000fff]
[    0.153586] pnp 00:0b: [mem 0xfff80000-0xffffffff]
[    0.153593] pnp 00:0b: [mem 0xffb00000-0xffbfffff]
[    0.153599] pnp 00:0b: [mem 0xfff00000-0xfff7ffff]
[    0.153605] pnp 00:0b: [mem 0x00100000-0x00ffffff]
[    0.153611] pnp 00:0b: [mem 0x01000000-0x2f7fffff]
[    0.153617] pnp 00:0b: [mem 0xfebffc00-0xfebfffff]
[    0.153662] pnp 00:0b: disabling [io  0xf100-0xf16f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf100-0xf17f]
[    0.153672] pnp 00:0b: disabling [io  0xf178-0xf17f] because it overlaps 0000:00:1f.0 BAR 13 [io  0xf100-0xf17f]
[    0.153703] pnp 00:0b: disabling [mem 0x00000000-0x000009ff] because it overlaps 0000:01:09.0 BAR 0 [mem 0x00000000-0x00000fff]
[    0.153714] pnp 00:0b: disabling [mem 0x00000f00-0x00000fff] because it overlaps 0000:01:09.0 BAR 0 [mem 0x00000000-0x00000fff]
[    0.153848] system 00:0b: [io  0xf200-0xf23f] has been reserved
[    0.153857] system 00:0b: [io  0x0380-0x038f] has been reserved
[    0.153865] system 00:0b: [io  0x04d0-0x04d1] has been reserved
[    0.153872] system 00:0b: [io  0x0580-0x0587] has been reserved
[    0.153883] system 00:0b: [mem 0xfff80000-0xffffffff] could not be reserved
[    0.153891] system 00:0b: [mem 0xffb00000-0xffbfffff] has been reserved
[    0.153899] system 00:0b: [mem 0xfff00000-0xfff7ffff] has been reserved
[    0.153908] system 00:0b: [mem 0x00100000-0x00ffffff] could not be reserved
[    0.153916] system 00:0b: [mem 0x01000000-0x2f7fffff] could not be reserved
[    0.153924] system 00:0b: [mem 0xfebffc00-0xfebfffff] has been reserved
[    0.153934] system 00:0b: Plug and Play ACPI device, IDs PNP0c02 (active)
[    0.156719] pnp: PnP ACPI: found 12 devices
[    0.156726] ACPI: ACPI bus type pnp unregistered
[    0.156735] PnPBIOS: Disabled by ACPI PNP
[    0.196736] Switching to clocksource acpi_pm
[    0.196815] PCI: max bus depth: 2 pci_try_num: 3
[    0.196877] pci 0000:00:1f.1: BAR 5: assigned [mem 0x30000000-0x300003ff]
[    0.196893] pci 0000:00:1f.1: BAR 5: set to [mem 0x30000000-0x300003ff] (PCI address [0x30000000-0x300003ff])
[    0.196903] pci 0000:00:1e.0: BAR 15: assigned [mem 0x34000000-0x37ffffff pref]
[    0.196916] pci 0000:01:09.0: BAR 0: assigned [mem 0x38000000-0x38000fff]
[    0.196927] pci 0000:01:09.0: BAR 0: set to [mem 0x38000000-0x38000fff] (PCI address [0x38000000-0x38000fff])
[    0.196937] pci 0000:01:09.0: BAR 16: assigned [mem 0x3c000000-0x3fffffff]
[    0.196945] pci 0000:01:09.0: BAR 15: assigned [mem 0x34000000-0x37ffffff pref]
[    0.196953] pci 0000:01:09.0: BAR 14: assigned [io  0x7400-0x74ff]
[    0.196961] pci 0000:01:09.0: BAR 13: assigned [io  0x7800-0x78ff]
[    0.196968] pci 0000:01:09.0: CardBus bridge to [bus 02-05]
[    0.196975] pci 0000:01:09.0:   bridge window [io  0x7800-0x78ff]
[    0.196984] pci 0000:01:09.0:   bridge window [io  0x7400-0x74ff]
[    0.196993] pci 0000:01:09.0:   bridge window [mem 0x34000000-0x37ffffff pref]
[    0.197001] pci 0000:01:09.0:   bridge window [mem 0x3c000000-0x3fffffff]
[    0.197010] pci 0000:00:1e.0: PCI bridge to [bus 01-01]
[    0.197018] pci 0000:00:1e.0:   bridge window [io  0x7000-0x7fff]
[    0.197028] pci 0000:00:1e.0:   bridge window [mem 0x80100000-0x801fffff]
[    0.197037] pci 0000:00:1e.0:   bridge window [mem 0x34000000-0x37ffffff pref]
[    0.197067] pci 0000:00:1e.0: setting latency timer to 64
[    0.197469] ACPI: PCI Interrupt Link [PILB] enabled at IRQ 11
[    0.197477] PCI: setting IRQ 11 as level-triggered
[    0.197488] pci 0000:01:09.0: PCI INT A -> Link[PILB] -> GSI 11 (level, low) -> IRQ 11
[    0.197501] pci_bus 0000:00: resource 0 [io  0x0000-0xffff]
[    0.197508] pci_bus 0000:00: resource 1 [mem 0x00000000-0xffffffff]
[    0.197516] pci_bus 0000:01: resource 0 [io  0x7000-0x7fff]
[    0.197523] pci_bus 0000:01: resource 1 [mem 0x80100000-0x801fffff]
[    0.197530] pci_bus 0000:01: resource 2 [mem 0x34000000-0x37ffffff pref]
[    0.197536] pci_bus 0000:01: resource 4 [io  0x0000-0xffff]
[    0.197542] pci_bus 0000:01: resource 5 [mem 0x00000000-0xffffffff]
[    0.197549] pci_bus 0000:02: resource 0 [io  0x7800-0x78ff]
[    0.197556] pci_bus 0000:02: resource 1 [io  0x7400-0x74ff]
[    0.197562] pci_bus 0000:02: resource 2 [mem 0x34000000-0x37ffffff pref]
[    0.197569] pci_bus 0000:02: resource 3 [mem 0x3c000000-0x3fffffff]
[    0.197712] NET: Registered protocol family 2
[    0.197904] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[    0.198808] TCP established hash table entries: 131072 (order: 8, 1048576 bytes)
[    0.204275] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[    0.207023] TCP: Hash tables configured (established 131072 bind 65536)
[    0.207034] TCP reno registered
[    0.207056] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.207152] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.207524] NET: Registered protocol family 1
[    0.207589] pci 0000:00:02.0: Boot video device
[    0.208007] ACPI: PCI Interrupt Link [PILA] enabled at IRQ 11
[    0.208117] pci 0000:00:1d.0: PCI INT A -> Link[PILA] -> GSI 11 (level, low) -> IRQ 11
[    0.208147] pci 0000:00:1d.0: PCI INT A disabled
[    0.208448] ACPI: PCI Interrupt Link [PILD] enabled at IRQ 11
[    0.208458] pci 0000:00:1d.1: PCI INT B -> Link[PILD] -> GSI 11 (level, low) -> IRQ 11
[    0.208479] pci 0000:00:1d.1: PCI INT B disabled
[    0.208736] ACPI: PCI Interrupt Link [PILC] enabled at IRQ 11
[    0.208745] pci 0000:00:1d.2: PCI INT C -> Link[PILC] -> GSI 11 (level, low) -> IRQ 11
[    0.208764] pci 0000:00:1d.2: PCI INT C disabled
[    0.208831] pci 0000:01:08.0: Firmware left e100 interrupts enabled; disabling
[    0.208851] PCI: CLS 32 bytes, default 32
[    0.209055] Simple Boot Flag at 0x41 set to 0x1
[    0.209931] audit: initializing netlink socket (disabled)
[    0.209968] type=2000 audit(1441718233.204:1): initialized
[    0.258210] Trying to unpack rootfs image as initramfs...
[    0.328437] HugeTLB registered 4 MB page size, pre-allocated 0 pages
[    0.372756] VFS: Disk quotas dquot_6.5.2
[    0.372963] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    0.374816] fuse init (API version 7.17)
[    0.375143] msgmni has been set to 1452
[    0.388528] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 253)
[    0.388737] io scheduler noop registered
[    0.388743] io scheduler deadline registered
[    0.388786] io scheduler cfq registered (default)
[    0.389207] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    0.389288] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    0.400262] ACPI: Deprecated procfs I/F for AC is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.404484] ACPI: AC Adapter [AC] (on-line)
[    0.408793] input: Sleep Button as /devices/LNXSYSTM:00/device:00/PNP0C0E:00/input/input0
[    0.408816] ACPI: Sleep Button [SLPB]
[    0.408996] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    0.412580] ACPI: Lid Switch [LID]
[    0.412801] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    0.412819] ACPI: Power Button [PWRF]
[    0.424798] Marking TSC unstable due to TSC halts in idle
[    0.424827] ACPI: acpi_idle registered with cpuidle
[    0.492940] thermal LNXTHERM:00: registered as thermal_zone0
[    0.492955] ACPI: Thermal Zone [THR1] (76 C)
[    0.520414] thermal LNXTHERM:01: registered as thermal_zone1
[    0.520427] ACPI: Thermal Zone [THR2] (53 C)
[    0.520583] ACPI: Deprecated procfs I/F for battery is loaded, please retry with CONFIG_ACPI_PROCFS_POWER cleared
[    0.520628] ACPI: Battery Slot [BAT0] (battery present)
[    0.520862] ERST: Table is not found!
[    0.520868] GHES: HEST is not enabled!
[    0.521185] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.536913] isapnp: Scanning for PnP cards...
[    0.543361] serial 00:08: [io  0x03f8-0x03ff]
[    0.543456] serial 00:08: [irq 3]
[    0.544230] serial 00:08: activated
[    0.564719] 00:08: ttyS0 at I/O 0x3f8 (irq = 3) is a 16550A
[    0.643540] ACPI: Battery Slot [BAT0] (battery present)
[    0.649065] serial 0000:00:1f.6: PCI INT B -> Link[PILB] -> GSI 11 (level, low) -> IRQ 11
[    0.649108] serial 0000:00:1f.6: PCI INT B disabled
[    0.649647] Linux agpgart interface v0.103
[    0.649802] agpgart-intel 0000:00:00.0: Intel 830M Chipset
[    0.649848] agpgart-intel 0000:00:00.0: detected gtt size: 131072K total, 131072K mappable
[    0.650278] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    0.650677] agpgart-intel 0000:00:00.0: AGP aperture is 128M @ 0x98000000
[    0.661364] brd: module loaded
[    0.663711] loop: module loaded
[    0.664300] ata_piix 0000:00:1f.1: version 2.13
[    0.664337] ata_piix 0000:00:1f.1: can't derive routing for PCI INT A
[    0.664441] ata_piix 0000:00:1f.1: setting latency timer to 64
[    0.665376] scsi0 : ata_piix
[    0.668811] scsi1 : ata_piix
[    0.670578] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xa890 irq 14
[    0.670588] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xa898 irq 15
[    0.672173] Fixed MDIO Bus: probed
[    0.672236] tun: Universal TUN/TAP device driver, 1.6
[    0.672241] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.672635] PPP generic driver version 2.4.2
[    0.672947] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.673008] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.673045] uhci_hcd: USB Universal Host Controller Interface driver
[    0.673153] uhci_hcd 0000:00:1d.0: PCI INT A -> Link[PILA] -> GSI 11 (level, low) -> IRQ 11
[    0.673178] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.673186] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.673306] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[    0.673358] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000a4a0
[    0.673786] hub 1-0:1.0: USB hub found
[    0.673800] hub 1-0:1.0: 2 ports detected
[    0.673972] uhci_hcd 0000:00:1d.1: PCI INT B -> Link[PILD] -> GSI 11 (level, low) -> IRQ 11
[    0.673993] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.674000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.680597] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[    0.680669] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000a4e0
[    0.681220] hub 2-0:1.0: USB hub found
[    0.681236] hub 2-0:1.0: 2 ports detected
[    0.681447] uhci_hcd 0000:00:1d.2: PCI INT C -> Link[PILC] -> GSI 11 (level, low) -> IRQ 11
[    0.681476] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.681484] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.681659] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[    0.681709] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000a800
[    0.682120] hub 3-0:1.0: USB hub found
[    0.682134] hub 3-0:1.0: 2 ports detected
[    0.682457] usbcore: registered new interface driver libusual
[    0.682603] i8042: PNP: PS/2 Controller [PNP0303:KBC0,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.684588] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.684615] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.685015] mousedev: PS/2 mouse device common for all mice
[    0.685462] rtc_cmos 00:04: RTC can wake from S4
[    0.685691] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.685732] rtc0: alarms up to one month, y3k, 242 bytes nvram
[    0.685975] device-mapper: uevent: version 1.0.3
[    0.686200] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.686313] EISA: Probing bus 0 at eisa.0
[    0.686356] Cannot allocate resource for EISA slot 7
[    0.686361] Cannot allocate resource for EISA slot 8
[    0.686366] EISA: Detected 0 cards.
[    0.686396] cpufreq-nforce2: No nForce2 chipset.
[    0.686494] cpuidle: using governor ladder
[    0.686632] cpuidle: using governor menu
[    0.686638] EFI Variables Facility v0.08 2004-May-17
[    0.687344] TCP cubic registered
[    0.687753] NET: Registered protocol family 10
[    0.694046] NET: Registered protocol family 17
[    0.694147] Registering the dns_resolver key type
[    0.694315] Using IPI No-Shortcut mode
[    0.694664] PM: Hibernation image not present or could not be loaded.
[    0.694702] registered taskstats version 1
[    0.836348] ata2.01: NODEV after polling detection
[    0.836553] ata1.00: ATA-5: IC25N020ATCS04-0, CA2OA71A, max UDMA/100
[    0.836562] ata1.00: 39070080 sectors, multi 16: LBA 
[    0.839179] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.845239] ata2.00: ATAPI: UJDA745 DVD/CDRW, 1.00, max UDMA/33
[    0.889100] ata1.00: configured for UDMA/100
[    0.933877] ata2.00: configured for UDMA/33
[    1.071650] usb 2-1: new full-speed USB device number 2 using uhci_hcd
[    1.131824] isapnp: No Plug & Play device found
[    1.132397] scsi 0:0:0:0: Direct-Access     ATA      IC25N020ATCS04-0 CA2O PQ: 0 ANSI: 5
[    1.132950] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.133477] sd 0:0:0:0: [sda] 39070080 512-byte logical blocks: (20.0 GB/18.6 GiB)
[    1.133614] sd 0:0:0:0: [sda] Write Protect is off
[    1.133623] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.133680] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.137771] scsi 1:0:0:0: CD-ROM            MATSHITA UJDA745 DVD/CDRW 1.00 PQ: 0 ANSI: 5
[    1.142061] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.142076] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.142514] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.142911] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.193631]  sda: sda1 sda2 sda3
[    1.194791] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.635301] Freeing initrd memory: 13896k freed
[    1.703962]   Magic number: 15:715:280
[    1.704257] tty tty17: hash matches
[    1.704377] rtc_cmos 00:04: setting system clock to 2015-09-08 13:17:14 UTC (1441718234)
[    1.704435] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.704440] EDD information not available.
[    1.704862] Freeing unused kernel memory: 712k freed
[    1.706913] Write protecting the kernel text: 5628k
[    1.707014] Write protecting the kernel read-only data: 2324k
[    1.772565] udevd[86]: starting version 175
[    2.282600] Floppy drive(s): fd0 is 1.44M
[    2.298363] FDC 0 is a National Semiconductor PC87306
[    2.447941] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[    2.447952] e100: Copyright(c) 1999-2006 Intel Corporation
[    2.495282] ACPI: PCI Interrupt Link [PILE] enabled at IRQ 11
[    2.495304] e100 0000:01:08.0: PCI INT A -> Link[PILE] -> GSI 11 (level, low) -> IRQ 11
[    2.555375] e100 0000:01:08.0: PME# disabled
[    2.562734] e100 0000:01:08.0: eth0: addr 0x80100000, irq 11, MAC addr 00:00:e2:82:0c:20
[    2.747665] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[    2.747681] EXT4-fs (sda2): write access will be enabled during recovery
[    5.423889] EXT4-fs (sda2): orphan cleanup on readonly fs
[    5.423916] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 5743
[    5.424071] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 1093
[    5.424096] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 5741
[    5.424234] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 5738
[    5.424275] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 5633
[    5.424372] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 143127
[    5.424412] EXT4-fs (sda2): ext4_orphan_cleanup: deleting unreferenced inode 188103
[    5.424445] EXT4-fs (sda2): 7 orphan inodes deleted
[    5.424452] EXT4-fs (sda2): recovery complete
[    5.708082] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   21.600508] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.825236] udevd[322]: starting version 175
[   21.985816] Adding 8188k swap on /dev/sda3.  Priority:-1 extents:1 across:8188k 
[   22.175308] lp: driver loaded but no devices found
[   22.397888] ------------[ cut here ]------------
[   22.397926] WARNING: at /build/buildd/linux-3.2.0/fs/proc/generic.c:808 remove_proc_entry+0x1ad/0x200()
[   22.397933] Hardware name: 26563CF
[   22.397937] name 'r8168'
[   22.397941] Modules linked in: r8168(O+) lp parport e100 floppy
[   22.397961] Pid: 333, comm: modprobe Tainted: G           O 3.2.0-23-generic #36-Ubuntu
[   22.397967] Call Trace:
[   22.397986]  [<c104b182>] warn_slowpath_common+0x72/0xa0
[   22.397995]  [<c118624d>] ? remove_proc_entry+0x1ad/0x200
[   22.398003]  [<c118624d>] ? remove_proc_entry+0x1ad/0x200
[   22.398011]  [<c104b253>] warn_slowpath_fmt+0x33/0x40
[   22.398019]  [<c118624d>] remove_proc_entry+0x1ad/0x200
[   22.398029]  [<efff8000>] ? 0xefff7fff
[   22.398053]  [<efff8013>] rtl8168_init_module+0x13/0x1000 [r8168]
[   22.398063]  [<c1001125>] do_one_initcall+0x35/0x170
[   22.398070]  [<efff8000>] ? 0xefff7fff
[   22.398080]  [<c108651d>] sys_init_module+0xad/0x210
[   22.398096]  [<c1130df3>] ? sys_close+0x73/0xc0
[   22.398109]  [<c1576ed4>] syscall_call+0x7/0xb
[   22.398122]  [<c1570000>] ? encode+0x26/0x2b
[   22.398129] ---[ end trace 73e82492f506cf20 ]---
[   22.433729] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   23.271715] [Firmware Bug]: ACPI(VGA0) defines _DOD but not _DOS
[   23.441276] ppdev: user-space parallel port driver
[   23.465555] parport_pc 00:06: reported by Plug and Play ACPI
[   23.465613] parport0: PC-style at 0x3bc, irq 7 [PCSPP,TRISTATE]
[   23.468869] Bluetooth: Core ver 2.16
[   23.469017] NET: Registered protocol family 31
[   23.469023] Bluetooth: HCI device and connection manager initialized
[   23.469031] Bluetooth: HCI socket layer initialized
[   23.469036] Bluetooth: L2CAP socket layer initialized
[   23.469050] Bluetooth: SCO socket layer initialized
[   23.520621] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.520631] Bluetooth: BNEP filters: protocol multicast
[   23.552173] Bluetooth: RFCOMM TTY layer initialized
[   23.552194] Bluetooth: RFCOMM socket layer initialized
[   23.552199] Bluetooth: RFCOMM ver 1.11
[   23.560817] lp0: using parport0 (interrupt-driven).
[   23.664586] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A03:00/LNXVIDEO:00/input/input4
[   23.664983] ACPI: Video Device [VGA0] (multi-head: yes  rom: no  post: no)
[   24.002288] [drm] Initialized drm 1.1.0 20060810
[   24.052175] Non-volatile memory driver v1.3
[   24.320480] irda_init()
[   24.320523] NET: Registered protocol family 23
[   24.409095] intel_rng: FWH not detected
[   24.409126] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   24.526731] i915 0000:00:02.0: PCI INT A -> Link[PILA] -> GSI 11 (level, low) -> IRQ 11
[   24.526747] i915 0000:00:02.0: setting latency timer to 64
[   24.590801] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   24.590812] [drm] Driver supports precise vblank timestamp query.
[   24.601987] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   24.662948] nsc-ircc 00:09: [io  0x02f8-0x02ff]
[   24.663067] nsc-ircc 00:09: [irq 4]
[   24.663077] nsc-ircc 00:09: [dma 1]
[   24.663719] nsc-ircc 00:09: activated
[   24.663729] nsc_ircc_pnp_probe() : From PnP, found firbase 0x2F8 ; irq 4 ; dma 1.
[   24.672139] nsc-ircc, chip->init
[   24.672159] nsc-ircc, Found chip at base=0x02e
[   24.672187] nsc-ircc, driver loaded (Dag Brattli)
[   24.697014] IrDA: Registered device irda0
[   24.697028] nsc-ircc, Using dongle: IBM31T1100 or Temic TFDS6000/TFDS6500
[   24.754348] yenta_cardbus 0000:01:09.0: CardBus bridge found [1014:1017]
[   24.754372] yenta_cardbus 0000:01:09.0: Enabling burst memory read transactions
[   24.754381] yenta_cardbus 0000:01:09.0: Using CSCINT to route CSC interrupts to PCI
[   24.754387] yenta_cardbus 0000:01:09.0: Routing CardBus interrupts to PCI
[   24.754396] yenta_cardbus 0000:01:09.0: TI: mfunc 0x01111c02, devctl 0x64
[   24.879000] [drm] initialized overlay support
[   24.984650] yenta_cardbus 0000:01:09.0: ISA IRQ mask 0x0438, PCI irq 11
[   24.984661] yenta_cardbus 0000:01:09.0: Socket status: 30000006
[   24.984670] pci_bus 0000:01: Raising subordinate bus# of parent bus (#01) from #01 to #05
[   24.984813] yenta_cardbus 0000:01:09.0: pcmcia: parent PCI bridge window: [io  0x7000-0x7fff]
[   24.984823] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x7000-0x7fff: excluding 0x7000-0x703f 0x7400-0x74ff
[   24.992607] udevd[348]: renamed network interface eth0 to eth1
[   25.010800] psmouse serio1: hgpk: ID: 10 00 64
[   25.015738]  0x7800-0x78ff
[   25.070176] yenta_cardbus 0000:01:09.0: pcmcia: parent PCI bridge window: [mem 0x80100000-0x801fffff]
[   25.070189] pcmcia_socket pcmcia_socket0: cs: memory probe 0x80100000-0x801fffff: excluding 0x80100000-0x8010ffff
[   25.070232] yenta_cardbus 0000:01:09.0: pcmcia: parent PCI bridge window: [mem 0x34000000-0x37ffffff pref]
[   25.070240] pcmcia_socket pcmcia_socket0: cs: memory probe 0x34000000-0x37ffffff: excluding 0x34000000-0x37ffffff
[   25.335601] IBM TrackPoint firmware: 0x0e, buttons: 3/3
[   25.338337] thinkpad_acpi: ThinkPad ACPI Extras v0.24
[   25.338389] thinkpad_acpi: http://ibm-acpi.sf.net/
[   25.338395] thinkpad_acpi: ThinkPad BIOS 1FETE8WW (3.080), EC unknown
[   25.338400] thinkpad_acpi: WARNING: Outdated ThinkPad BIOS/EC firmware
[   25.338405] thinkpad_acpi: WARNING: This firmware may be missing critical bug fixes and/or important features
[   25.349010] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/input/input5
[   25.374128] thinkpad_acpi: detected a 8-level brightness capable ThinkPad
[   25.438185] Chip Version Info: CHIP_8188E_Normal_Chip_TSMC_D_CUT_1T1R_RomVer(0)
[   25.438577] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   25.448206] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input6
[   25.727646] EEPROM ID = 0x8129
[   25.735497] usbcore: registered new interface driver r8188eu
[   26.465207] init: failsafe main process (618) killed by TERM signal
[   26.558404] fbcon: inteldrmfb (fb0) is primary device
[   26.587467] Console: switching to colour frame buffer device 128x48
[   26.587562] fb0: inteldrmfb frame buffer device
[   26.587566] drm: registered panic notifier
[   26.587656] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   26.587764] snd_intel8x0 0000:00:1f.5: PCI INT B -> Link[PILB] -> GSI 11 (level, low) -> IRQ 11
[   26.587801] snd_intel8x0 0000:00:1f.5: setting latency timer to 64
[   27.242876] intel8x0_measure_ac97_clock: measured 58618 usecs (2816 samples)
[   27.242887] intel8x0: clocking to 48000
[   27.812769] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x2f8-0x2ff 0x370-0x377 0x380-0x38f
[   27.814476] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3ff 0x4d0-0x4d7
[   27.815197] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   27.815800] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   27.852934] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xf0000-0xfffff
[   27.853006] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: clean.
[   27.853071] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: clean.
[   27.853135] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   28.240537] R8188EU: Firmware Version 11, SubVersion 1, Signature 0x88e1
[   29.589949] MAC Address = 00:65:0e:01:98:d7
[   29.627765] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.638523] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   29.779796] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   29.788408] ADDRCONF(NETDEV_UP): eth1: link is not ready
[   31.718176] init: lightdm main process (985) killed by TERM signal
[   34.561294] R8188EU: INFO assoc success
[   34.594665] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.025146] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[   38.025159] watchdog: failed to be enabled on some cpus
[   39.178050] init: plymouth-stop pre-start process (1288) terminated with status 1
[   81.614677] NMI watchdog disabled (cpu0): not supported (no LAPIC?)
[   81.614694] watchdog: failed to be enabled on some cpus
jwg@q ~ $ 

```

---

### Post by chili555 on 2015-09-09
It appears that you rebooted in the interim. We also see no evidence of a crash. We therefor still see nothing alarming to fix.

Let's try another way. Please open a terminal and do:```
tail -f /var/log/syslog
```Now open Firefox on wireless only and crash it. What are the last 15 or 20 lines that erupted in the terminal watching syslog? Please paste them here.

Get out of *tail *with Ctrl+c.

---

