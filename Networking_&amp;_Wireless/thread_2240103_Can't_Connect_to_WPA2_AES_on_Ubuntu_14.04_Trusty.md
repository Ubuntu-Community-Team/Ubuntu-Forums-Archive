---
title: "Can't Connect to WPA2 AES on Ubuntu 14.04 Trusty"
date: 2014-08-17
forum: Networking &amp; Wireless
---

### Post by jrolland2 on 2014-08-17
Hello, all!

I have a Toshiba Satellite A215-4697 (which I bought without a wifi card) running Ubuntu 14.04 Trusty. I purchased a NetGear N300 WiFi USB adaptor. I am trying to get it connected to a my home network, run by a NetGear N300 Wireless Router WNR2000v3.

When I turn off all encryption on the router, I am able to connect and transmit data.

However, the router only supports 3 flavors of WPA2 (one of which is Enterprise, which I can't test) for encryption, and when I have the router set to WPA2-PSK [AES] or WPA2-PSK [TKIP] + WPA2-PSK [AES], I cannot connect. I am able to see and select the network, but the OS keeps on bringing up a dialog box for the password and won't connect to the network.

Here is the result of the wireless script from the sticky:

```

########## wireless info START ##########

Report from: 17 Aug 2014 22:16 CDT -0500

Script from: 17 Aug 2014 02:46 UTC +0000

##### release #####

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:    14.04
Codename:    trusty

##### kernel #####

Linux 3.13.0-34-generic #60-Ubuntu SMP Wed Aug 13 15:49:09 UTC 2014 i686 athlon i686 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop #####

Ubuntu

##### lspci #####

0e:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 01)
    Subsystem: Toshiba America Info Systems Device [1179:ff00]
    Kernel driver in use: r8169

##### lsusb #####

Bus 001 Device 003: ID 0846:9020 NetGear, Inc. WNA3100(v1) Wireless-N 300 [Broadcom BCM43231]
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 0461:4d46 Primax Electronics, Ltd 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info #####

PRODID_1=""
PRODID_2=""
PRODID_3=""
PRODID_4=""
MANFID=0000,0000
FUNCID=255

##### rfkill #####

##### lsmod #####

wmi                    18673  1 toshiba_acpi
ndiswrapper           192915  0 

##### interfaces #####

auto lo
iface lo inet loopback

##### ifconfig #####

eth0      Link encap:Ethernet  HWaddr <MAC addr eth0>  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21b:38ff:fe11:ab0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:721 errors:0 dropped:0 overruns:0 frame:0
          TX packets:841 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:299278 (299.2 KB)  TX bytes:123075 (123.0 KB)

wlan0     Link encap:Ethernet  HWaddr <MAC addr wlan0>  
          inet6 addr: fe80::e6f4:c6ff:fe3f:7183/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:24 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:452 (452.0 B)  TX bytes:4713 (4.7 KB)

##### iwconfig #####

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:300 Mb/s   Tx-Power:32 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

##### route #####

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #####

nameserver 127.0.1.1

##### nm-tool #####

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             disconnected
  Default:           no
  HW Address:        <MAC addr wlan0>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    NETGEAR69:       Infra, <MAC addr NETGEAR69>, Freq 2437 MHz, Rate 54 Mb/s, Strength 54 WPA2
    Jacobi:          Infra, <MAC addr Jacobi>, Freq 2417 MHz, Rate 54 Mb/s, Strength 42 WPA2
    samcross85:      Infra, <MAC addr samcross85>, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WPA2
    T. Ritter:       Infra, <MAC addr T. Ritter>, Freq 2462 MHz, Rate 54 Mb/s, Strength 27 WPA2
    HP-Print-B1-Deskjet 2540 series: Infra, <MAC addr HP-Print-B1-Deskjet 2540 series>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    Bob&Irma:        Infra, <MAC addr Bob<MAC address>Irma>, Freq 2412 MHz, Rate 54 Mb/s, Strength 24 WPA2
    Rolland:         Infra, <MAC addr Rolland>, Freq 2422 MHz, Rate 54 Mb/s, Strength 84 WPA2
    TootsWiFi:       Infra, <MAC addr TootsWiFi>, Freq 2452 MHz, Rate 54 Mb/s, Strength 27 WPA
    julie:           Infra, <MAC addr julie>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WEP
    NETGEAR14:       Infra, <MAC addr NETGEAR14>, Freq 2442 MHz, Rate 54 Mb/s, Strength 22 WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC addr eth0>

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.1.4
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1

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
          Current Frequency:2.422 GHz (Channel 3)

##### iwlist scan #####

Channel occupancy:

     1   WLAPs on   Frequency:2.417 GHz (Channel 2)
     1   WLAPs on   Frequency:2.422 GHz (Channel 3)
     1   WLAPs on   Frequency:2.437 GHz (Channel 6)
     1   WLAPs on   Frequency:2.442 GHz (Channel 7)
     2   WLAPs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC addr Rolland>
                    ESSID:"Rolland"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.422 GHz (Channel 3)
                    Quality:68/100  Signal level:-52 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC addr NETGEAR69>
                    ESSID:"NETGEAR69"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC addr NETGEAR14>
                    ESSID:"NETGEAR14"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.442 GHz (Channel 7)
                    Quality:14/100  Signal level:-87 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC addr samcross85>
                    ESSID:"samcross85"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:26/100  Signal level:-79 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC addr T. Ritter>
                    ESSID:"T. Ritter"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.462 GHz (Channel 11)
                    Quality:15/100  Signal level:-86 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

eth0      Interface doesn't support scanning.

00000000
          Cell 06 - Address: <MAC addr Jacobi>
                    ESSID:"Jacobi"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Frequency:2.417 GHz (Channel 2)
                    Quality:32/100  Signal level:-75 dBm  Noise level:-96 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos #####

[ndiswrapper]
filename:       /lib/modules/3.13.0-34-generic/updates/dkms/ndiswrapper.ko
license:        GPL
version:        1.59
description:    NDIS wrapper driver
author:         ndiswrapper team <ndiswrapper-general@lists.sourceforge.net>
srcversion:     C101C962263FFF26465A483
depends:        
vermagic:       3.13.0-34-generic SMP mod_unload modversions 686 
parm:           if_name:Network interface name or template (default: wlan%d) (charp)
parm:           proc_uid:The uid of the files created in /proc (default: 0). (int)
parm:           proc_gid:The gid of the files created in /proc (default: 0). (int)
parm:           debug:debug level (int)
parm:           hangcheck_interval:The interval, in seconds, for checking if driver is hung. (default: 0) (int)
parm:           utils_version:Compatible version of utils (read only: 1.9) (charp)

##### module parameters #####

grep: /sys/module/ndiswrapper/parameters/debug: Permission denied
grep: /sys/module/ndiswrapper/parameters/hangcheck_interval: Permission denied
grep: /sys/module/ndiswrapper/parameters/if_name: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_gid: Permission denied
grep: /sys/module/ndiswrapper/parameters/proc_uid: Permission denied
grep: /sys/module/ndiswrapper/parameters/utils_version: Permission denied
[ndiswrapper]

##### /etc/modules #####

lp
ndiswrapper

##### blacklists #####

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

##### udev rules #####

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:/sys/devices/pci0000:00/0000:00:06.0/0000:0e:00.0 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# USB device 0x:0x (ndiswrapper)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC addr wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #####

[   16.602336] ndiswrapper: module verification failed: signature and/or  required key missing - tainting kernel
[   16.604386] ndiswrapper version 1.59 loaded (smp=yes, preempt=no)
[   94.254956] ndiswrapper: driver bcmwlhigh5 (Netgear,11/05/2009, 5.60.180.11) loaded
[   94.847208] wlan0: ethernet device <MAC addr wlan0> using NDIS driver: bcmwlhigh5, version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter', 0846:9020.F.conf
[   94.852065] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK; AES/CCMP with WPA, WPA2, WPA2-PSK
[   95.102485] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 2 times)
[  110.536566] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############

```

Any assistance you can supply is appreciated. Chili555, your support in the previous threads was superlative; I you could help in particular, I would be greatly appreciative.

Please let me know if there is any additional information you require. Thanks in advance.

---

### Post by chili555 on 2014-08-18
> Chili555, your support in the previous threads was superlative; I you could help in particular, I would be greatly appreciative.
I don't know if I should love or hate getting called out by name!

The driver in question, ndiswrapper, is a bit of a roll of the dice. It depends on the ancient and creaky Windows XP .inf and .sys files. Every time I walk through the big box store and see those Netgears on the shelf, I reflexively curse ndiswrapper! There are a few things I suggest you try. First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, I have better luck with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. After making these changes, reboot the router. I assume you are trying to connect to 'Rolland' that is on channel 3. There is some overlap with channel 2. Assuming the router can do it, I'd try channels 11, 12 or 13.

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

Next, I'd set IPv6 to Ignore in Network Manager: [http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png](http://docs.fedoraproject.org/en-US/Fedora/18/html/Installation_Guide/images/netconfig/network-connections-ipv6-ignore.png)  This example is for ethernet, but you want wireless.

---

### Post by jrolland2 on 2014-08-18
Chili555! Thank you so much for replying!

I implemented all of your suggestions, but to no avail; I still can't log into the router

Thanks anyways for your help.

(Out of a little more than idle curiosity, you seem to have singled out NetGear as working ineffectively with ndiswrapper; is there another brand name of USB wireless adapter that would work better with Ubuntu? It was more-or-less a fluke that I decided on NetGear; I can easily go with a different wireless adapter.)

Thanks again.

---

### Post by chili555 on 2014-08-18
There are many devices that are fully supported with native Linux drivers. However, before we give up, let's see if we can coax the Netgear to life. Please detach the ethernet and try to connect. As it is trying, run:```
cat /var/log/syslog | grep -e wlan -e etwork  >  wifi.txt
nm-tool  >>  wifi.txt
```Attach the ethernet, connect and then find the file wifi.txt in your user directory and post the contents here.

---

### Post by jrolland2 on 2014-08-30
Whoops - I was called unexpectedly out of town, then classes started - sorry it took me so long to get back to you.

I  have a linux-native driver wifi adapter now  <[http://www.newegg.com/Product/Product.aspx?Item=9SIA4641EU6353&Tpk=9SIA4641EU6353](http://www.newegg.com/Product/Product.aspx?Item=9SIA4641EU6353&Tpk=9SIA4641EU6353)>,  so the point is a little moot, but I may need to attach with the  NetGear adapter in a pinch, so any assistance you can provide is still  appreciated.

Here is the output from your commands:

```

Aug 22 19:14:13 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:14:13 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:14:13 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:14:13 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:14:13 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:14:13 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:15:07 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:15:07 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:15:07 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:15:07 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:15:07 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:15:07 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:15:54 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:15:54 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:15:54 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:15:54 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:15:54 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:15:54 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:16:41 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:16:41 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:16:41 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:16:41 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:16:41 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:16:41 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:17:30 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:17:30 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:17:30 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:17:30 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:17:30 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:17:30 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:18:13 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:18:13 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:18:13 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:18:13 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:18:13 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:18:13 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:19:03 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:19:03 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:19:03 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:19:03 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:19:03 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:19:03 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:19:47 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:19:47 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:19:47 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:19:47 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:19:47 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:19:47 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:20:35 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:20:35 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:20:35 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:20:35 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:20:35 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:20:35 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:21:23 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:21:23 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:21:23 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:21:23 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:21:23 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:21:23 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:22:12 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:22:12 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:22:12 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:22:12 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:22:12 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:22:12 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:23:05 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:23:05 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:23:05 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:23:05 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:23:05 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:23:05 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:23:53 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:23:53 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:23:53 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:23:53 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:23:53 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:23:53 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:24:39 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:24:39 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:24:39 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:24:39 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:24:39 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:24:39 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:25:22 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:25:22 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:25:22 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:25:22 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:25:22 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:25:22 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:26:15 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:26:15 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:26:15 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:26:15 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:26:15 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:26:15 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:27:07 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:27:07 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:27:07 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:27:07 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:27:07 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:27:07 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:28:01 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:28:01 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:28:01 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:28:01 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:28:01 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:28:01 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:28:48 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:28:48 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:28:48 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:28:48 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:28:48 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:28:48 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:29:31 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:29:31 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:29:31 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:29:31 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:29:31 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:29:31 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:30:26 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:30:26 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:30:26 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:30:26 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:30:26 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:30:26 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:31:18 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:31:18 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:31:18 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:31:18 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:31:18 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:31:18 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:32:01 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:32:01 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:32:01 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:32:01 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:32:01 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:32:01 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:32:45 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:32:45 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:32:45 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:32:45 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:32:45 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:32:45 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:33:37 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:33:37 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:33:37 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:33:37 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:33:37 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:33:37 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:34:21 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:34:21 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:34:21 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:34:21 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:34:21 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:34:21 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:35:10 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:35:10 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:35:10 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:35:10 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:35:10 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:35:10 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:35:58 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:35:58 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:35:58 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:35:58 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:35:58 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:35:58 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:36:45 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:36:45 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:36:45 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:36:45 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:36:45 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:36:45 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:37:28 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:37:28 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:37:28 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:37:28 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:37:28 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:37:28 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:38:11 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:38:11 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:38:11 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:38:11 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:38:11 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:38:11 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:38:56 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:38:56 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:38:56 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:38:56 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:38:56 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:38:56 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:39:40 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:39:40 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:39:40 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:39:40 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:39:40 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:39:40 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:40:31 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:40:31 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:40:31 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:40:31 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:40:31 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:40:31 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:41:22 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:41:22 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:41:22 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:41:22 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:41:22 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:41:22 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:42:07 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:42:07 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:42:07 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:42:07 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:42:07 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:42:07 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:42:51 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:42:51 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:42:51 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:42:51 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:42:51 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:42:51 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:43:46 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:43:46 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:43:46 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:43:46 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:43:46 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:43:46 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:44:40 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:44:40 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:44:40 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:44:40 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:44:40 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:44:40 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:45:20 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:45:20 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:45:20 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:45:20 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:45:20 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:45:20 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:46:08 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:46:08 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:46:08 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:46:08 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:46:08 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:46:08 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:46:58 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:46:58 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:46:58 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:46:58 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:46:58 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:46:58 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:47:49 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:47:49 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:47:49 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:47:49 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:47:49 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:47:49 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:48:38 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:48:38 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:48:38 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:48:38 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:48:38 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:48:38 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:49:21 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:49:21 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:49:21 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:49:21 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:49:21 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:49:21 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:50:14 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:50:14 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:50:14 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:50:14 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:50:14 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:50:14 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:51:06 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:51:06 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:51:06 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:51:06 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:51:06 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:51:06 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:51:49 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:51:49 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:51:49 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:51:49 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:51:49 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:51:49 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:52:39 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:52:39 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:52:39 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:52:39 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:52:39 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:52:39 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:53:33 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:53:33 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:53:33 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:53:33 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:53:33 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:53:33 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug 22 19:54:22 speed-racer2 NetworkManager[791]: <info> (eth0): DHCPv4 state changed renew -> renew
Aug 22 19:54:22 speed-racer2 NetworkManager[791]: <info>   address 192.168.0.148
Aug 22 19:54:22 speed-racer2 NetworkManager[791]: <info>   prefix 24 (255.255.255.0)
Aug 22 19:54:22 speed-racer2 NetworkManager[791]: <info>   gateway 192.168.0.1
Aug 22 19:54:22 speed-racer2 NetworkManager[791]: <info>   hostname 'speed-racer2'
Aug 22 19:54:22 speed-racer2 NetworkManager[791]: <info>   nameserver '192.168.0.1'
Aug  30 20:15:07 speed-racer2 kernel: [   16.807391] type=1400  audit(1409447706.539:3): apparmor="STATUS" operation="profile_load"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371  comm="apparmor_parser"
Aug 30 20:15:07 speed-racer2 kernel: [    16.808258] type=1400 audit(1409447706.543:5): apparmor="STATUS"  operation="profile_replace" profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=371  comm="apparmor_parser"
Aug 30 20:15:08 speed-racer2 avahi-daemon[658]: Network interface enumeration completed.
Aug 30 20:15:09 speed-racer2 NetworkManager[714]: <info> NetworkManager (version 0.9.8.8) is starting...
Aug 30 20:15:09 speed-racer2 NetworkManager[714]: <info> Read config file /etc/NetworkManager/NetworkManager.conf
Aug 30 20:15:09 speed-racer2 NetworkManager[714]: <info> WEXT support is enabled
Aug 30 20:15:10 speed-racer2 NetworkManager[714]: <info> VPN: loaded org.freedesktop.NetworkManager.pptp
Aug 30 20:15:10 speed-racer2 NetworkManager[714]: <info> DNS: loaded plugin dnsmasq
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ifupdown: init!
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ifupdown: update_system_hostname
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:       interface-parser: parsing file /etc/network/interfaces
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:       interface-parser: finished parsing file /etc/network/interfaces
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    SCPluginIfupdown: management mode: unmanaged
Aug  30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ifupdown:  devices added (path:  /sys/devices/pci0000:00/0000:00:06.0/0000:0e:00.0/net/eth0, iface: eth0)
Aug  30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ifupdown:  device added (path:  /sys/devices/pci0000:00/0000:00:06.0/0000:0e:00.0/net/eth0, iface:  eth0): no ifupdown configuration found.
Aug 30 20:15:10 speed-racer2  NetworkManager[714]:    SCPlugin-Ifupdown: devices added (path:  /sys/devices/virtual/net/lo, iface: lo)
Aug 30 20:15:10 speed-racer2  NetworkManager[714]:    SCPlugin-Ifupdown: device added (path:  /sys/devices/virtual/net/lo, iface: lo): no ifupdown configuration  found.
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ifupdown: end _init.
Aug  30 20:15:10 speed-racer2 NetworkManager[714]: <info> Loaded  plugin ifupdown: (C) 2008 Canonical Ltd.  To report bugs please use the  NetworkManager mailing list.
Aug 30 20:15:10 speed-racer2  NetworkManager[714]: <info> Loaded plugin keyfile: (c) 2007 - 2010  Red Hat, Inc.  To report bugs please use the NetworkManager mailing  list.
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ofono: Acquired D-Bus service com.canonical.NMOfono
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ofono: init!
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ofono: end _init.
Aug 30 20:15:10 speed-racer2 NetworkManager[714]: <info> Loaded plugin (null): (null)
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    Ifupdown: get unmanaged devices count: 0
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ifupdown: (150103896) ... get_connections.
Aug  30 20:15:10 speed-racer2 NetworkManager[714]:    SCPlugin-Ifupdown:  (150103896) ... get_connections (managed=false): return empty list.
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    keyfile: parsing MU_Wireless ... 
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    keyfile:     read connection 'MU_Wireless'
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    keyfile: parsing Rolland 2 ... 
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    keyfile:     read connection 'Rolland 2'
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    keyfile: parsing Rolland 1 ... 
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    keyfile:     read connection 'Rolland 1'
Aug 30 20:15:10 speed-racer2 NetworkManager[714]:    keyfile: parsing Jacobi ... 
Aug 30 20:15:11 speed-racer2 NetworkManager[714]:    keyfile:     read connection 'Jacobi'
Aug 30 20:15:11 speed-racer2 NetworkManager[714]:    keyfile: parsing Rolland ... 
Aug 30 20:15:11 speed-racer2 NetworkManager[714]:    keyfile:     read connection 'Rolland'
Aug 30 20:15:11 speed-racer2 NetworkManager[714]:    SCPlugin-Ofono: (150146584) ... get_connections.
Aug 30 20:15:11 speed-racer2 NetworkManager[714]:    SCPlugin-Ofono: (150146584) connections count: 0
Aug 30 20:15:11 speed-racer2 NetworkManager[714]:    Ifupdown: get unmanaged devices count: 0
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> monitoring kernel firmware directory '/lib/firmware'.
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> WiFi enabled by radio killswitch; enabled by state file
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> WWAN enabled by radio killswitch; enabled by state file
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> WiMAX enabled by radio killswitch; enabled by state file
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> Networking is enabled by state file
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <warn> failed to allocate link cache: (-12) Object not found
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> (eth0): carrier is OFF
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> (eth0): new Ethernet device (driver: 'r8169' ifindex: 2)
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> (eth0): exported as /org/freedesktop/NetworkManager/Devices/0
Aug  30 20:15:11 speed-racer2 NetworkManager[714]: <info> (eth0):  device state change: unmanaged -> unavailable (reason 'managed') [10  20 2]
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> (eth0): bringing up device.
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> (eth0): preparing device.
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> (eth0): deactivating device (reason 'managed') [2]
Aug  30 20:15:11 speed-racer2 NetworkManager[714]: <info> Added  default wired connection 'Wired connection 1' for  /sys/devices/pci0000:00/0000:00:06.0/0000:0e:00.0/net/eth0
Aug 30  20:15:11 speed-racer2 NetworkManager[714]: <warn>  /sys/devices/virtual/net/lo: couldn't determine device driver;  ignoring...
Aug 30 20:15:11 speed-racer2 NetworkManager[714]:  <warn> /sys/devices/virtual/net/lo: couldn't determine device  driver; ignoring...
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> urfkill disappeared from the bus
Aug 30 20:15:11 speed-racer2 NetworkManager[714]: <info> ModemManager available in the bus
Aug  30 20:15:15 speed-racer2 kernel: [   25.461040] type=1400  audit(1409447715.195:15): apparmor="STATUS" operation="profile_replace"  profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=865  comm="apparmor_parser"
Aug 30 20:15:15 speed-racer2 kernel: [    25.461902] type=1400 audit(1409447715.195:17): apparmor="STATUS"  operation="profile_replace" profile="unconfined"  name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=865  comm="apparmor_parser"
Aug 30 20:15:21 speed-racer2 NetworkManager[714]: <info> WiFi hardware radio set enabled
Aug  30 20:16:55 speed-racer2 NetworkManager[714]: <warn> error  requesting auth for org.freedesktop.NetworkManager.wifi.share.open: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.enable-disable-network: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.sleep-wake: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.enable-disable-wifi: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.enable-disable-wwan: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.enable-disable-wimax: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.network-control: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.wifi.share.protected: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.wifi.share.open: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.settings.modify.system: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.settings.modify.own: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:16:55 speed-racer2  NetworkManager[714]: <warn> error requesting auth for  org.freedesktop.NetworkManager.settings.modify.hostname: (3)  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner:  GDBus.Error:org.freedesktop.DBus.Error.NameHasNoOwner: Could not get UID  of name ':1.21': no such name
Aug 30 20:18:07 speed-racer2  NetworkManager[714]: <info> rfkill0: found WiFi radio killswitch  (at  /sys/devices/pci0000:00/0000:00:13.5/usb1/1-2/1-2:1.0/ieee80211/phy0/rfkill0)  (driver rtl8187)
Aug 30 20:18:07 speed-racer2  NetworkManager[714]:    SCPlugin-Ifupdown: devices added (path:  /sys/devices/pci0000:00/0000:00:13.5/usb1/1-2/1-2:1.0/net/wlan1, iface:  wlan1)
Aug 30 20:18:07 speed-racer2 NetworkManager[714]:     SCPlugin-Ifupdown: device added (path:  /sys/devices/pci0000:00/0000:00:13.5/usb1/1-2/1-2:1.0/net/wlan1, iface:  wlan1): no ifupdown configuration found.
Aug 30 20:18:07 speed-racer2 NetworkManager[714]: <info> (wlan1): using nl80211 for WiFi device control
Aug 30 20:18:07 speed-racer2 NetworkManager[714]: <info> (wlan1): new 802.11 WiFi device (driver: 'rtl8187' ifindex: 3)
Aug 30 20:18:07 speed-racer2 NetworkManager[714]: <info> (wlan1): exported as /org/freedesktop/NetworkManager/Devices/1
Aug  30 20:18:07 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: unmanaged -> unavailable (reason 'managed') [10  20 2]
Aug 30 20:18:07 speed-racer2 NetworkManager[714]: <info> (wlan1): bringing up device.
Aug 30 20:18:09 speed-racer2 NetworkManager[714]: <info> (wlan1): preparing device.
Aug 30 20:18:09 speed-racer2 NetworkManager[714]: <info> (wlan1): deactivating device (reason 'managed') [2]
Aug 30 20:18:09 speed-racer2 kernel: [  200.005387] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Aug 30 20:18:09 speed-racer2 kernel: [  200.006146] IPv6: ADDRCONF(NETDEV_UP): wlan1: link is not ready
Aug 30 20:18:09 speed-racer2 NetworkManager[714]: <info> wpa_supplicant started
Aug 30 20:18:09 speed-racer2 NetworkManager[714]: <info> (wlan1) supports 4 scan SSIDs
Aug 30 20:18:09 speed-racer2 NetworkManager[714]: <warn> Trying to remove a non-existant call id.
Aug 30 20:18:09 speed-racer2 NetworkManager[714]: <info> (wlan1): supplicant interface state: starting -> ready
Aug  30 20:18:09 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: unavailable -> disconnected (reason  'supplicant-available') [20 30 42]
Aug 30 20:18:09 speed-racer2 NetworkManager[714]: <info> (wlan1): supplicant interface state: ready -> disconnected
Aug 30 20:18:09 speed-racer2 NetworkManager[714]: <info> (wlan1) supports 4 scan SSIDs
Aug 30 20:18:09 speed-racer2 wpa_supplicant[2435]: wlan1: CTRL-EVENT-SCAN-STARTED 
Aug 30 20:18:11 speed-racer2 NetworkManager[714]: <info> (wlan1): supplicant interface state: disconnected -> inactive
Aug 30 20:18:18 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) starting connection 'Rolland 3'
Aug  30 20:18:18 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: disconnected -> prepare (reason 'none') [30 40  0]
Aug 30 20:18:18 speed-racer2 NetworkManager[714]: <info> NetworkManager state is now CONNECTING
Aug 30 20:18:18 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 20:18:18 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Aug 30 20:18:18 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 20:18:18 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug 30 20:18:18 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug  30 20:18:18 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: prepare -> config (reason 'none') [40 50 0]
Aug  30 20:18:18 speed-racer2 NetworkManager[714]: <info> Activation  (wlan1/wireless): access point 'Rolland 3' has security, but secrets are  required.
Aug 30 20:18:18 speed-racer2 NetworkManager[714]:  <info> (wlan1): device state change: config -> need-auth  (reason 'none') [50 60 0]
Aug 30 20:18:18 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug  30 20:18:33 speed-racer2 NetworkManager[714]: get_secret_flags:  assertion 'is_secret_prop (setting, secret_name, error)' failed
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) started...
Aug  30 20:18:33 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: need-auth -> prepare (reason 'none') [60 40 0]
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 1 of 5 (Device Prepare) complete.
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) starting...
Aug  30 20:18:33 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: prepare -> config (reason 'none') [40 50 0]
Aug  30 20:18:33 speed-racer2 NetworkManager[714]: <info> Activation  (wlan1/wireless): connection 'Rolland 3' has security, and secrets  exist.  No new secrets needed.
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Config: added 'ssid' value 'Rolland'
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Config: added 'scan_ssid' value '1'
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Config: added 'auth_alg' value 'OPEN'
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Config: added 'psk' value '<omitted>'
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 2 of 5 (Device Configure) complete.
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> Config: set interface ap_scan to 1
Aug 30 20:18:33 speed-racer2 NetworkManager[714]: <info> (wlan1): supplicant interface state: inactive -> scanning
Aug 30 20:18:33 speed-racer2 wpa_supplicant[2435]: message repeated 2 times: [ wlan1: CTRL-EVENT-SCAN-STARTED ]
Aug  30 20:18:35 speed-racer2 wpa_supplicant[2435]: wlan1: SME: Trying to  authenticate with 84:1b:5e:86:aa:df (SSID='Rolland' freq=2462 MHz)
Aug 30 20:18:35 speed-racer2 kernel: [  225.372662] wlan1: authenticate with 84:1b:5e:86:aa:df
Aug  30 20:18:35 speed-racer2 NetworkManager[714]: <info> (wlan1):  supplicant interface state: scanning -> authenticating
Aug 30 20:18:35 speed-racer2 kernel: [  225.615273] wlan1: send auth to 84:1b:5e:86:aa:df (try 1/3)
Aug  30 20:18:35 speed-racer2 wpa_supplicant[2435]: wlan1: Trying to  associate with 84:1b:5e:86:aa:df (SSID='Rolland' freq=2462 MHz)
Aug 30 20:18:35 speed-racer2 kernel: [  225.621474] wlan1: authenticated
Aug 30 20:18:35 speed-racer2 kernel: [  225.624604] wlan1: associate with 84:1b:5e:86:aa:df (try 1/3)
Aug 30 20:18:35 speed-racer2 kernel: [  225.626938] wlan1: RX AssocResp from 84:1b:5e:86:aa:df (capab=0x431 status=0 aid=1)
Aug  30 20:18:35 speed-racer2 NetworkManager[714]: <info> (wlan1):  supplicant interface state: authenticating -> associating
Aug 30 20:18:35 speed-racer2 wpa_supplicant[2435]: wlan1: Associated with 84:1b:5e:86:aa:df
Aug 30 20:18:35 speed-racer2 kernel: [  225.628745] wlan1: associated
Aug 30 20:18:35 speed-racer2 kernel: [  225.628851] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
Aug 30 20:18:35 speed-racer2 NetworkManager[714]: <info> (wlan1): supplicant interface state: associating -> associated
Aug  30 20:18:35 speed-racer2 NetworkManager[714]: <info> (wlan1):  supplicant interface state: associated -> 4-way handshake
Aug 30  20:18:35 speed-racer2 wpa_supplicant[2435]: wlan1: WPA: Key negotiation  completed with 84:1b:5e:86:aa:df [PTK=CCMP GTK=CCMP]
Aug 30 20:18:35  speed-racer2 wpa_supplicant[2435]: wlan1: CTRL-EVENT-CONNECTED -  Connection to 84:1b:5e:86:aa:df completed [id=0 id_str=]
Aug 30  20:18:35 speed-racer2 NetworkManager[714]: <info> (wlan1):  supplicant interface state: 4-way handshake -> completed
Aug 30  20:18:35 speed-racer2 NetworkManager[714]: <info> Activation  (wlan1/wireless) Stage 2 of 5 (Device Configure) successful.  Connected  to wireless network 'Rolland'.
Aug 30 20:18:35 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) scheduled.
Aug 30 20:18:35 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) started...
Aug  30 20:18:35 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: config -> ip-config (reason 'none') [50 70 0]
Aug  30 20:18:35 speed-racer2 NetworkManager[714]: <info> Activation  (wlan1) Beginning DHCPv4 transaction (timeout in 45 seconds)
Aug 30 20:18:35 speed-racer2 NetworkManager[714]: <info> dhclient started with pid 2511
Aug 30 20:18:35 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Beginning IP6 addrconf.
Aug 30 20:18:35 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 3 of 5 (IP Configure Start) complete.
Aug 30 20:18:35 speed-racer2 NetworkManager[714]: <info> (wlan1): DHCPv4 state changed nbi -> preinit
Aug 30 20:18:35 speed-racer2 dhclient: Listening on LPF/wlan1/00:e0:4c:06:53:28
Aug 30 20:18:35 speed-racer2 dhclient: Sending on   LPF/wlan1/00:e0:4c:06:53:28
Aug 30 20:18:35 speed-racer2 dhclient: DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3 (xid=0x19162c0d)
Aug  30 20:18:37 speed-racer2 avahi-daemon[658]: Joining mDNS multicast  group on interface wlan1.IPv6 with address fe80::2e0:4cff:fe06:5328.
Aug 30 20:18:37 speed-racer2 avahi-daemon[658]: New relevant interface wlan1.IPv6 for mDNS.
Aug 30 20:18:37 speed-racer2 avahi-daemon[658]: Registering new address record for fe80::2e0:4cff:fe06:5328 on wlan1.*.
Aug 30 20:18:37 speed-racer2 dhclient: DHCPREQUEST of 192.168.1.3 on wlan1 to 255.255.255.255 port 67 (xid=0x19162c0d)
Aug 30 20:18:37 speed-racer2 NetworkManager[714]: <info> (wlan1): DHCPv4 state changed preinit -> bound
Aug 30 20:18:37 speed-racer2 NetworkManager[714]: <info>   address 192.168.1.3
Aug 30 20:18:37 speed-racer2 NetworkManager[714]: <info>   prefix 24 (255.255.255.0)
Aug 30 20:18:37 speed-racer2 NetworkManager[714]: <info>   gateway 192.168.1.1
Aug 30 20:18:37 speed-racer2 NetworkManager[714]: <info>   nameserver '192.168.1.1'
Aug  30 20:18:37 speed-racer2 NetworkManager[714]: <info> Activation  (wlan1) Stage 5 of 5 (IPv4 Configure Commit) scheduled...
Aug 30 20:18:37 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) started...
Aug 30 20:18:37 speed-racer2 avahi-daemon[658]: Joining mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.3.
Aug 30 20:18:37 speed-racer2 avahi-daemon[658]: New relevant interface wlan1.IPv4 for mDNS.
Aug 30 20:18:37 speed-racer2 avahi-daemon[658]: Registering new address record for 192.168.1.3 on wlan1.IPv4.
Aug  30 20:18:38 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: ip-config -> secondaries (reason 'none') [70 90  0]
Aug 30 20:18:38 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) Stage 5 of 5 (IPv4 Commit) complete.
Aug  30 20:18:38 speed-racer2 NetworkManager[714]: <info> (wlan1):  device state change: secondaries -> activated (reason 'none') [90 100  0]
Aug 30 20:18:38 speed-racer2 NetworkManager[714]: <info> NetworkManager state is now CONNECTED_GLOBAL
Aug  30 20:18:38 speed-racer2 NetworkManager[714]: <info> Policy set  'Rolland 3' (wlan1) as default for IPv4 routing and DNS.
Aug 30 20:18:38 speed-racer2 NetworkManager[714]: <info> DNS: starting dnsmasq...
Aug 30 20:18:38 speed-racer2 NetworkManager[714]: <warn> dnsmasq not available on the bus, can't update servers.
Aug  30 20:18:38 speed-racer2 NetworkManager[714]: <error>  [1409447918.591669] [nm-dns-dnsmasq.c:396] update(): dnsmasq owner not  found on bus: Could not get owner of name  'org.freedesktop.NetworkManager.dnsmasq': no such name
Aug 30 20:18:38 speed-racer2 NetworkManager[714]: <warn> DNS: plugin dnsmasq update failed
Aug 30 20:18:38 speed-racer2 NetworkManager[714]: <info> Writing DNS information to /sbin/resolvconf
Aug 30 20:18:39 speed-racer2 NetworkManager[714]: <info> Activation (wlan1) successful, device activated.
Aug 30 20:18:39 speed-racer2 NetworkManager[714]: <warn> dnsmasq appeared on DBus: :1.84
Aug 30 20:18:39 speed-racer2 NetworkManager[714]: <info> Writing DNS information to /sbin/resolvconf
Aug 30 20:18:53 speed-racer2 NetworkManager[714]: <info> (wlan1): IP6 addrconf timed out or failed.
Aug  30 20:18:53 speed-racer2 NetworkManager[714]: <info> Activation  (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) scheduled...
Aug 30  20:18:53 speed-racer2 NetworkManager[714]: <info> Activation  (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) started...
Aug 30  20:18:53 speed-racer2 NetworkManager[714]: <info> Activation  (wlan1) Stage 4 of 5 (IPv6 Configure Timeout) complete.
Aug 30 20:19:03 speed-racer2 wpa_supplicant[2435]: wlan1: CTRL-EVENT-SCAN-STARTED 
Aug 30 20:22:11 speed-racer2 kernel: [  443.940094] wlan1: deauthenticating from 84:1b:5e:86:aa:df by local choice (reason=3)
Aug 30 20:20:49 speed-racer2 wpa_supplicant[2435]: message repeated 2 times: [ wlan1: CTRL-EVENT-SCAN-STARTED ]
Aug  30 20:22:11 speed-racer2 wpa_supplicant[2435]: wlan1:  CTRL-EVENT-DISCONNECTED bssid=84:1b:5e:86:aa:df reason=3  locally_generated=1
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <warn> Connection disconnected (reason -3)
Aug 30 20:22:11 speed-racer2 avahi-daemon[658]: Interface wlan1.IPv6 no longer relevant for mDNS.
Aug  30 20:22:11 speed-racer2 avahi-daemon[658]: Leaving mDNS multicast  group on interface wlan1.IPv6 with address fe80::2e0:4cff:fe06:5328.
Aug 30 20:22:11 speed-racer2 dhclient: receive_packet failed on wlan1: Network is down
Aug 30 20:22:11 speed-racer2 avahi-daemon[658]: Interface wlan1.IPv4 no longer relevant for mDNS.
Aug 30 20:22:11 speed-racer2 avahi-daemon[658]: Leaving mDNS multicast group on interface wlan1.IPv4 with address 192.168.1.3.
Aug  30 20:22:11 speed-racer2 NetworkManager[714]:    SCPlugin-Ifupdown:  devices removed (path:  /sys/devices/pci0000:00/0000:00:13.5/usb1/1-2/1-2:1.0/net/wlan1, iface:  wlan1)
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <info>  (wlan1): device state change: activated -> unmanaged (reason  'removed') [100 10 36]
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <info> (wlan1): deactivating device (reason 'removed') [36]
Aug 30 20:22:11 speed-racer2 avahi-daemon[658]: Withdrawing address record for fe80::2e0:4cff:fe06:5328 on wlan1.
Aug 30 20:22:11 speed-racer2 avahi-daemon[658]: Withdrawing address record for 192.168.1.3 on wlan1.
Aug 30 20:22:11 speed-racer2 avahi-daemon[658]: Withdrawing workstation service for wlan1.
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <info> (wlan1): canceled DHCP transaction, DHCP client pid 2511
Aug  30 20:22:11 speed-racer2 NetworkManager[714]: <warn> sysctl:  failed to open '/proc/sys/net/ipv6/conf/wlan1/accept_ra': (2) No such  file or directory
Aug 30 20:22:11 speed-racer2 NetworkManager[714]:  <warn> sysctl: failed to open  '/proc/sys/net/ipv6/conf/wlan1/use_tempaddr': (2) No such file or  directory
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <warn> (3) failed to find interface name for index
Aug  30 20:22:11 speed-racer2 NetworkManager[714]:  (nm-system.c:766):nm_system_iface_get_flags: runtime check failed:  (iface != NULL)
Aug 30 20:22:11 speed-racer2 NetworkManager[714]:  <error> [1409448131.887184] [nm-system.c:768]  nm_system_iface_get_flags(): (unknown): failed to get interface link  object
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <warn> (3) failed to find interface name for index
Aug  30 20:22:11 speed-racer2 NetworkManager[714]:  (nm-system.c:766):nm_system_iface_get_flags: runtime check failed:  (iface != NULL)
Aug 30 20:22:11 speed-racer2 NetworkManager[714]:  <error> [1409448131.887335] [nm-system.c:768]  nm_system_iface_get_flags(): (unknown): failed to get interface link  object
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <info> (wlan1): bringing up device.
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <warn> (3) failed to find interface name for index
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: nm_system_iface_flush_routes: assertion 'iface != NULL' failed
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <warn> (3) failed to find interface name for index
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <warn> DNS: plugin dnsmasq update failed
Aug 30 20:22:11 speed-racer2 NetworkManager[714]: <info> Removing DNS information from /sbin/resolvconf
Aug 30 20:22:12 speed-racer2 NetworkManager[714]: <info> (wlan1): cleaning up...
Aug 30 20:22:12 speed-racer2 NetworkManager[714]: <warn> (3) failed to find interface name for index
Aug  30 20:22:12 speed-racer2 NetworkManager[714]:  (nm-system.c:766):nm_system_iface_get_flags: runtime check failed:  (iface != NULL)
Aug 30 20:22:12 speed-racer2 NetworkManager[714]:  <error> [1409448132.67667] [nm-system.c:768]  nm_system_iface_get_flags(): (unknown): failed to get interface link  object
Aug 30 20:22:12 speed-racer2 NetworkManager[714]: <info>  Unmanaged Device found; state CONNECTED forced. (see  http://bugs.launchpad.net/bugs/191889)
Aug 30 20:22:12 speed-racer2  NetworkManager[714]: <info> radio killswitch  /sys/devices/pci0000:00/0000:00:13.5/usb1/1-2/1-2:1.0/ieee80211/phy0/rfkill0  disappeared
Aug 30 20:22:31 speed-racer2 kernel: [  464.359401]  wlan0: ethernet device e4:f4:c6:3f:71:83 using NDIS driver: bcmwlhigh5,  version: 0x53cb40b, NDIS version: 0x501, vendor: 'NDIS Network Adapter',  0846:9020.F.conf
Aug 30 20:22:31 speed-racer2 kernel: [  464.364214]  wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2-PSK;  AES/CCMP with WPA, WPA2, WPA2-PSK
Aug 30 20:22:31 speed-racer2  NetworkManager[714]:    SCPlugin-Ifupdown: devices added (path:  /sys/devices/pci0000:00/0000:00:13.5/usb1/1-2/1-2:1.0/net/wlan0, iface:  wlan0)
Aug 30 20:22:31 speed-racer2 NetworkManager[714]:     SCPlugin-Ifupdown: device added (path:  /sys/devices/pci0000:00/0000:00:13.5/usb1/1-2/1-2:1.0/net/wlan0, iface:  wlan0): no ifupdown configuration found.
Aug 30 20:22:31 speed-racer2 NetworkManager[714]: <warn> failed to allocate link cache: (-12) Object not found
Aug 30 20:22:31 speed-racer2 NetworkManager[714]: <info> (wlan0): driver does not support SSID scans (scan_capa 0x00).
Aug 30 20:22:31 speed-racer2 NetworkManager[714]: <info> (wlan0): using WEXT for WiFi device control
Aug  30 20:22:31 speed-racer2 NetworkManager[714]: <info> (wlan0): new  802.11 WiFi device (driver: 'ndiswrapper' ifindex: 4)
Aug 30 20:22:31 speed-racer2 NetworkManager[714]: <info> (wlan0): exported as /org/freedesktop/NetworkManager/Devices/2
Aug  30 20:22:31 speed-racer2 NetworkManager[714]: <info> (wlan0):  device state change: unmanaged -> unavailable (reason 'managed') [10  20 2]
Aug 30 20:22:31 speed-racer2 NetworkManager[714]: <info> (wlan0): bringing up device.
Aug 30 20:22:32 speed-racer2 NetworkManager[714]: <info> (wlan0): preparing device.
Aug 30 20:22:32 speed-racer2 NetworkManager[714]: <info> (wlan0): deactivating device (reason 'managed') [2]
Aug 30 20:22:32 speed-racer2 kernel: [  464.457111] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 30 20:22:32 speed-racer2 kernel: [  464.458615] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
Aug 30 20:22:32 speed-racer2 NetworkManager[714]: <info> NetworkManager state is now DISCONNECTED
Aug 30 20:22:32 speed-racer2 NetworkManager[714]: <info> (wlan0) supports 1 scan SSIDs
Aug 30 20:22:32 speed-racer2 NetworkManager[714]: <info> (wlan0): supplicant interface state: starting -> ready
Aug  30 20:22:32 speed-racer2 NetworkManager[714]: <info> (wlan0):  device state change: unavailable -> disconnected (reason  'supplicant-available') [20 30 42]
Aug 30 20:22:32 speed-racer2 NetworkManager[714]: <warn> Trying to remove a non-existant call id.
Aug 30 20:22:32 speed-racer2 NetworkManager[714]: <info> (wlan0): supplicant interface state: ready -> disconnected
Aug 30 20:22:32 speed-racer2 NetworkManager[714]: <info> (wlan0) supports 1 scan SSIDs
Aug 30 20:22:42 speed-racer2 NetworkManager[714]: <info> (wlan0): supplicant interface state: disconnected -> inactive
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Activation (wlan0) starting connection 'Rolland'
Aug  30 20:22:56 speed-racer2 NetworkManager[714]: <info> (wlan0):  device state change: disconnected -> prepare (reason 'none') [30 40  0]
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> NetworkManager state is now CONNECTING
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Aug  30 20:22:56 speed-racer2 NetworkManager[714]: <info> (wlan0):  device state change: prepare -> config (reason 'none') [40 50 0]
Aug  30 20:22:56 speed-racer2 NetworkManager[714]: <info> Activation  (wlan0/wireless): connection 'Rolland' has security, and secrets exist.   No new secrets needed.
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Config: added 'ssid' value 'Rolland'
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Config: added 'scan_ssid' value '1'
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Config: added 'auth_alg' value 'OPEN'
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Config: added 'psk' value '<omitted>'
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Aug 30 20:22:56 speed-racer2 NetworkManager[714]: <info> Config: set interface ap_scan to 1

NetworkManager Tool

State: connecting

- Device: wlan0  [Rolland] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ndiswrapper
  State:             connecting (configuring)
  Default:           no
  HW Address:        E4:F4:C6:3F:71:83

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    wisdomnetwork:   Infra, 9C:AD:97:8B:7F:20, Freq 2412 MHz, Rate 54 Mb/s, Strength 57 WPA2
    Jacobi:          Infra, 20:4E:7F:3B:32:59, Freq 2417 MHz, Rate 54 Mb/s, Strength 50 WPA2
    NETGEAR69:       Infra, E4:F4:C6:D4:24:72, Freq 2437 MHz, Rate 54 Mb/s, Strength 45 WPA2
    Mary Guest Network: Infra, 96:27:E4:5E:06:2D, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2
    TootsWiFi:       Infra, 00:1A:C4:68:CC:09, Freq 2452 MHz, Rate 54 Mb/s, Strength 24 WPA
    mardic:          Infra, 90:27:E4:5E:06:2D, Freq 2452 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    T. Ritter:       Infra, A4:17:31:3F:67:17, Freq 2437 MHz, Rate 54 Mb/s, Strength 29 WPA2
    julie:           Infra, 00:1C:10:B5:CA:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WEP
    Rolland:         Infra, 84:1B:5E:86:AA:DF, Freq 2462 MHz, Rate 54 Mb/s, Strength 95 WPA2
    samcross85:      Infra, 90:48:9A:35:8E:97, Freq 2462 MHz, Rate 54 Mb/s, Strength 32 WPA2


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:1B:38:11:0A:B0

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

```

(Hope I needn't have redacted that more.)

Thanks again for all your assistance up to this point, and for any you can provide in the future.

---

