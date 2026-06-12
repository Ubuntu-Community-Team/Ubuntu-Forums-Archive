---
title: "Internet not working with Wifi router but working with Personal Hotsport/Wifi Tether"
date: 2014-11-30
forum: Networking &amp; Wireless
---

### Post by priyank3 on 2014-11-30
Hello Experts,

Recently I installed Unbuntu, however it was my bad luck that I clicked on recommended installation which wiped my whole hard disk. Well now what I seen is that when I connect my laptop with Wifi (Home) which is netgear wireless router with WPA2-PSK encryption then it goes connected but internet is not working getting Destination Host unreachable while ping to router IP and 4.2.2.2. Well I ran the script and here is the code.```

########## wireless info START ##########

Report from: 30 Nov 2014 02:03 IST +0530

Booted last: 30 Nov 2014 01:27 IST +0530

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-32-generic #57-Ubuntu SMP Tue Jul 15 03:51:08 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Inspiron M5010 / XPS 8300 [1028:0010]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 005: ID 05ac:12a8 Apple, Inc. 
Bus 002 Device 003: ID 1d57:0001 Xenta 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 004: ID 0c45:641d Microdia 1.3 MPixel Integrated Webcam
Bus 001 Device 007: ID 413c:8160 Dell Computer Corp. Wireless 365 Bluetooth
Bus 001 Device 006: ID 413c:8162 Dell Computer Corp. Integrated Touchpad [Synaptics]
Bus 001 Device 005: ID 413c:8161 Dell Computer Corp. Integrated Keyboard
Bus 001 Device 003: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

dell_wmi               12761  0 
sparse_keymap          13948  1 dell_wmi
dell_laptop            18168  0 
dcdbas                 14928  1 dell_laptop
wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl
wmi                    19177  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:172.20.10.4  Bcast:172.20.10.15  Mask:255.255.255.240
          inet6 addr: fe80::60d9:c7ff:fe88:a1f5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9012 errors:0 dropped:2 overruns:0 frame:0
          TX packets:6592 errors:2 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9723254 (9.7 MB)  TX bytes:703618 (703.6 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:10.0.0.4  Bcast:10.0.0.255  Mask:255.255.255.0
          inet6 addr: fe80::72f1:a1ff:feec:830b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:148 errors:0 dropped:0 overruns:0 frame:29299
          TX packets:719 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10137 (10.1 KB)  TX bytes:66824 (66.8 KB)
          Interrupt:17 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Boozers"  
          Mode:Managed  Frequency:2.432 GHz  Access Point: <MAC 'Boozers' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         172.20.10.1     0.0.0.0         UG    0      0        0 eth0
10.0.0.0        0.0.0.0         255.255.255.0   U     9      0        0 wlan0
172.20.10.0     0.0.0.0         255.255.255.240 U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            ipheth
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         172.20.10.4
    Prefix:          28 (255.255.255.240)
    Gateway:         172.20.10.1

    DNS:             172.20.10.1

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

- Device: wlan0  [Boozers] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    ASUS:            Infra, <MAC 'ASUS' [AC2]>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Rajesh464:       Infra, <MAC 'Rajesh464' [AC5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Vikas_G:         Infra, <MAC 'Vikas_G' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    MOTI CHAND:      Infra, <MAC 'MOTI CHAND' [AC3]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 39 WEP
    *Boozers:        Infra, <MAC 'Boozers' [AC1]>, Freq 2432 MHz, Rate 54 Mb/s, Strength 71 WPA2
    VARUN-PC_Network:Infra, <MAC 'VARUN-PC_Network' [AN6]>, Freq 2457 MHz, Rate 54 Mb/s, Strength 17 WPA2

  IPv4 Settings:
    Address:         10.0.0.4
    Prefix:          24 (255.255.255.0)
    Gateway:         10.0.0.1

    DNS:             8.8.8.8

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

[[/etc/NetworkManager/system-connections/Boozers]] (600 root)
[connection] id=Boozers | type=802-11-wireless
[802-11-wireless] ssid=Boozers | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/iPhone Yankee]] (600 root)
[connection] id=iPhone Yankee | type=802-11-wireless
[802-11-wireless] ssid=iPhone Yankee | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Vikas_G]] (600 root)
[connection] id=Vikas_G | type=802-11-wireless
[802-11-wireless] ssid=Vikas_G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

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

lo        no frequency information.

wlan0     26 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 153 : 5.765 GHz
          Channel 157 : 5.785 GHz
          Channel 161 : 5.805 GHz
          Channel 165 : 5.825 GHz
          Current Frequency:2.432 GHz (Channel 5)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.432 GHz (Channel 5)
      1   APs on   Frequency:2.452 GHz (Channel 9)
      1   APs on   Frequency:2.457 GHz (Channel 10)
      1   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Boozers' [AC1]>
                    Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=61/70  Signal level=-49 dBm  
                    Encryption key:on
                    ESSID:"Boozers"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'ASUS' [AC2]>
                    Channel:9
                    Frequency:2.452 GHz (Channel 9)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"ASUS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'MOTI CHAND' [AC3]>
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"MOTI CHAND"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
          Cell 04 - Address: <MAC 'Vikas_G' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"Vikas_G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'Rajesh464' [AC5]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:on
                    ESSID:"Rajesh464"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 48ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/3.13.0-32-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.13.0-32-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E786D076B61F97809B04B64
depends:        
intree:         Y
vermagic:       3.13.0-32-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        5E:3C:0F:9C:A6:E3:65:43:53:5F:A2:BB:5B:70:9E:84:F1:6D:A7:C7
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/pm/power.d/wireless] (644 root)
/sbin/iwconfig wlan0 power off
exit0

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x14e4:0x4727 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[ 2186.721875] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

---

### Post by Hadaka on 2014-11-30
Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe brcmsmac
```
thanks.

---

### Post by priyank3 on 2014-11-30
Hello,

I have done but nothing happend below is output of first command.

x-hacker@Xhacker:~$ sudo apt-get remove --purge bcwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package bcwl-kernel-source
x-hacker@Xhacker:~$ sudo modprobe brcmsmac
x-hacker@Xhacker:~$ ^C
x-hacker@Xhacker:~$ 



I am sorry but my hand is loose on Ubuntu Kindly help and I am not able to understand why the hell it is not working on my Wifi however I am able to do in Wifiteher or Personal hotspot iPhone.
















> **Hadaka said:**
> Hi, please do..
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe brcmsmac
```
thanks.

---

### Post by priyank3 on 2014-11-30
below is latest output:


x-hacker@Xhacker:~$ sudo apt-get remove --purge bcmwl-kernel-source
[sudo] password for x-hacker: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  dkms fakeroot libfakeroot linux-headers-generic linux-image-generic
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  bcmwl-kernel-source*
0 upgraded, 0 newly installed, 1 to remove and 245 not upgraded.
After this operation, 5,800 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 164158 files and directories currently installed.)
Removing bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
Removing all DKMS Modules
Done.
update-initramfs: deferring update (trigger activated)
Purging configuration files for bcmwl-kernel-source (6.30.223.141+bdcom-0ubuntu2) ...
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools (0.103ubuntu4.2) ...
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
x-hacker@Xhacker:~$ sudo modprobe brcmsmac
x-hacker@Xhacker:~$ rfkill list al
Bogus list argument 'al'.
x-hacker@Xhacker:~$ rfkill list all
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
x-hacker@Xhacker:~$ 


Stil no sucess

---

### Post by priyank3 on 2014-11-30
Oh Its working thanks after restart.. Dude...

Thanks alot saved my lot of time...

could you please explain to me what exactly the issue.

---

### Post by Hadaka on 2014-11-30
Hi, glad that worked for you,the issue was..you had the inncorrect
driver loaded for your wifi card,once that was corrected it worked
correctly.
thanks

---

### Post by wildmanne39 on 2014-11-30
Please use normal fonts.
Thanks

---

