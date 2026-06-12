---
title: "Ubuntu 14.04; bcm4352 wlan unstable: intermittently disconnects"
date: 2015-06-18
forum: Networking &amp; Wireless
---

### Post by Bob_Briscoe on 2015-06-18
I recently installed Ubuntu 14.04 on a new Lenovo Yoga 3 Pro with a Broadcom BCM4352 wlan adapter. I used to be a Unix sysadmin, but in the intervening 20yrs windows has prob fried my brain. So Ubuntu package mgmt is new to me, but otherwise I'm not really a newbie.

I've been trying to fix unstable WiFi connectivity all week, researching the numerous threads. However, I believe I have correctly followed the [guidelines for installing Broadcom drivers]("http://ubuntuforums.org/showthread.php?t=2214110") (altho I discovered them after the fact). So, in desperation, I'm resorting to a forum post.

Here's two thumbnail plots of pings at 5s and  60s intervals respectively, with an otherwise quiet radio environment. Click on them to see periods of "Destination Unreachable"  (not just timed out) lasting tens of minutes for just over half the time.

[ATTACH=CONFIG]262679[/ATTACH]
[ATTACH=CONFIG]262680[/ATTACH]

Other  machines can successfully use the same wifi with no problems during the periods when the Broadcom driver fails to transmit. And to prove it's not  the hardware or the access point, here's pings at 60s intervals from the  same machine booted into Win8.1 (also note that when Linux is  'working', there are more unusually delayed pings than with Windows).

[ATTACH=CONFIG]262681[/ATTACH]

Workround: disconnect/reconnect from the access point whenever connectivity stalls, but that's not tenable long-term.

I have ruled out channel switching or security problems, because I'm 300m  from the next nearest house, so I've turned off WiFi authentication and there's no reason why there would be any switching between access points or between channels.

Here's the output from wireless-info:
```


########## wireless info START ##########

Report from: 18 Jun 2015 12:49 BST +0100

Booted last: 18 Jun 2015 11:10 BST +0100

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-41-generic #55~14.04.1-Ubuntu SMP Sun Jun 14 18:43:36 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Lenovo Device [17aa:0623]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 004: ID 1bcf:2c43 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 002: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no

##### lsmod #############################

wl                   6367833  0 
cfg80211              494362  1 wl
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9248:9aff:fefb:25cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:7464 errors:0 dropped:0 overruns:0 frame:1833
          TX packets:8980 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3759461 (3.7 MB)  TX bytes:1173314 (1.1 MB)
          Interrupt:18 

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Home-Farm"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'Home-Farm' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       789     1  0 11:10 ?        00:00:00 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Home-Farm] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           144 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Home-Farm:      Infra, <MAC 'Home-Farm' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39

  IPv4 Settings:
    Address:         192.168.1.5
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

no-auto-default=<MAC address>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/USR9108]] (600 root)
[connection] id=USR9108 | type=802-11-wireless
[802-11-wireless] ssid=USR9108 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Home-Farm]] (600 root)
[connection] id=Home-Farm | type=802-11-wireless
[802-11-wireless] ssid=Home-Farm | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

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
          Channel 54 : 5.27 GHz
          Channel 56 : 5.28 GHz
          Channel 58 : 5.29 GHz
          Channel 60 : 5.3 GHz
          Channel 62 : 5.31 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 102 : 5.51 GHz
          Channel 104 : 5.52 GHz
          Channel 106 : 5.53 GHz
          Channel 108 : 5.54 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Home-Farm' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Home-Farm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-41-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     DF2576C38AD45205B3556DD
depends:        cfg80211
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        42:AE:B7:DF:54:E6:D9:1C:A0:F4:01:21:E2:2F:EA:E6:B2:30:88:16
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
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[    2.393027] bluetooth hci0: Direct firmware load failed with error -2
[    2.396088] Bluetooth: hci0: BCM: patch brcm/BCM20702A0-0489-e07a.hcd not found
[ 5921.193960] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

I've also included the output of dmesg below, because the wireless-info script doesn't reveal the transmit power error:
```

$ dmesg -T | grep wl
[Thu Jun 18 11:10:53 2015] wl: module license 'MIXED/Proprietary' taints kernel.
[Thu Jun 18 11:10:53 2015] wl: module verification failed: signature and/or  required key missing - tainting kernel
[Thu Jun 18 11:10:54 2015] wlan0: Broadcom BCM43b1 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[Thu Jun 18 12:49:33 2015] ERROR @wl_dev_intvar_get : error (-1)
[Thu Jun 18 12:49:33 2015] ERROR @wl_cfg80211_get_tx_power : error (-1)

```

---

### Post by Bob_Briscoe on 2015-06-19
Follow up (and bump): I tried removing the ideapad_laptop module with
```

sudo modprobe -r ideapad_laptop 

```

but no improvement. At first, I thought it had fixed it, but as you see from the graph of pings below, just less than an hour afterwards it started to disconnect intermittently again.

[ATTACH=CONFIG]262700[/ATTACH]

I can find no other indicators that the WiFi is failing to transmit or receive, except... it just doesn't. E.g. 
[FONT=courier new]route[/FONT] and [FONT=courier new]netstat -r[/FONT] both look no different whether the wifi is working or not.
[FONT=courier new]iwconfig wlan0[/FONT] and [FONT=courier new]ifconfig wlan0[/FONT] outputs are no different.

I'm baffled.

---

### Post by him610 on 2015-06-19
Hello Baffled,

It appears to me you have driver problems. Recommend you refer to Chilli555's Broadcom HowTo post.
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

Remove all red flagged items before launch.

---

### Post by him610 on 2015-06-20
Baffled,

After giving your problem some thought overnight, I don't believe you have driver problems. I think you have poor reception. From the results of both, 'ifconfig' and 'iwconfig', it can be seen your machine is getting it's ip assignment from your router which leads me to believe there is degradation of the wifi signal.

What is the distance between your wireless router/AP and your Yoga3Pro? Are there any intervening walls, appliances, air conditioning ductwork, microwave ovens, or such?

I looked up the specs on Lenovo Yoga 3 Pro - impressive. Maybe we can figure this out between the two of us.

---

### Post by Bob_Briscoe on 2015-06-20
I had already followed Chilli555's Broadcom post (I linked to it in my  first posting). Like you, I don't think this is a driver problem. But  I'm pretty sure it's not a signal strength issue either - everything so  far (and everything below) has happened with the laptop(s) about 5m from  the access point.

Anyway, I'm now much-less-baffled. And I guess I could say I have 'fixed' *my* problem.

However, I'm still trying to establish whether I might have got us  closer to the cause of many other intermittent connectivity problems  that I've seen in a number of posts that ended leaving the OP in  mid-air. I suspect that the Linux on my Yoga 3 Pro is (sometimes?) not  sending out its ARP requests and responses at a slow enough rate when  the peer device only supports a slower variant of 802.11. I would  appreciate help determining whether Ubuntu is part of the problem, and  if so what needs fixing.

I've been tracking down the problem with: another older access point; an  old WinXP laptop; and wireshark on my Ubuntu 14.04 Yoga 3 Pro and  on  the WinXP laptop. As keeping track of all the different devices will get  complex, I will start with the cast list in order of appearance:

[TABLE="width: 1000, align: center"]
[TR]
[TD]Ra[/TD]
[TD]Lenovo Yoga 3 Pro[/TD]
[TD]Ubuntu 14.04 LTS 802.11a/b/g/n/ac[/TD]
[TD]new laptop[/TD]
[/TR]
[TR]
[TD]Sage[/TD]
[TD]SagemCom 2704n[/TD]
[TD]802.11b/g/n[/TD]
[TD]new access point / home router recently supplied by my new broadband provider[/TD]
[/TR]
[TR]
[TD]Robotics[/TD]
[TD]US Robotics 9108 MaxG[/TD]
[TD]802.11a/b/g[/TD]
[TD]old access point /  home router[/TD]
[/TR]
[TR]
[TD]Mut[/TD]
[TD]Toshiba Portege R100[/TD]
[TD]WinXP 802.11a/b[/TD]
[TD]old laptop[/TD]
[/TR]
[TR]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[TD][/TD]
[/TR]
[TR]
[TD]extras[/TD]
[TD][/TD]
[TD][/TD]
[TD]non-speaking parts[/TD]
[/TR]
[/TABLE]

My posts so far have been about Ra connecting to Sage. Recall that I had  tested 4 other devices with Sage as the access point, and they all  worked fine - without disconnections. That obviously made me suspect the  newly installed Ubuntu machine (Ra).

[B]#1/ Black-holed pings
[/B]
First, does anyone know what could cause pings to black-hole without a    timeout error? As in the output sample below, seqnos 16-24 just  disappear. 

```
Tue 16 Jun 2015 22:01:27 BST  64 bytes from 192.168.1.254: icmp_seq=1 ttl=64 time=2.57 ms 
Tue 16 Jun 2015 22:01:32 BST  64 bytes from 192.168.1.254: icmp_seq=2 ttl=64 time=2.37 ms 
Tue 16 Jun 2015 22:01:37 BST  64 bytes from 192.168.1.254: icmp_seq=3 ttl=64 time=2.42 ms 
Tue 16 Jun 2015 22:01:42 BST  64 bytes from 192.168.1.254: icmp_seq=4 ttl=64 time=1.83 ms 
Tue 16 Jun 2015 22:01:47 BST  64 bytes from 192.168.1.254: icmp_seq=5 ttl=64 time=3.22 ms 
Tue 16 Jun 2015 22:01:52 BST  64 bytes from 192.168.1.254: icmp_seq=6 ttl=64 time=2.51 ms 
Tue 16 Jun 2015 22:01:57 BST  64 bytes from 192.168.1.254: icmp_seq=7 ttl=64 time=5.35 ms 
Tue 16 Jun 2015 22:02:02 BST  64 bytes from 192.168.1.254: icmp_seq=8 ttl=64 time=2.59 ms 
Tue 16 Jun 2015 22:02:07 BST  64 bytes from 192.168.1.254: icmp_seq=9 ttl=64 time=3.26 ms 
Tue 16 Jun 2015 22:02:12 BST  64 bytes from 192.168.1.254: icmp_seq=10 ttl=64 time=2.00 ms 
Tue 16 Jun 2015 22:02:17 BST  64 bytes from 192.168.1.254: icmp_seq=11 ttl=64 time=2.27 ms 
Tue 16 Jun 2015 22:02:22 BST  64 bytes from 192.168.1.254: icmp_seq=12 ttl=64 time=1.61 ms 
Tue 16 Jun 2015 22:02:27 BST  64 bytes from 192.168.1.254: icmp_seq=13 ttl=64 time=1.83 ms 
Tue 16 Jun 2015 22:02:32 BST  64 bytes from 192.168.1.254: icmp_seq=14 ttl=64 time=1.65 ms 
Tue 16 Jun 2015 22:02:37 BST  64 bytes from 192.168.1.254: icmp_seq=15 ttl=64 time=2.47 ms 
Tue 16 Jun 2015 22:03:30 BST  From 192.168.1.254 icmp_seq=25 Destination Host Unreachable 
Tue 16 Jun 2015 22:03:35 BST  From 192.168.1.254 icmp_seq=26 Destination Host Unreachable 
Tue 16 Jun 2015 22:03:40 BST  From 192.168.1.254 icmp_seq=27 Destination Host Unreachable 
Tue 16 Jun 2015 22:03:45 BST  From 192.168.1.254 icmp_seq=28 Destination Host Unreachable 
Tue 16 Jun 2015 22:03:50 BST  From 192.168.1.254 icmp_seq=29 Destination Host Unreachable 
Tue 16 Jun 2015 22:03:55 BST  From 192.168.1.254 icmp_seq=30 Destination Host Unreachable 
Tue 16 Jun 2015 22:04:00 BST  From 192.168.1.254 icmp_seq=31 Destination Host Unreachable 
Tue 16 Jun 2015 22:04:05 BST  From 192.168.1.254 icmp_seq=32 Destination Host Unreachable 
Tue 16 Jun 2015 22:04:10 BST  From 192.168.1.254 icmp_seq=33 Destination Host Unreachable 
Tue 16 Jun 2015 22:04:15 BST  From 192.168.1.254 icmp_seq=34 Destination Host Unreachable 
Tue 16 Jun 2015 22:04:20 BST  From 192.168.1.254 icmp_seq=35 Destination Host Unreachable 

```

Note that the output says these DHU messages come from the access point  (192.168.1.254). Whereas, later, I noticed I it started reporting DHU  from my local IP (192.168.1.5). By the time I had got wireshark on it, I  found the DHU errors were not triggered by an actual ICMP response  packet with  the dest. unreachable code. But I haven't yet managed to  reproduce DHU errors reported as coming from the access point, like  those above from last Tuesday. So I have not been able to check these  with wireshark.

**Expt #2/ Still between Ra and Sage.**

I used wireshark to watch packets leaving and arriving at Ra,  particularly around the start and end of each period of disconnection.  To take an example (17:48:11 19-Jun-2015) I could see Ra sending 8 Echo  Requests (pings) at 5s intervals but no Echo Responses. Ra happened to  be trying to open a TCP connection to the router (Sage) at the same time  (I had been looking at the router's Web interface). Ra retransmitted  the initial TCP segment (SYN) 8 times before giving up, because no  SYN/ACKs were coming back the other way. After eight black-holed pings,  Ra sent 1 ARP request per second for 3s direct to Sage's MAC, asking  "Who has 192.168.1.254?". Given this was Sage's IP address, it was  sending to the MAC it was asking for, so I assume it was checking  whether something had changed. Then Ra It stopped sending ping requests  and started sending 1 ARP request per second to the broadcast MAC, which  implies Ra believed its ARP entry for the access point was stale. For  about 3 minutes no ARP response (or anything) was sent to Ra. Then, as  soon as an ARP response finally appeared from Sage, Ra restarted sending  echo requests and also opened four TCP connections, which all get  responded to properly and it all sorted itself out (until the next  time).

I am keeping an open mind as to whether the lack of responses from Sage  was Sage's fault, or whether Ra switched into sending everything to Sage  (including ARP requests) at 802.11ac symbol rate, which Sage wouldn't  undersdtand. During the whole outage, Sage was correctly interacting  with all the other machines on the subnet - proved by all their packets  in the capture (that Ra could see, because it was in promiscuous mode on  the wlan and it supports a wider range of rates than all the other  machines).  

Unfortunately, I don't have access to Sage, other than through the  rudimentary Web GUI. So I can't see whether it sees frames arriving when  Ra sends them (it has a received-bytes counter, but it's rounded to the  nearest MB).

[B] Expt #3/ Replaced new access router (Sage) with my old one (Robotics)
[/B]
I replaced Sage with Robotics, which I hooked up to my broadband  provider. I ran the same ping test at 5s intervals for 3hrs from Ra to  Robotics. There were no periods of "destination unreachable" errors:
[ATTACH=CONFIG]262754[/ATTACH]



However, I noticed one episode where echo requests from Ra were being  black-holed without timeouts and without dest. unreachable errors, which  I think shows that Ubuntu is not completely blameless. Over a period of  40s starting 21:31:28 on 19-Jun-2015 (bang in the middle of the plot  above), TCP on Ra retransmitted one segment (to a remote machine on the  Internet) 8 times. And over the same period 8 ICMP echo requests from  the Ubuntu laptop (ICMP sequence nos. 1384-1391) received no response,  but there were no ping timeouts. Unlike with Sage, this episode ended  when ping request seq 1392 received a response from the Robotics access  point. 6us after wireshark saw this response, it saw the Ubuntu laptop  send out an ARP request to the access point's MAC asking "Who has  192.168.0.1?" and the access point replied with its own MAC address.  Here's a screenshot from wireshark, filtered to display onlly ARP and  ICMP:
[ATTACH=CONFIG]262755[/ATTACH]

My guess is that this string of packets from the Ubuntu machine to  Robotics is exactly the same symptom as the packets that caused its  connection with the Sagemcom access point to black-hole, but some  difference in the Robotics response at the link layer gets the Ubuntu  machine back on track. I believe that it could be episodes like these  that are causing other people to experience weird outages, dependent on  whether their access router can tolerate it.

However, my evidence is thin. It is just as likely that the fault lies  with the Sagemcom router. If anyone can suggest a way to measure whether  frames from the Ubuntu machine are received/receivable by the Sagemcom  access point, or at least to measure what rate each frame is being sent  at, pls shout.

[B]Expt #4/ Mystery RTT variability
[/B]
I reinstalled the ideapad_laptop module with: ```
$ sudo modprobe ideapad_laptop
```

Then I ran ping tests overnight to test the older Robotics access point for longer. The re-inclusion of [FONT=courier new]ideapad_laptop[/FONT]  initially seemed to give consistently low (1-2ms) ping times, but later  in the night it returned to the variability I had seen without  ideadpad_laptop, particularly after about 06:30am when the RTT often hit  100ms - just to go across the room and back.
[ATTACH=CONFIG]262756[/ATTACH]

I tried to find traffic  reasons to explain the sudden return to variable RTTs. But there was no  evidence of increased traffic from the wireshark capture. Mystery. 
  
I did not find any further occurrence of black-holed echo requests...

[B]Expt #5/ The smoking gun
[/B]
Nonetheless, next I captured smoking gun evidence against Ra (Ubuntu). I  ran wireshark on Ra and found an identical pathological sequence of ARP  requests from Ra over 20secs that seemed to go unheard by any other  device. As before, Ra started by sending one ARP request per second to  the Robotics MAC address, asking "Who has 192.168.0.1?" This was the IP  address of Robotics - the machine the ARPs were addressed to, but Ra saw  no response. Then Ra sent 17 broadcast ARP requests, once per second.  Nothing responded to any of these until the last (which Robotics  responded to, and everything sorted itself out).

[ATTACH=CONFIG]262753[/ATTACH]

I was running wireshark on my old laptop (Mut) at the same time to check  if Ra was correctly broadcasting ARP request at the lowest rate (Mut  only supports 802.11b). In general, as expected, Mut only saw unicast  ARPs if they were destined for itself, or sent by  itself - because all  the other devices on the  wlan were capable of sending at higher rates.  However all machines are meant to  broadcast ARP requests at the lowest  possible rate, so everyone can hear them. Indeed I checked all the  broadcast ARPs that wireshark on Ra saw, and Mut did see them all too,  except...

Mut should have been able to see all 17 of Ra's broadcast ARPs, but it  only saw the last one (14:05:09 20-Jun-2015), which seems to be the only  one that Robotics saw as well. This strongly suggests that Ra (Ubuntu)  broadcasted the first 16 ARP requests at a transmission rate too fast  for any of my other device to understand (Ra is my only machine that  supports 802.11ac). It may be that Robotics couldn't hear the previous 3  ARP requests directed at it for the same reason.

___
I have kept (haphazard) records of pings, packet captures, arp tables, etc. So if anyone wants to dig deeper, just ask.

---

### Post by him610 on 2015-06-20
Baffled,

Don't like to admit this, but this is getting beyond my level of knowledge. Several years ago, I experienced some difficulty with a Broadcom wireless device that I was able to work through with help of an entry by another member of Ubuntu forums. There seem to be a lot of folks that have problems with Broadcom devices, and a few other brands also. It is discouraging to have a new system that has problems connecting consistently. 

I wish I could have been of better assistance. Keep at it. Maybe one of the network gurus will take notice of your problem after the weekend is over.  Good luck.

---

### Post by Bob_Briscoe on 2015-06-21
OK. Given I've tracked down an intermittent bug (which are the nastiest kind), I certainly hope a 'network guru' notices this thread. I'll summarise, given it's been a long thread:

The bug is repeatable with Ubuntu 14.04 LTS running on a Lenovo Yoga 3 Pro with a Broadcom bcm4352 802.11ac wireless network adapter.

Occasionally, usually at intervals of tens of minutes, the wireless adapter transmits packets that neither of my two different lower-rate access points seem to be able to detect. When connected to my 802.11g access point (a US Robotics 9108) this makes network-dependent processes frequently hang for 20secs. When connected to my 802.11n access point (a Sagemcom 2704n) network-dependent processes hang for tens of minutes, and typically for about an hour. Disconnecting and reconnecting from the access point cures the hang... until the next time. 

In both cases, the start of a problem is always detectable by when the laptop unicasts three ARP requests to the access point's MAC address, one per second, asking the access point to confirm the MAC address associated with its IP address. Neither access point seems to be able to detect these packets, so there is no response. The laptop then transmits the same ARP request, still one per  second, but to the broadcast MAC address. In the case of the 802.11n access point, it seems to hear none of this, so the laptop continues to hang for tens of minutes, while broadcasting ARP requests every second that nothing else seems to be able to hear. In the case of the 802.11g access point, it seems not to detect the first 16 broadcasts, but it responds to the 17th and the hang ends (after a period of 20 secs).

While monitoring the wlan with wireshark on an even slower 802.11b adapter on an old laptop, it couldn't see the three unicasts or the first 16 broadcasts. However, like the 802.11g access point, it saw the 17th. Other packets that the Ubuntu laptop sends out during these hang periods (pings, TCP packets etc) all seem not to be responded to by anything, as if they are also undetectable to the access point.

Questions: 
a) Can someone confirm my config is OK, by checking my wireless-info.txt in my first post - I'm new to Ubuntu?
b) Does my diagnosis make sense?
c) Can someone advise how I can downgrade my 802.11ac adapter to 802.11n or g until this is sorted out, so at least I have a stable machine (and it will help confirm the diagnosis). Below doesn't work:
```
$ iwlist wlan0 modulation
wlan0     unknown modulation information.
$ sudo iwconfig wlan0 modu 11g
Error for wireless request "Set Modulation" (8B2F) :
    SET failed on device wlan0 ; Operation not supported.
```
I had to guess '11g' because the iwconfig man page says use iwlist to find valid parameters for your card (but it doesn't - see above), so I noticed '11g' in one of the examples.

d) Can anyone repeat this bug? It seems possible this would be a kernel problem, perhaps not just specific to Ubuntu. Possibly even a hardware problem.

---

### Post by Bob_Briscoe on 2015-06-22
Is anyone there? I'd really appreciate some help with any of the questions (a-d) in my last post.

Latest: I found an "expert user" Web GUI on my Sagemcom access router (Sage) <http://{IPaddr}/expert_user.html>, altho still no telnet/ssh access. I manually added the MAC address of my Ubuntu latop (Ra) into the router's ARP cache, and I configured the MAC of Sage into Ra permanently too. When pinging Sage from Ra continually, it still intermittently gave dest host unreachable about half the time for tens of minutes at a time. So ARPs not getting through was a symptom not the cause. It seems all transmissions from Ra to Sage get black-holed during the dead periods, even tho wireshark on Ra thinks it is sending packets.

Next experiment: I now have access to a LAN statistics page on the router. So when the link next black holes, I will send large numbers of pings and see if they increase the receive statistics on the router. Then I can tell if they are incomprehensible to the router, or whether the router receives them but does nothing about them.

---

### Post by Bob_Briscoe on 2015-06-22
I would still appreciate an expert confirming whether my Ubutu config is correct (and any of my other 3 questions b-d). I would like to send back my router while I'm still within 2wks of starting with this broadband provider/ However, until someone knowledgeable confirms my Ubuntu config is not at fault, I can't - I'm not confident enough of my Ubuntu knowledge.

Latest experiment: When pings from my Ubuntu machine to my access router at 0.1sec intervals are showing "dest host unreachable" (or no response at all), the router's packet count for incoming and outgoing is rising consistent with it both receiving the echo requests and returning echo replies. However, wireshark on my Ubuntu machine is only seeing outgoing echo requests, and no incoming echo responses during these periods. 

During the whole black-holing period, Wireshark on my Ubuntu machine sees packets to and from other machines and broadcasts intended for it (eg. ARP), but no incoming unicast packets for itself at all, even tho wireshark sees many packets going out that ought to be responded to (pings) or acknowledged (TCP). So TCP is sending lots of retransmissions but never seeing ACKs or incoming data. The only incoming packets it sees (broadcasted ARP requests from the access router) lead it to send an ARP response immediately, and the router's ARP cache looks healthy throughout (I have removed the permanent MAC addresses I added for testing earlier).

After tens of minutes wireshark starts to see incoming packets again, and it all gets back to normal,... until the next time...

---

### Post by chili555 on 2015-06-23
> I tried removing the ideapad_laptop module with...

This is only sometimes useful to correct or diagnose a hard-blocked wireless; that is, when the switch or key combination has no effect and the wireless is inoperative even with a proper driver. It will have no effect here.

> wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Home-Farm' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    [COLOR="#FF0000"]Quality=29/70[/COLOR]  Signal level=-81 dBm  
                    Encryption key:off
                    ESSID:"Home-Farm"
                    <snip>

I feel like most of the trouble is right there: Quality 29/70. In my own situation, when I carry my laptop to the extremes of my property, and the signal strength drops, I have trouble connecting and then, once connected, staying connected. I urge you to find some way to relocate the router, re-orient its antennae, etc. in order to boost its visibility to the Broadcom.

I am also troubled by the lack of encryption here. In effect, your tax returns and banking details are sitting on the front porch in plain view. I urge you to switch to WPA2-AES with a strong password immediately.

> I replaced Sage with Robotics, which I hooked up to my broadband provider. I ran the same ping test at 5s intervals for 3hrs from Ra to Robotics. There were no periods of "destination unreachable" errors:

Now I think we're getting somewhere! I wonder if there is a setting in the new router that may be adjusted to help here. About a year ago, I got a new router and had a few issues with my several Intel wireless devices, all running Ubuntu. I experimented and honed a few techniques. Here is what I typically recommend:

First, check the settings in the router. WPA2-AES is preferred; not any WPA and WPA2 mixed mode and certainly not TKIP. Second, if your router is capable of N speeds, you may have better connectivity with a channel width of 20 MHz in the 2.4 GHz band instead of automatic 20/40 MHz, although it is likely to affect N speeds. I also have better luck with a fixed channel, either 1, 6 or 11, rather than automatic channel selection. Also, be certain the router is not set to use N speeds only; auto B, G and N is preferred. After making these changes, reboot the router. 

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

I am wondering if the "black holes" are when your 802.11ac device is trying to negotiate up to AC speeds which the router may not provide and, I am quite sure, the driver has, as of yet, poorly or not yet at all supported.

There are a few parameters available in the driver wl:

```
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string
```

And a few in the helper module cfg80211:

```
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
```

There is no documentation about what the driver modules do, at least that Google and I can find, so I am reluctant to suggest adding any parameters. Google finds these quoted in the driver .c code, but I'm not quite sure to do with it. 

Should you be adventurous, the usual process is to create a conf file with the parameter in it, like this:

```
sudo -i
echo "options wl some_paramter=1"  >  /etc/modprobe.d/wl.conf
exit
```

If it proves ineffective, remove it:

```
sudo rm /etc/modprobe.d/wl.conf
```

Note that each parameter tells you what the setting should be; for example 'int' wants 0 or 1 or 256 or some such. 'bool' wants Y or N. 'charp' wants, in this case, a country code like US. Yours is already set so you may ignore this.

> Latest: I found an "expert user" Web GUI on my Sagemcom access router (Sage) <http://{IPaddr}/expert_user.html>

Can we see a screenshot, please? Of course, obscure any personal details like your new WPA2 key. Perhaps there is a setting we can help with.

---

### Post by Bob_Briscoe on 2015-06-23
Thanks for taking up my case. 

**First**, in case they are relevant, I need to update you on a couple of module commands I ran a few hours ago (before you responded). I was tempted into them when I ran:
```

$ sudo apt-get install bcmwl-kernel-source
{snip...}
bcmwl-kernel-source is already the newest version.
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libupstart1 linux-headers-3.16.0-30
  linux-headers-3.16.0-30-generic linux-image-3.16.0-30-generic
  linux-image-extra-3.16.0-30-generic
Use 'apt-get autoremove' to remove them.
0 to upgrade, 0 to newly install, 0 to remove and 7 not to upgrade.

```
It suggested I autoremove, so I did:
```

$ sudo apt-get autoremove
{snip...}
Error! Your kernel headers for kernel 3.16.0-30-generic cannot be found.
$ sudo apt-get install linux-headers-3.16.0-30-generic
{snip...}
$ sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED
  linux-headers-3.16.0-38 linux-headers-3.16.0-38-generic
  linux-image-3.16.0-38-generic linux-image-extra-3.16.0-38-generic
  linux-signed-image-3.16.0-38-generic
0 to upgrade, 0 to newly install, 5 to remove and 7 not to upgrade.
After this operation, 280 MB disk space will be freed.
Do you want to continue? [Y/n]
(Reading database ... 273147 files and directories currently installed.)
Removing linux-headers-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Removing linux-headers-3.16.0-38 (3.16.0-38.52~14.04.1) ...
Removing linux-signed-image-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
Found linux image: /boot/vmlinuz-3.16.0-38-generic
Found initrd image: /boot/initrd.img-3.16.0-38-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-extra-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
run-parts: executing /etc/kernel/postinst.d/apt-auto-removal 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
run-parts: executing /etc/kernel/postinst.d/dkms 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
run-parts: executing /etc/kernel/postinst.d/initramfs-tools 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
update-initramfs: Generating /boot/initrd.img-3.16.0-38-generic
run-parts: executing /etc/kernel/postinst.d/pm-utils 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
run-parts: executing /etc/kernel/postinst.d/update-notifier 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
run-parts: executing /etc/kernel/postinst.d/zz-update-grub 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
Found linux image: /boot/vmlinuz-3.16.0-38-generic
Found initrd image: /boot/initrd.img-3.16.0-38-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
Removing linux-image-3.16.0-38-generic (3.16.0-38.52~14.04.1) ...
Examining /etc/kernel/prerm.d.
run-parts: executing /etc/kernel/prerm.d/dkms 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
dkms: removing: bcmwl 6.30.223.248+bdcom (3.16.0-38-generic) (x86_64)

-------- Uninstall Beginning --------
Module:  bcmwl
Version: 6.30.223.248+bdcom
Kernel:  3.16.0-38-generic (x86_64)
-------------------------------------

Status: Before uninstall, this module version was ACTIVE on this kernel.

wl.ko:
 - Uninstallation
   - Deleting from: /lib/modules/3.16.0-38-generic/updates/dkms/
 - Original module
   - No original module was found for this module on this kernel.
   - Use the dkms install command to reinstall any previous module version.

depmod....

DKMS: uninstall completed.
Examining /etc/kernel/postrm.d .
run-parts: executing /etc/kernel/postrm.d/initramfs-tools 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
update-initramfs: Deleting /boot/initrd.img-3.16.0-38-generic
run-parts: executing /etc/kernel/postrm.d/zz-update-grub 3.16.0-38-generic /boot/vmlinuz-3.16.0-38-generic
Generating grub configuration file ...
Found linux image: /boot/vmlinuz-3.16.0-41-generic
Found initrd image: /boot/initrd.img-3.16.0-41-generic
Found Windows Boot Manager on /dev/sda2@/EFI/Microsoft/Boot/bootmgfw.efi
Adding boot menu entry for EFI firmware configuration
done
bobbriscoe@Ra:~$ lsmod | grep wl
wl                   6367833  0
cfg80211              494362  1 wl

```

I'm not sure what I've done here - it looks relevant to my broadcom driver. Should I have done this?

Since then, I've seen at least one period of black-holing, so let's return to your suggestions now:

**ideapad_laptop**: Yes, further down my thread I confirmed removing it made no difference, and reinstated it.

My first question was:
***Qa) Can someone confirm my config is OK***
So, can I take it that you're saying there's nothing obviously wrong with my config? Here it is again, given I've fiddled since I first posted it:

```

########## wireless info START ##########

Report from: 23 Jun 2015 20:21 BST +0100

Booted last: 20 Jun 2015 22:27 BST +0100

Script from: 21 May 2015 09:10 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 3.16.0-41-generic #57~14.04.1-Ubuntu SMP Thu Jun 18 18:01:13 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

01:00.0 Network controller [0280]: Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03)
    Subsystem: Lenovo Device [17aa:0623]
    Kernel driver in use: wl

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 005: ID 048d:8386 Integrated Technology Express, Inc. 
Bus 001 Device 004: ID 1bcf:2c43 Sunplus Innovation Technology Inc. 
Bus 001 Device 003: ID 0489:e07a Foxconn / Hon Hai 
Bus 001 Device 007: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
3: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
6: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6367833  0 
cfg80211              494362  1 wl
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop
wmi                    19193  0 

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9248:9aff:fefb:25cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:963582 errors:0 dropped:0 overruns:0 frame:312046
          TX packets:313543 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:531705132 (531.7 MB)  TX bytes:40715703 (40.7 MB)
          Interrupt:18 

##### iwconfig ##########################

lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.254   0.0.0.0         UG    0      0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       784     1  0 Jun20 ?        00:00:16 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0  [Home-Farm] ---------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    USR9108:         Infra, <MAC 'USR9108' [AC2]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 46
    Home-Farm:       Infra, <MAC 'Home-Farm' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 70

  IPv4 Settings:
    Address:         192.168.1.2
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

no-auto-default=<MAC address>,

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/USR9108]] (600 root)
[connection] id=USR9108 | type=802-11-wireless
[802-11-wireless] ssid=USR9108 | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

[[/etc/NetworkManager/system-connections/Home-Farm]] (600 root)
[connection] id=Home-Farm | type=802-11-wireless
[802-11-wireless] ssid=Home-Farm | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

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
          Channel 14 : 2.484 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Channel 48 : 5.24 GHz
          Channel 149 : 5.745 GHz
          Channel 150 : 5.75 GHz
          Channel 151 : 5.755 GHz
          Channel 152 : 5.76 GHz
          Channel 153 : 5.765 GHz
          Channel 154 : 5.77 GHz
          Channel 155 : 5.775 GHz
          Channel 156 : 5.78 GHz
          Channel 157 : 5.785 GHz
          Channel 158 : 5.79 GHz
          Channel 159 : 5.795 GHz

##### iwlist scan #######################

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'Home-Farm' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=69/70  Signal level=-41 dBm  
                    Encryption key:off
                    ESSID:"Home-Farm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
          Cell 02 - Address: <MAC 'USR9108' [AC2]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=38/70  Signal level=-72 dBm  
                    Encryption key:off
                    ESSID:"USR9108"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago

##### module infos ######################

[wl]
filename:       /lib/modules/3.16.0-41-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     DF2576C38AD45205B3556DD
depends:        cfg80211
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/3.16.0-41-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     33ED2C1448F5AEDBE7AF59E
depends:        
intree:         Y
vermagic:       3.16.0-41-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        E5:A2:46:0C:FF:17:AE:74:6B:8B:53:6A:72:D3:79:FB:B5:47:76:DB
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
# PCI device 0x14e4:0x43b1 (wl)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (ax88179_178a)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

##### dmesg #############################

[174629.457326] ERROR @wl_dev_intvar_get : error (-1)
[174727.051257] device wlan0 left promiscuous mode
[174738.382898] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############


```

**Signal Quality**: Since earlier postings I had used [FONT=courier new]wavemon [/FONT]to locate and orientate the access point better. I'd got quality up into the 40's. While I'm typing I am testing the link to the 802.11n access point 10cm away from my 802.11ac Ubuntu machine (it's not connected to the WAN, but I'm solely testing the wifi link and using another machine to write this response). 
```
Quality=70/70   Signal level=-33dBm

```

Are you saying Quality=29/70 might cause this black-holing? I hadn't appreciated that. Over the next few hours I will experiment.

**WiFi Security**: Thanks for your concern, but I live 300m from the nearest house. I turned off link security, just to eliminate this extra possible complication from our investigations (anyway, e2e encryption and authentication is sufficient for tax returns and banking).

**OK with my other router?** Care! You've picked one occasion where I report 3 hrs without an error on another router. If you look earlier in the thread (find 'smoking gun') you will see I got similar back-holing symptoms with this other router (802.11g US Robotics 9108), altho not at all as frequent, and not as long-lasting when it happens.

**Regulatory domain**: In the wireless-info.txt in my first posting, you will see I had set this to GB already (as I said, I had followed all your advice in your broadcom sticky, and as many other postings as I could find, before I posted anything - I don't like to waste people's time).

**IPv6**: OK, I hadn't set it to ignore. I have now temporarily. But I will need to revert this once I've proved it's not part of the problem.

> I am wondering if the "black holes" are when your 802.11ac device is  trying to negotiate up to AC speeds which the router may not provide  and, I am quite sure, the driver has, as of yet, poorly or not yet at  all supported.

I'm interested in doing more than wondering about this. Many people have been having  intermittent black-holing with various Broadcom adapters for a year or two (you probably have longer experience - I'm just going by postings I've found). Some have been  identified as module misconfiguration by helpful folks like you. However, many  have never been solved. All those people have spent good money in  return for weeks of grief and a pile of useless silicon, and Broadcom have taken that money from companies  like Lenovo for these adapters. If you can help me, I am willing to try to run experiments that nail this problem. It's giving Linux a bad reputation for unreliability.

<RANT>Even if the problem is signal quality, these access routers ought to prioritise connectivity over speed - 512kb/s with connectivity is far more useful than 1Gb/s without connectivity. I get increasingly irritated by the industry's focus on raw bit-rate, to the exclusion of connectivity (and latency). 
<RANT>...don't get me started on latency - this little Sagemcom access point has 18 minutes (!!!) of bufferbloat (from my initial tests - I've got to test it more scientifically). 
</RANT>
</RANT>

Indeed, one of my outstanding questions is:
[I][B]c) Can someone advise how I can downgrade my 802.11ac adapter to 802.11n or g (on Ubuntu)?
[/B][/I]because, as I have made clear, neither of my routers supports 802.11ac (see my "cast of characters"), and if I could get [FONT=courier new]iwconfig wlan0 modu <modulation>[/FONT] to do anything, it would help shed more light on this problem.

I take it that you don't know an answer. I'll dig a bit deeper into the driver parameters you list, but from a quick scan of the names, none look like they will limit the modulation.

The expert_user GUI on my Sagemcom router isn't as useful as it sounds. It's still fairly limited - it's got nothing about the WLAN at all. It would require a lot of screen shots to show you not much, so I'll just list all the menus and their submenus. if any pique your interest, just shout and I can show a screen shot:[INDENT]Device Info
[/INDENT]
[INDENT=2]Summary
WAN
Statistics
Route
ARP
DHCP[/INDENT]
[INDENT]Advanced Setup[/INDENT]
[INDENT=2]VPN
LAN
NAT
DNS[/INDENT]
[INDENT]Diagnostics[/INDENT]
[INDENT]Management[/INDENT]
[INDENT=2]Settings
Access Control
Update Software
Reboot
[/INDENT]
 
Nonetheless, in the non-expert_user GUI there is an interesting setting on the WiFi:
Wi-Fi mode: 
802.11b/g/n (up to 300Mb/s)
802.11b/g/n (up to 144Mb/s)
802.11b/g (up to 54Mb/s)

It's set to 144 by default. For my next experiments I'll try 54Mb/s (after all, the fastest my DSL line goes is 3.1Mb/s - another 'feature' of living in the middle of nowhere).

[B]Black hole between n -> ac
[/B]What did you think of my last experiment (before you posted), which showed that over durations of minutes the Sagemcom router was sending out packets that my Ubuntu laptop wasn't detecting? I was going on the theory that the ac (Ubuntu) machine might be transmitting too fast for the n router. But I have proved that the problem is in the other direction, which was really unexpected. I still need to prove which end is to blame tho.

I'll report back. Thank you for your help so far.

---

### Post by chili555 on 2015-06-23
> So, can I take it that you're saying there's nothing obviously wrong with my config?

I see nothing wrong so far, except regulatory domain. Although you said, and it's true:

> In the wireless-info.txt in my first posting, you will see I had set this to GB already 

However, now it has somehow reverted:

```
##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
```

I have seen enough cases, including my own fighting with a cheap USB wireless that seems to be hard-coded to China, where the country code helps. I therefore recommend that the code be re-set.

> Quality=70/70   Signal level=-33dBm

I will be interested to see if the charts look better or the same.

> All those people have spent good money in return for weeks of grief and a pile of useless silicon, and Broadcom have taken that money from companies like Lenovo for these adapters.

Yes, indeed. I myself have two Lenovo laptops and I can tell you from calls and letters to them that they care not one bit about Linux. They sold me a laptop with a working wireless device in W7 and they don't really care or respond beyond that. 

Ohhhh! Nested rants! A first, as far as I know!

> For my next experiments I'll try 54Mb/s (after all, the fastest my DSL line goes is 3.1Mb/s - another 'feature' of living in the middle of nowhere).

Again, I will be interested in the result. Of course, the detriment, even in the country, is that back-ups to or from, for example, an NAS, creep along at 54 Mb/s rather than 300 Mb/s. 

> What did you think of my last experiment (before you posted), which showed that over durations of minutes the Sagemcom router was sending out packets that my Ubuntu laptop wasn't detecting?

I put that down, provisionally, to the signal strength. I think the laptop and router were shouting but too far away to be heard clearly.

> Can someone advise how I can downgrade my 802.11ac adapter to 802.11n or g (on Ubuntu)?

I know of no way. Sorry.

Your device, Broadcom Corporation BCM4352 802.11ac Wireless Network Adapter [14e4:43b1] (rev 03), is pretty new and I don't think the driver *wl* is quite well enough developed.

---

### Post by Bob_Briscoe on 2015-06-24
OK. Thanks, chili555, for pointing out that signal quality might be the cause. It was. Nonetheless, the drivers shouldn't sacrifice connectivity for speed. If a high rate adapter can't get reception, it should drop to a lower  rate within milliseconds, not continue banging its head against a brick  wall (sometimes literally) for tens of minutes.

Altho I can work round *my* problem by downgrading my access point to 802.11g (not a true solution - as you say it prevents me using the higher rates when they would be possible and necessary), I'm willing to continue gathering evidence that this needs fixing properly, probably in the driver. 

Should I continue on this Ubuntu forum, or is there a better place for such a venture?

**Latest experiments**

1/ While I had the 802.11n access point 10cm away with 70/70 quality (at 23:11 I started walking the laptop to different distances from the access point until reception broke):
[ATTACH=CONFIG]262835[/ATTACH]

Note that I have started to record "no answer yet" as well as "Destination Host Unreachable". Reason: 
[LIST]
[*]I came to understand that ping returns DHU from the local stack only when the local stack has no next hop address to send the ping to, which in this case is because the local ARP cache has expired and it's not heard any response to its ARP request, which only happens after a period of 35s of black-holing; 
[*]By using the -O switch, you can get ping to return "No answer yet"  (rather than just missing the report for that seq no) if it hasn't  received a response just before it sends the next request, ie you get at least one line of output per seqno rather than having to search for skips in the seqno. This gives immediate finer-grained visibility of the occurrence of black-holes, rather than only reporting the pathological cases when black-holes are long enough to break ARP. 
[/LIST]

2/ After having downgraded my 802.11n access point to 802.11g (up to 54Mb/s).
[ATTACH=CONFIG]262837[/ATTACH]
This gives 'reasonable' reception over 5.5m and a brick wall. The level of ping loss is rather 'unreasonable' at 0.4%. This might be expected if there was other capacity-seeking (TCP) traffic, but that should have been rare - the experiment was conducted overnight with only very occasional background traffic. It is worse than with my 'true' 802.11g access router. Also latency is much worse.

**Planned next steps**

[LIST=1]
[*]Boot my Ubuntu machine into Windows8.1, revert the access point to 802.11n and run similar tests over 5.5m and a brick wall to see if the Windows driver sacrifices connectivity for speed, or whether such sefl-harm is only in the Linux driver; 
[*]Run an equivalent test to those above with my native 802.11g  access point (previously I did not use ping -O and I have since aligned the access point better as well); 
[*]Get on with the rest of my life. 
[/LIST]

---

### Post by Bob_Briscoe on 2015-06-25
With my dual boot Yoga 3 Pro, I've confirmed that the Broadcom bcm4352 802.11ac wireless network adapter driver in Ubuntu 14.04 LTS is dysfunctional by comparing its reception range to that of the same laptop running Win8.1.
[TABLE="width: 700, align: center"]
[TR]
[TD]OS[/TD]
[TD]Access Point[/TD]
[TD]Walls etc[/TD]
[TD]Range[/TD]
[/TR]
[TR]
[TD]Win8.1[/TD]
[TD]802.11b/g/n[/TD]
[TD]one 1-brick wall + 1 stud wall + massive 16C brick chimney[/TD]
[TD]13.5m[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]802.11b/g/n[/TD]
[TD]two 2-brick walls + one 1-brick wall[/TD]
[TD]25m[/TD]
[/TR]
[TR]
[TD][/TD]
[TD]802.11b/g/n[/TD]
[TD]2 stud walls[/TD]
[TD]35m[/TD]
[/TR]
[TR]
[TD]Ubuntu 14.04 LTS[/TD]
[TD]802.11b/g/n[/TD]
[TD]one 2-brick wall[/TD]
[TD]5.5m :([/TD]
[/TR]
[TR]
[TD][/TD]
[TD]802.11b/g [SUP]{1}[/SUP][/TD]
[TD]one 2-brick wall[/TD]
[TD]10m :(
[/TD]
[/TR]
[/TABLE]


It seems the Broadcom driver in Linux doesn't adapt down to a lower rate when reception quality is poor at a higher rate, which is necessary to comply with the 802.11 spec.
[SUP]{1}[/SUP] Forcing the Broadcom driver down to 802.11g (by configuring a downgrade on the access point) gives the Linux driver a little more range.

Below are comparative plots of ping tests with the access point at a fixed range of 5.5m through one 2-brick-thick wall. They show that even at this (pathetic) range, Broadcom's Linux driver does not offer a workable solution.

[TABLE="width: 1300, align: center"]
[TR]
[TD="align: center"][B]Round Trip Time against Time of Day Plots (the different durations of the runs are not significant)
[/B][HR][/HR][/TD]
[TD="align: center"]**Cumulative Distribution Function of RTT**[HR][/HR][/TD]
[TD="align: center"]**Comments**[HR][/HR][/TD]
[/TR]
[TR]
[TD][IMG]http://bobbriscoe.net/images/bcm4352-ping-5s-linux-11n-5.5m50.png[/IMG][/TD]
[TD][IMG]http://bobbriscoe.net/images/bcm4352-ping-5s-linux-11n-5.5m-cdf50.png[/IMG][/TD]
[TD]Linux was unusable only 5.5m away from an 802.11n access point. And this was a relatively good run. More typically it black-holed over half the time at this distance.[/TD]
[/TR]
[TR]
[TD][IMG]http://bobbriscoe.net/images/bcm4352-ping-5s-linux-11g-5.5m50.png[/IMG][/TD]
[TD][IMG]http://bobbriscoe.net/images/bcm4352-ping-5s-linux-11g-5.5m-cdf50.png[/IMG][/TD]
[TD]Downgrading the access point to 802.11g made the wlan usable but over a range no greater than 5.5m.

However, the latency was poor and highly variable (250ms at the 95th percentile)[/TD]
[/TR]
[TR]
[TD][IMG]http://bobbriscoe.net/images/bcm4352-ping-5s-win81-11n-5.5m50.png[/IMG][/TD]
[TD][IMG]http://bobbriscoe.net/images/bcm4352-ping-5s-win81-11n-5.5m-cdf50.png[/IMG][/TD]
[TD]Windows on the same hardware gave solid connectivity with low latency variability (5ms at the 95th percentile)[/TD]
[/TR]
[TR]
[TD][IMG]http://bobbriscoe.net/images/bcm4352-ping-5s-win81-11g-5.5m50.png[/IMG][/TD]
[TD][IMG]http://bobbriscoe.net/images/bcm4352-ping-5s-win81-11g-5.5m-cdf50.png[/IMG][/TD]
[TD]Windows on the same laptop hardware but with the access point downgraded to 802.11g dropped fewer packets ad gave even more reliably low latency (3.5ms at the 95th percentile).[/TD]
[/TR]
[/TABLE]

---

### Post by Bob_Briscoe on 2015-06-25
> <RANT>...don't get me started on latency - this little Sagemcom  access point has 18 minutes (!!!) of bufferbloat (from my initial tests -  I've got to test it more scientifically). 
</RANT>

I must correct my over-stated criticism of the Sagemcom 2704n access router. The 18mins of buffer must have been somewhere else on the path. Having tested it, the Sagemcom has about 1.65secs of upstream buffer at my upstream rate of 650kb/s, which translates into 134kB of buffer or 90x 1500B packets. I can still be critical though (just not so over-critical): that ought to be reduced by about 15 times using active queue management. Otherwise an average Web page will unnecessarily take 10-30secs longer to complete, if viewed while uploading something else.

---

### Post by chili555 on 2015-06-26
In the case of the Linux driver, I suspect you are seeing the effect of a do-all, be-all driver, *bcmwl-kernel-source*, that tries to cover several disparate devices. As well, I don't think the 802.11AC capabilities are present at all in the driver. Broadcom's own b43 suite and Intel's iwlwifi suite address this with specific firmware that is called up and loaded for each specific device. For example:```
$ modinfo b43
filename:       /lib/modules/4.0.1-040001-generic/kernel/drivers/net/wireless/b43/b43.ko
[COLOR="#FF0000"]firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw[/COLOR]

```I wonder if the information you've developed will be helpful to Broadcom. I'm not exactly sure where to report it, but here is a start: [http://www.broadcom.com/support/?gid=1](http://www.broadcom.com/support/?gid=1)

I wish I had another suggestion, but I think this may be a case of a not well developed driver suite for a very new technology. I'm confident it will work better in a year or so, but I know that doesn't help you today.

---

### Post by Bob_Briscoe on 2015-06-26
Thanks for your help so far. OK, I'll try to find how to report it, but it might be better coming from folks who already have a channel into Broadcom (I know many people in Broadcom but not appropriate to this context). Would there be a good Linux kernel forum that might be able to advise how best to report this?

I assume this is not specific to Ubuntu and that any distro is likely to be affected. I've seen all sorts of people who say they have it 'working' on various distros, but that could be because,... they have an 802.11g access point; or they are sitting close to their access point; or their room has paper walls, or... whatever.

While I was initially searching for other postings about this, I found this [Arch Linux thread about the broadcom-wl 6.30.223.248-6 package]("https://aur.archlinux.org/packages/broadcom-wl/?comments=all"): I didn't feel my concerns would be appropriate for that list at the time, but perhaps they might be able to point me in the right direction now I have some proof that just getting it to run without crashing is not enough?

BTW, I also found this ['SOLVED' thread]("http://ubuntuforums.org/showthread.php?t=2229472") for Ubuntu (the solution is to rip out the Broadcom board and replace it with the Intel alternative). This is the approach I'm going to take for my own machine, presumably voiding my guarantee. But I'm still willing to report this so it gets fixed for others.

Cheers

---

### Post by Cashalow on 2015-11-17
Ok somehow I missed this topic.

I bought a ASUS PCE AC56 card to put on my desktop, to go along with my ac capable router. I had very good connectivity on the 2.4GHz band, but I could never detect nor connect to the 5GHz band, even when I disabled the 2.4GHz one. Which was very very strange because I could scan all channels, from 01 to 159. Max speed was aroung 50 Mbps, ping 10, which is highly disappointing for a 50$ card. After trying many things for one week, I'll bring back the card today and go for an intel based, ac capable, if that even exists for Linux.

---

### Post by chili555 on 2015-11-17
>  intel based, ac capable, if that even existsProbably not in a desktop form factor.

---

### Post by hans12345 on 2016-01-07
My two-pence worth of comments:
- Bob_Briscoe needs a medal, even if I did not understand 80% of what he did
- I also have major problems with connecting on 802 n while using different USB sticks, but the old 802 a/b/g ones work much better

---

### Post by hal9000ht on 2016-02-08
[https://www.broadcom.com/support/802.11](https://www.broadcom.com/support/802.11)

---

### Post by juannm on 2016-07-26
Hi Bob Briscoe;

it's almost August 2016, and I'm reading your analysis of the Broadcom card just now. The analysis you did in this thread was fantastic, and I really wish there were more knowledgeable people which studied technical problems in this manner. It probably helps that I've been able to understand all you did...
Now I'd love to keep the track of what happened with this topic. I bought a computer some months ago, its motherboard came with an integrated BCM4352 wireless card, and it is incredibly unreliable under Ubuntu 14.04. I have been convinced all this time that the driver was at fault, but never had enough time to perform a detailed study as you did. I just found that absolutely all other devices were working fine.

Did you get to post an issue on some Linux Kernel development list, or maybe Broadcom support?

Of course it's been a year and Ubuntu 16.04 is already around, but I'd rather wait until they stabilize that bug ridden mess before jumping onto the new version of the distribution. Also, it's been proved already that this iteration of Ubuntu has been disastrous regarding the regressions and inconsistencies compared to the previous 14.04, so jumping abroad to the newest version isn't actually a granted improvement...
(note: it seems that there hasn't been any update to the driver since 14.04, according to this page: [https://launchpad.net/ubuntu/+source/bcmwl](https://launchpad.net/ubuntu/+source/bcmwl))

In any case I'd like to keep on the track of this issue, if I'm lucky and you read this :-)

Best regards
Juan

---

