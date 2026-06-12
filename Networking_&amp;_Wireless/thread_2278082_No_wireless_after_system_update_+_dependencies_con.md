---
title: "No wireless after system update + dependencies conflict"
date: 2015-05-13
forum: Networking &amp; Wireless
---

### Post by zhenia on 2015-05-13
After a system update I cannot connect using the wireless connection.
Here is what I get

```
sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: f0:1f:af:3e:5e:10
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.5.1-k duplex=full firmware=0.13-3 ip=192.168.2.102 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 memory:f7700000-f771ffff memory:f7739000-f7739fff ioport:f040(size=32)
  *-network
       description: Wireless interface
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth1
       version: 01
       serial: 70:18:8b:b9:7c:fe
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=6.20.155.1 (r326264) latency=0 multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:f7600000-f7603fff

```
*****************
```
ifconfig
eth0      Link encap:Ethernet  HWaddr f0:1f:af:3e:5e:10  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::f21f:afff:fe3e:5e10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54633 errors:0 dropped:0 overruns:0 frame:0
          TX packets:34957 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:71522881 (71.5 MB)  TX bytes:3663996 (3.6 MB)
          Interrupt:20 Memory:f7700000-f7720000 

eth1      Link encap:Ethernet  HWaddr 70:18:8b:b9:7c:fe  
          inet6 addr: fe80::7218:8bff:feb9:7cfe/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:52 errors:1 dropped:0 overruns:0 frame:13076
          TX packets:188 errors:220 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6694 (6.6 KB)  TX bytes:45464 (45.4 KB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2736 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2736 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:252808 (252.8 KB)  TX bytes:252808 (252.8 KB)

```

****************
And when I try co clean or update I get

```
sudo apt-get install linux-headers-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 linux-image-extra-3.13.0-32-generic : Depends: linux-image-3.13.0-32-generic but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```


********
I have tried force purging, autoremoving, everything, but always get the dependencies conflict. -f install does not help.

Hope you can advise me!

(The router works fine, and LAN works, too)

---

### Post by zhenia on 2015-05-13
I have tried to remove old images to win space, did not help
-f install gets me
```
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb (--unpack):
 trying to overwrite '/lib/modules/3.13.0-32-generic/kernel/net/packet/af_packet_diag.ko', which is also in package linux-image-extra-3.13.0-32-generic 3.13.0-32.57
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Errors were encountered while processing:
 /var/cache/apt/archives/linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

*****
and in case this helps, to complete the picture
*****
```
rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

---

### Post by grahammechanical on 2015-05-13
ifconfig will not show a WiFi adapter if Enable WiFi is not ticked. When WiFi is enabled ifconfig will show a listing for the WiFi adapter even if the WiFi adapter is not connected. Among other information ifconfig will show this.

> UP BROADCAST MULTICAST  MTU:1500  Metric:1

When WiFi is connected ifconfig should show this

> UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

I do not think the two problems are connected. As kernel 3.13.0-32 has not been successful processed I do not think your system is running on it. At the boot menu under Advanced Options we can load an earlier kernel. Doing that will tell if the problem with WiFi is connected to this new kernel.

If WiFi is not enabled then rfkill list will show soft blocked: yes. But if WiFi is enabled and the WiFi network is disconnected then you will see soft blocked: no. So seeing soft block: no does not prove that the WiFi adapter is connected to the router. We need to see UP BROADCAST RUNNING MULTICAST

Regards.

---

### Post by wildmanne39 on 2015-05-13
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks
It looks like your wifi may be working. Can you browse the internet?

These error messages you are getting:
```
dpkg: error processing /var/cache/apt/archives/linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb (--unpack):
trying to overwrite '/lib/modules/3.13.0-32-generic/kernel/net/packet/af_packet_diag.ko', which is also in package linux-image-extra-3.13.0-32-generic 3.13.0-32.57
dpkg-deb: error: subprocess paste was killed by signal (Broken pipe)
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.13.0-32-generic /boot/vmlinuz-3.13.0-32-generic
Errors were encountered while processing:
/var/cache/apt/archives/linux-image-3.13.0-32-generic_3.13.0-32.57~precise1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
is an issue with apt-get or the updater which is for installing applications.
That update failed.
Thanks

---

### Post by zhenia on 2015-05-14
I tried to post the script yesterday but it gets blocked because of too many images. Here it is split in bits and pieces. Wifi does work but no connection can be established wirelessly, I am now working via LAN connection.

```
########## wireless info START ##########

Report from: 14 May 2015 01:00 CEST +0200

Booted last: 14 May 2015 00:50 CEST +0200

Script from: 30 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.5 LTS
Release:    12.04
Codename:    precise

##### kernel ############################

Linux 3.2.0-83-generic #120-Ubuntu SMP Wed Apr 29 15:37:05 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, vga=0x318, "acpi_osi=!Windows, 2009", quiet, splash

##### desktop ###########################

Ubuntu 2D

##### lspci #############################

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Dell Device [1028:0534]
    Kernel driver in use: e1000e

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    Subsystem: Dell Device [1028:0015]
    Kernel driver in use: wl

##### lsusb #############################

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 003 Device 002: ID 046d:c018 Logitech, Inc. Optical Wheel Mouse
Bus 001 Device 003: ID 413c:8197 Dell Computer Corp. 
Bus 001 Device 004: ID 0c45:648b Microdia 
Bus 002 Device 003: ID 0a5c:5801 Broadcom Corp. BCM5880 Secure Applications Processor with fingerprint swipe sensor
```

---

### Post by zhenia on 2015-05-14
```
##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: dell-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: dell-bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

ath9k                 132556  0 
mac80211              506862  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411239  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
wl                   3074895  0 
dell_laptop            18119  0 
dcdbas                 14490  1 dell_laptop
cfg80211              205774  4 ath9k,mac80211,ath,wl
lib80211               14381  2 lib80211_crypt_tkip,wl
wmi                    19256  1 dell_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.102  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::f21f:afff:fe3e:5e10/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4618 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7305814 (7.3 MB)  TX bytes:525936 (525.9 KB)
          Interrupt:20 Memory:f7700000-f7720000 

eth1      Link encap:Ethernet  HWaddr <MAC 'eth1' [IF]>  
          inet6 addr: fe80::7218:8bff:feb9:7cfe/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31 errors:2 dropped:0 overruns:0 frame:4478
          TX packets:97 errors:97 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4071 (4.0 KB)  TX bytes:23374 (23.3 KB)
          Interrupt:17 

##### iwconfig ##########################

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11abg  ESSID:"EasyBox-1BBF45"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'EasyBox-1BBF45' [AC1]>   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.0.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth1  [EasyBox-1BBF45] -----------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connecting (getting IP configuration)
  Default:           no
  HW Address:        <MAC 'eth1' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    FRITZ!Box Fon WLAN 6360: Infra, <MAC 'FRITZ!Box Fon WLAN 6360' [AC4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 59 WPA WPA2
    ALICE-WLAN48:    Infra, <MAC 'ALICE-WLAN48' [AC2]>, Freq 2422 MHz, Rate 54 Mb/s, Strength 22 WPA2
    o2-WLAN01:       Infra, <MAC 'o2-WLAN01' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 12 WPA2
    EasyBox-1BBF45:  Infra, <MAC 'EasyBox-1BBF45' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 100 WPA WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            e1000e
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.2.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1

    DNS:             192.168.2.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/EasyBox-1BBF45]] (600 root)
[connection] id=EasyBox-1BBF45 | type=802-11-wireless
[802-11-wireless] ssid=EasyBox-1BBF45 | mac-address=<MAC 'eth1' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/Berlin (based on set time zone)

country DE:
    (2400 - 2483 @ 40), (N/A, 20)
    (5150 - 5250 @ 40), (N/A, 20), NO-OUTDOOR
    (5250 - 5350 @ 40), (N/A, 20), NO-OUTDOOR, DFS
    (5470 - 5725 @ 40), (N/A, 26), DFS

##### iwlist channels ###################

lo        no frequency information.

eth0      no frequency information.

eth1      32 channels in total; available frequencies :
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
          Channel 34 : 5.17 GHz
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
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      2   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      1   APs on   Frequency:2.462 GHz (Channel 11)

lo        Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: <MAC 'EasyBox-1BBF45' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=70/70  Signal level=-22 dBm  
                    Encryption key:on
                    ESSID:"EasyBox-1BBF45"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 84ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 02 - Address: <MAC 'ALICE-WLAN48' [AC2]>
                    Channel:3
                    Frequency:2.422 GHz (Channel 3)
                    Quality=20/70  Signal level=-90 dBm  
                    Encryption key:on
                    ESSID:"ALICE-WLAN48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
            eth0      Interface doesn't support scanning.

          Cell 03 - Address: <MAC 'o2-WLAN01' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"o2-WLAN01"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
          Cell 04 - Address: <MAC 'FRITZ!Box Fon WLAN 6360' [AC4]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"FRITZ!Box Fon WLAN 6360"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
```

---

### Post by zhenia on 2015-05-14
```
##### module infos ######################

[ath9k]
filename:       /lib/modules/3.2.0-83-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     14D825B9480637C9A617AD3
depends:        ath9k_hw,ath9k_common,mac80211,cfg80211,ath
intree:         Y
vermagic:       3.2.0-83-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           ps_enable:Enable WLAN PowerSave (int)

[mac80211]
filename:       /lib/modules/3.2.0-83-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     E240EFDC3EE774AE3EEA5D1
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-83-generic SMP mod_unload modversions 
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)

[ath9k_common]
filename:       /lib/modules/3.2.0-83-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     22A34AE648BB82201A1A7AF
depends:        ath,ath9k_hw
intree:         Y
vermagic:       3.2.0-83-generic SMP mod_unload modversions 

[ath9k_hw]
filename:       /lib/modules/3.2.0-83-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     A764DEB226B84498BCFE72A
depends:        ath
intree:         Y
vermagic:       3.2.0-83-generic SMP mod_unload modversions 
parm:           force_new_ani:Force new ANI for AR5008, AR9001, AR9002 (int)

[ath]
filename:       /lib/modules/3.2.0-83-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     8B429DBE4586F4065E2EA2E
depends:        cfg80211
intree:         Y
vermagic:       3.2.0-83-generic SMP mod_unload modversions 

[wl]
filename:       /lib/modules/3.2.0-83-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     CBEDDD2D4888AAD1517D3C9
depends:        cfg80211,lib80211
vermagic:       3.2.0-83-generic SMP mod_unload modversions 
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.2.0-83-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     3F81584A8E06499FBACA9C1
depends:        
intree:         Y
vermagic:       3.2.0-83-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[ath9k]
blink: 0
btcoex_enable: 0
nohwcrypt: 0
ps_enable: 0

[mac80211]
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[ath9k_hw]
force_new_ani: 0

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc
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

[/etc/modprobe.d/oss-compat.conf]
install snd-pcm modprobe --ignore-install snd-pcm $CMDLINE_OPTS && { modprobe --quiet snd-pcm-oss ; : ; }
install snd-mixer modprobe --ignore-install snd-mixer $CMDLINE_OPTS && { modprobe --quiet snd-mixer-oss ; : ; }
install snd-seq modprobe --ignore-install snd-seq $CMDLINE_OPTS && { modprobe --quiet snd-seq-midi ; modprobe --quiet snd-seq-oss ; : ; }

##### rc.local ##########################

modprobe -r ath9k
sleep 5
modprobe ath9k
exit 0

##### pm-utils ##########################

[/etc/pm/sleep.d/90GlidePoint] (755 root)
case "$1" in
    hibernate|suspend)
        ;;
    resume|thaw)
        sudo killall -s SIGKILL glided
        ;;
    *) exit 0
        ;;
    esac

[/etc/pm/sleep.d/99bcmbluetooth] (755 root)
start_bluetooth()
{
    if [ x"$(lsmod | grep btusb)" = "x" ]; then
        modprobe btusb
        sleep 2
    fi
    for dev in $(hcitool dev | grep hci | cut -f2)
    do
        hciconfig $dev up
        sleep 1
    done
    if [ x"$(service bluetooth status | grep process)" = "x" ]; then
        service bluetooth start
    fi
}
stop_bluetooth()
{
    service bluetooth stop
    sleep 2
    for dev in $(hcitool dev | grep hci | cut -f2)
    do
        hciconfig $dev down
    done
    sleep 2
    modprobe -r btusb
}
case "$1" in
    hibernate|suspend)
        # check if there exists any bluetooth device
        [ $(hcitool dev | grep hci | wc -l) -eq 0 ] && exit 0
        stop_bluetooth
        ;;
    thaw|resume)
        start_bluetooth
        ;;
    *) exit $NA
        ;;
esac

[/etc/pm/sleep.d/wakenet.sh] (644 root)
case "$1" in
thaw|resume)
nmcli nm sleep false
pkill -f wpa_supplicant
;;
*)
;;
esac
exit $?

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x8086:/sys/devices/pci0000:00/0000:00:19.0 (e1000e)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# PCI device 0x14e4:/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth1' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth1"

##### dmesg #############################

[  619.708731] eth1: IPv6 duplicate address fe80::7218:8bff:feb9:7cfe detected!
[  657.997433] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############
```

---

### Post by slickymaster on 2015-05-14
> **zhenia said:**
> I tried to post the script yesterday but it gets blocked because of too many images. Here it is split in bits and pieces. <---snip--->
That's because you didn't use code tags to post the output of the script.

I've now edit your posts in this thread, adding code tags to all. Output code, posted as plain text, loses its formatting and parts of it sometimes turn into smileys making it difficult to read and understand. The [use of code tags]("http://ubuntuforums.org/showthread.php?t=2171721&p=12776168&viewfull=1#post12776168") makes the post clean, compact and more appealing, thus getting more attention from readers.

---

### Post by zhenia on 2015-05-14
should i try to update the system to ubuntu 14? am new to this and am not really sure what's best

---

### Post by wildmanne39 on 2015-05-14
Hi, I notice you have the driver ath9k loaded, did you remove this device and use only the broadcom now?
Thanks

---

### Post by praseodym on 2015-05-14
Please run:
```

sudo modprobe -rfv wl ath9k
sudo apt-get remove --purge bcmwl-kernel-source
```
Download this file and save it in "Downloads":

[http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/04/32/2480236-Broadcom_Firmware.tar.gz) 

Installation:
```

cd ~/Downloads/
sudo tar xvf 2480236-Broadcom_Firmware.tar.gz -C /lib/firmware/ 
```
Reboot.

---

### Post by wildmanne39 on 2015-05-14
The driver for the device you are using has a bug in it so we are going to install a new driver, just copy and paste for accuracy the commands one line at a time into the terminal CTRL+ALT+T.
First let's purge the old one:
```
sudo apt-get purge bcmwl-kernel-source
```
```
sudo mkdir /usr/src/hybrid-portsrc_x86_64-6.30.223.141
wget http://media.cdn.ubuntu-de.org/forum/attachments/36/49/2865859-hybrid-portsrc_x86_64-v6_30_223_141_dkms.tar.gz
sudo tar xvf 2865859-hybrid-portsrc_x86_64-v6_30_223_141_dkms.tar.gz -C /usr/src/hybrid-portsrc_x86_64-6.30.223.141 
```
Then to build the driver:
```
sudo apt-get install --reinstall linux-headers-$(uname -r) linux-headers-generic build-essential dkms
sudo dkms add -m hybrid-portsrc_x86_64 -v 6.30.223.141
sudo dkms build -m hybrid-portsrc_x86_64 -v 6.30.223.141
sudo dkms install -m hybrid-portsrc_x86_64 -v 6.30.223.141 
```
Watch for errors as the commands run.

I recommend blacklisting the ath9k driver if it is not needed.
```
echo "blacklist ath9k | sudo tee -a /etc/modprobe.d/blacklist.conf

```
Original Post can be found here:
[http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS](http://forum.ubuntuusers.de/topic/w-lan-acer-4820tg-broadcom-installation-schlae/#Installation-mittels-DKMS)
Reboot
Thanks

---

### Post by zhenia on 2015-05-14
thanks praseodym's tip has worked perfectly well!

---

