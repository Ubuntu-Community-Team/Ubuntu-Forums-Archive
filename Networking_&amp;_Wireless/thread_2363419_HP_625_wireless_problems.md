---
title: "HP 625 wireless problems"
date: 2017-06-09
forum: Networking &amp; Wireless
---

### Post by hardcoretexan on 2017-06-09
I received an old HP-625 laptop and I had to replace the hard drive(brand new), I installed Ubuntu 16.04 lts on it, no other os and the wireless light is orange and not connecting. I have looked on the net and found a few fixes but not for this os version.
Also the processor is an athlon AMD (TM)II p340 dual core processor x2, I have another laptop with linux lite installed on it so I am somewhat familiar with its OS but this is my first time dealing with Ubuntu. 

Thanksin advance for any help

---

### Post by wildmanne39 on 2017-06-09
*Thread moved to **Networking & Wireless**.*

Please click on the wireless script in my signature and follow the directions to run it and paste the output to pastebin, then the link back here.

---

### Post by hardcoretexan on 2017-06-10
I tried to install pastebinet but could not. This is what I got.
"reading package list...done
Building dependancy tree
Reading state information... Done
E: Unable to locate package pastebinet"

System is fully updated

---

### Post by wildmanne39 on 2017-06-10
You have a typo it should be pastebinit, just copy and past the commands for accuracy.

Thanks

---

### Post by hardcoretexan on 2017-06-10
Don't know how to use pastebin, it did download but if I right click on file no option for pastebin. Here is the file.

```
########## wireless info START ##########

Report from: 10 Jun 2017 15:19 CDT -0500

Booted last: 10 Jun 2017 00:00 CDT -0500

Script from: 25 Mar 2017 07:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.2 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.8.0-54-generic #57~16.04.1-Ubuntu SMP Wed May 24 16:22:28 UTC 2017 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller [103c:1475]
    Kernel driver in use: r8169

06:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
    DeviceName: WLAN
    Subsystem: Hewlett-Packard Company BCM4313 802.11bgn Wireless Network Adapter [103c:145c]

##### lsusb #############################

Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05c8:0403 Cheng Uei Precision Industry Co., Ltd (Foxlink) Webcam
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes

##### lsmod #############################

wl                   6447104  0
cfg80211              581632  1 wl
hp_wmi                 16384  0
sparse_keymap          16384  1 hp_wmi
wmi                    16384  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp2s0    Link encap:Ethernet  HWaddr <MAC 'enp2s0' [IF1]>  
          inet addr:192.168.254.16  Bcast:192.168.254.255  Mask:255.255.255.0
          inet6 addr: fe80::7e3d:51b8:a9ff:19a8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:52620 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36137 errors:2 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:58376069 (58.3 MB)  TX bytes:3451964 (3.4 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:93722 errors:0 dropped:0 overruns:0 frame:0
          TX packets:93722 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:7119448 (7.1 MB)  TX bytes:7119448 (7.1 MB)

wlo1      Link encap:Ethernet  HWaddr <MAC 'wlo1' [IF2]>  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:17 

##### iwconfig ##########################

enp2s0    no wireless extensions.

lo        no wireless extensions.

wlo1      IEEE 802.11  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.254.254 0.0.0.0         UG    100    0        0 enp2s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 enp2s0
192.168.254.0   0.0.0.0         255.255.255.0   U     100    0        0 enp2s0

##### resolv.conf #######################

nameserver 127.0.1.1
search Home

##### network managers ##################

Installed:

    NetworkManager

Running:

root       774     1  0 Jun09 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         enp2s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp2s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:04.0/0000:02:00.0/net/enp2s0
GENERAL.IP-IFACE:                       enp2s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Wired connection 1
GENERAL.CON-UUID:                       47663741-c3c9-3751-995d-57fafd893556
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/12
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     100 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               on
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   47663741-c3c9-3751-995d-57fafd893556 | Wired connection 1
IP4.ADDRESS[1]:                         192.168.254.16/24
IP4.GATEWAY:                            192.168.254.254
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.254.254
IP4.DOMAIN[1]:                          Home
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 0.0.0.0
DHCP4.OPTION[10]:                       expiry = 1733051780
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.254.254
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.254.16
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Home
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.254.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 235926000
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.254.254
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.254.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.254.254
IP6.ADDRESS[1]:                         fe80::7e3d:51b8:a9ff:19a8/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         wlo1
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4313 802.11bgn Wireless Network Adapter
GENERAL.DRIVER:                         wl
GENERAL.DRIVER-VERSION:                 6.30.223.271 (r587334)
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'wlo1' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:09.0/0000:06:00.0/net/wlo1
GENERAL.IP-IFACE:                       
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID  BSSID  MODE  CHAN  FREQ  RATE  SIGNAL  BARS  SECURITY  ACTIVE  * 

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/Home]] (600 root)
[connection] id=Home | type=wifi | permissions=
[wifi] mac-address-blacklist= | ssid=WIN_eo1b
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: America/Chicago (based on set time zone)

country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 40), (N/A, 20), (N/A), NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

enp2s0    no frequency information.

lo        no frequency information.

wlo1      32 channels in total; available frequencies :
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

##### iwlist scan #######################

enp2s0    Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlo1      Interface doesn't support scanning : Network is down

##### module infos ######################

[wl]
filename:       /lib/modules/4.8.0-54-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     0ADAE750C888A523D63D8B5
depends:        cfg80211
vermagic:       4.8.0-54-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.8.0-54-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     46F63B461AA5E38D042F531
depends:        
intree:         Y
vermagic:       4.8.0-54-generic SMP mod_unload modversions 
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

##### dmesg #############################

[ 7236.909787] ERROR @wl_wowl_ind_wake_reason : Unable to get wake reason, err = -95
[ 7236.935674] r8169 0000:02:00.0 enp2s0: link down
[ 7238.650429] r8169 0000:02:00.0 enp2s0: link up
[ 7245.006697] IPv6: ADDRCONF(NETDEV_UP): wlo1: link is not ready
[ 7245.008336] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 7245.022992] r8169 0000:02:00.0 enp2s0: link down
[ 7245.023076] IPv6: ADDRCONF(NETDEV_UP): enp2s0: link is not ready
[ 7245.025719] r8169 0000:02:00.0 enp2s0: link down
[ 7246.650793] r8169 0000:02:00.0 enp2s0: link up
[ 7246.650810] IPv6: ADDRCONF(NETDEV_CHANGE): enp2s0: link becomes ready
[ 7298.151138] r8169 0000:02:00.0 enp2s0: link down
[ 7299.874860] r8169 0000:02:00.0 enp2s0: link up
[ 7390.090566] r8169 0000:02:00.0 enp2s0: link down
[ 7401.759248] r8169 0000:02:00.0 enp2s0: link up
[ 7402.166342] r8169 0000:02:00.0 enp2s0: link down
[ 7403.772401] r8169 0000:02:00.0 enp2s0: link up
[ 7447.046911] r8169 0000:02:00.0 enp2s0: link down
[ 7448.649329] r8169 0000:02:00.0 enp2s0: link up
[ 7458.574588] r8169 0000:02:00.0 enp2s0: link down
[ 7460.214293] r8169 0000:02:00.0 enp2s0: link up
[ 7504.298057] r8169 0000:02:00.0 enp2s0: link down
[ 7505.930634] r8169 0000:02:00.0 enp2s0: link up
[ 7695.998366] r8169 0000:02:00.0 enp2s0: link down
[ 7697.600793] r8169 0000:02:00.0 enp2s0: link up
[ 8080.051343] r8169 0000:02:00.0 enp2s0: link down
[ 8345.095817] r8169 0000:02:00.0 enp2s0: link up
[ 8349.924069] r8169 0000:02:00.0 enp2s0: link down
[73287.607627] r8169 0000:02:00.0 enp2s0: link up
[73513.859053] r8169 0000:02:00.0 enp2s0: link down
[73515.619584] r8169 0000:02:00.0 enp2s0: link up
[73546.427343] r8169 0000:02:00.0 enp2s0: link down
[73548.366193] r8169 0000:02:00.0 enp2s0: link up
[73548.870810] r8169 0000:02:00.0 enp2s0: link down
[73550.493459] r8169 0000:02:00.0 enp2s0: link up
[73550.575761] r8169 0000:02:00.0 enp2s0: link down
[73552.150368] r8169 0000:02:00.0 enp2s0: link up
[73574.591119] r8169 0000:02:00.0 enp2s0: link down
[73576.234792] r8169 0000:02:00.0 enp2s0: link up
[73671.767231] r8169 0000:02:00.0 enp2s0: link down
[73680.552819] r8169 0000:02:00.0 enp2s0: link up
[74866.116786] r8169 0000:02:00.0 enp2s0: link down
[75035.676285] r8169 0000:02:00.0 enp2s0: link up
[75045.571348] r8169 0000:02:00.0 enp2s0: link down
[75057.894621] r8169 0000:02:00.0 enp2s0: link up
[75227.869093] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############
```

---

### Post by wildmanne39 on 2017-06-10
When you ran the script it uploaded the file to pastebin, then created a link in the terminal, then you just paste that link here for us to click on.

Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

Give us a few minutes to look over the information in the file.

Thanks

---

### Post by wildmanne39 on 2017-06-10
Please do:
```
sudo apt purge bcmwl-kernel-source
```
Then:
```
sudo -i
echo "blacklist b43" >>  /etc/modprobe.d/blacklist.conf
echo "blacklist ssb" >>  /etc/modprobe.d/blacklist.conf
exit
```
Reboot and you wifi should come on if it does not turn your wifi on using the physical switch or button that turns it on but only do this if it does not come on when you reboot.

If you have any questions please ask.

---

### Post by hardcoretexan on 2017-06-10
Still does not work.

---

### Post by wildmanne39 on 2017-06-10
Run the wireless script again please and post the file so we can see if the changes stuck.

Thanks

---

### Post by hardcoretexan on 2017-06-10
[http://paste.ubuntu.com/24828628/](http://paste.ubuntu.com/24828628/)

---

### Post by Hadaka on 2017-06-10
Hi, your wireless report indicates you have a hard block..
```
0: hp-wifi: Wireless LAN
Soft blocked: no
Hard blocked: yes
```
The wifi button is located fourth from the right (delete key) on the top row of the keyboard
Please press that ONE time
then open a terminal ctrl...alt..t and copy and paste one line at a time...
```
sudo sed -i 's/3/2/' /etc/NetworkManager/conf.d/*
sudo modprobe -rf brcmsmac
sudo modprobe -v brcmsmac
```
disconnect any wired connection and any usb, boot and test wireless
thanks,

---

### Post by hardcoretexan on 2017-06-11
I really appreciate everything your doing but it's still not working.
[http://paste.ubuntu.com/24832922/](http://paste.ubuntu.com/24832922/)

---

### Post by wildmanne39 on 2017-06-11
It is still hard blocked, did you do what I said and turn the wifi on with the switch or button?

---

### Post by hardcoretexan on 2017-06-11
I did it just like you said, rebooted and pushed the button, nothing, then I even tried to turn it on via the connection icon at the top of the page.

---

### Post by wildmanne39 on 2017-06-11
Now that we have the right driver please do:
```
sudo modprobe -r hp-wireless
```
is it working now? if not do:
```
sudo modprobe hp-wmi
```
is the wifi button working now?

You can check with:
```
rfkill list all shows
```
Thanks

---

### Post by hardcoretexan on 2017-06-11
nope, tried them both, first one, no, second one no,
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

Is there a shortcut to reboot?

---

### Post by wildmanne39 on 2017-06-11
You can type:
```
sudo reboot
```
Go into your bios and see if the wifi is enabled, make sure it is enabled in windows if you have windows installed, if it is of in windows it will be off in ubuntu with no way to turn it on.

If you have a normal bios reset it and see if that helps.
Thanks

---

### Post by hardcoretexan on 2017-06-11
Low and behold it worked, this was a factory new HD with ubuntu being  the only os installed. There was n o wifi settings other than the  keyboard light which was already on, but after the reset of the bios   the wifi is working now.
Thankyou so much.

Greg

---

### Post by hardcoretexan on 2017-06-11
Also now  *have my 10 post *_****_and can edit my profile, many thanks, I really like the OS, a little different from Linux lite but I am determined to learn more. I started out with windows 5 then then made it to XP but never went any further, I tried some of the other upgrades but stayed with XP long after the updates stopped. Just never liked windows after XP

---

### Post by wildmanne39 on 2017-06-11
I am glad it is working, your welcome and enjoy!:)

---

