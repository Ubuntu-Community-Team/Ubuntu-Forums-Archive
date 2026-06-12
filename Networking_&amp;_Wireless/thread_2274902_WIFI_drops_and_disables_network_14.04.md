---
title: "WIFI drops and disables network 14.04"
date: 2015-04-23
forum: Networking &amp; Wireless
---

### Post by martin154 on 2015-04-23
Hi All,

First of all, here Information on my Laptop/wifi Hardware:

Linux jones-hp 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux 03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)    Subsystem: Hewlett-Packard Company Device [103c:2230]    Kernel driver in use: wl

 When I installed UBUNTU the wifi Card was completely deactivated by default. When I went into the proprietory Drivers page in the update menu, I saw that my broadcom device was inactive, even though there was a Driver available. I activated the suggested Driver directly from the menu which was then installed, after which my wifi was working. I did notice however, that the Signal strength seemed to be fluctuating according to the Applet in the taskbar. Now the Connection not only regularly Drops out completely, but also seems to Crash the Network so that no other device can connect to the wireless modem! I know this, because my NAS is attached by cable to the router and sends me an email every time the Connection is dropped.have you any idea what could be causing this? Is it a Driver issue or could it even be a modem Setting (encryption etc.)? 

I am currently travelling and will be home this evening where I will run and post the contents of the wireless script to enable more detailed Information about the Laptop.

 Regards
 Martin

---

### Post by martin154 on 2015-04-23
here the results of the wireless script. Looking forward to your feedback:

[COLOR=#000000]```
[/COLOR]

Report from: 23 Apr 2015 18:34 CEST +0200

Booted last: 23 Apr 2015 18:27 CEST +0200

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:2230]
    Kernel driver in use: wl

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:22cd]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:216c Broadcom Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

wl                   6367833  0 
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
cfg80211              494362  1 wl
wmi                    19193  1 hp_wmi

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

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: 2a02:8389:4002:2f80:416b:f959:be0c:c114/64 Scope:Global
          inet6 addr: fe80::3ab1:dbff:fef7:51ab/64 Scope:Link
          inet6 addr: 2a02:8389:4002:2f80:3ab1:dbff:fef7:51ab/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7120 errors:0 dropped:0 overruns:0 frame:2001
          TX packets:4633 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:9359098 (9.3 MB)  TX bytes:468693 (468.6 KB)
          Interrupt:36 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"TPLINKACCESS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'TPLINKACCESS' [AC1]>   
          Retry short limit:7   RTS thr off   Fragment thr off
          Power Management off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search local

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

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

- Device: wlan0  [TPLINKACCESS] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    UPC2301519:      Infra, <MAC 'UPC2301519' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
    Stiegl:          Infra, <MAC 'Stiegl' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 55 WPA2
    devolo-bcf2afb1e44e: Infra, <MAC 'devolo-bcf2afb1e44e' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA2
    NETGEAR75:       Infra, <MAC 'NETGEAR75' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA2
    3WebCube7F34:    Infra, <MAC '3WebCube7F34' [AN5]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    CIA Security Network: Infra, <MAC 'CIA Security Network' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    michael:         Infra, <MAC 'michael' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    PBS-66934D:      Infra, <MAC 'PBS-66934D' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 9 WPA
    *TPLINKACCESS:   Infra, <MAC 'TPLINKACCESS' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 67 WPA WPA2
    UPC016077:       Infra, <MAC 'UPC016077' [AN10]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    PBS-47C681:      Infra, <MAC 'PBS-47C681' [AN11]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 20 WPA

  IPv4 Settings:
    Address:         192.168.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

  IPv6 Settings:
    Address:         2a02:8389:4002:2f80:416b:f959:be0c:c114
    Prefix:          64
    Gateway:         fe80::20b:ff:fe00:add0

    Address:         2a02:8389:4002:2f80:3ab1:dbff:fef7:51ab
    Prefix:          64
    Gateway:         fe80::20b:ff:fe00:add0

    Address:         fe80::3ab1:dbff:fef7:51ab
    Prefix:          64
    Gateway:         fe80::20b:ff:fe00:add0

    DNS:             2a02:8389:4002:2f80:20b:ff:fe00:add0

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

[[/etc/NetworkManager/system-connections/TPLINKACCESS]] (600 root)
[connection] id=TPLINKACCESS | type=802-11-wireless
[802-11-wireless] ssid=TPLINKACCESS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country AT:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TPLINKACCESS' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"TPLINKACCESS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC2301519' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"UPC2301519"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 56ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
     lo        Interface doesn't support scanning.

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.747452] wl: module license 'MIXED/Proprietary' taints kernel.
[   13.752628] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   13.909155] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[  425.359847] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

[COLOR=#000000]
```[/COLOR]

---

### Post by jeremy31 on 2015-04-23
It might help to change the wifi router encryption to WPA2-AES or WPA2 only as TKIP isn't needed by many devices any more and is less secure

If you are in Germany ```
sudo iw reg set DE
```

Reboot

Can you edit your second post to put code tags around the wireless script report, just put [ code ] before it, without the spaces between code and brackets and [ /code ] after again without spaces

---

### Post by martin154 on 2015-04-24
> **jeremy31 said:**
> It might help to change the wifi router encryption to WPA2-AES or WPA2 only as TKIP isn't needed by many devices any more and is less secure

If you are in Germany ```
sudo iw reg set DE
```

Reboot

Can you edit your second post to put code tags around the wireless script report, just put [ code ] before it, without the spaces between code and brackets and [ /code ] after again without spaces


Hi!

done, I see what you did there with the code tags.... will remember that :p

I am actually in Austria, what does the code do which you have posted? I have changed the router settings as mentioned but there is no improvement.

---

### Post by jeremy31 on 2015-04-24
If you are in Austria, your machine is set correctly then as the results in the wireless report shows AT for the ```
iw reg get
``` command

You could also see if your router is set to channel 6 as auto channel might cause problems if the router switches channels.  Then in Network Manager change the connection settings under the IPv6 tab to ignore

Chili555 may also have some ideas

The code tags help keep the formatting and prevents smilies from showing up in terminal output.  In the advanced reply window, there is a # you can click on that will place the tags and you just paste your info between them

---

### Post by martin154 on 2015-04-24
> **jeremy31 said:**
> If you are in Austria, your machine is set correctly then as the results in the wireless report shows AT for the ```
iw reg get
``` command

You could also see if your router is set to channel 6 as auto channel might cause problems if the router switches channels.  Then in Network Manager change the connection settings under the IPv6 tab to ignore

Chili555 may also have some ideas

The code tags help keep the formatting and prevents smilies from showing up in terminal output.  In the advanced reply window, there is a # you can click on that will place the tags and you just paste your info between them

many thanks Jeremy for your help.

I have changed the encryption to WPA2 AES = no improvement
I have deactivated IPv6 = no improvement

I will set the router to channel 6 only, at the moment I think it is set to auto.

Regards from Austria!
Martin

---

### Post by martin154 on 2015-04-24
here the updated output from the wireless script:

```



########## wireless info START ##########

Report from: 24 Apr 2015 11:51 CEST +0200

Booted last: 24 Apr 2015 11:46 CEST +0200

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu (from ~/.dmrc)

##### lspci #############################

03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:2230]
    Kernel driver in use: wl

04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 07)
    Subsystem: Hewlett-Packard Company Device [103c:22cd]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 003: ID 0bda:5776 Realtek Semiconductor Corp. 
Bus 002 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 003: ID 0a5c:216c Broadcom Corp. 
Bus 001 Device 002: ID 0438:7900 Advanced Micro Devices, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

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

wl                   6367833  0 
hp_wmi                 14109  0 
sparse_keymap          13948  1 hp_wmi
cfg80211              494362  1 wl
wmi                    19193  1 hp_wmi

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

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.15  Bcast:192.168.0.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1166 errors:0 dropped:0 overruns:0 frame:2237
          TX packets:1296 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:735033 (735.0 KB)  TX bytes:191196 (191.1 KB)
          Interrupt:36 

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"TPLINKACCESS"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: <MAC 'TPLINKACCESS' [AC1]>   
          Bit Rate=72 Mb/s   Tx-Power=200 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=57/70  Signal level=-53 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search local

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: <MAC address> ----------------------------------------------------
  Type:              Bluetooth
  Driver:            bluez
  State:             disconnected
  Default:           no

  Capabilities:

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

- Device: wlan0  [TPLINKACCESS] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    UPC2301519:      Infra, <MAC 'UPC2301519' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    *TPLINKACCESS:   Infra, <MAC 'TPLINKACCESS' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 48 WPA2
    PBS-66934D:      Infra, <MAC 'PBS-66934D' [AN3]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA
    UPC2607425:      Infra, <MAC 'UPC2607425' [AN4]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 25 WPA WPA2
    SS-69C419:       Infra, <MAC 'SS-69C419' [AN5]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 2 WPA WPA2
    devolo-bcf2afb1e44e: Infra, <MAC 'devolo-bcf2afb1e44e' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA2
    PBS-47C681:      Infra, <MAC 'PBS-47C681' [AN7]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 15 WPA
    3WebCube7F34:    Infra, <MAC '3WebCube7F34' [AN8]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 20 WPA2
    UPC016077:       Infra, <MAC 'UPC016077' [AN9]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    CIA Security Network: Infra, <MAC 'CIA Security Network' [AN10]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 19 WPA
    NETGEAR75:       Infra, <MAC 'NETGEAR75' [AN11]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 17 WPA2

  IPv4 Settings:
    Address:         192.168.0.15
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

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

[[/etc/NetworkManager/system-connections/TPLINKACCESS]] (600 root)
[connection] id=TPLINKACCESS | type=802-11-wireless
[802-11-wireless] ssid=TPLINKACCESS | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country AT:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Current Frequency:2.437 GHz (Channel 6)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'TPLINKACCESS' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:on
                    ESSID:"TPLINKACCESS"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'UPC2301519' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=21/70  Signal level=-89 dBm  
                    Encryption key:on
                    ESSID:"UPC2301519"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

0C5541415034333035323438331054000800060050F2040001101100074556573332323610080002200C103C0001011049000600372A000120

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-34-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     9A49255BA90267D99664757
depends:        cfg80211
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
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

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:0x4365 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[   13.995522] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   14.854537] Bluetooth: hci0: BCM: firmware hci_ver=06 hci_rev=00e7 lmp_ver=06 lmp_subver=210b

########## wireless info END ############



```

---

### Post by jeremy31 on 2015-04-24
I wonder if the drops aren't caused by bluetooth, try ```
rfkill block bluetooth
```

---

### Post by martin154 on 2015-04-24
> **jeremy31 said:**
> I wonder if the drops aren't caused by bluetooth, try ```
rfkill block bluetooth
```

unfortunately no improvement, unblocked now with rfkill unblock bluetooth

---

### Post by jeremy31 on 2015-04-24
I wonder if this is an odd case where wifi power management needs to be on
```
sudo iwconfig wlan0 power on
```

---

### Post by martin154 on 2015-04-25
> **jeremy31 said:**
> I wonder if this is an odd case where wifi power management needs to be on
```
sudo iwconfig wlan0 power on
```

hi there,

that has not helped. What I CAN confirm however is that since yesterday and changing the encryption, setting channel etc. the wifi seems to be alot more stable and my complete network is not dropping. What is still a pain however is the very weak signal. I am literally only 10feet away from the router with max. 2 bars showing on the taskbar applet. if I walk into the next room it loses signal completely. 

Driver issue?

---

### Post by aoharra on 2015-04-25
> **martin154 said:**
> Hi All,

First of all, here Information on my Laptop/wifi Hardware:

Linux jones-hp 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux 03:00.0 Network controller [0280]: **Broadcom Corporation BCM43142 802.11b/g/n** [COLOR=#b22222]**[14e4:4365]**[/COLOR] (rev 01)    Subsystem: Hewlett-Packard Company Device [103c:2230]    Kernel driver in use: wl

 When I installed UBUNTU the wifi Card was completely deactivated by default. When I went into the proprietory Drivers page in the update menu, I saw that my broadcom device was inactive, even though there was a Driver available. I activated the suggested Driver directly from the menu which was then installed, after which my wifi was working. I did notice however, that the Signal strength seemed to be fluctuating according to the Applet in the taskbar. Now the Connection not only regularly Drops out completely, but also seems to Crash the Network so that no other device can connect to the wireless modem! I know this, because my NAS is attached by cable to the router and sends me an email every time the Connection is dropped.have you any idea what could be causing this? Is it a Driver issue or could it even be a modem Setting (encryption etc.)? 

I am currently travelling and will be home this evening where I will run and post the contents of the wireless script to enable more detailed Information about the Laptop.

 Regards
 Martin

Hi Martin - 
I recognize that critter... You have the Broadcom BCM43xxx wireless card, as did my "learning partner"; it has known "issues" which can be resolved by installing a proprietary driver, as described in **[Installing Broadcom Wireless Drivers]("http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers")** (and it looks like yours is on the list). This procedure resolved our very similar problems; check it out, and good luck!
ADOHarra

---

### Post by martin154 on 2015-04-25
> **aoharra said:**
> Hi Martin - 
I recognize that critter... You have the Broadcom BCM43xxx wireless card, as did my "learning partner"; it has known "issues" which can be resolved by installing a proprietary driver, as described in **[Installing Broadcom Wireless Drivers]("http://askubuntu.com/questions/55868/installing-broadcom-wireless-drivers")** (and it looks like yours is on the list). This procedure resolved our very similar problems; check it out, and good luck!
ADOHarra

thanks for the feedback, I have the non-free and BCMWL packages installed already.

how about disabling wifi N in my laptop so it can only use b or g? Can anyone give me a command to disable N?

---

