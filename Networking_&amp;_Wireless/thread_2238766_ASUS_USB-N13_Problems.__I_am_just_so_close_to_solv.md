---
title: "ASUS USB-N13 Problems.  I am just so close to solving this.  (I think)"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by pfleurymadison on 2014-08-09
OK.  I have Kubuntu 14.04 (trusty) on an HP machine and I am trying to get wireless going on it.  I can hook up to the internet through a wired connection but that is a temporary measure since I have to run the cable about fifty feet through two rooms and my wife is exceedingly unhappy with this.  (She thinks she'll trip too many times.)  Thus I must get wireless going soon.  (Soon = by Tuesday - that's when she gets back.)

Here is the situation.

I have plugged and ASUS USB-N13 into the HP machine which, by the way, is not dual booting with anything.  Wireless does not work but wired does.

I found a script on this forum and I ran it to get some information.  Here is the output.  I have lightly edited the output to make it more readable for you.

########## wireless info START ##########

Report from: 09 Aug 2014 20:38 CDT -0500

Script from: 04 Aug 2014 18:47 UTC +0000

##### release #####

Distributor ID: Ubuntu
Description: Ubuntu 14.04.1 LTS
Release: 14.04
Codename: trusty

##### kernel #####

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:12 UTC 2014 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

KDE Plasma Workspace

##### lspci #####

06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
Subsystem: Hewlett-Packard Company Device [103c:2ac2]
Kernel driver in use: r8169

##### lsusb #####

Bus 002 Device 005: ID 0b05:17ab ASUSTek Computer, Inc. USB-N13 802.11n Network Adapter (rev. B1) [Realtek RTL8192CU]
Bus 002 Device 004: ID 058f:6366 Alcor Micro Corp. Multi Flash Reader
Bus 002 Device 023: ID 046d:c069 Logitech, Inc. M500 Laser Mouse
Bus 002 Device 006: ID 04ca:004b Lite-On Technology Corp.
Bus 002 Device 003: ID 0557:7000 ATEN International Co., Ltd Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA Card Info #####

##### rfkill #####

##### lsmod #####

8192cu 572775 0

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0 Link encap:Ethernet HWaddr <MAC addr eth0>
inet addr:192.168.1.123 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::3a60:77ff:fe40:a44b/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:501717 errors:0 dropped:0 overruns:0 frame:0
TX packets:460145 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:315268879 (315.2 MB) TX bytes:396266766 (396.2 MB)

wlan0 Link encap:Ethernet HWaddr <MAC addr wlan0>
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:3525 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

##### iwconfig #####

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 unassociated Nickname:"<WIFI@REALTEK>"
Mode:Managed Frequency=2.412 GHz Access Point: Not-Associated
Sensitivity:0/0
Retryff RTS thrff Fragment thrff
Power Managementff
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0

##### route #####

Kernel IP routing table
Destination Gateway Genmask Flags Metric Ref Use Iface
0.0.0.0 192.168.1.1 0.0.0.0 UG 0 0 0 eth0
192.168.1.0 0.0.0.0 255.255.255.0 U 1 0 0 eth0

##### resolv.conf #####

nameserver 127.0.1.1
search home.network

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
Type: 802.11 WiFi
Driver: rtl8192cu
State: disconnected
Default: no
HW Address: <MAC addr wlan0>

Capabilities:

Wireless Properties
WEP Encryption: yes
WPA Encryption: yes
WPA2 Encryption: yes

Wireless Access Points
GRUMPY: Infra, <MAC addr COUTU>, Freq 2462 MHz, Rate 16 Mb/s, Strength 91 WPA WPA2
myNetwork: Infra, <MAC addr myNetwork>, Freq 2462 MHz, Rate 16 Mb/s, Strength 80 WPA WPA2
HAPPY: Infra, <MAC addr HAPPY>, Freq 2437 MHz, Rate 8 Mb/s, Strength 89 WPA WPA2
SLEEPY: Infra, <MAC addr SLEEPY>, Freq 2462 MHz, Rate 16 Mb/s, Strength 63 WPA WPA2

- Device: eth0 [Wired connection 1] -------------------------------------------
Type: Wired
Driver: r8169
State: connected
Default: yes
HW Address: <MAC addr eth0>

Capabilities:
Carrier Detect: yes
Speed: 100 Mb/s

Wired Properties
Carrier: on

IPv4 Settings:
Address: 192.168.1.123
Prefix: 24 (255.255.255.0)
Gateway: 192.168.1.1

DNS: 75.75.75.75
DNS: 75.75.76.76

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
managed=true

##### iw reg get #####

country 00:
(2402 - 2472 @ 40), (3, 20)
(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels #####

lo no frequency information.

eth0 no frequency information.

wlan0 11 channels in total; available frequencies :
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
Current Frequency=2.412 GHz (Channel 1)

##### iwlist scan #####

lo Interface doesn't support scanning.

eth0 Interface doesn't support scanning.

wlan0 Scan completed :


Cell 19 - Address: <MAC addr GRUMPY>
ESSID:"GRUMPY"
Protocol:IEEE 802.11bg
Mode:Master
Frequency:2.452 GHz (Channel 9)
Encryption keyn
Bit Rates:54 Mb/s
Quality=68/100 Signal level=66/100
Cell 20 - Address: <MAC addr myNetwork>
ESSID:"myNetwork"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.462 GHz (Channel 11)
Encryption keyn
Bit Rates:144 Mb/s
Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Quality=72/100 Signal level=92/100
Cell 21 - Address: <MAC addr HAPPY>
ESSID:"HAPPY"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.462 GHz (Channel 11)
Encryption keyn
Bit Rates:144 Mb/s
Extra:wpa_ie=dd1c0050f20101000050f20202000050f2040050f20201000050f2020c00
IE: WPA Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Extra:rsn_ie=30180100000fac020200000fac04000fac020100000fac020c00
IE: IEEE 802.11i/WPA2 Version 1
Group Cipher : TKIP
Pairwise Ciphers (2) : CCMP TKIP
Authentication Suites (1) : PSK
Quality=50/100 Signal level=57/100
Cell 22 - Address: <MAC addr SLEEPY>
ESSID:"SLEEPY"
Protocol:IEEE 802.11bgn
Mode:Master
Frequency:2.462 GHz (Channel 11)
Encryption keyff
Bit Rates:144 Mb/s
Quality=58/100 Signal level=96/100


##### module infos #####

[8192cu]
filename: /lib/modules/3.13.0-32-generic/updates/dkms/8192cu.ko
version: v4.0.2_9000.20130911
author: Realtek Semiconductor Corp.
description: Realtek Wireless Lan Driver
license: GPL
srcversion: 98913FB8609F2F16E0996C2
alias: usb:v0BDAp8186d*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0789p016Dd*dc*dsc*dp*ic*isc*ip*in*
alias: usb:v0DF6p0070d*dc*dsc*dp*ic*isc*ip*in*
.
many alaises deleted
.
alias: usb:v0BDAp8191d*dc*dsc*dp*ic*isc*ip*in*
depends:
vermagic: 3.13.0-32-generic SMP mod_unload modversions 686
parm: rtw_ips_mode:The default IPS mode (int)
parm: ifname:The default name to allocate for first interface (charp)
parm: if2name:The default name to allocate for second interface (charp)
parm: rtw_initmac:charp
.
many parms deleted
.
parm: rtw_notch_filter:0isable, 1:Enable, 2:Enable only for P2P (uint)

##### module parameters #####

[8192cu]
if2name: wlan%d
ifname: wlan%d
rtw_80211d: 0
rtw_ampdu_amsdu: 0
rtw_ampdu_enable: 1
rtw_antdiv_cfg: 2
rtw_busy_thresh: 40
rtw_cbw40_enable: 3
rtw_channel: 1
rtw_channel_plan: 65
rtw_chip_version: 0
rtw_enusbss: 0
rtw_force_iol: N
rtw_ht_enable: 1
rtw_hwpdn_mode: 2
rtw_hwpwrp_detect: 0
rtw_hw_wps_pbc: 1
rtw_initmac: (null)
rtw_ips_mode: 1
rtw_lbkmode: 0
rtw_low_power: 0
rtw_lowrate_two_xmit: 1
rtw_mac_phy_mode: 0
rtw_max_roaming_times: 2
rtw_mc2u_disable: 0
rtw_mp_mode: 0
rtw_network_mode: 0
rtw_notch_filter: 0
rtw_power_mgnt: 1
rtw_rf_config: 5
rtw_rfintfs: 2
rtw_rx_stbc: 1
rtw_special_rf_path: 0
rtw_vcs_type: 1
rtw_vrtl_carrier_sense: 2
rtw_wifi_spec: 0
rtw_wmm_enable: 1

##### /etc/modules #####

lp
8192cu

##### blacklists #####

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
blacklist rtl8192cu

##### udev rules #####

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# USB device 0x:0x (rtl8192cu)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

########## wireless info END ############

In the above, my network is called "myNetwork" and I have changed the names of my neighbors networks to the names of the seven dwarfs.  I have also deleted a bunch of other network names.  

I am not quite a newbie with Linux but wireless is just something I am not accustomed to.

I have noticed a few things but I do not know how to change them.

1) udev rules do not have the right device name for the interface.  They have 
    
# USB device 0x:0x (rtl8192cu)

I think it should be 
# USB device 0x0b05:0x17ab(rtl8192cu)

If so, how do I change it permanently.

2)wlan0 seems to be broadcasting on channel 1 while my interface seems to be broadcasting on channel 11.  

Is this a problem?  If so, how do I solve it permanently?

3) I am not unused to typing commands but the graphical interface would be easier.  How do I download graphical network tools for the KDE inteface?  Should I instead use Gnome?

4) If I must use the console, how to I refer to my ESSID?  Is it "myNetwork" or just plain myNetwork without quotes?

5) What else have I done that is dumb?

6) How do you get the nice boxes around the code snippets?  They would make this much easier to read.


Thanks for any help.

--PatF

---

### Post by praseodym on 2014-08-10
Which of that three networks is yours? Try the fixed channel 1 and pure WPA2-AES (CCMP) encryption

---

