---
title: "Dell Latitude D410 wifi not working after fresh 14.04 install"
date: 2014-12-29
forum: Networking &amp; Wireless
---

### Post by stu7 on 2014-12-29
Have installed 14.04 on my Dell Latitude D410, everything works apart from the wifi chip.  I have run

sudo apt-get update
sudo apt-get dist-upgrade

 to no avail.

I have also tried [COLOR=#000000][FONT=Ubuntu Mono]sudo apt-get install [/FONT][/COLOR][COLOR=#000000][FONT=Ubuntu Mono]firmware-b43-installer

[/FONT][/COLOR]The wifi light doesn't light up when I hit try to enable with the fn key combination.  

Just to be clear I don't get the wifi segment icon in the top left. I'm not sure how to trouble shoot this.  I've checked in the bios and the wifi chip is definitely enabled.  

Any help  would be greatly appreciated.

Thanks
```



########## wireless info START ##########


Report from: 28 Dec 2014 13:33 GMT +0000


Booted last: 28 Dec 2014 13:28 GMT +0000


Script from: 20 Sep 2014 23:04 UTC +0000


##### release ###########################


Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty


##### kernel ############################


Linux 3.13.0-43-generic #72-Ubuntu SMP Mon Dec 8 19:35:44 UTC 2014 i686 i686 i686 GNU/Linux


Parameters: ro, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


01:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5751 Gigabit Ethernet PCI Express [14e4:1677] (rev 01)
    Subsystem: Dell Device [1028:018f]
    Kernel driver in use: tg3


02:03.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce 54g] 802.11a/b/g PCI Express Transceiver [14e4:4319] (rev 02)
    Subsystem: Dell Wireless 1470 Dual Band WLAN Mini-PCI Card [1028:0005]
    Kernel driver in use: wl


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


##### lsmod #############################


wl                   3999690  1 
dell_laptop            17808  0 
dcdbas                 14448  1 dell_laptop
lib80211               14040  1 wl
cfg80211              409394  1 wl


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.82  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::214:22ff:fefc:9454/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5533 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3873 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6360293 (6.3 MB)  TX bytes:399159 (399.1 KB)
          Interrupt:16 


##### iwconfig ##########################


lo        no wireless extensions.


eth0      no wireless extensions.


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0


##### resolv.conf #######################


nameserver 127.0.1.1
search lan


##### nm-tool ###########################


NetworkManager Tool


State: connected (global)


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            tg3
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>


  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s


  Wired Properties
    Carrier:         on


  IPv4 Settings:
    Address:         192.168.1.82
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254


    DNS:             192.168.1.254


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


[[/etc/NetworkManager/system-connections/Wi-Fi connection 1]] (600 root)
[connection] id=Wi-Fi connection 1 | type=802-11-wireless
[802-11-wireless] ssid=PLUSNETWIRELESS20544B
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/London (based on set time zone)


country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


##### iwlist channels ###################


lo        no frequency information.


eth0      no frequency information.


##### iwlist scan #######################


lo        Interface doesn't support scanning.


eth0      Interface doesn't support scanning.


##### module infos ######################


[wl]
filename:       /lib/modules/3.13.0-43-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-43-generic SMP mod_unload modversions 686 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string


[cfg80211]
filename:       /lib/modules/3.13.0-43-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     C2478077E22138832B71659
depends:        
intree:         Y
vermagic:       3.13.0-43-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        3C:74:D8:78:9C:AA:5E:CB:12:DD:D1:AA:C2:15:E1:2C:62:FC:AC:A5
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00


##### /etc/modules ######################


lp


##### modprobe options ##################


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
# PCI device 0x14e4:0x1677 (tg3)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"


##### dmesg #############################


[    9.916989]  [<f91cb3c3>] wl_free_if.isra.12+0x23/0xa0 [wl]
[    9.917034]  [<f91cba68>] wl_free+0x78/0x260 [wl]
[    9.917095]  [<f91cbf5e>] wl_pci_probe+0x30e/0x630 [wl]
[    9.917172]  [<f8969017>] wl_module_init+0x17/0x1000 [wl]
[    9.917276] EIP: [<f91d2fb6>] wdev_priv.part.9+0x3/0x5 [wl] SS:ESP 0068:f4967bb8


########## wireless info END ############



```

---

### Post by Hadaka on 2014-12-29
please open a terminal and do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -rf b43
sudo modprobe b43
```
also please copy and paste to a terminal
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
thanks.

---

### Post by stu7 on 2014-12-30
Hi Hadaka

Thanks for helping.  I have ran those commands in sequence.  When running '[COLOR=#000000][FONT=Ubuntu Mono]sudo modprobe b43[/FONT][/COLOR]' there was no output from the terminal, the command looked as if it was still busy, I waited an hour then proceeded with the other commands in a new terminal tab.

I have since rebooted and now when pressing the Fn F2 combo my wifi starts and I'm able to connect. :guitar:

Many thanks for your help!

PS I would be interested to know what those commands did if you have time to explain.

---

### Post by Hadaka on 2014-12-30
Hi Stu7, glad that worked for you. this command,,,
```
sudo apt-get remove --purge bcmwl-kernel-source
```
is basically what corrected the problem, the "wl" driver..bcmwl-kernel-source
loads in error almost anytime the load process detects a broadcom wifi card.
The problem has been reported several times yet continues. The b43 commands
were just toggeling on and off the b43 dirver module, the correct module which
by the way the "wl" module blacklists. So in conclusion it was nothing you did
incorrectly other than follow os install directions.
The other commands were to set your "country code" GB as it was not set.
Please take the time to mark your thread solved
thanks

---

### Post by stu7 on 2014-12-31
OK makes sense.  Thanks again!

---

