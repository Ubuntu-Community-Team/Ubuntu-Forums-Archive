---
title: "Ubuntu 14.04 Wifi networks visible but can't connect"
date: 2014-08-09
forum: Networking &amp; Wireless
---

### Post by F._Magikian on 2014-08-09
Hello: I am on my second attempt at utilizing wifi on a toshiba Tecra. Prior to installing Ubuntu 14.04, wifi functioned fie on windows XP. I am able to see wifi networks but am unable to connect. Below, I have included information created using "wireless_script" recommended on this site.
Fumio

```

########## wireless info START ##########
Report from: 09 Aug 2014 17:31 EDT -0400
Script from: 04 Aug 2014 18:47 UTC +0000
##### release #####
Distributor ID: Ubuntu
Description: Ubuntu 14.04 LTS
Release: 14.04
Codename: trusty
##### kernel #####
Linux 3.13.0-24-generic #46-Ubuntu SMP Thu Apr 10 19:08:14 UTC 2014 i686 i686 i686 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=7
##### desktop #####
Ubuntu
##### lspci #####
01:08.0 Ethernet controller [0200]: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller [8086:103d] (rev 83)
 Subsystem: Toshiba America Info Systems Device [1179:0001]
 Kernel driver in use: e100
##### lsusb #####
Bus 001 Device 002: ID 058f:6331 Alcor Micro Corp. SD/MMC/MS Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
##### PCMCIA Card Info #####
PRODID_1="TOSHIBA
"
PRODID_2="Wireless LAN Card
"
PRODID_3="Version 01.01
"
PRODID_4=""
MANFID=0156,0002
FUNCID=6
PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255
##### rfkill #####
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
##### lsmod #####
wmi                    18673  1 toshiba_acpi
##### interfaces #####
auto lo
iface lo inet loopback
##### ifconfig #####
eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
eth1      Link encap:Ethernet  HWaddr <MAC addr eth1>  
          inet6 addr: fe80::202:2dff:fe7e:9939/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:738 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:78966 (78.9 KB)  TX bytes:6048 (6.0 KB)
          Interrupt:11 Base address:0xc100 
##### iwconfig #####
lo        no wireless extensions.
eth0      no wireless extensions.
eth1      IEEE 802.11b  ESSID:"homelibrary"  
          Mode:Managed  Frequency:2.427 GHz  Access Point: <MAC address>   
          Bit Rate:11 Mb/s   Sensitivity:1/0  
          Retry limit:8   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-42 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:70
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
##### route #####
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
##### resolv.conf #####
##### nm-tool #####
NetworkManager Tool
State: disconnected
- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr eth1>
  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
  Wireless Access Points 
- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            e100
  State:             unavailable
  Default:           no
  HW Address:        <MAC addr eth0>
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
##### iw reg get #####
country 00:
 (2402 - 2472 @ 40), (3, 20)
 (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
 (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
 (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
 (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
##### iwlist channels #####
lo        no frequency information.
eth0      no frequency information.
eth1      11 channels in total; available frequencies :
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
          Current Frequency=2.427 GHz (Channel 4)
##### iwlist scan #####
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
eth1      Interface doesn't support scanning : Device or resource busy
##### module infos #####
##### module parameters #####
##### /etc/modules #####
lp
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
##### udev rules #####
# PCI device 0x8086:0x103d (e100)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCMCIA device 0x0002:0x0156 (orinoco_cs)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth1>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"
##### dmesg #####
[    1.630494] e100: Intel(R) PRO/100 Network Driver, 3.5.24-k2-NAPI
[   17.804485] type=1400 audit(1407615299.962:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=326 comm="apparmor_parser"
[   17.805790] type=1400 audit(1407615299.962:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=326 comm="apparmor_parser"
[   23.739949] type=1400 audit(1407615305.893:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=728 comm="apparmor_parser"
[   23.758259] type=1400 audit(1407615305.913:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=728 comm="apparmor_parser"
[   25.400959] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   25.402030] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[  189.496234] eth1: Lucent/Agere firmware doesn't support manual roaming
[  189.638488] eth1: New link status: Connected (0001)
[  189.638531] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[  190.388331] eth1: Information frame lost.
[  190.772407] eth1: Information frame lost.
[  190.780329] eth1: Information frame lost.
[  190.873607] eth1: Information frame lost.
[  190.963751] eth1: Information frame lost.
[  190.989723] eth1: Information frame lost.
[  191.214491] eth1: Information frame lost.
[  191.448332] eth1: Information frame lost.
[  191.465158] eth1: Information frame lost.
[  191.608359] eth1: Information frame lost.
[  197.876765] eth1: Information frame lost.
[  199.650093] eth1: Information frame lost.
[  199.657325] eth1: Information frame lost.
[  199.668467] eth1: Information frame lost.
[  199.675801] eth1: Information frame lost.
[  199.684518] eth1: Information frame lost.
[  199.692112] eth1: Information frame lost.
[  199.702464] eth1: Information frame lost.
[  199.714242] eth1: Information frame lost.
[  199.723990] eth1: Information frame lost.
[  200.068120] eth1: Lucent/Agere firmware doesn't support manual roaming
[  205.081520] eth1: Information frame lost.
[  205.089316] eth1: Information frame lost.
[  205.099490] eth1: Information frame lost.
[  205.106648] eth1: Information frame lost.
[  205.113828] eth1: Information frame lost.
[  205.124085] eth1: Information frame lost.
[  205.134354] eth1: Information frame lost.
[  205.145717] eth1: Information frame lost.
[  205.155864] eth1: Information frame lost.
[  205.181529] eth1: Information frame lost.
[  210.411696] eth1: Information frame lost.
[  210.413332] eth1: Information frame lost.
[  210.429705] eth1: Information frame lost.
[  210.436861] eth1: Information frame lost.
[  210.447115] eth1: Information frame lost.
[  210.457529] eth1: Information frame lost.
[  210.467641] eth1: Information frame lost.
[  210.477883] eth1: Information frame lost.
[  210.485048] eth1: Information frame lost.
[  210.492226] eth1: Information frame lost.
[  217.276184] eth1: New link status: Disconnected (0002)
[  217.285316] eth1: Information frame lost.
[  217.292152] eth1: Information frame lost.
[  217.302440] eth1: Information frame lost.
[  217.309606] eth1: Information frame lost.
[  217.319828] eth1: Information frame lost.
[  217.339351] eth1: Information frame lost.
[  217.346513] eth1: Information frame lost.
[  217.353687] eth1: Information frame lost.
[  217.360867] eth1: Information frame lost.
[  217.377289] eth1: Information frame lost.
[  217.465165] eth1: New link status: Connected (0001)
[  222.589931] eth1: Information frame lost.
[  222.591257] eth1: Information frame lost.
[  222.598834] eth1: Information frame lost.
[  222.615251] eth1: Information frame lost.
[  222.626141] eth1: Information frame lost.
[  222.636785] eth1: Information frame lost.
[  222.650098] eth1: Information frame lost.
[  222.661470] eth1: Information frame lost.
[  222.668532] eth1: Information frame lost.
[  222.675714] eth1: Information frame lost.
[  222.844196] eth1: Lucent/Agere firmware doesn't support manual roaming
[  227.858588] eth1: Information frame lost.
[  227.866584] eth1: Information frame lost.
[  227.876741] eth1: Information frame lost.
[  227.883917] eth1: Information frame lost.
[  227.891093] eth1: Information frame lost.
[  227.898277] eth1: Information frame lost.
[  227.912293] eth1: Information frame lost.
[  227.919793] eth1: Information frame lost.
[  227.935225] eth1: Information frame lost.
[  227.951601] eth1: Information frame lost.
[  233.148446] eth1: Information frame lost.
[  233.149216] eth1: Information frame lost.
[  233.162883] eth1: Information frame lost.
[  233.170041] eth1: Information frame lost.
[  233.180817] eth1: Information frame lost.
[  233.191597] eth1: Information frame lost.
[  233.209258] eth1: Information frame lost.
[  233.225413] eth1: Information frame lost.
[  233.233180] eth1: Information frame lost.
[  233.241940] eth1: Information frame lost.
[  238.287964] eth1: Information frame lost.
[  238.288790] eth1: Information frame lost.
[  238.296240] eth1: Information frame lost.
[  238.303430] eth1: Information frame lost.
[  238.313704] eth1: Information frame lost.
[  238.323962] eth1: Information frame lost.
[  238.331125] eth1: Information frame lost.
[  238.338304] eth1: Information frame lost.
[  238.348551] eth1: Information frame lost.
[  238.355721] eth1: Information frame lost.
[  238.516199] eth1: Lucent/Agere firmware doesn't support manual roaming
[  243.530657] eth1: Information frame lost.
[  243.538302] eth1: Information frame lost.
[  243.560864] eth1: Information frame lost.
[  243.568043] eth1: Information frame lost.
[  243.575217] eth1: Information frame lost.
[  243.582385] eth1: Information frame lost.
[  243.620325] eth1: Information frame lost.
[  243.630606] eth1: Information frame lost.
[  243.648938] eth1: Information frame lost.
[  243.665460] eth1: Information frame lost.
[  253.888735] eth1: Information frame lost.
[  255.780173] eth1: New link status: Disconnected (0002)
[  255.787726] eth1: Information frame lost.
[  255.794550] eth1: Information frame lost.
[  255.804830] eth1: Information frame lost.
[  255.812006] eth1: Information frame lost.
[  255.822655] eth1: Information frame lost.
[  255.841735] eth1: Information frame lost.
[  255.851975] eth1: Information frame lost.
[  255.868365] eth1: Information frame lost.
[  255.875545] eth1: Information frame lost.
[  255.968638] eth1: New link status: Connected (0001)
[  268.170439] eth1: New link status: Disconnected (0002)
[  268.178724] eth1: Information frame lost.
[  268.186089] eth1: Information frame lost.
[  268.196344] eth1: Information frame lost.
[  268.203527] eth1: Information frame lost.
[  268.213287] eth1: Information frame lost.
[  268.232172] eth1: Information frame lost.
[  268.242501] eth1: Information frame lost.
[  268.258925] eth1: Information frame lost.
[  268.284545] eth1: Information frame lost.
[  268.307103] eth1: Information frame lost.
[  268.368564] eth1: New link status: Connected (0001)
[  274.939121] eth1: New link status: Disconnected (0002)
[  274.948493] eth1: Information frame lost.
[  274.955620] eth1: Information frame lost.
[  274.984324] eth1: Information frame lost.
[  274.994592] eth1: Information frame lost.
[  275.004834] eth1: Information frame lost.
[  275.012020] eth1: Information frame lost.
[  275.019195] eth1: Information frame lost.
[  275.032942] eth1: Information frame lost.
[  275.042787] eth1: Information frame lost.
[  275.065373] eth1: Information frame lost.
[  275.158849] eth1: New link status: Connected (0001)
[  287.474415] eth1: New link status: Disconnected (0002)
[  287.483854] eth1: Information frame lost.
[  287.490786] eth1: Information frame lost.
[  287.501064] eth1: Information frame lost.
[  287.511301] eth1: Information frame lost.
[  287.518460] eth1: Information frame lost.
[  287.530820] eth1: Information frame lost.
[  287.542242] eth1: Information frame lost.
[  287.552308] eth1: Information frame lost.
[  287.559480] eth1: Information frame lost.
[  287.585627] eth1: Information frame lost.
[  287.715441] eth1: New link status: Connected (0001)
[  299.917721] eth1: New link status: Disconnected (0002)
[  299.926005] eth1: Information frame lost.
[  299.934713] eth1: Information frame lost.
[  299.944874] eth1: Information frame lost.
[  299.953328] eth1: Information frame lost.
[  299.960247] eth1: Information frame lost.
[  299.982806] eth1: Information frame lost.
[  300.005376] eth1: Information frame lost.
[  300.015623] eth1: Information frame lost.
[  300.023961] eth1: Information frame lost.
[  300.040220] eth1: Information frame lost.
[  300.141205] eth1: New link status: Connected (0001)
[  312.369446] eth1: New link status: Disconnected (0002)
[  312.378792] eth1: Information frame lost.
[  312.385591] eth1: Information frame lost.
[  312.395868] eth1: Information frame lost.
[  312.403034] eth1: Information frame lost.
[  312.410212] eth1: Information frame lost.
[  312.420459] eth1: Information frame lost.
[  312.430724] eth1: Information frame lost.
[  312.442582] eth1: Information frame lost.
[  312.453273] eth1: Information frame lost.
[  312.469707] eth1: Information frame lost.
[  312.638435] eth1: New link status: Connected (0001)
[  317.891194] eth1: Information frame lost.
[  324.835407] eth1: New link status: Disconnected (0002)
[  324.844696] eth1: Information frame lost.
[  324.853096] eth1: Information frame lost.
[  324.860247] eth1: Information frame lost.
[  324.867439] eth1: Information frame lost.
[  324.874607] eth1: Information frame lost.
[  324.896088] eth1: Information frame lost.
[  324.912560] eth1: Information frame lost.
[  324.922820] eth1: Information frame lost.
[  324.930568] eth1: Information frame lost.
[  325.000818] eth1: New link status: Connected (0001)
[  337.227721] eth1: New link status: Disconnected (0002)
[  337.237241] eth1: Information frame lost.
[  337.246021] eth1: Information frame lost.
[  337.259383] eth1: Information frame lost.
[  337.278870] eth1: Information frame lost.
[  337.286025] eth1: Information frame lost.
[  337.297788] eth1: Information frame lost.
[  337.307573] eth1: Information frame lost.
[  337.317090] eth1: Information frame lost.
[  337.323961] eth1: Information frame lost.
[  337.354850] eth1: Information frame lost.
[  337.498380] eth1: New link status: Connected (0001)
[  349.796157] eth1: New link status: Disconnected (0002)
[  349.804402] eth1: Information frame lost.
[  349.814442] eth1: Information frame lost.
[  349.822082] eth1: Information frame lost.
[  349.831684] eth1: Information frame lost.
[  349.838703] eth1: Information frame lost.
[  349.845659] eth1: Information frame lost.
[  349.858742] eth1: Information frame lost.
[  349.873525] eth1: Information frame lost.
[  349.880525] eth1: Information frame lost.
[  349.908917] eth1: Information frame lost.
[  350.032562] eth1: New link status: Connected (0001)
[  362.285379] eth1: New link status: Disconnected (0002)
[  362.293621] eth1: Information frame lost.
[  362.302135] eth1: Information frame lost.
[  362.309191] eth1: Information frame lost.
[  362.316366] eth1: Information frame lost.
[  362.323541] eth1: Information frame lost.
[  362.339982] eth1: Information frame lost.
[  362.347150] eth1: Information frame lost.
[  362.354322] eth1: Information frame lost.
[  362.361503] eth1: Information frame lost.
[  362.391935] eth1: Information frame lost.
[  362.501954] eth1: New link status: Connected (0001)
[  368.073741] eth1: Information frame lost.
[  368.075193] eth1: Information frame lost.
[  368.091476] eth1: Information frame lost.
[  368.098639] eth1: Information frame lost.
[  368.109727] eth1: Information frame lost.
[  368.120176] eth1: Information frame lost.
[  368.131497] eth1: Information frame lost.
[  368.139553] eth1: Information frame lost.
[  368.171420] eth1: Information frame lost.
[  368.178583] eth1: Information frame lost.
[  374.714673] eth1: New link status: Disconnected (0002)
[  374.724329] eth1: Information frame lost.
[  374.731712] eth1: Information frame lost.
[  374.748127] eth1: Information frame lost.
[  374.758378] eth1: Information frame lost.
[  374.765546] eth1: Information frame lost.
[  374.776634] eth1: Information frame lost.
[  374.787108] eth1: Information frame lost.
[  374.797346] eth1: Information frame lost.
[  374.820108] eth1: Information frame lost.
[  374.839366] eth1: Information frame lost.
[  374.996719] eth1: New link status: Connected (0001)
[  387.246532] eth1: New link status: Disconnected (0002)
[  387.254926] eth1: Information frame lost.
[  387.261675] eth1: Information frame lost.
[  387.271968] eth1: Information frame lost.
[  387.279123] eth1: Information frame lost.
[  387.286299] eth1: Information frame lost.
[  387.293476] eth1: Information frame lost.
[  387.300659] eth1: Information frame lost.
[  387.313251] eth1: Information frame lost.
[  387.321194] eth1: Information frame lost.
[  387.347012] eth1: Information frame lost.
[  387.505417] eth1: New link status: Connected (0001)
[  394.009102] eth1: Information frame lost.
[  394.010552] eth1: Information frame lost.
[  394.017666] eth1: Information frame lost.
[  394.024833] eth1: Information frame lost.
[  394.032006] eth1: Information frame lost.
[  394.042289] eth1: Information frame lost.
[  394.049463] eth1: Information frame lost.
[  394.072023] eth1: Information frame lost.
[  394.100749] eth1: Information frame lost.
[  394.107910] eth1: Information frame lost.
[  399.722470] eth1: New link status: Disconnected (0002)
[  399.730859] eth1: Information frame lost.
[  399.738243] eth1: Information frame lost.
[  399.748631] eth1: Information frame lost.
[  399.755794] eth1: Information frame lost.
[  399.762970] eth1: Information frame lost.
[  399.773215] eth1: Information frame lost.
[  399.780394] eth1: Information frame lost.
[  399.790671] eth1: Information frame lost.
[  399.803979] eth1: Information frame lost.
[  399.823372] eth1: Information frame lost.
[  400.005852] eth1: New link status: Connected (0001)
[  412.160790] eth1: New link status: Disconnected (0002)
[  412.169118] eth1: Information frame lost.
[  412.177220] eth1: Information frame lost.
[  412.187388] eth1: Information frame lost.
[  412.194546] eth1: Information frame lost.
[  412.201726] eth1: Information frame lost.
[  412.211991] eth1: Information frame lost.
[  412.222226] eth1: Information frame lost.
[  412.230572] eth1: Information frame lost.
[  412.237785] eth1: Information frame lost.
[  412.260183] eth1: Information frame lost.
[  412.371641] eth1: New link status: Connected (0001)
[  424.559137] eth1: New link status: Disconnected (0002)
[  424.568631] eth1: Information frame lost.
[  424.577129] eth1: Information frame lost.
[  424.590234] eth1: Information frame lost.
[  424.597402] eth1: Information frame lost.
[  424.605721] eth1: Information frame lost.
[  424.612775] eth1: Information frame lost.
[  424.623042] eth1: Information frame lost.
[  424.633306] eth1: Information frame lost.
[  424.663098] eth1: Information frame lost.
[  424.681558] eth1: Information frame lost.
[  424.785379] eth1: New link status: Connected (0001)
[  437.086461] eth1: New link status: Disconnected (0002)
[  437.096301] eth1: Information frame lost.
[  437.109944] eth1: Information frame lost.
[  437.132478] eth1: Information frame lost.
[  437.139650] eth1: Information frame lost.
[  437.146710] eth1: Information frame lost.
[  437.154012] eth1: Information frame lost.
[  437.170417] eth1: Information frame lost.
[  437.180665] eth1: Information frame lost.
[  437.195598] eth1: Information frame lost.
[  437.216657] eth1: Information frame lost.
[  437.330817] eth1: New link status: Connected (0001)
[  445.900975] eth1: Information frame lost.
[  449.561434] eth1: New link status: Disconnected (0002)
[  449.569770] eth1: Information frame lost.
[  449.577380] eth1: Information frame lost.
[  449.587644] eth1: Information frame lost.
[  449.594808] eth1: Information frame lost.
[  449.601983] eth1: Information frame lost.
[  449.615340] eth1: Information frame lost.
[  449.622510] eth1: Information frame lost.
[  449.633997] eth1: Information frame lost.
[  449.640967] eth1: Information frame lost.
[  449.750287] eth1: New link status: Connected (0001)
[  461.963022] eth1: New link status: Disconnected (0002)
[  461.972565] eth1: Information frame lost.
[  461.980199] eth1: Information frame lost.
[  461.990557] eth1: Information frame lost.
[  461.998482] eth1: Information frame lost.
[  462.005807] eth1: Information frame lost.
[  462.022368] eth1: Information frame lost.
[  462.032594] eth1: Information frame lost.
[  462.040033] eth1: Information frame lost.
[  462.068782] eth1: Information frame lost.
[  462.086934] eth1: Information frame lost.
[  462.292406] eth1: New link status: Connected (0001)
[  470.006879] eth1: Information frame lost.
[  470.009195] eth1: Information frame lost.
[  470.017897] eth1: Information frame lost.
[  470.024802] eth1: Information frame lost.
[  470.035409] eth1: Information frame lost.
[  470.048409] eth1: Information frame lost.
[  470.072165] eth1: Information frame lost.
[  470.079128] eth1: Information frame lost.
[  470.088297] eth1: Information frame lost.
[  470.095528] eth1: Information frame lost.
[  474.512442] eth1: New link status: Disconnected (0002)
[  474.703110] eth1: New link status: Connected (0001)
[  475.027496] eth1: Information frame lost.
[  475.054658] eth1: Information frame lost.
[  481.276499] eth1: New link status: Disconnected (0002)
[  481.286927] eth1: Information frame lost.
[  481.294183] eth1: Information frame lost.
[  481.304455] eth1: Information frame lost.
[  481.311617] eth1: Information frame lost.
[  481.318682] eth1: Information frame lost.
[  481.332121] eth1: Information frame lost.
[  481.339293] eth1: Information frame lost.
[  481.349576] eth1: Information frame lost.
[  481.356740] eth1: Information frame lost.
[  481.382386] eth1: Information frame lost.
[  481.495726] eth1: New link status: Connected (0001)
[  493.706413] eth1: New link status: Disconnected (0002)
[  493.716015] eth1: Information frame lost.
[  493.723738] eth1: Information frame lost.
[  493.734017] eth1: Information frame lost.
[  493.741172] eth1: Information frame lost.
[  493.748346] eth1: Information frame lost.
[  493.766810] eth1: Information frame lost.
[  493.777064] eth1: Information frame lost.
[  493.786891] eth1: Information frame lost.
[  493.796976] eth1: Information frame lost.
[  493.834484] eth1: Information frame lost.
[  494.003774] eth1: New link status: Connected (0001)
[  523.008105] eth1: Information frame lost.
[  523.009723] eth1: Information frame lost.
[  523.023062] eth1: Information frame lost.
[  523.030511] eth1: Information frame lost.
[  523.041464] eth1: Information frame lost.
[  523.051717] eth1: Information frame lost.
[  523.061941] eth1: Information frame lost.
[  523.072211] eth1: Information frame lost.
[  523.079381] eth1: Information frame lost.
[  523.086583] eth1: Information frame lost.
[  523.133841] eth1: New link status: Disconnected (0002)
[  523.383066] eth1: New link status: Connected (0001)
[  535.610162] eth1: New link status: Disconnected (0002)
[  535.618582] eth1: Information frame lost.
[  535.626354] eth1: Information frame lost.
[  535.637127] eth1: Information frame lost.
[  535.644281] eth1: Information frame lost.
[  535.651456] eth1: Information frame lost.
[  535.661720] eth1: Information frame lost.
[  535.675057] eth1: Information frame lost.
[  535.684375] eth1: Information frame lost.
[  535.698403] eth1: Information frame lost.
[  535.715030] eth1: Information frame lost.
[  535.896624] eth1: New link status: Connected (0001)
[  548.309474] eth1: New link status: Disconnected (0002)
[  548.317802] eth1: Information frame lost.
[  548.324907] eth1: Information frame lost.
[  548.332094] eth1: Information frame lost.
[  548.339255] eth1: Information frame lost.
[  548.346428] eth1: Information frame lost.
[  548.361482] eth1: Information frame lost.
[  548.385417] eth1: Information frame lost.
[  548.392831] eth1: Information frame lost.
[  548.399725] eth1: Information frame lost.
[  548.425917] eth1: Information frame lost.
[  548.625634] eth1: New link status: Connected (0001)
[  560.874806] eth1: New link status: Disconnected (0002)
[  560.883185] eth1: Information frame lost.
[  560.890761] eth1: Information frame lost.
[  560.897936] eth1: Information frame lost.
[  560.905103] eth1: Information frame lost.
[  560.912276] eth1: Information frame lost.
[  560.928686] eth1: Information frame lost.
[  560.954347] eth1: Information frame lost.
[  560.963892] eth1: Information frame lost.
[  560.970731] eth1: Information frame lost.
[  560.993198] eth1: Information frame lost.
[  561.090243] eth1: New link status: Connected (0001)
[  586.005547] eth1: Information frame lost.
[  586.008326] eth1: Information frame lost.
[  586.016003] eth1: Information frame lost.
[  586.023174] eth1: Information frame lost.
[  586.033345] eth1: Information frame lost.
[  586.043713] eth1: Information frame lost.
[  586.053961] eth1: Information frame lost.
[  586.073416] eth1: Information frame lost.
[  586.099043] eth1: Information frame lost.
[  586.106206] eth1: Information frame lost.
[  586.147765] eth1: New link status: Disconnected (0002)
[  586.322164] eth1: New link status: Connected (0001)
[  598.563775] eth1: New link status: Disconnected (0002)
[  598.573031] eth1: Information frame lost.
[  598.579806] eth1: Information frame lost.
[  598.611591] eth1: Information frame lost.
[  598.621844] eth1: Information frame lost.
[  598.632093] eth1: Information frame lost.
[  598.639265] eth1: Information frame lost.
[  598.652599] eth1: Information frame lost.
[  598.663300] eth1: Information frame lost.
[  598.679269] eth1: Information frame lost.
[  598.705564] eth1: Information frame lost.
[  598.954002] eth1: New link status: Connected (0001)
[  611.314091] eth1: New link status: Disconnected (0002)
[  611.323419] eth1: Information frame lost.
[  611.331030] eth1: Information frame lost.
[  611.341326] eth1: Information frame lost.
[  611.348476] eth1: Information frame lost.
[  611.355650] eth1: Information frame lost.
[  611.365896] eth1: Information frame lost.
[  611.379235] eth1: Information frame lost.
[  611.386397] eth1: Information frame lost.
[  611.402806] eth1: Information frame lost.
[  611.423822] eth1: Information frame lost.
[  611.515627] eth1: New link status: Connected (0001)
[  623.738426] eth1: New link status: Disconnected (0002)
[  623.746847] eth1: Information frame lost.
[  623.754453] eth1: Information frame lost.
[  623.764725] eth1: Information frame lost.
[  623.771888] eth1: Information frame lost.
[  623.785223] eth1: Information frame lost.
[  623.798587] eth1: Information frame lost.
[  623.833431] eth1: Information frame lost.
[  623.843674] eth1: Information frame lost.
[  623.860075] eth1: Information frame lost.
[  623.876490] eth1: Information frame lost.
[  623.937549] eth1: New link status: Connected (0001)
[  649.006815] eth1: Information frame lost.
[  649.008254] eth1: Information frame lost.
[  649.015261] eth1: Information frame lost.
[  649.025047] eth1: Information frame lost.
[  649.038005] eth1: Information frame lost.
[  649.048064] eth1: Information frame lost.
[  649.055230] eth1: Information frame lost.
[  649.067632] eth1: Information frame lost.
[  649.074728] eth1: Information frame lost.
[  649.081914] eth1: Information frame lost.
[  649.127762] eth1: New link status: Disconnected (0002)
[  649.348084] eth1: New link status: Connected (0001)
[  661.545394] eth1: New link status: Disconnected (0002)
[  661.553724] eth1: Information frame lost.
[  661.574047] eth1: Information frame lost.
[  661.587256] eth1: Information frame lost.
[  661.594430] eth1: Information frame lost.
[  661.601610] eth1: Information frame lost.
[  661.612488] eth1: Information frame lost.
[  661.620079] eth1: Information frame lost.
[  661.630321] eth1: Information frame lost.
[  661.643657] eth1: Information frame lost.
[  661.663178] eth1: Information frame lost.
[  661.950120] eth1: New link status: Connected (0001)
[  674.148712] eth1: New link status: Disconnected (0002)
[  674.161751] eth1: Information frame lost.
[  674.172211] eth1: Information frame lost.
[  674.182881] eth1: Information frame lost.
[  674.190046] eth1: Information frame lost.
[  674.197228] eth1: Information frame lost.
[  674.208117] eth1: Information frame lost.
[  674.227983] eth1: Information frame lost.
[  674.236496] eth1: Information frame lost.
[  674.258738] eth1: Information frame lost.
[  674.282318] eth1: Information frame lost.
[  674.412722] eth1: New link status: Connected (0001)
[  686.651043] eth1: New link status: Disconnected (0002)
[  686.661001] eth1: Information frame lost.
[  686.669396] eth1: Information frame lost.
[  686.679973] eth1: Information frame lost.
[  686.687128] eth1: Information frame lost.
[  686.694308] eth1: Information frame lost.
[  686.704573] eth1: Information frame lost.
[  686.714828] eth1: Information frame lost.
[  686.724908] eth1: Information frame lost.
[  686.735308] eth1: Information frame lost.
[  686.754782] eth1: Information frame lost.
[  686.818878] eth1: New link status: Connected (0001)
[  693.347841] eth1: New link status: Disconnected (0002)
[  693.357445] eth1: Information frame lost.
[  693.364428] eth1: Information frame lost.
[  693.374716] eth1: Information frame lost.
[  693.381870] eth1: Information frame lost.
[  693.389050] eth1: Information frame lost.
[  693.399312] eth1: Information frame lost.
[  693.406482] eth1: Information frame lost.
[  693.413664] eth1: Information frame lost.
[  693.420843] eth1: Information frame lost.
[  693.437265] eth1: Information frame lost.
[  693.578443] eth1: New link status: Connected (0001)
[  701.909642] eth1: Information frame lost.
[  705.781014] eth1: New link status: Disconnected (0002)
[  705.789320] eth1: Information frame lost.
[  705.797041] eth1: Information frame lost.
[  705.807323] eth1: Information frame lost.
[  705.814484] eth1: Information frame lost.
[  705.821661] eth1: Information frame lost.
[  705.831926] eth1: Information frame lost.
[  705.845256] eth1: Information frame lost.
[  705.852415] eth1: Information frame lost.
[  705.859594] eth1: Information frame lost.
[  705.968067] eth1: New link status: Connected (0001)
[  712.005549] eth1: Information frame lost.
[  712.007864] eth1: Information frame lost.
[  712.014919] eth1: Information frame lost.
[  712.022720] eth1: Information frame lost.
[  712.033387] eth1: Information frame lost.
[  712.043632] eth1: Information frame lost.
[  712.053867] eth1: Information frame lost.
[  712.065654] eth1: Information frame lost.
[  712.084637] eth1: Information frame lost.
[  712.091787] eth1: Information frame lost.
[  718.172480] eth1: New link status: Disconnected (0002)
[  718.180841] eth1: Information frame lost.
[  718.200918] eth1: Information frame lost.
[  718.214263] eth1: Information frame lost.
[  718.221426] eth1: Information frame lost.
[  718.231670] eth1: Information frame lost.
[  718.241801] eth1: Information frame lost.
[  718.255255] eth1: Information frame lost.
[  718.269505] eth1: Information frame lost.
[  718.282941] eth1: Information frame lost.
[  718.306606] eth1: Information frame lost.
[  718.420235] eth1: New link status: Connected (0001)
[  730.620669] eth1: New link status: Disconnected (0002)
[  730.629019] eth1: Information frame lost.
[  730.636522] eth1: Information frame lost.
[  730.648149] eth1: Information frame lost.
[  730.654987] eth1: Information frame lost.
[  730.662170] eth1: Information frame lost.
[  730.670908] eth1: Information frame lost.
[  730.681662] eth1: Information frame lost.
[  730.692471] eth1: Information frame lost.
[  730.716682] eth1: Information frame lost.
[  730.739071] eth1: Information frame lost.
[  730.911744] eth1: New link status: Connected (0001)
[  743.128333] eth1: New link status: Disconnected (0002)
[  743.136679] eth1: Information frame lost.
[  743.143931] eth1: Information frame lost.
[  743.157267] eth1: Information frame lost.
[  743.164444] eth1: Information frame lost.
[  743.171606] eth1: Information frame lost.
[  743.184967] eth1: Information frame lost.
[  743.192131] eth1: Information frame lost.
[  743.203099] eth1: Information frame lost.
[  743.215936] eth1: Information frame lost.
[  743.270384] eth1: Information frame lost.
[  743.322827] eth1: New link status: Connected (0001)
[  755.512342] eth1: New link status: Disconnected (0002)
[  755.520669] eth1: Information frame lost.
[  755.528199] eth1: Information frame lost.
[  755.535471] eth1: Information frame lost.
[  755.542643] eth1: Information frame lost.
[  755.549821] eth1: Information frame lost.
[  755.560093] eth1: Information frame lost.
[  755.567265] eth1: Information frame lost.
[  755.574446] eth1: Information frame lost.
[  755.581624] eth1: Information frame lost.
[  755.598054] eth1: Information frame lost.
[  755.778282] eth1: New link status: Connected (0001)
[  768.047492] eth1: New link status: Disconnected (0002)
[  768.056837] eth1: Information frame lost.
[  768.067339] eth1: Information frame lost.
[  768.077736] eth1: Information frame lost.
[  768.087953] eth1: Information frame lost.
[  768.095114] eth1: Information frame lost.
[  768.109017] eth1: Information frame lost.
[  768.116666] eth1: Information frame lost.
[  768.127029] eth1: Information frame lost.
[  768.149484] eth1: Information frame lost.
[  768.165898] eth1: Information frame lost.
[  768.306628] eth1: New link status: Connected (0001)
[  775.007840] eth1: Information frame lost.
[  775.009421] eth1: Information frame lost.
[  775.016196] eth1: Information frame lost.
[  775.025620] eth1: Information frame lost.
[  775.037915] eth1: Information frame lost.
[  775.047964] eth1: Information frame lost.
[  775.059340] eth1: Information frame lost.
[  775.069509] eth1: Information frame lost.
[  775.076675] eth1: Information frame lost.
[  775.090783] eth1: Information frame lost.
[  780.544998] eth1: New link status: Disconnected (0002)
[  780.555103] eth1: Information frame lost.
[  780.565663] eth1: Information frame lost.
[  780.578993] eth1: Information frame lost.
[  780.586063] eth1: Information frame lost.
[  780.593340] eth1: Information frame lost.
[  780.600512] eth1: Information frame lost.
[  780.616951] eth1: Information frame lost.
[  780.631770] eth1: Information frame lost.
[  780.641534] eth1: Information frame lost.
[  780.657976] eth1: Information frame lost.
[  780.824025] eth1: New link status: Connected (0001)
[  792.985323] eth1: New link status: Disconnected (0002)
[  792.993315] eth1: Information frame lost.
[  793.002553] eth1: Information frame lost.
[  793.013511] eth1: Information frame lost.
[  793.020790] eth1: Information frame lost.
[  793.027966] eth1: Information frame lost.
[  793.038232] eth1: Information frame lost.
[  793.045402] eth1: Information frame lost.
[  793.055667] eth1: Information frame lost.
[  793.062725] eth1: Information frame lost.
[  793.091536] eth1: Information frame lost.
[  793.226318] eth1: New link status: Connected (0001)
[  805.383663] eth1: New link status: Disconnected (0002)
[  805.393345] eth1: Information frame lost.
[  805.401102] eth1: Information frame lost.
[  805.420588] eth1: Information frame lost.
[  805.430843] eth1: Information frame lost.
[  805.438005] eth1: Information frame lost.
[  805.448266] eth1: Information frame lost.
[  805.457107] eth1: Information frame lost.
[  805.467769] eth1: Information frame lost.
[  805.475826] eth1: Information frame lost.
[  805.492383] eth1: Information frame lost.
[  805.597066] eth1: New link status: Connected (0001)
[  817.817000] eth1: New link status: Disconnected (0002)
[  817.828111] eth1: Information frame lost.
[  817.835654] eth1: Information frame lost.
[  817.842946] eth1: Information frame lost.
[  817.854302] eth1: Information frame lost.
[  817.864469] eth1: Information frame lost.
[  817.871641] eth1: Information frame lost.
[  817.891127] eth1: Information frame lost.
[  817.903712] eth1: Information frame lost.
[  817.919883] eth1: Information frame lost.
[  818.000924] eth1: Information frame lost.
[  818.200423] eth1: New link status: Connected (0001)
[  830.381315] eth1: New link status: Disconnected (0002)
[  830.389973] eth1: Information frame lost.
[  830.397453] eth1: Information frame lost.
[  830.407732] eth1: Information frame lost.
[  830.417954] eth1: Information frame lost.
[  830.425114] eth1: Information frame lost.
[  830.435391] eth1: Information frame lost.
[  830.443952] eth1: Information frame lost.
[  830.453825] eth1: Information frame lost.
[  830.461905] eth1: Information frame lost.
[  830.478452] eth1: Information frame lost.
[  830.568814] eth1: New link status: Connected (0001)
[  838.005584] eth1: Information frame lost.
[  838.007059] eth1: Information frame lost.
[  838.014405] eth1: Information frame lost.
[  838.021567] eth1: Information frame lost.
[  838.031850] eth1: Information frame lost.
[  838.042095] eth1: Information frame lost.
[  838.052331] eth1: Information frame lost.
[  838.062605] eth1: Information frame lost.
[  838.085152] eth1: Information frame lost.
[  838.092319] eth1: Information frame lost.
[  842.914643] eth1: New link status: Disconnected (0002)
[  843.016545] eth1: Information frame lost.
[  843.026805] eth1: Information frame lost.
[  843.038563] eth1: Information frame lost.
[  843.096504] eth1: Information frame lost.
[  843.098795] eth1: New link status: Connected (0001)
[  843.107897] eth1: Information frame lost.
[  843.114985] eth1: Information frame lost.
[  843.125279] eth1: Information frame lost.
[  843.132429] eth1: Information frame lost.
[  843.140472] eth1: Information frame lost.
[  843.153973] eth1: Information frame lost.
[  901.007209] eth1: Information frame lost.
[  901.011677] eth1: Information frame lost.
[  901.023303] eth1: Information frame lost.
[  901.030567] eth1: Information frame lost.
[  901.040830] eth1: Information frame lost.
[  901.051082] eth1: Information frame lost.
[  901.061315] eth1: Information frame lost.
[  901.074653] eth1: Information frame lost.
[  901.085509] eth1: Information frame lost.
[  901.099248] eth1: Information frame lost.
[  901.170449] eth1: New link status: Disconnected (0002)
[  901.361575] eth1: New link status: Connected (0001)
[  913.527852] eth1: New link status: Disconnected (0002)
[  913.537228] eth1: Information frame lost.
[  913.544109] eth1: Information frame lost.
[  913.554043] eth1: Information frame lost.
[  913.564580] eth1: Information frame lost.
[  913.571741] eth1: Information frame lost.
[  913.588155] eth1: Information frame lost.
[  913.595324] eth1: Information frame lost.
[  913.605590] eth1: Information frame lost.
[  913.612754] eth1: Information frame lost.
[  913.635328] eth1: Information frame lost.
[  913.700590] eth1: New link status: Connected (0001)
[  925.903187] eth1: New link status: Disconnected (0002)
[  925.913927] eth1: Information frame lost.
[  925.921298] eth1: Information frame lost.
[  925.928479] eth1: Information frame lost.
[  925.935639] eth1: Information frame lost.
[  925.943783] eth1: Information frame lost.
[  925.954122] eth1: Information frame lost.
[  925.961292] eth1: Information frame lost.
[  925.971560] eth1: Information frame lost.
[  925.978720] eth1: Information frame lost.
[  926.007333] eth1: Information frame lost.
[  926.091332] eth1: New link status: Connected (0001)
[  938.302515] eth1: New link status: Disconnected (0002)
[  938.310911] eth1: Information frame lost.
[  938.317944] eth1: Information frame lost.
[  938.337442] eth1: Information frame lost.
[  938.348707] eth1: Information frame lost.
[  938.355861] eth1: Information frame lost.
[  938.366140] eth1: Information frame lost.
[  938.373194] eth1: Information frame lost.
[  938.383573] eth1: Information frame lost.
[  938.392481] eth1: Information frame lost.
[  938.415362] eth1: Information frame lost.
[  938.481980] eth1: New link status: Connected (0001)
[  950.685850] eth1: New link status: Disconnected (0002)
[  950.694182] eth1: Information frame lost.
[  950.702935] eth1: Information frame lost.
[  950.709621] eth1: Information frame lost.
[  950.716787] eth1: Information frame lost.
[  950.723954] eth1: Information frame lost.
[  950.734232] eth1: Information frame lost.
[  950.744467] eth1: Information frame lost.
[  950.754713] eth1: Information frame lost.
[  950.761891] eth1: Information frame lost.
[  950.787557] eth1: Information frame lost.
[  950.872680] eth1: New link status: Connected (0001)
[  963.075188] eth1: New link status: Disconnected (0002)
[  963.084857] eth1: Information frame lost.
[  963.091887] eth1: Information frame lost.
[  963.102167] eth1: Information frame lost.
[  963.109206] eth1: Information frame lost.
[  963.116711] eth1: Information frame lost.
[  963.127284] eth1: Information frame lost.
[  963.134955] eth1: Information frame lost.
[  963.145201] eth1: Information frame lost.
[  963.152378] eth1: Information frame lost.
[  963.178035] eth1: Information frame lost.
[  963.263493] eth1: New link status: Connected (0001)
[  975.468517] eth1: New link status: Disconnected (0002)
[  975.476842] eth1: Information frame lost.
[  975.484544] eth1: Information frame lost.
[  975.497880] eth1: Information frame lost.
[  975.508138] eth1: Information frame lost.
[  975.516011] eth1: Information frame lost.
[  975.526582] eth1: Information frame lost.
[  975.536866] eth1: Information frame lost.
[  975.544156] eth1: Information frame lost.
[  975.554268] eth1: Information frame lost.
[  975.580965] eth1: Information frame lost.
[  975.654072] eth1: New link status: Connected (0001)
[  987.855763] eth1: New link status: Disconnected (0002)
[  987.865135] eth1: Information frame lost.
[  987.871942] eth1: Information frame lost.
[  987.882222] eth1: Information frame lost.
[  987.889384] eth1: Information frame lost.
[  987.896562] eth1: Information frame lost.
[  987.909909] eth1: Information frame lost.
[  987.917075] eth1: Information frame lost.
[  987.927342] eth1: Information frame lost.
[  987.934510] eth1: Information frame lost.
[  987.960148] eth1: Information frame lost.
[  988.044652] eth1: New link status: Connected (0001)
[ 1000.247186] eth1: New link status: Disconnected (0002)
[ 1000.258544] eth1: Information frame lost.
[ 1000.265651] eth1: Information frame lost.
[ 1000.275939] eth1: Information frame lost.
[ 1000.283091] eth1: Information frame lost.
[ 1000.290274] eth1: Information frame lost.
[ 1000.300540] eth1: Information frame lost.
[ 1000.307704] eth1: Information frame lost.
[ 1000.317955] eth1: Information frame lost.
[ 1000.325134] eth1: Information frame lost.
[ 1000.350787] eth1: Information frame lost.
[ 1000.435555] eth1: New link status: Connected (0001)
[ 1012.740423] eth1: New link status: Disconnected (0002)
[ 1012.748908] eth1: Information frame lost.
[ 1012.756528] eth1: Information frame lost.
[ 1012.782164] eth1: Information frame lost.
[ 1012.793467] eth1: Information frame lost.
[ 1012.800610] eth1: Information frame lost.
[ 1012.807787] eth1: Information frame lost.
[ 1012.822100] eth1: Information frame lost.
[ 1012.832414] eth1: Information frame lost.
[ 1012.840403] eth1: Information frame lost.
[ 1012.861214] eth1: Information frame lost.
[ 1013.049005] eth1: New link status: Connected (0001)
[ 1025.309760] eth1: New link status: Disconnected (0002)
[ 1025.318363] eth1: Information frame lost.
[ 1025.331532] eth1: Information frame lost.
[ 1025.341807] eth1: Information frame lost.
[ 1025.348972] eth1: Information frame lost.
[ 1025.356153] eth1: Information frame lost.
[ 1025.366406] eth1: Information frame lost.
[ 1025.392093] eth1: Information frame lost.
[ 1025.402373] eth1: Information frame lost.
[ 1025.414185] eth1: Information frame lost.
[ 1025.441252] eth1: Information frame lost.
[ 1025.595449] eth1: New link status: Connected (0001)
[ 1037.774180] eth1: New link status: Disconnected (0002)
[ 1037.788005] eth1: Information frame lost.
[ 1037.799279] eth1: Information frame lost.
[ 1037.813443] eth1: Information frame lost.
[ 1037.820681] eth1: Information frame lost.
[ 1037.828197] eth1: Information frame lost.
[ 1037.835027] eth1: Information frame lost.
[ 1037.842212] eth1: Information frame lost.
[ 1037.852490] eth1: Information frame lost.
[ 1037.868875] eth1: Information frame lost.
[ 1037.888363] eth1: Information frame lost.
[ 1037.973262] eth1: New link status: Connected (0001)
[ 1050.259494] eth1: New link status: Disconnected (0002)
[ 1050.269017] eth1: Information frame lost.
[ 1050.285978] eth1: Information frame lost.
[ 1050.296195] eth1: Information frame lost.
[ 1050.306478] eth1: Information frame lost.
[ 1050.316702] eth1: Information frame lost.
[ 1050.327027] eth1: Information frame lost.
[ 1050.349555] eth1: Information frame lost.
[ 1050.359817] eth1: Information frame lost.
[ 1050.373073] eth1: Information frame lost.
[ 1050.426439] eth1: Information frame lost.
[ 1050.537969] eth1: New link status: Connected (0001)
[ 1062.740825] eth1: New link status: Disconnected (0002)
[ 1062.749173] eth1: Information frame lost.
[ 1062.756482] eth1: Information frame lost.
[ 1062.767810] eth1: Information frame lost.
[ 1062.774954] eth1: Information frame lost.
[ 1062.782131] eth1: Information frame lost.
[ 1062.792377] eth1: Information frame lost.
[ 1062.824181] eth1: Information frame lost.
[ 1062.834440] eth1: Information frame lost.
[ 1062.841602] eth1: Information frame lost.
[ 1062.864174] eth1: Information frame lost.
[ 1062.960354] eth1: New link status: Connected (0001)
[ 1075.226159] eth1: New link status: Disconnected (0002)
[ 1075.234546] eth1: Information frame lost.
[ 1075.243187] eth1: Information frame lost.
[ 1075.253733] eth1: Information frame lost.
[ 1075.263955] eth1: Information frame lost.
[ 1075.274197] eth1: Information frame lost.
[ 1075.290609] eth1: Information frame lost.
[ 1075.319323] eth1: Information frame lost.
[ 1075.329594] eth1: Information frame lost.
[ 1075.336258] eth1: Information frame lost.
[ 1075.353067] eth1: Information frame lost.
[ 1075.443025] eth1: New link status: Connected (0001)
[ 1087.632541] eth1: New link status: Disconnected (0002)
[ 1087.640893] eth1: Information frame lost.
[ 1087.648357] eth1: Information frame lost.
[ 1087.658606] eth1: Information frame lost.
[ 1087.665777] eth1: Information frame lost.
[ 1087.672945] eth1: Information frame lost.
[ 1087.693291] eth1: Information frame lost.
[ 1087.703730] eth1: Information frame lost.
[ 1087.710888] eth1: Information frame lost.
[ 1087.718068] eth1: Information frame lost.
[ 1087.740640] eth1: Information frame lost.
[ 1087.793209] eth1: New link status: Connected (0001)
[ 1100.046881] eth1: New link status: Disconnected (0002)
[ 1100.055287] eth1: Information frame lost.
[ 1100.062519] eth1: Information frame lost.
[ 1100.072815] eth1: Information frame lost.
[ 1100.079967] eth1: Information frame lost.
[ 1100.087147] eth1: Information frame lost.
[ 1100.097410] eth1: Information frame lost.
[ 1100.106958] eth1: Information frame lost.
[ 1100.116862] eth1: Information frame lost.
[ 1100.133294] eth1: Information frame lost.
[ 1100.151083] eth1: Information frame lost.
[ 1100.310441] eth1: New link status: Connected (0001)
[ 1112.632155] eth1: New link status: Disconnected (0002)
[ 1112.640181] eth1: Information frame lost.
[ 1112.650920] eth1: Information frame lost.
[ 1112.661295] eth1: Information frame lost.
[ 1112.671548] eth1: Information frame lost.
[ 1112.683654] eth1: Information frame lost.
[ 1112.691016] eth1: Information frame lost.
[ 1112.698195] eth1: Information frame lost.
[ 1112.708473] eth1: Information frame lost.
[ 1112.743317] eth1: Information frame lost.
[ 1112.760990] eth1: Information frame lost.
[ 1112.911427] eth1: New link status: Connected (0001)
[ 1125.081474] eth1: New link status: Disconnected (0002)
[ 1125.089145] eth1: Information frame lost.
[ 1125.096913] eth1: Information frame lost.
[ 1125.107178] eth1: Information frame lost.
[ 1125.114229] eth1: Information frame lost.
[ 1125.121519] eth1: Information frame lost.
[ 1125.131799] eth1: Information frame lost.
[ 1125.145112] eth1: Information frame lost.
[ 1125.155377] eth1: Information frame lost.
[ 1125.164114] eth1: Information frame lost.
[ 1125.187134] eth1: Information frame lost.
[ 1125.265208] eth1: New link status: Connected (0001)
[ 1137.472816] eth1: New link status: Disconnected (0002)
[ 1137.482260] eth1: Information frame lost.
[ 1137.489543] eth1: Information frame lost.
[ 1137.506293] eth1: Information frame lost.
[ 1137.516202] eth1: Information frame lost.
[ 1137.523365] eth1: Information frame lost.
[ 1137.536718] eth1: Information frame lost.
[ 1137.543885] eth1: Information frame lost.
[ 1137.554166] eth1: Information frame lost.
[ 1137.562891] eth1: Information frame lost.
[ 1137.585947] eth1: Information frame lost.
[ 1137.657780] eth1: New link status: Connected (0001)
[ 1149.870568] eth1: New link status: Disconnected (0002)
[ 1149.878975] eth1: Information frame lost.
[ 1149.886186] eth1: Information frame lost.
[ 1149.897151] eth1: Information frame lost.
[ 1149.904655] eth1: Information frame lost.
[ 1149.911927] eth1: Information frame lost.
[ 1149.922212] eth1: Information frame lost.
[ 1149.939818] eth1: Information frame lost.
[ 1149.949866] eth1: Information frame lost.
[ 1149.957042] eth1: Information frame lost.
[ 1149.976528] eth1: Information frame lost.
[ 1150.123704] eth1: New link status: Connected (0001)
[ 1162.402471] eth1: New link status: Disconnected (0002)
[ 1162.411275] eth1: Information frame lost.
[ 1162.418435] eth1: Information frame lost.
[ 1162.428715] eth1: Information frame lost.
[ 1162.438716] eth1: Information frame lost.
[ 1162.449188] eth1: Information frame lost.
[ 1162.459469] eth1: Information frame lost.
[ 1162.469698] eth1: Information frame lost.
[ 1162.480256] eth1: Information frame lost.
[ 1162.493270] eth1: Information frame lost.
[ 1162.500447] eth1: Information frame lost.
[ 1162.604641] eth1: New link status: Connected (0001)
[ 1174.883804] eth1: New link status: Disconnected (0002)
[ 1174.894619] eth1: Information frame lost.
[ 1174.905225] eth1: Information frame lost.
[ 1174.930978] eth1: Information frame lost.
[ 1174.938140] eth1: Information frame lost.
[ 1174.947420] eth1: Information frame lost.
[ 1174.954549] eth1: Information frame lost.
[ 1174.964813] eth1: Information frame lost.
[ 1174.977132] eth1: Information frame lost.
[ 1174.990443] eth1: Information frame lost.
[ 1175.012983] eth1: Information frame lost.
[ 1175.168595] eth1: New link status: Connected (0001)
[ 1187.343141] eth1: New link status: Disconnected (0002)
[ 1187.351531] eth1: Information frame lost.
[ 1187.358331] eth1: Information frame lost.
[ 1187.377820] eth1: Information frame lost.
[ 1187.384986] eth1: Information frame lost.
[ 1187.392159] eth1: Information frame lost.
[ 1187.400716] eth1: Information frame lost.
[ 1187.413710] eth1: Information frame lost.
[ 1187.423976] eth1: Information frame lost.
[ 1187.432030] eth1: Information frame lost.
[ 1187.454720] eth1: Information frame lost.
[ 1187.575116] eth1: New link status: Connected (0001)
[ 1199.751466] eth1: New link status: Disconnected (0002)
[ 1199.760971] eth1: Information frame lost.
[ 1199.768419] eth1: Information frame lost.
[ 1199.791010] eth1: Information frame lost.
[ 1199.798162] eth1: Information frame lost.
[ 1199.805342] eth1: Information frame lost.
[ 1199.824835] eth1: Information frame lost.
[ 1199.831999] eth1: Information frame lost.
[ 1199.842245] eth1: Information frame lost.
[ 1199.849420] eth1: Information frame lost.
[ 1199.872018] eth1: Information frame lost.
[ 1199.976919] eth1: New link status: Connected (0001)
[ 1212.167792] eth1: New link status: Disconnected (0002)
[ 1212.177850] eth1: Information frame lost.
[ 1212.185594] eth1: Information frame lost.
[ 1212.209226] eth1: Information frame lost.
[ 1212.216351] eth1: Information frame lost.
[ 1212.223520] eth1: Information frame lost.
[ 1212.233782] eth1: Information frame lost.
[ 1212.244046] eth1: Information frame lost.
[ 1212.256640] eth1: Information frame lost.
[ 1212.263517] eth1: Information frame lost.
[ 1212.292271] eth1: Information frame lost.
[ 1212.490967] eth1: New link status: Connected (0001)
[ 1224.763854] eth1: New link status: Disconnected (0002)
[ 1224.773547] eth1: Information frame lost.
[ 1224.781045] eth1: Information frame lost.
[ 1224.791337] eth1: Information frame lost.
[ 1224.798594] eth1: Information frame lost.
[ 1224.808837] eth1: Information frame lost.
[ 1224.831421] eth1: Information frame lost.
[ 1224.838587] eth1: Information frame lost.
[ 1224.850593] eth1: Information frame lost.
[ 1224.861154] eth1: Information frame lost.
[ 1224.891661] eth1: Information frame lost.
[ 1225.071596] eth1: New link status: Connected (0001)
[ 1279.021444] eth1: Information frame lost.
[ 1279.022872] eth1: Information frame lost.
[ 1279.030364] eth1: Information frame lost.
[ 1279.037531] eth1: Information frame lost.
[ 1279.047820] eth1: Information frame lost.
[ 1279.058063] eth1: Information frame lost.
[ 1279.080621] eth1: Information frame lost.
[ 1279.093942] eth1: Information frame lost.
[ 1279.104178] eth1: Information frame lost.
[ 1279.112707] eth1: Information frame lost.
[ 1279.157174] eth1: New link status: Disconnected (0002)
[ 1279.494012] eth1: New link status: Connected (0001)
[ 1291.732526] eth1: New link status: Disconnected (0002)
[ 1291.742264] eth1: Information frame lost.
[ 1291.749061] eth1: Information frame lost.
[ 1291.759323] eth1: Information frame lost.
[ 1291.773759] eth1: Information frame lost.
[ 1291.780843] eth1: Information frame lost.
[ 1291.791120] eth1: Information frame lost.
[ 1291.802555] eth1: Information frame lost.
[ 1291.812582] eth1: Information frame lost.
[ 1291.822879] eth1: Information frame lost.
[ 1291.845475] eth1: Information frame lost.
[ 1291.923444] eth1: New link status: Connected (0001)
[ 1304.125861] eth1: New link status: Disconnected (0002)
[ 1304.135275] eth1: Information frame lost.
[ 1304.142608] eth1: Information frame lost.
[ 1304.152900] eth1: Information frame lost.
[ 1304.166195] eth1: Information frame lost.
[ 1304.173360] eth1: Information frame lost.
[ 1304.183631] eth1: Information frame lost.
[ 1304.193885] eth1: Information frame lost.
[ 1304.204135] eth1: Information frame lost.
[ 1304.217461] eth1: Information frame lost.
[ 1304.243124] eth1: Information frame lost.
[ 1304.403076] eth1: New link status: Connected (0001)
[ 1316.601197] eth1: New link status: Disconnected (0002)
[ 1316.608958] eth1: Information frame lost.
[ 1316.616155] eth1: Information frame lost.
[ 1316.626384] eth1: Information frame lost.
[ 1316.633540] eth1: Information frame lost.
[ 1316.640729] eth1: Information frame lost.
[ 1316.656719] eth1: Information frame lost.
[ 1316.690921] eth1: Information frame lost.
[ 1316.698111] eth1: Information frame lost.
[ 1316.708369] eth1: Information frame lost.
[ 1316.725882] eth1: Information frame lost.
[ 1316.830024] eth1: New link status: Connected (0001)
[ 1342.005568] eth1: Information frame lost.
[ 1342.007883] eth1: Information frame lost.
[ 1342.016606] eth1: Information frame lost.
[ 1342.026417] eth1: Information frame lost.
[ 1342.033575] eth1: Information frame lost.
[ 1342.043857] eth1: Information frame lost.
[ 1342.054974] eth1: Information frame lost.
[ 1342.063985] eth1: Information frame lost.
[ 1342.071505] eth1: Information frame lost.
[ 1342.081768] eth1: Information frame lost.
[ 1342.113817] eth1: New link status: Disconnected (0002)
[ 1342.256628] eth1: New link status: Connected (0001)
[ 1354.458165] eth1: New link status: Disconnected (0002)
[ 1354.466575] eth1: Information frame lost.
[ 1354.474318] eth1: Information frame lost.
[ 1354.484612] eth1: Information frame lost.
[ 1354.491764] eth1: Information frame lost.
[ 1354.498824] eth1: Information frame lost.
[ 1354.506120] eth1: Information frame lost.
[ 1354.513306] eth1: Information frame lost.
[ 1354.523572] eth1: Information frame lost.
[ 1354.530734] eth1: Information frame lost.
[ 1354.556379] eth1: Information frame lost.
[ 1354.693609] eth1: New link status: Connected (0001)
[ 1367.979435] eth1: New link status: Disconnected (0002)
[ 1367.989090] eth1: Information frame lost.
[ 1367.996447] eth1: Information frame lost.
[ 1368.006707] eth1: Information frame lost.
[ 1368.013980] eth1: Information frame lost.
[ 1368.021160] eth1: Information frame lost.
[ 1368.034501] eth1: Information frame lost.
[ 1368.041672] eth1: Information frame lost.
[ 1368.048849] eth1: Information frame lost.
[ 1368.056028] eth1: Information frame lost.
[ 1368.081029] eth1: Information frame lost.
[ 1368.224387] eth1: New link status: Connected (0001)
[ 1380.421050] eth1: New link status: Disconnected (0002)
[ 1380.429381] eth1: Information frame lost.
[ 1380.436208] eth1: Information frame lost.
[ 1380.443427] eth1: Information frame lost.
[ 1380.450479] eth1: Information frame lost.
[ 1380.457770] eth1: Information frame lost.
[ 1380.468045] eth1: Information frame lost.
[ 1380.484039] eth1: Information frame lost.
[ 1380.494705] eth1: Information frame lost.
[ 1380.517232] eth1: Information frame lost.
[ 1380.533659] eth1: Information frame lost.
[ 1380.733778] eth1: New link status: Connected (0001)
[ 1393.126087] eth1: New link status: Disconnected (0002)
[ 1393.135031] eth1: Information frame lost.
[ 1393.142509] eth1: Information frame lost.
[ 1393.152793] eth1: Information frame lost.
[ 1393.159955] eth1: Information frame lost.
[ 1393.167135] eth1: Information frame lost.
[ 1393.177400] eth1: Information frame lost.
[ 1393.184571] eth1: Information frame lost.
[ 1393.191746] eth1: Information frame lost.
[ 1393.198927] eth1: Information frame lost.
[ 1393.218408] eth1: Information frame lost.
[ 1393.272339] eth1: New link status: Connected (0001)
[ 1405.006853] eth1: Information frame lost.
[ 1405.008297] eth1: Information frame lost.
[ 1405.015499] eth1: Information frame lost.
[ 1405.023682] eth1: Information frame lost.
[ 1405.034005] eth1: Information frame lost.
[ 1405.044170] eth1: Information frame lost.
[ 1405.051429] eth1: Information frame lost.
[ 1405.066424] eth1: Information frame lost.
[ 1405.073963] eth1: Information frame lost.
[ 1405.081142] eth1: Information frame lost.
[ 1405.455422] eth1: New link status: Disconnected (0002)
[ 1405.735671] eth1: New link status: Connected (0001)
[ 1417.998719] eth1: New link status: Disconnected (0002)
[ 1418.009674] eth1: Information frame lost.
[ 1418.016982] eth1: Information frame lost.
[ 1418.027266] eth1: Information frame lost.
[ 1418.034429] eth1: Information frame lost.
[ 1418.044694] eth1: Information frame lost.
[ 1418.055989] eth1: Information frame lost.
[ 1418.063121] eth1: Information frame lost.
[ 1418.073381] eth1: Information frame lost.
[ 1418.081760] eth1: Information frame lost.
[ 1418.104160] eth1: Information frame lost.
[ 1418.177453] eth1: New link status: Connected (0001)
[ 1430.390019] eth1: New link status: Disconnected (0002)
[ 1430.400975] eth1: Information frame lost.
[ 1430.408573] eth1: Information frame lost.
[ 1430.415853] eth1: Information frame lost.
[ 1430.422920] eth1: Information frame lost.
[ 1430.430202] eth1: Information frame lost.
[ 1430.440478] eth1: Information frame lost.
[ 1430.450730] eth1: Information frame lost.
[ 1430.460985] eth1: Information frame lost.
[ 1430.472117] eth1: Information frame lost.
[ 1430.494814] eth1: Information frame lost.
[ 1430.567005] eth1: New link status: Connected (0001)
[ 1468.005506] eth1: Information frame lost.
[ 1468.006957] eth1: Information frame lost.
[ 1468.015664] eth1: Information frame lost.
[ 1468.025064] eth1: Information frame lost.
[ 1468.032056] eth1: Information frame lost.
[ 1468.042323] eth1: Information frame lost.
[ 1468.055242] eth1: Information frame lost.
[ 1468.068977] eth1: Information frame lost.
[ 1468.079213] eth1: Information frame lost.
[ 1468.086380] eth1: Information frame lost.
[ 1468.125134] eth1: New link status: Disconnected (0002)
[ 1468.376944] eth1: New link status: Connected (0001)
[ 1480.539389] eth1: New link status: Disconnected (0002)
[ 1480.548822] eth1: Information frame lost.
[ 1480.555905] eth1: Information frame lost.
[ 1480.563082] eth1: Information frame lost.
[ 1480.570247] eth1: Information frame lost.
[ 1480.579661] eth1: Information frame lost.
[ 1480.586643] eth1: Information frame lost.
[ 1480.597182] eth1: Information frame lost.
[ 1480.607161] eth1: Information frame lost.
[ 1480.614326] eth1: Information frame lost.
[ 1480.630762] eth1: Information frame lost.
[ 1480.713583] eth1: New link status: Connected (0001)
[ 1492.988620] eth1: New link status: Disconnected (0002)
[ 1492.996334] eth1: Information frame lost.
[ 1493.005916] eth1: Information frame lost.
[ 1493.015967] eth1: Information frame lost.
[ 1493.023140] eth1: Information frame lost.
[ 1493.032549] eth1: Information frame lost.
[ 1493.048792] eth1: Information frame lost.
[ 1493.062125] eth1: Information frame lost.
[ 1493.069282] eth1: Information frame lost.
[ 1493.076460] eth1: Information frame lost.
[ 1493.105187] eth1: Information frame lost.
[ 1493.250961] eth1: New link status: Connected (0001)
[ 1505.455870] eth1: New link status: Disconnected (0002)
[ 1505.466966] eth1: Information frame lost.
[ 1505.474269] eth1: Information frame lost.
[ 1505.499926] eth1: Information frame lost.
[ 1505.507098] eth1: Information frame lost.
[ 1505.514267] eth1: Information frame lost.
[ 1505.539888] eth1: Information frame lost.
[ 1505.547062] eth1: Information frame lost.
[ 1505.557322] eth1: Information frame lost.
[ 1505.565200] eth1: Information frame lost.
[ 1505.597334] eth1: Information frame lost.
[ 1505.732034] eth1: New link status: Connected (0001)
[ 1517.921269] eth1: New link status: Disconnected (0002)
[ 1518.130581] eth1: New link status: Connected (0001)
[ 1530.284776] eth1: New link status: Disconnected (0002)
[ 1530.518316] eth1: New link status: Connected (0001)
[ 1542.690515] eth1: New link status: Disconnected (0002)
[ 1542.865803] eth1: New link status: Connected (0001)
[ 1555.217372] eth1: New link status: Disconnected (0002)
[ 1555.363223] eth1: New link status: Connected (0001)
[ 1561.805346] eth1: New link status: Disconnected (0002)
[ 1562.075501] eth1: New link status: Connected (0001)
[ 1574.213414] eth1: New link status: Disconnected (0002)
[ 1574.402316] eth1: New link status: Connected (0001)
[ 1586.618860] eth1: New link status: Disconnected (0002)
[ 1586.792987] eth1: New link status: Connected (0001)
[ 1599.038078] eth1: New link status: Disconnected (0002)
[ 1599.184259] eth1: New link status: Connected (0001)
[ 1657.129498] eth1: New link status: Disconnected (0002)
[ 1657.380198] eth1: New link status: Connected (0001)
[ 1720.134761] eth1: New link status: Disconnected (0002)
[ 1720.396765] eth1: New link status: Connected (0001)
[ 1732.537741] eth1: New link status: Disconnected (0002)
[ 1733.893582] eth1: New link status: Connected (0001)
[ 1740.289319] eth1: New link status: Disconnected (0002)
[ 1740.535597] eth1: New link status: Connected (0001)
[ 1752.727757] eth1: New link status: Disconnected (0002)
[ 1752.954804] eth1: New link status: Connected (0001)
[ 1765.274095] eth1: New link status: Disconnected (0002)
[ 1765.542839] eth1: New link status: Connected (0001)
[ 1777.729315] eth1: New link status: Disconnected (0002)
[ 1778.011274] eth1: New link status: Connected (0001)
[ 1790.322732] eth1: New link status: Disconnected (0002)
[ 1790.511559] eth1: New link status: Connected (0001)
[ 1802.722957] eth1: New link status: Disconnected (0002)
[ 1802.988797] eth1: New link status: Connected (0001)
[ 1815.177474] eth1: New link status: Disconnected (0002)
[ 1815.416874] eth1: New link status: Connected (0001)
[ 1827.602717] eth1: New link status: Disconnected (0002)
[ 1827.888621] eth1: New link status: Connected (0001)
[ 1840.176027] eth1: New link status: Disconnected (0002)
[ 1840.504074] eth1: New link status: Connected (0001)
[ 1852.705387] eth1: New link status: Disconnected (0002)
[ 1852.978449] eth1: New link status: Connected (0001)
[ 1909.130710] eth1: New link status: Disconnected (0002)
[ 1909.377821] eth1: New link status: Connected (0001)
[ 1921.615559] eth1: New link status: Disconnected (0002)
[ 1921.857213] eth1: New link status: Connected (0001)
[ 1972.164662] eth1: New link status: Disconnected (0002)
[ 1972.339629] eth1: New link status: Connected (0001)
[ 1984.643180] eth1: New link status: Disconnected (0002)
[ 1984.831683] eth1: New link status: Connected (0001)
[ 1997.050611] eth1: New link status: Disconnected (0002)
[ 1997.222624] eth1: New link status: Connected (0001)
[ 2009.528933] eth1: New link status: Disconnected (0002)
[ 2009.715591] eth1: New link status: Connected (0001)
[ 2035.129793] eth1: New link status: Disconnected (0002)
[ 2035.457209] eth1: New link status: Connected (0001)
[ 2098.119493] eth1: New link status: Disconnected (0002)
[ 2098.295502] eth1: New link status: Connected (0001)
[ 2161.140274] eth1: New link status: Disconnected (0002)
[ 2161.449723] eth1: New link status: Connected (0001)
[ 2173.684101] eth1: New link status: Disconnected (0002)
[ 2173.867679] eth1: New link status: Connected (0001)
[ 2186.069838] eth1: New link status: Disconnected (0002)
[ 2186.258299] eth1: New link status: Connected (0001)
[ 2198.462575] eth1: New link status: Disconnected (0002)
[ 2198.648854] eth1: New link status: Connected (0001)
[ 2210.851094] eth1: New link status: Disconnected (0002)
[ 2211.144529] eth1: New link status: Connected (0001)
[ 2224.136909] eth1: New link status: Disconnected (0002)
[ 2224.352031] eth1: New link status: Connected (0001)
[ 2236.553723] eth1: New link status: Disconnected (0002)
[ 2236.742733] eth1: New link status: Connected (0001)
[ 2243.177906] eth1: New link status: Disconnected (0002)
[ 2243.434511] eth1: New link status: Connected (0001)
[ 2255.640684] eth1: New link status: Disconnected (0002)
[ 2255.846659] eth1: New link status: Connected (0001)
[ 2268.037925] eth1: New link status: Disconnected (0002)
[ 2268.234183] eth1: New link status: Connected (0001)
[ 2280.410355] eth1: New link status: Disconnected (0002)
[ 2280.741893] eth1: New link status: Connected (0001)
[ 2293.019675] eth1: New link status: Disconnected (0002)
[ 2293.342997] eth1: New link status: Connected (0001)
[ 2305.612066] eth1: New link status: Disconnected (0002)
[ 2305.766944] eth1: New link status: Connected (0001)
[ 2318.007424] eth1: New link status: Disconnected (0002)
[ 2318.278123] eth1: New link status: Connected (0001)
[ 2330.515556] eth1: New link status: Disconnected (0002)
[ 2330.749460] eth1: New link status: Connected (0001)
[ 2343.002901] eth1: New link status: Disconnected (0002)
[ 2343.304307] eth1: New link status: Connected (0001)
[ 2355.485328] eth1: New link status: Disconnected (0002)
[ 2355.675487] eth1: New link status: Connected (0001)
[ 2362.064152] eth1: New link status: Disconnected (0002)
[ 2362.316528] eth1: New link status: Connected (0001)
[ 2374.631510] eth1: New link status: Disconnected (0002)
[ 2374.894108] eth1: New link status: Connected (0001)
[ 2387.136613] eth1: New link status: Disconnected (0002)
[ 2387.330327] eth1: New link status: Connected (0001)
[ 2399.541946] eth1: New link status: Disconnected (0002)
[ 2399.808609] eth1: New link status: Connected (0001)
[ 2412.039190] eth1: New link status: Disconnected (0002)
[ 2412.282076] eth1: New link status: Connected (0001)
[ 2424.522515] eth1: New link status: Disconnected (0002)
[ 2424.895326] eth1: New link status: Connected (0001)
[ 2437.106832] eth1: New link status: Disconnected (0002)
[ 2437.364906] eth1: New link status: Connected (0001)
[ 2449.845252] eth1: New link status: Disconnected (0002)
[ 2450.052831] eth1: New link status: Connected (0001)
[ 2462.249695] eth1: New link status: Disconnected (0002)
[ 2462.469620] eth1: New link status: Connected (0001)
[ 2468.868379] eth1: New link status: Disconnected (0002)
[ 2469.136581] eth1: New link status: Connected (0001)
[ 2481.331470] eth1: New link status: Disconnected (0002)
[ 2481.487404] eth1: New link status: Connected (0001)
[ 2487.914602] eth1: New link status: Disconnected (0002)
[ 2488.097789] eth1: New link status: Connected (0001)
[ 2539.142201] eth1: New link status: Disconnected (0002)
[ 2539.445719] eth1: New link status: Connected (0001)
[ 2551.646772] eth1: New link status: Disconnected (0002)
[ 2551.870926] eth1: New link status: Connected (0001)
[ 2564.090097] eth1: New link status: Disconnected (0002)
[ 2564.391300] eth1: New link status: Connected (0001)
[ 2576.588206] eth1: New link status: Disconnected (0002)
[ 2576.878066] eth1: New link status: Connected (0001)
[ 2589.188660] eth1: New link status: Disconnected (0002)
[ 2589.577288] eth1: New link status: Connected (0001)
[ 2601.764985] eth1: New link status: Disconnected (0002)
[ 2602.097820] eth1: New link status: Connected (0001)
########## wireless info END ############

```

---

### Post by praseodym on 2014-08-09
Imho the driver supports WEP and WPA encryption only, no WPA2. Check the settings.

---

### Post by F._Magikian on 2014-08-12
I agree with praseodym that the settings appear to only cover up to WPA. This computer did connect to my wifi with WPA2 while running Windows XP. Also while previously sampling Ubuntu 14.04, this computer would connect to WPA2, but on an interrmittent basis, which was the reason I decided to but Ubuntu aside until later. I am using a fresh install and have had everything updated via wire connectiuon. Is there a way to change setting to include WPA2 or to upgrade drivers for wifi?

---

### Post by praseodym on 2014-08-12
Those PCMCIA cards are pretty old, I don't think there is a driver update possible.

```
- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            orinoco_cs
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr eth1>
  Capabilities:
  Wireless Properties
[COLOR="#FF0000"]    WEP Encryption:  yes
    WPA Encryption:  yes[/COLOR]
```
There is no WPA2 listed.

---

### Post by F._Magikian on 2014-08-12
Yes I see that WPA2 is not listed, however I am curious as to why I would have been able to connect &#8212;although intermittently&#8212; when I originally installed Ubuntu 14.04. As I stated I had no luck getting reliable connections so reinstalled windows. This time around I cannot connect at all. Just able to see various networks in the neighborhood. Would this have something to do with wpasupplicant? Or would I have to work with some type of wrapper for windows drivers, such as "ndis"

---

### Post by praseodym on 2014-08-12
If your network is WPA/WPA2 encrypted, then WPA is the "fallback" mode, maybe this is the reason for the intermittend connectivity.

---

### Post by F._Magikian on 2014-08-12
I checked router and it is the case that network is WPA/WPA2 encrypted, but would that not allow my currently configured version of ubuntu connect?
And thank you for your interest in my issue.

---

### Post by praseodym on 2014-08-13
No, in mixed mode WPA2 is default and WPA is fallback. Can you change to WPA only?

---

### Post by F._Magikian on 2014-08-15
Hello praseodyn: set my router security to WPA only and still no connection. Set my router security to 'none' and still unable to connect. I checked with other devices and was able to connect without issues when using these two settings. Interestingly Ubunto wireless connection setup does not allow for WPA only, just options for WPA-WPA2 personal and WPA-WPA2-enterprise. Still the fact I cannot connect with 'no encryption' is significant. It suggests something fundamentally incorrect in my wifi setting. I admit I am out of my league on this issue, as the system worked flawlessly on XP and as I mentioned previously, the system did function intermittently when originally testing Ubuntu 14.04.

---

### Post by praseodym on 2014-08-15
WPA-WPA2 personal is right. Check:
[LIST]
[*]
[*]MAC-address filter in your router is off
[*]fixed channel
[*]no hidden network
[*]no blanks or "strange" characters in your ESSID or PW
[/LIST]

---

### Post by F._Magikian on 2014-08-16
Changed router to fixed channel all else ok but still only able to associate with router, cannot gain internet access.

---

### Post by praseodym on 2014-08-16
Do you have PPPoE login data of your ISP? Can you add it in your router?

---

### Post by F._Magikian on 2014-08-16
I checked all the above and MAC filter off, network visible, oneword ESSID. Set channel to fixed, but still no connection, just an association with the router which has occured all along.

---

