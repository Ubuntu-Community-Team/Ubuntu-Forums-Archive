---
title: "Uubuntu 14.4 / Netgear wna3100 problem"
date: 2015-04-13
forum: Networking &amp; Wireless
---

### Post by kowo2 on 2015-04-13
Hi at firs sorry for my grammar as I am not a native speaker.
I tried install USB WIFI Netgear wna3100 EXTERNAL WIFI , because I have read that I have to use external wifi on the one one motherboard ,I did install driver and everything but no succes.
I will appreciate any kind of help.
This is my output /system doesn't recognize my usb ....


```

########## wireless info START ##########


Report from: 13 Apr 2015 21:46 IST +0100


Booted last: 12 Apr 2015 03:26 IST +0100


Script from: 06 Apr 2015 17:23 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.16.0-30-generic #40~14.04.1-Ubuntu SMP Thu Jan 15 17:43:14 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, quiet, splash


##### desktop ###########################


Ubuntu


##### lspci #############################


02:01.0 Ethernet controller [0200]: Advanced Micro Devices, Inc. [AMD] 79c970 [PCnet32 LANCE] [1022:2000] (rev 10)
    Subsystem: Advanced Micro Devices, Inc. [AMD] PCnet - Fast 79C971 [1022:2000]
    Kernel driver in use: pcnet32


##### lsusb #############################


Bus 001 Device 004: ID 0bda:0129 Realtek Semiconductor Corp. RTS5129 Card Reader Controller
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 0e0f:0008 VMware, Inc. 
Bus 002 Device 003: ID 0e0f:0002 VMware, Inc. Virtual USB Hub
Bus 002 Device 002: ID 0e0f:0003 VMware, Inc. Virtual Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


##### lsmod #############################


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.93.131  Bcast:192.168.93.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:29ff:fe38:1371/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8866 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4329 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11565884 (11.5 MB)  TX bytes:252311 (252.3 KB)
          Interrupt:19 Base address:0x2000 


##### iwconfig ##########################


eth0      no wireless extensions.


lo        no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.93.2    0.0.0.0         UG    0      0        0 eth0
192.168.93.0    0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search localdomain


##### NetworkManager info ###############


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            pcnet32
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.93.131
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.93.2


    DNS:             192.168.93.2


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


##### iw reg get ########################


Region: Europe/Dublin (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (6, 20)
    (2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN
    (2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN
    (5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN
    (5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN
    (5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN


##### iwlist channels ###################


eth0      no frequency information.


lo        no frequency information.


##### iwlist scan #######################


eth0      Interface doesn't support scanning.


lo        Interface doesn't support scanning.


##### module infos ######################


##### module parameters #################


##### /etc/modules ######################


lp
rtc


##### modprobe options ##################


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


[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


grep: /etc/udev/rules.d/*net*.rules: No such file or directory


##### dmesg #############################


########## wireless info END ############

```

---

### Post by michi1983 on 2015-04-16
Well it could be that the stick is damaged or the USB port you are using.
Have you tried another USB port?

---

