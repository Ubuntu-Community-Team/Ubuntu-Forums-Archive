---
title: "How do I check my firmware on Intel 2200BG"
date: 2014-10-22
forum: Networking &amp; Wireless
---

### Post by SchoolDaGeek on 2014-10-22
I have a Edubuntu 14.04 LTR Fresh install with a Intel 2200BG card, ipw2200, 1.2.2kmprq

I am having the notorious dropouts I have read as far back as 2005-6 on earlier installs.

I read that Intel released 3.01 firmware in 2009 but my firmware is ABG:9.0.5.27 (Dec 12 2007)

I did dpkg -s ipw and got a whole slew of stuff I don't understand except maybe for the .h (header) files if that.

Does 14.04 with all updates installed have a way of checking the firmware?  I don't know if my 1.2.2kmprq is looking for 3.0, 3.1, or possibly even a 2100 firmware.  I know there was also a -7 and a -8 with some Intel cards that I came across.

I "guess" I have 3.13.0-24 and 3.13.0-37 kernels because that is what I am seeing.  I found a ton of stuff on Debian but cannot translate the commands to see if I can update my firmware, OR DOWNGRADE if it is better, and get rid of all the 2100 stuff that I saw you do in a post about 2 days ago that was pretty much archived.

Can you walk me through checking my firmware, updating it, and getting rid of any bad calls for 2100?

---

### Post by Bucky Ball on 2014-10-22
Please address support requests to the community rather than individual members. Chili555 is not the only networking guru here and may be on holidays or otherwise detained. If you wish to address an individual, PM them. You will then probably be refused individual support as very few members give it via PM.

Posting to the whole community improves your chances of support. Good luck.

Post back the result of:

```
sudo lshw -C network
```

For a more comprehensive look, post the output of the wireless script:

[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)

---

### Post by SchoolDaGeek on 2014-10-22
Thank you!

---

### Post by Bucky Ball on 2014-10-22
All good. Not sure if you got this from my last post. I edited:

For a more comprehensive look, post the output of the wireless script:

[http://ubuntuforums.org/showthread.p...5#post12350385](http://ubuntuforums.org/showthread.p...5#post12350385)

Chili would probably ask you to do this in any case. ;)

And welcome to the forums.

PS: This section of the forums is a regular haunt for Chili555 and others cluey with wireless so he'll probably catch you eventually.

---

### Post by SchoolDaGeek on 2014-10-23
I would also accept a script, Edubuntu 14.04 LTR.  Update ipw2200 to latest using open source/non-free on all Unix/Linux platforms including firmware.

Got a 404 on that link. 12350385

What is the command to list?  If it involves dmsg I need you holding my hand...

---

### Post by Bucky Ball on 2014-10-23
> **Bucky Ball said:**
> 

Open a terminal, post back the result of:

```
sudo lshw -C network
```



Use this command. And don't know what happened with the link. Try this one:

[http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385](http://ubuntuforums.org/showthread.php?t=2082305&p=12350385#post12350385)

---

### Post by chili555 on 2014-10-23
Along with my coffee, Mrs. Chili handed me my laptop this morning and said, "Get busy, mister, they're calling for you!"

You can see what firmware, but not what version, is called for here:```
modinfo ipw2200
```In my case, it says:> firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
You can see what is actually called up with:```
dmesg | grep ipw
```You may see something like:> ipw2200 0000:04:02.0: firmware: requesting ipw2200-bss.fwWhat you probably can't see is what version is being used.

Intel long ago turned over the ipw2200 project to others: [http://ipw2200.sourceforge.net/firmware.php](http://ipw2200.sourceforge.net/firmware.php) The firmware links are dead. The firmware files included in the Ubuntu package *linux-firmware* are updated pretty frequently. I sincerely doubt, although I am unable to prove, that the firmware has been updated recently. > my firmware is ABG:9.0.5.27 (Dec 12 2007)Where can we see this?

I honestly believe your troubles are elsewhere than firmware.

---

### Post by SchoolDaGeek on 2014-10-23
Here is the first results:

```
  *-network:0             
       description: Ethernet interface
       product: RTL8169 PCI Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 10
       serial: 00:c0:9f:ed:48:46
       size: 10Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
       resources: irq:19 ioport:2000(size=256) memory:c8006000-c80060ff memory:84000000-8401ffff
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2200BG [Calexico2] Network Connection
       vendor: Intel Corporation
       physical id: 4
       bus info: pci@0000:06:04.0
       logical name: eth1
       version: 05
       serial: 00:13:ce:00:64:fc
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.5.27 (Dec 12 2007) ip=192.168.1.74 latency=32 link=yes maxlatency=24 mingnt=3 multicast=yes wireless=IEEE 802.11bg
       resources: irq:17 memory:c8007000-c8007fff
```

```
########## wireless info START ##########


Report from: 23 Oct 2014 13:57 EDT -0400


Booted last: 22 Oct 2014 15:37 EDT -0400


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.1 LTS
Release:	14.04
Codename:	trusty


##### kernel ############################


Linux 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:30:01 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8169 PCI Gigabit Ethernet Controller [10ec:8169] (rev 10)
	Subsystem: QUANTA Computer Inc Device [152d:0729]
	Kernel driver in use: r8169


06:04.0 Network controller [0280]: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection [8086:4220] (rev 05)
	Subsystem: Intel Corporation Device [8086:2751]
	Kernel driver in use: ipw2200


##### lsusb #############################


Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
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


0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ipw2200               136401  0 
mxm_wmi                12893  1 nouveau
libipw                 33144  1 ipw2200
lib80211               14040  4 lib80211_crypt_ccmp,lib80211_crypt_tkip,libipw,ipw2200
cfg80211              409394  2 libipw,ipw2200
wmi                    18673  2 mxm_wmi,nouveau


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
          inet addr:192.168.1.74  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2602:306:c45d:f880:213:ceff:fe00:64fc/64 Scope:Global
          inet6 addr: 2602:306:c45d:f880:c854:2e7f:bf2:7920/64 Scope:Global
          inet6 addr: fe80::213:ceff:fe00:64fc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18354 errors:3 dropped:3 overruns:0 frame:0
          TX packets:8073 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:13993405 (13.9 MB)  TX bytes:880450 (880.4 KB)


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


eth1      IEEE 802.11bg  ESSID:"ATT460"  
          Mode:Managed  Frequency:2.447 GHz  Access Point: <MAC 'ATT460' [AC2]>   
          Bit Rate:5.5 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/100  Signal level=-66 dBm  Noise level=-82 dBm
          Rx invalid nwid:0  Rx invalid crypt:3  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:13


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth1
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 eth1


##### resolv.conf #######################


nameserver 127.0.1.1
search gateway.pace.com


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth1  [ATT460] -------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ipw2200
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth1' [IF]>


  Capabilities:
    Speed:           5 Mb/s


  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes


  Wireless Access Points (* = current AP)
    bruce Network:   Infra, <MAC 'bruce Network' [AN1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 47 WPA2
    ATT311:          Infra, <MAC 'ATT311' [AN2]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 50 WPA WPA2
    *ATT460:         Infra, <MAC 'ATT460' [AC2]>, Freq 2447 MHz, Rate 54 Mb/s, Strength 58 WPA WPA2
    2WIRE138:        Infra, <MAC '2WIRE138' [AC1]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    HP-Print-A2-ENVY 5530 series: Infra, <MAC 'HP-Print-A2-ENVY 5530 series' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 42 WPA2
    2WIRE941:        Infra, <MAC '2WIRE941' [AC3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 49 WPA WPA2
    ATTTTI9RMS:      Infra, <MAC 'ATTTTI9RMS' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 54 WPA WPA2


  IPv4 Settings:
    Address:         192.168.1.74
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


  IPv6 Settings:
    Address:         2602:306:c45d:f880:c854:2e7f:bf2:7920
    Prefix:          64
    Gateway:         fe80::bae6:25ff:fe0c:ff81


    Address:         2602:306:c45d:f880:213:ceff:fe00:64fc
    Prefix:          64
    Gateway:         fe80::bae6:25ff:fe0c:ff81


    Address:         fe80::213:ceff:fe00:64fc
    Prefix:          64
    Gateway:         fe80::bae6:25ff:fe0c:ff81


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


[ifupdown]
managed=false


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/ATT460]] (600 root)
[connection] id=ATT460 | type=802-11-wireless
[802-11-wireless] ssid=ATT460 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: America/New_York (based on set time zone)


country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


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
          Current Frequency=2.447 GHz (Channel 8)


##### iwlist scan #######################


Channel occupancy:


      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.447 GHz (Channel 8)
      1   APs on   Frequency:2.457 GHz (Channel 10)


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


eth1      Scan completed :
          Cell 01 - Address: <MAC '2WIRE138' [AC1]>
                    ESSID:"2WIRE138"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-68 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 32ms ago
          Cell 02 - Address: <MAC 'ATT460' [AC2]>
                    ESSID:"ATT460"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.447 GHz (Channel 8)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=55/100  Signal level=-68 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 60ms ago
          Cell 03 - Address: <MAC '2WIRE941' [AC3]>
                    ESSID:"2WIRE941"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=44/100  Signal level=-74 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 152ms ago


##### module infos ######################


[ipw2200]
filename:       /lib/modules/3.13.0-37-generic/kernel/drivers/net/wireless/ipw2x00/ipw2200.ko
firmware:       ipw2200-bss.fw
firmware:       ipw2200-sniffer.fw
firmware:       ipw2200-ibss.fw
license:        GPL
author:         Copyright(c) 2003-2006 Intel Corporation
version:        1.2.2kmprq
description:    Intel(R) PRO/Wireless 2200/2915 Network Driver
srcversion:     6432FDB1497A8B2EC025CB2
depends:        cfg80211,libipw,lib80211
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512
parm:           disable:manually disable the radio (default 0 [radio on]) (int)
parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
parm:           led:enable led control on some systems (default 1 on) (int)
parm:           debug:debug output mask (int)
parm:           channel:channel to limit associate to (default 0 [ANY]) (int)
parm:           rtap_iface:create the rtap interface (1 - create, default 0) (int)
parm:           qos_enable:enable all QoS functionalitis (int)
parm:           qos_burst_enable:enable QoS burst mode (int)
parm:           qos_no_ack_mask:mask Tx_Queue to no ack (int)
parm:           burst_duration_CCK:set CCK burst value (int)
parm:           burst_duration_OFDM:set OFDM burst value (int)
parm:           mode:network mode (0=BSS,1=IBSS,2=Monitor) (int)
parm:           bt_coexist:enable bluetooth coexistence (default off) (int)
parm:           hwcrypto:enable hardware crypto (default off) (int)
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)
parm:           antenna:select antenna 1=Main, 3=Aux, default 0 [both], 2=slow_diversity (choose the one with lower background noise) (int)


[cfg80211]
filename:       /lib/modules/3.13.0-37-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-37-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        7A:CF:8E:D9:48:D7:7B:6A:80:F2:4F:59:D5:D8:ED:03:87:AA:B4:26
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ipw2200]
antenna: 0
associate: 0
auto_create: 1
bt_coexist: 0
burst_duration_CCK: 0
burst_duration_OFDM: 0
channel: 0
cmdlog: 0
debug: 0
disable: 0
hwcrypto: 0
led: 1
mode: 0
qos_burst_enable: 0
qos_enable: 0
qos_no_ack_mask: 0
roaming: 1
rtap_iface: 0


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


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


##### rc.local ##########################


exit 0


##### pm-utils ##########################


##### udev rules ########################


[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8169 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x8086:0x4220 (ipw2200)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"


##### dmesg #############################


[ 1384.085237] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[ 1387.106029] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[11463.480490] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[79084.000389] IPv6: ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready


########## wireless info END ############
```

Hey Chili, my hero!  Ever Google your screen name?  LOL  I have read as many posts as my brain would hold all the way back to 2005 or so.  Tell Mrs. Chili she's a good woman, and thank you!

So I have already MD5 my three files, they match an earlier post you had on another forum, I am pretty much stuck on the firmware thing.  I cannot reconcile the 2007 tag fw with the announcement that Intel put out 3.1 in 2009.  This laptop has been in storage so long I just had to order another fresh battery off Ebay.

It appears that when the computer gets confused about the charging state of the battery is when the drop occurs, or when I walk away for more than 10min.

I found more information on the Debian channels and I could probably track down the 3.1 firmware from one of the links I have, but my thoughts are that maybe these old cards actually DO have to be flashed in Windows or something.  I am just remembering the older CD burners that had firmware updates to make them run better and more compatible.

I cannot find ANY information on what a 3.0 or 3.1 fw should look like in a Linux report.

I do have a Broadcom card I could swap in there, albeit a new post because I dislike Broadcom on Ubuntu, but {insert Kermit Meme here} that's none of my business, tho...

I read back through the wireless report and I noticed:

parm:           associate:auto associate when scanning (default off) (int)
parm:           auto_create:auto create adhoc network (default on) (int)
...
parm:           cmdlog:allocate a ring buffer for logging firmware commands (int)
parm:           roaming:enable roaming support (default on) (int)

Do you think I could toggle #1,2,4 to the opposite state and achieve a better result?  Also in #3 is there a way to hack the cmdlog/ring buffer to get the firmware version?

---

### Post by chili555 on 2014-10-23
I managed to find the 3.1 firmware here: [http://pkgs.fedoraproject.org/repo/pkgs/ipw2200-firmware/ipw2200-fw-3.1.tgz/eaba788643c7cc7483dd67ace70f6e99/](http://pkgs.fedoraproject.org/repo/pkgs/ipw2200-firmware/ipw2200-fw-3.1.tgz/eaba788643c7cc7483dd67ace70f6e99/) I downloaded it, extracted it and checked the properties of ipw2200-bss.fw. It is 191,154 bytes. The copy I have in /lib/firmware is also 191,154 bytes. Their md5sums are identical. They are one and the same.

As to the driver parameters, it may be helpful to try a few, although certainly not the one that forces adhoc mode! That is for computer-to-computer arrangements, not computer-to-router. I suggest we try:```
gksudo gedit /etc/modprobe.d/ipw2200.conf
```Use nano or kate or leafpad if you don't have the text editor gedit. Add a new line to the empty file:```
options ipw2200 associate=1 
```Proofread carefully, save and close the text editor. 

Next, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router.

Next, I recommend that your regulatory domain be set explicitly. Check yours:```
sudo iw reg get
```If you get 00, that is a one-size-maybe-fits-all setting. Find yours here: [http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2](http://en.wikipedia.org/wiki/ISO_3166-1_alpha-2) Then set it temporarily:```
sudo iw reg set IS
```Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```Use nano or kate or leafpad if you don't have the text editor gedit.

Change the last line to read:```
REGDOMAIN=IS
```Proofread carefully, save and close the text editor.

You might also experiment with IPv6 disabled. I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.> It appears that when the computer gets confused about the charging state of the battery is when the drop occurs, or when I walk away for more than 10min.I notice in your wireless info that power management is off. When you step away and it drops, is power management toggled back on?```
iwconfig
```

---

### Post by SchoolDaGeek on 2014-10-23
I am not going to be arrogant here, but these changes are far more than I have time to sit an monitor one by one.  I think you solved my firmware issue as long as you are comparing the files, you didn't post the sum, though, I am under the assumption we are talking about what is included in 14.04LTR.  I will try that first to be sure, and then I think I am just going to go with option 1 of setting auto associate to 1.  It really depends on how much time I have over the next day or so, and I don't want to make global changes that offend Occam's Razor.  My logic is that the dropouts are extremely sporadic, in the last 3 hours I haven't had one, and it really only takes a "Enter" stroke on the keyboard to re-associate, so I will go with for now to auto-associate to ON and see if this works over the next week.  I will report back ONLY if I have problems, but thank you VERY MUCH for checking the MD5 and I will do likewise.  Chili!!! ;)

Not going to submit a bug report or anything but it would be nice if we could get the information header in the fw to report 3.1 instead of x.x.x.x (2007) that shouldn't be hard in the Debian and Ubuntu community for the next distro....ARCH seems to have it all sorted out with packages already...  Just sayin' would waste far less time...  As far as standard options are concerned, why would auto-associate be set to 0 anyway in the original?  Noobs like me think wireless is supposed to be like a 4G signal on your phone, you "get" a symbol that you are either connected or not.  Linux people are usually hacking Windows clients if they have an auto associate.  It is on the router side and there are very few trolls in your own house, although if you leave your account logged in on facebook, there will usually be punky remarks...  Hypothesizing this works, it could also be something added into the distribution config file now that Intel gave it up to opensource.  Thoughts as I monitor the changes?

---

### Post by SchoolDaGeek on 2014-10-28
OK so all the way current now, last reboot...

---

### Post by SchoolDaGeek on 2014-10-28
Preliminary findings are that I went 48 hours without a dis-associate, But then I had a batch of 10 until I rebooted.  The New Boot settings are country=iceland.  I will let you know.

---

### Post by SchoolDaGeek on 2014-10-29
Iceland code was worse, had a full drop and did not reappear for maybe 90 seconds.  I had time to check iw and power mgmt was still set to off.  iw did say that maximum attempts were set at 7 to TX and excessive retries was 1.  So does that mean it tried 8 times?

I read post:  [http://ubuntuforums.org/showthread.php?t=2250481](http://ubuntuforums.org/showthread.php?t=2250481) and would just like instructions at this point to install my Broadcom54g Max Performance QDS-BRCM1013 / 4324A-BRCM1013.

Thank you again!!!!!!  ;)

---

### Post by SchoolDaGeek on 2014-10-29
> **chili555 said:**
> Of course, substitute your country code if not Iceland. Set it permanently:```
gksudo gedit /etc/default/crda
```

HA HA HA that is why I chose my screename.  Something below ADD they tell me...

Setting to US and I will fight another day!

---

### Post by Bucky Ball on 2014-10-29
> **SchoolDaGeek said:**
> 

I read post:  [http://ubuntuforums.org/showthread.php?t=2250481](http://ubuntuforums.org/showthread.php?t=2250481) and would just like instructions at this point to install my Broadcom54g Max Performance QDS-BRCM1013 / 4324A-BRCM1013.



Then please post an new, appropriately titled thread as this new support request is not related to the title or topic of this thread. You will greatly improve your chances of help and avoid confusion. Feel free to post a link to the new thread here. Thanks and good luck.

---

### Post by SchoolDaGeek on 2014-10-29
If beans were beers, needing 10 beans to get your timezone recognized is excessive.  I made a post asking about this during registration, most of the time zones were asked for in .php so this whole Iceland Debacle will go into the history books....

---

### Post by chili555 on 2014-10-30
> **SchoolDaGeek said:**
> 

I read post:  [http://ubuntuforums.org/showthread.php?t=2250481](http://ubuntuforums.org/showthread.php?t=2250481) and would just like instructions at this point to install my Broadcom54g Max Performance QDS-BRCM1013 / 4324A-BRCM1013.I will be very happy to assist in your new post. Feel free to PM me with the link if I don't catch it right away.

---

### Post by SchoolDaGeek on 2014-10-30
I found this.  Thank you for the offer!  [http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers](http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers)

---

