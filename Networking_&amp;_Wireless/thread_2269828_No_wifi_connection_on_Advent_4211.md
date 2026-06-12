---
title: "No wifi connection on Advent 4211"
date: 2015-03-18
forum: Networking &amp; Wireless
---

### Post by Sandy0848 on 2015-03-18
XP on my well used and well travelled Advent 4211 went sick about six months ago and this persuaded me to install Lubuntu and remove the XP completely

On ethernet connection all works fine but I am not able to establish any wifi connection.

I have set out to follow the instructions given by Bapoumpa at the head of this forum and I attach the wireless-info text which results.

It would be great if someone who knows what is what would review the text and advise me on what to do next.


Regards   Sandy Sanderson



```
########## wireless info START ##########

Report from: 15 Mar 2015 09:08 CET +0100

Booted last: 14 Mar 2015 13:05 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:08:14 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################


01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:0110]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Micro-Star International Co., Ltd. [MSI] MN54G2 / MS-6894 Wireless Mini PCIe Card [1462:6894]
    Kernel driver in use: r8180

##### lsusb #############################

Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################


##### lsmod #############################

cfg80211              409394  0 
msi_wmi                13130  0 
sparse_keymap          13708  1 msi_wmi
r8187se               155125  0 
eeprom_93cx6           13168  1 r8187se
wmi                    18673  1 msi_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr 00:21:85:4f:8a:52  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: 2a02:a03f:2887:8900:221:85ff:fe4f:8a52/64 Scope:Global
          inet6 addr: fe80::221:85ff:fe4f:8a52/64 Scope:Link
          inet6 addr: 2a02:a03f:2887:8900:ddb2:a83b:2492:72c9/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:18816 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17885 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4069597 (4.0 MB)  TX bytes:1699882 (1.6 MB)

wlan0     Link encap:Ethernet  HWaddr 00:21:85:7b:5b:79  
          inet6 addr: fe80::221:85ff:fe7b:5b79/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:95 errors:0 dropped:370 overruns:0 frame:0
          TX packets:32895 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10735 (10.7 KB)  TX bytes:2410099 (2.4 MB)
          Interrupt:17 Memory:f8480000-f8480100 


##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"WiFi-2.4-0FE7"  
          Mode:Managed  Frequency=2.472 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### nm-tool ###########################


NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8180
  State:             disconnected
  Default:           no
  HW Address:        00:21:85:7B:5B:79

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    PROXIMUS_FON:    Infra, 32:91:8F:49:0F:E8, Freq 2462 MHz, Rate 54 Mb/s, Strength 97
    WiFi-2.4-0FE7:   Infra, 30:91:8F:49:0F:E7, Freq 2462 MHz, Rate 54 Mb/s, Strength 97 WPA2


- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        00:21:85:4F:8A:52

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1



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

no-auto-default=00:21:85:4F:8A:52,

[ifupdown]
managed=false

##### NetworkManager profiles ###########
```

---

### Post by wildmanne39 on 2015-03-19
There is a lot of that file missings, could you please run the script again and post the results here.
Install rfkill first.
Thanks

---

### Post by Sandy0848 on 2015-03-19
Thanks for your reply, Wild Man.  I will do as you advise but it may take a day or to.

Cheers   Sandy

---

### Post by Sandy0848 on 2015-03-23
I am afraid I didn't understand your instruction to install refkill. When I enteresd rfkill at a terminal it appeared to request other information.

I then proceeded to run the Bapoumba instructions again and will; add the wireless-info text below.

[code]
########## wireless info START ##########

Report from: 23 Mar 2015 10:44 CET +0100

Booted last: 23 Mar 2015 10:31 CET +0100

Script from: 20 Sep 2014 23:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.13.0-46-generic #79-Ubuntu SMP Tue Mar 10 20:08:14 UTC 2015 i686 i686 i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Lubuntu

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Micro-Star International Co., Ltd. [MSI] Device [1462:0110]
    Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8187SE Wireless LAN Controller [10ec:8199] (rev 22)
    Subsystem: Micro-Star International Co., Ltd. [MSI] MN54G2 / MS-6894 Wireless Mini PCIe Card [1462:6894]
    Kernel driver in use: r8180

##### lsusb #############################

Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 13fe:4100 Kingston Technology Company Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 002: ID 0db0:a97a Micro Star International Bluetooth EDR Device
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

'pccardctl' is not installed (package "pcmciautils").

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

cfg80211              409394  0 
msi_wmi                13130  0 
sparse_keymap          13708  1 msi_wmi
r8187se               155125  0 
eeprom_93cx6           13168  1 r8187se
wmi                    18673  1 msi_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:85ff:fe4f:8a52/64 Scope:Link
          inet6 addr: 2a02:a03f:289f:8600:1912:df94:8cd4:3739/64 Scope:Global
          inet6 addr: 2a02:a03f:289f:8600:221:85ff:fe4f:8a52/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31815 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16783 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:47089134 (47.0 MB)  TX bytes:1495591 (1.4 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:420 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:30952 (30.9 KB)
          Interrupt:17 Memory:f84e8000-f84e8100 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     802.11b/g  ESSID:"g\xC6isQ\xFFJ\xEC)\xCD\xBA\xAB\xF2\xFB\xE3F|\xC2T\xF8\x1B\xE8\xE7\x8DvZ.c3\x9F\xC9\x9A"  
          Mode:Managed  Frequency=2.422 GHz  Access Point: Not-Associated   
          Bit Rate:11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### nm-tool ###########################

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            r8180
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.5
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

  IPv6 Settings:
    Address:         2a02:a03f:289f:8600:1912:df94:8cd4:3739
    Prefix:          64
    Gateway:         fe80::3291:8fff:fe49:fe6

    Address:         2a02:a03f:289f:8600:221:85ff:fe4f:8a52
    Prefix:          64
    Gateway:         fe80::3291:8fff:fe49:fe6

    Address:         fe80::221:85ff:fe4f:8a52
    Prefix:          64
    Gateway:         fe80::3291:8fff:fe49:fe6

    DNS:             fe80::3291:8fff:fe49:fe6

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

no-auto-default=<MAC 'eth0' [IF]>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/PROXIMUS_FON]] (600 root)
[connection] id=PROXIMUS_FON | type=802-11-wireless
[802-11-wireless] ssid=PROXIMUS_FON | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/ThingyNet]] (600 root)
[connection] id=ThingyNet | type=802-11-wireless | autoconnect=false
[802-11-wireless] ssid=ThingyNet | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/WiFi-2.4-0FE7]] (600 root)
[connection] id=WiFi-2.4-0FE7 | type=802-11-wireless
[802-11-wireless] ssid=WiFi-2.4-0FE7 | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/GRENONBBOX-EXT]] (600 root)
[connection] id=GRENONBBOX-EXT | type=802-11-wireless
[802-11-wireless] ssid=GRENONBBOX-EXT | mac-address=<MAC address>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

'iw' is not installed (package "iw").

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
          Current Channel=3

##### iwlist scan #######################

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     No scan results

##### module infos ######################

[cfg80211]
filename:       /lib/modules/3.13.0-46-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     5C139B156678DB83EDA757D
depends:        
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        6B:0C:44:F3:70:56:1E:18:0C:94:6F:75:FE:6D:F2:27:33:5D:49:D4
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[r8187se]
filename:       /lib/modules/3.13.0-46-generic/kernel/drivers/staging/rtl8187se/r8187se.ko
description:    Linux driver for Realtek RTL8187SE WiFi cards
author:         Andrea Merello <andrea.merello@gmail.com>
license:        GPL
license:        GPL
author:         Copyright (C) 2004 Intel Corporation <jketreno@linux.intel.com>
description:    802.11 data/management/control stack
license:        GPL
description:    HostAP crypto
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: TKIP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: CCMP
author:         Jouni Malinen
license:        GPL
description:    Host AP crypt: WEP
author:         Jouni Malinen
srcversion:     7BE01256633B67BF1ADB4FF
depends:        eeprom_93cx6
staging:        Y
intree:         Y
vermagic:       3.13.0-46-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        6B:0C:44:F3:70:56:1E:18:0C:94:6F:75:FE:6D:F2:27:33:5D:49:D4
sig_hashalgo:   sha512
parm:           ifname:string
parm:           hwwep: Try to use hardware WEP support. Still broken and not available on all cards (int)

##### module parameters #################

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

[r8187se]
hwwep: 0
ifname: wlan%d

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

[/etc/modprobe.d/libpisock9.conf]
blacklist visor

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8199 (r8180)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   23.475282] r8180: Bringing up iface
[   23.673987] r8180: Card successfully reset
[   24.412780] r8180: WIRELESS_MODE_G
[   24.443862] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)

########## wireless info END ############

Wildman, please tell me that I am making progress

Cheers   Sandy

---

### Post by wildmanne39 on 2015-03-23
You need to do:
```
sudo apt-get install rfkill
```
Then the terminal will ask for your password just type it and hit enter, you will not see the password as you type it for security reasons.
I just assumed you knew how to install software through the software center, sorry about that.
Thanks

---

### Post by Sandy0848 on 2015-03-23
I should have made it clear that I am an aged beginner

Installed rfkill as per your instructions and got answer thar rfkill was already the newest version

Was that last code output of any value.

I remain your aged pupil

Sandy

---

### Post by stephen_ward on 2015-03-23
Some files are missing. Unless you provide more information it will be quite hard to help.

---

### Post by wildmanne39 on 2015-03-23
Please run:
```
rfkill list all
```
if it produces out post it here if not try it like this.
```
sudo rfkill list all
```
Thanks

---

### Post by Sandy0848 on 2015-03-24
0: hc10: Bluetooth
          Soft blocked:no
          Hard blocked: no


Hope this helps   Sandy

---

### Post by wildmanne39 on 2015-03-24
That only shows your bluethooth and not your wifi that is strange, was this with the second command or the first?
Thanks

---

### Post by Sandy0848 on 2015-03-25
Same answer both ways, Wildman.

What a so and so

Cheers   Sandy

---

### Post by Sandy0848 on 2015-03-26
Some of my replies seem to have gone missing

I got the same results with both commands.

I then switched off the bluetooth and repeated the exercise and got a nil reply on both commands.

Where do I go next

Sandy

---

### Post by wildmanne39 on 2015-03-26
Remove all your connections from network manager then reboot computer then change your settings in network manager at the top right of the screen to match the screenshots.
In your router change the channel to 1 or 11 then sav the settings.
If it does not connect post a new scriot file.
Also note that your ethernet and usb connection needs to be disbaled for your wireless to work.
Thanks

---

### Post by Sandy0848 on 2015-04-04
At first I didn't appear to have a Network Manager. Review of the forum showed me that othe people had this problem about a year ago. Was eventually able adjust network settings and could see on the screen two connections on of which was the successful ethernet.

Review of the other showed no connection.

Does any of this make sense.

I have read elsewhere in the forum that the r818x and r 8187 drivers are blacklisted. Is this the source of my problems.

Sorry Wildman I did say that I was very old and not up with all this business

---

