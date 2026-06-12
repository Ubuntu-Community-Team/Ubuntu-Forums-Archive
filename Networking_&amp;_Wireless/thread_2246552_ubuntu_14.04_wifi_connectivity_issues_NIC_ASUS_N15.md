---
title: "ubuntu 14.04 wifi connectivity issues NIC ASUS N15 driver trl8192ce"
date: 2014-10-01
forum: Networking &amp; Wireless
---

### Post by murtyvonna on 2014-10-01
After upgrading to UBUNTU 14.04 (fresh install), I have been facing wifi connectivity problems. Inially wifi is to get connected but there was no internet coonectivity. I have tried some suggestions and now there is no wifi connectivity. I had run the script as suggested and the result is given below:

########## wireless info START ##########

Report from: 01 Oct 2014 23:10 IST +0530

Booted last: 01 Oct 2014 21:55 IST +0530

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.0-36-generic #63-Ubuntu SMP Wed Sep 3 21:30:07 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b6]

05:00.0 IDE interface [0101]: JMicron Technology Corp. JMB368 IDE controller [197b:2368]

##### lsusb #############################

Bus 002 Device 003: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 048d:1336 Integrated Technology Express, Inc. SD/MMC Cardreader
Bus 001 Device 008: ID 12d1:14dc Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 3938:1031  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

##### lsmod #############################

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5a2c:80ff:fe13:9263/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:77456 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80250 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:66474810 (66.4 MB)  TX bytes:9760157 (9.7 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1

##### resolv.conf #######################

nameserver 127.0.1.1
search hi.link

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth1  [Wired connection 3] -------------------------------------------
  Type:              Wired
  Driver:            cdc_ether
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1
    DNS:             8.8.8.8
    DNS:             8.8.4.4

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

no-auto-default=<MAC address>,<MAC 'eth1' [IF]>,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Netone]] (600 root)
[connection] id=Netone | type=802-11-wireless
[802-11-wireless] ssid=Netone | bssid=<MAC address> | mac-address=F4:6D:04:A2:AC:87
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (6, 20)
	(2457 - 2482 @ 40), (6, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (6, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 160), (6, 20), PASSIVE-SCAN, NO-IBSS
	(5250 - 5330 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS
	(5490 - 5730 @ 160), (6, 20), DFS, PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

eth1      no frequency information.

lo        no frequency information.

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

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

[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=1
options rtl8192ce fwlps=0
options rtl8192ce swenc=1

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000010ECd00008176sv00000315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001139sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001629sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000169Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000016B3sd000010CFbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001786sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001A39sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002057sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002A57sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003824sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003874sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007185sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007611sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008175sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd0000185Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008194sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008197sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008204sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008205sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008206sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008207sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008208sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008209sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008210sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008211sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008212sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008213sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008214sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008215sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008216sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008217sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008218sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008219sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008220sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008221sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008222sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000824Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000084B5sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000874Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009196sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009197sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009204sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008177sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001178sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001400sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001401sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001402sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007622sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv000084B6sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008191sv*sd*bc*sc*i* ndiswrapper

[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee ips=0 fwlps=0

[/etc/modprobe.d/rtl8192ce.conf]
echo options rtl8192ce swlps=0 ips=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[   20.372652] cdc_ether 1-1.3:1.0 eth1: register 'cdc_ether' at usb-0000:00:1a.0-1.3, CDC Ethernet Device, <MAC 'eth1' [IF]>
[  779.096883] cdc_ether 1-1.3:1.0 eth1: unregister 'cdc_ether' usb-0000:00:1a.0-1.3, CDC Ethernet Device
[  792.707933] cdc_ether 1-1.3:1.0 eth1: register 'cdc_ether' at usb-0000:00:1a.0-1.3, CDC Ethernet Device, <MAC 'eth1' [IF]>

########## wireless info END ############
[COLOR="#0000FF"]**Would be gratedull if some solution comes.**[/COLOR]
Regards

---

### Post by murtyvonna on 2014-10-02
To day I have used " sudo modprobe rtl8192ce" command and the net work connection resumesds bt there is no INTERNET connection and Pingiing IP has 100% packet loss.
Regards

---

### Post by jeremy31 on 2014-10-02
Run the script again as the module was not loaded the first time ```
./wireless_script
```

---

### Post by murtyvonna on 2014-10-03
Thank you for guidence. Every time I have to start the wifi connection with the same modprobe command. As suggested I have run the script again:


########## wireless info START ##########

Report from: 03 Oct 2014 12:01 IST +0530

Booted last: 03 Oct 2014 11:25 IST +0530

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.13.9 #2 SMP Tue May 20 09:57:03 CDT 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: ASUSTeK Computer Inc. M4A785TD Motherboard [1043:83a3]
	Kernel driver in use: r8169

04:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8192CE PCIe Wireless Network Adapter [10ec:8178] (rev 01)
	Subsystem: ASUSTeK Computer Inc. Device [1043:84b6]
	Kernel driver in use: rtl8192ce

##### lsusb #############################

Bus 002 Device 003: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 048d:1336 Integrated Technology Express, Inc. SD/MMC Cardreader
Bus 001 Device 007: ID 12d1:14dc Huawei Technologies Co., Ltd. 
Bus 001 Device 003: ID 3938:1031  
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8192ce              53550  0 
rtl_pci                26690  1 rtl8192ce
rtlwifi                63475  2 rtl_pci,rtl8192ce
rtl8192c_common        53099  1 rtl8192ce
mac80211              626194  3 rtl_pci,rtlwifi,rtl8192ce
cfg80211              483865  2 mac80211,rtlwifi
ndiswrapper           283985  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet addr:192.168.1.100  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5a2c:80ff:fe13:9263/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:25374 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13635143 (13.6 MB)  TX bytes:3776305 (3.7 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::f66d:4ff:fea2:ac87/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:662 (662.0 B)  TX bytes:11153 (11.1 KB)

##### iwconfig ##########################

eth0      no wireless extensions.

eth1      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"Netone"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Netone' [AC1]>   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search hi.link

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Wi-Fi connection 1] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192ce
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Netone:         Infra, <MAC 'Netone' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 76 WPA2

  IPv4 Settings:
    Address:         192.168.1.2
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth1  [Auto Ethernet] ------------------------------------------------
  Type:              Wired
  Driver:            cdc_ether
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.100
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

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

no-auto-default=<MAC address>,<MAC 'eth1' [IF]>,<MAC 'eth0' [IF]>,

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=Netone
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Asia/Kolkata (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

eth1      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Netone' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=60/70  Signal level=-50 dBm  
                    Encryption key:on
                    ESSID:"Netone"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000000cf99671b
                    Extra: Last beacon: 64ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192ce]
filename:       /lib/modules/3.13.9/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfwU_B.bin
firmware:       rtlwifi/rtl8192cfwU.bin
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     BF8278DF19B67D7D6C6B8C5
depends:        rtlwifi,rtl_pci,rtl8192c-common,mac80211
intree:         Y
vermagic:       3.13.9 SMP mod_unload modversions 
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.13.9/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B6B8AA929B5F982954A6DE1
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.13.9 SMP mod_unload modversions 

[rtlwifi]
filename:       /lib/modules/3.13.9/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C21FC2F90947540319DE390
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.13.9 SMP mod_unload modversions 

[rtl8192c_common]
filename:       /lib/modules/3.13.9/kernel/drivers/net/wireless/rtlwifi/rtl8192c/rtl8192c-common.ko
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Ziv Huang	<ziv_huang@realtek.com>
author:         Georgia		<georgia@realtek.com>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     32F826C623BC49F764F7974
depends:        
intree:         Y
vermagic:       3.13.9 SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/3.13.9/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
intree:         Y
vermagic:       3.13.9 SMP mod_unload modversions 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.9/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
intree:         Y
vermagic:       3.13.9 SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ndiswrapper]
filename:       /lib/modules/3.13.9/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     DC1EFD919FDF2DB80D424C6
depends:        
vermagic:       3.13.9 SMP mod_unload modversions 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #################

[rtl8192ce]
debug: 0
fwlps: N
ips: N
swenc: Y
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

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

[/etc/modprobe.d/modprobe.conf]
options rtl8192ce ips=1
options rtl8192ce fwlps=0
options rtl8192ce swenc=1

[/etc/modprobe.d/ndiswrapper.conf]
alias pci:v000010ECd00008176sv00000315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001139sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001629sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000169Fsd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000016B3sd000010CFbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001786sd0000103Cbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00001A39sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002057sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002315sd00001A32bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00002A57sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003824sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00003874sd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00006195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007177sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007179sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007180sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007181sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007182sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007185sd0000144Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00007611sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008175sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008176sd0000185Fbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008194sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008197sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008204sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008205sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008206sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008207sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008208sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008209sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008210sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008211sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008212sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008213sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008214sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008215sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008216sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008217sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008218sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008219sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008220sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008221sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00008222sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000824Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv000084B5sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv0000874Asd00001462bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009150sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009176sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009181sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009182sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009184sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009185sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009186sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009187sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009192sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009193sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009194sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009195sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009196sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009197sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009198sd00001028bc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009199sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009200sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009201sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009202sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009203sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv00009204sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008176sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008177sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001178sd00001A3Bbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001400sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001401sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00001402sd00001B9Abc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00006180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00007622sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008186sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008189sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00008191sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv000084B6sd00001043bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009178sd000010ECbc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009179sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv00009180sd00001025bc*sc*i* ndiswrapper
alias pci:v000010ECd00008178sv*sd*bc*sc*i* ndiswrapper
alias pci:v000010ECd00008191sv*sd*bc*sc*i* ndiswrapper

[/etc/modprobe.d/rtl8188ee.conf]
options rtl8188ee ips=0 fwlps=0

[/etc/modprobe.d/rtl8192ce.conf]
 options rtl8192ce swlps=0 ips=0
 echo options rtl8192ce swlps=0 ips=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8178 (rtl8192ce)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (cdc_ether)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[  136.891394] cdc_ether 1-1.3:1.0 eth1: register 'cdc_ether' at usb-0000:00:1a.0-1.3, CDC Ethernet Device, <MAC 'eth1' [IF]>
[ 1189.566136] rtl8192ce: rtl8192ce: Power Save off (module option)
[ 1189.566140] rtl8192ce: rtl8192ce: FW Power Save off (module option)
[ 1189.566146] rtl8192ce: Using firmware rtlwifi/rtl8192cfw.bin
[ 1189.614697] ieee80211 phy0: Selected rate control algorithm 'rtl_rc'
[ 1189.615010] rtlwifi: wireless switch is on
[ 1189.962354] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[ 1190.866841] wlan0: authenticate with <MAC 'Netone' [AC1]>
[ 1190.866944] wlan0: send auth to <MAC 'Netone' [AC1]> (try 1/3)
[ 1190.869822] wlan0: authenticated
[ 1190.869953] rtl8192ce 0000:04:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1190.869957] rtl8192ce 0000:04:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1190.870170] wlan0: associate with <MAC 'Netone' [AC1]> (try 1/3)
[ 1190.874253] wlan0: RX AssocResp from <MAC 'Netone' [AC1]> (capab=0x411 status=0 aid=1)
[ 1190.874310] wlan0: associated
[ 1190.874334] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1190.950431]  [<ffffffffa04ca3ad>] ? rtl_is_special_data+0x2d/0x110 [rtlwifi]

########## wireless info END ############

Regards

---

### Post by jeremy31 on 2014-10-03
I am not sure why that module is not loading by itself but ```
echo rtl8192ce | sudo tee -a /etc/modules
```

Try to use code tags around terminal outputs so that the format is preserved,  [ code ] terminal output [ /code ]  without the spaces around code and in the advanced reply window there is the # that will place the code tags in the reply window

---

### Post by murtyvonna on 2014-10-03
murtyvonna@Asus-System-Product-Name:~$ echo rtl8192ce | sudo tee -a /etc/modules
[sudo] password for murtyvonna: 
rtl8192ce
murtyvonna@Asus-System-Product-Name:~$

---

### Post by jeremy31 on 2014-10-03
> **murtyvonna said:**
> murtyvonna@Asus-System-Product-Name:~$ echo rtl8192ce | sudo tee -a /etc/modules
[sudo] password for murtyvonna: 
rtl8192ce
murtyvonna@Asus-System-Product-Name:~$
It should load on its own now

---

### Post by murtyvonna on 2014-10-03
Thank you for the reply. It is not getting loaded automatically. Kindly go through the command prompt for finding out the cause of not automatically loading. 

murtyvonna@Asus-System-Product-Name:~$ sudo modprobe rtl8192ce
[sudo] password for murtyvonna: 
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/rtl8192ce.conf line 2: ignoring bad line starting with 'echo'
murtyvonna@Asus-System-Product-Name:~$sudo nano etc/modeprob.d/rtl8192ce.conf
The ouput is : 
 blank
Regards

---

### Post by jeremy31 on 2014-10-03
> **murtyvonna said:**
> Thank you for the reply. It is not getting loaded automatically. Kindly go through the command prompt for finding out the cause of not automatically loading. 

murtyvonna@Asus-System-Product-Name:~$ sudo modprobe rtl8192ce
[sudo] password for murtyvonna: 
libkmod: ERROR ../libkmod/libkmod-config.c:686 kmod_config_parse: /etc/modprobe.d/rtl8192ce.conf line 2: ignoring bad line starting with 'echo'
murtyvonna@Asus-System-Product-Name:~$sudo nano etc/modeprob.d/rtl8192ce.conf
The ouput is : 
 blank
Regards

```
sudo nano /etc/modprobe.d/rtl8192ce.conf
```
One of the lines in that file probably starts with echo, so just delete that line since it is the same as the line above

---

### Post by murtyvonna on 2014-10-03
Thank you for the help. Now the main problem of connecting to the web sites or onternest is remaining. I have this problem from the day UBUBTU up grading to 14.04.
Any help?
Regards

---

### Post by murtyvonna on 2014-10-03
Thank you for the help. Now the main problem of connecting to the web sites or onternest is remaining. I have this problem from the day UBUBTU is upgraded to 14.04. Any help?
Regards

---

### Post by jeremy31 on 2014-10-03
Unplug the ethernet cable, check to make sure wifi is connected and ```
ping -c3 8.8.8.8
``````
ping -c3 google.com
```

---

### Post by murtyvonna on 2014-10-03
Thank you for the suggetion. I trieds but no help. Now I have changed the WIFi router and it is fine. Connectivity is notmal. The problem appear to tobe with the frequency of the earlier router. The thread may kindly be closed.Once again thanks for the guidance.
Regards

---

### Post by jeremy31 on 2014-10-03
> **murtyvonna said:**
> Thank you for the suggetion. I trieds but no help. Now I have changed the WIFi router and it is fine. Connectivity is notmal. The problem appear to tobe with the frequency of the earlier router. The thread may kindly be closed.Once again thanks for the guidance.
Regards

Good to hear you found the issue.  You can click on "edit post" for your first post in the thread and add [SOLVED] or [CLOSED] to the thread's title

---

