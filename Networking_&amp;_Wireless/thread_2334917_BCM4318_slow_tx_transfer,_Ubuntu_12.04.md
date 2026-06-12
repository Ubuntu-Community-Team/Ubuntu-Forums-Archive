---
title: "BCM4318 slow tx transfer, Ubuntu 12.04"
date: 2016-08-23
forum: Networking &amp; Wireless
---

### Post by darkzu2 on 2016-08-23
So basically I have a old laptop running ubuntu server 12.04 that I am using as a server which is connected via wifi, everything is pretty much perfect except one thing.
The transfer speed when uploading from the server is for some reason slow, while the speed when downloading to the server is almost at its maximum for 54g.

I have no clue what could be the issue, the server is on the second floor, there is only the concrete slab in-between, and the signal and quality looks okay which the download speed also proves..

Here a picture: [http://prnt.sc/c9kaeo](http://prnt.sc/c9kaeo)

And some info
```

########## wireless info START ##########

Report from: 23 Aug 2016 23:16 CEST +0200

Booted last: 23 Aug 2016 22:34 CEST +0200

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.2 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.5.0-23-generic #35~precise1-Ubuntu SMP Fri Jan 25 17:15:33 UTC 2013 i686 i686 i386 GNU/Linux

Parameters: ro

##### desktop ###########################

sed: can't read /root/.dmrc: No such file or directory

Could not be determined.

##### lspci #############################

06:05.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
    Subsystem: AMBIT Microsystem Corp. TravelMate 2410 [1468:0312]
    Kernel driver in use: b43-pci-bridge

06:07.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
    Subsystem: Acer Incorporated [ALI] Device [1025:006a]
    Kernel driver in use: 8139too

##### lsusb #############################

Bus 001 Device 002: ID 046d:081d Logitech, Inc. HD Webcam C510
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

./wireless-info: line 192: rfkill: command not found

##### lsmod #############################

acer_wmi               27975  0 
sparse_keymap          13659  1 acer_wmi
b43                   351489  0 
mac80211              475488  1 b43
cfg80211              181041  2 b43,mac80211
bcma                   34573  1 b43
wmi                    18745  1 acer_wmi
video                  19070  2 acer_wmi,i915
ssb                    50757  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.5.55
netmask 255.255.255.0
network 192.168.5.0
gateway 192.168.5.1
dns-nameservers 213.191.128.8 8.8.8.8
wpa-ssid <removed>
wpa-psk <WPA key removed>

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF1]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.5.55  Bcast:192.168.5.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlan0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:175890 errors:0 dropped:1249 overruns:0 frame:0
          TX packets:185597 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:166154297 (166.1 MB)  TX bytes:174542300 (174.5 MB)

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"<removed>"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC '<removed>' [AC1]>   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=62/70  Signal level=-48 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:12   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.5.1     0.0.0.0         UG    100    0        0 wlan0
192.168.5.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 213.191.128.8
nameserver 8.8.8.8

##### network managers ##################

Installed:

    None found.

Running:

    None found.

##### NetworkManager info ###############

NetworkManager is not installed (package "network-manager").

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

No NetworkManager profiles found.

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 20), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

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
          Current Frequency=2.437 GHz (Channel 6)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC '<removed>' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=59/70  Signal level=-51 dBm  
                    Encryption key:on
                    ESSID:"<removed>"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000003d2f3e349
                    Extra: Last beacon: 60ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[b43]
filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/net/wireless/b43/b43.ko
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
srcversion:     B17695451431A52A474624A
depends:        ssb,mac80211,bcma,cfg80211
intree:         Y
vermagic:       3.5.0-23-generic SMP mod_unload modversions 686 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)

[mac80211]
filename:       /lib/modules/3.5.0-23-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     77DDAF975978437CB1FFCDC
depends:        cfg80211
intree:         Y
vermagic:       3.5.0-23-generic SMP mod_unload modversions 686 
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.5.0-23-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     35B4715292094C5C2B31995
depends:        
intree:         Y
vermagic:       3.5.0-23-generic SMP mod_unload modversions 686 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     2C92CCB735C6654CB7E788B
depends:        
intree:         Y
vermagic:       3.5.0-23-generic SMP mod_unload modversions 686 

[ssb]
filename:       /lib/modules/3.5.0-23-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     657007C65032F6BDD9475AB
depends:        
intree:         Y
vermagic:       3.5.0-23-generic SMP mod_unload modversions 686 

##### module parameters #################

[b43]
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

loop
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

##### rc.local ##########################

exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/000cancel-hibernate-suspend] (755 root)
. "$PM_FUNCTIONS"
case "${1}" in
  suspend|hibernate)
    inhibit
    ;;
  resume|thaw)
    exit 0
    ;;
esac

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:1e.0/0000:06:07.0 (8139too)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF1]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1e.0/0000:06:05.0/ssb0:0 (b43-pci-bridge)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF2]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   12.944888] b43-phy0: Broadcom 4318 WLAN found (core revision 9)
[   13.480379] Registered led device: b43-phy0::tx
[   13.480403] Registered led device: b43-phy0::rx
[   13.480426] Registered led device: b43-phy0::radio
[   13.692042] b43-phy0: Loading firmware version 508.1084 (2009-01-14 01:32:01)
[   13.757038] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   15.940492] wlan0: authenticate with <MAC '<removed>' [AC1]>
[   15.964193] wlan0: send auth to <MAC '<removed>' [AC1]> (try 1/3)
[   15.968468] wlan0: authenticated
[   15.972016] wlan0: associate with <MAC '<removed>' [AC1]> (try 1/3)
[   15.974546] wlan0: RX AssocResp from <MAC '<removed>' [AC1]> (capab=0x411 status=0 aid=1)
[   15.975025] wlan0: associated
[   15.975197] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############


```

---

### Post by darkzu2 on 2016-08-26
Is this forum dead?

Edit: didnt wanted to do it, but then did a do-release-upgrade, it jumped to 2000kb/s so solved

---

