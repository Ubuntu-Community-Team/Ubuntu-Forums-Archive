---
title: "BCM4352 wireless (Dell M6800 branded &quot;1550&quot;) on U1404, weird 'cannot connect' bug"
date: 2014-06-13
forum: Networking &amp; Wireless
---

### Post by jonathan.battle on 2014-06-13
- BTW this issue absolutely does justify this new thread, altho it is alluded to in existing threads (search BCM4352, Dell, esp M4800 and M6800, and DW1550 which is what Dell calls the mini-card).
- Over several weeks, I've perused all other related threads, and tried some helpful fix suggestions; and perused the many related discussions, all of which are utterly irrelevant to the underlying problem here. Now I have a final, complete resolution.
***- Do not buy any Broadcom hardware, period. Replace what you have with another manufacturer.***

- BCM4352 works on W8x, because the Broadcom staff shared the correct config parameters with Microsoft. They have refused to share the same, trivial, details with any linux community, and fherefore, all the Linux drivers fail with  BCM4352.

- i will now replace the DW1550 card with an **Intel **[COLOR=#444444][FONT=Tahoma]**Dual Band Wireless-AC 7260 PCI Express Half Mini Card. **
[/FONT][/COLOR]***- It is imperative that if you have a Dell Mx800, you do this: trash the Broadcom rubbish now.***
- And ..
(a) save yourself hundreds of hours of totally unnecessary debugging.
(b) contribute toward the eventual goal of removing enterprises like Broadcom from our industry.


[COLOR=#444444][FONT=Tahoma]
[/FONT][/COLOR]

---

### Post by etb513 on 2014-07-04
It's sad to hear that there still isn't proper driver support for the BCM4352/Dell-Wireless-1550. I spent weeks journeying to hell and back trying to get the card to properly function back in January before giving up on transitioning to linux. I figured that by now, the card would have functional drivers, but since that isn't the case, I'll just have to purchase an alternative solution.

My question is, **what are my options?** I have a Dell Precision M4800 and I know absolutely nothing about current mobile wireless NICs. Is the Intel 7260 mentioned a good buy for linux?

---

### Post by phico on 2014-08-12
Hello,  I had many issues on Linux Mint (Ubuntu based) with BCM4352 on DELL M6800 ..
Most drivers I found were unstable or could not authenticate on WPA2 (bcmwl-kernel-source, ..) 

I had to compile and install broadcom hybrid driver  : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and now I have no problem any more .. all works perfectly !

Hope this help ..

---

### Post by miro-radenovic on 2015-01-17
> **jonathan.battle said:**
> - BTW this issue absolutely does justify this new thread, altho it is alluded to in existing threads (search BCM4352, Dell, esp M4800 and M6800, and DW1550 which is what Dell calls the mini-card).
- Over several weeks, I've perused all other related threads, and tried some helpful fix suggestions; and perused the many related discussions, all of which are utterly irrelevant to the underlying problem here. Now I have a final, complete resolution.
***- Do not buy any Broadcom hardware, period. Replace what you have with another manufacturer.***

- BCM4352 works on W8x, because the Broadcom staff shared the correct config parameters with Microsoft. They have refused to share the same, trivial, details with any linux community, and fherefore, all the Linux drivers fail with  BCM4352.

- i will now replace the DW1550 card with an **Intel **[COLOR=#444444][FONT=Tahoma]**Dual Band Wireless-AC 7260 PCI Express Half Mini Card. **
[/FONT][/COLOR]***- It is imperative that if you have a Dell Mx800, you do this: trash the Broadcom rubbish now.***
- And ..
(a) save yourself hundreds of hours of totally unnecessary debugging.
(b) contribute toward the eventual goal of removing enterprises like Broadcom from our industry.
[COLOR=#444444][FONT=Tahoma]
[/FONT][/COLOR]

i have followed you hint  and I have replace it with **Intel **[COLOR=#444444][FONT=Tahoma][B]Dual Band Wireless-AC 7260 PCI Express Half Mini Card
[/B][/FONT][/COLOR]my M64000 now works perfectly on W7 (with additional drivers) and Ubuntu 14.04.

Thanks for posting it!

---

### Post by can.gungor on 2015-02-04
Hello,
I have Dell Precision M6800. I installed ubuntu 14.04.1 LTS.
I have similar &#305;ssue. I turn my wireless on and I see the possible connections available in the area but when I click to connect it tries connecting but turn me to ask the password even if the pasword is correct. Then can not connect wifi.
I stucked between reading the solutions. There is no way I found to connect. To change my card is impossible because it is a debit computer given from my institute.

Thanks for your help.

---

### Post by Bob_Briscoe on 2015-06-17
> **phico said:**
> I had to compile and install broadcom hybrid driver  : [http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
and now I have no problem any more .. all works perfectly !

Can you confirm whether your advice is still current? In the README on the Broadcom site you point to it says it has been upgraded to support 3.11 and that this driver has now been integrated into standardard distributions (Fedora & Ubuntu at least). I'm running kernel v 3.16 and Ubuntu 14.04.2 LTS.

It won't build, with the errors given below.
(I'm effectively a newbie and I'm not a programmer - I'm new to Linux/Ubuntu package mgmt - I was a Unix sysadmin 20 years ago but my brain has been destroyed by Windows  in the intervening years)

I downloaded the v. 6.30.223.248 Linux STA 64-bit driver you pointed to, ungzipped, installed the pre-requistie packages as instructed in the README. Ran [FONT=courier new]make[/FONT], but got warnings and and errors - I don't really understand what I'm doing.

```

bobbriscoe@Ra:~/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248$ make
KBUILD_NOPEDANTIC=1 make -C /lib/modules/`uname -r`/build M=`pwd`
make[1]: Entering directory `/usr/src/linux-headers-3.16.0-41-generic'
CFG80211 API is prefered for this kernel version
Using CFG80211 API
  LD      /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/built-in.o
  CC [M]  /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/shared/linux_osl.o
  CC [M]  /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_linux.o
  CC [M]  /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_iw.o
  CC [M]  /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.o
/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c: In function &#8216;wl_cfg80211_get_key&#8217;:
/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c:1390:2: warning: passing argument 1 of &#8216;memcpy&#8217; discards &#8216;const&#8217; qualifier from pointer target type [enabled by default]
  memcpy(params.key, key.data, params.key_len);
  ^
In file included from ./arch/x86/include/asm/string.h:4:0,
                 from include/linux/string.h:17,
                 from include/linux/bitmap.h:8,
                 from include/linux/cpumask.h:11,
                 from ./arch/x86/include/asm/cpumask.h:4,
                 from ./arch/x86/include/asm/msr.h:10,
                 from ./arch/x86/include/asm/processor.h:20,
                 from ./arch/x86/include/asm/thread_info.h:23,
                 from include/linux/thread_info.h:54,
                 from ./arch/x86/include/asm/preempt.h:6,
                 from include/linux/preempt.h:18,
                 from include/linux/spinlock.h:50,
                 from include/linux/seqlock.h:35,
                 from include/linux/time.h:5,
                 from include/linux/stat.h:18,
                 from include/linux/module.h:10,
                 from /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/include/linuxver.h:40,
                 from /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c:26:
./arch/x86/include/asm/string_64.h:32:14: note: expected &#8216;void *&#8217; but argument is of type &#8216;const u8 *&#8217;
 extern void *memcpy(void *to, const void *from, size_t len);
              ^
/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c: At top level:
/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c:1778:2: warning: initialization from incompatible pointer type [enabled by default]
  .get_station = wl_cfg80211_get_station,
  ^
/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c:1778:2: warning: (near initialization for &#8216;wl_cfg80211_ops.get_station&#8217;) [enabled by default]
/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c: In function &#8216;wl_notify_connect_status&#8217;:
/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c:2074:4: warning: passing argument 3 of &#8216;cfg80211_ibss_joined&#8217; makes pointer from integer without a cast [enabled by default]
    cfg80211_ibss_joined(ndev, (u8 *)&wl->bssid, GFP_KERNEL);
    ^
In file included from /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c:33:0:
include/net/cfg80211.h:4002:6: note: expected &#8216;struct ieee80211_channel *&#8217; but argument is of type &#8216;unsigned int&#8217;
 void cfg80211_ibss_joined(struct net_device *dev, const u8 *bssid,
      ^
/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c:2074:4: error: too few arguments to function &#8216;cfg80211_ibss_joined&#8217;
    cfg80211_ibss_joined(ndev, (u8 *)&wl->bssid, GFP_KERNEL);
    ^
In file included from /home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.c:33:0:
include/net/cfg80211.h:4002:6: note: declared here
 void cfg80211_ibss_joined(struct net_device *dev, const u8 *bssid,
      ^
make[2]: *** [/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248/src/wl/sys/wl_cfg80211_hybrid.o] Error 1
make[1]: *** [_module_/home/bobbriscoe/Downloads/Broadcom/hybrid-v35_64-nodebug-pcoem-6_30_223_248] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-3.16.0-41-generic'
make: *** [all] Error 2


```

Here's some background to my problem... I've just installed Ubuntu (dual-boot with Win8.1) on a Lenovo Yoga 3 Pro laptop with config as shown in the wireless-info script output below.

```

########## wireless info START ##########

Report from: 17 Jun 2015 12:05 BST +0100

Booted last: 16 Jun 2015 18:31 BST +0100

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
Bus 001 Device 006: ID 093a:2510 Pixart Imaging, Inc. Optical Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
    Soft blocked: yes
    Hard blocked: no
1: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: ideapad_bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
4: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

wl                   6367833  0 
cfg80211              494362  1 wl
wmi                    19193  0 
ideapad_laptop         18278  0 
sparse_keymap          13948  1 ideapad_laptop

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::9248:9aff:fefb:25cf/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:65612 errors:0 dropped:0 overruns:0 frame:7030
          TX packets:66226 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:56776176 (56.7 MB)  TX bytes:17330693 (17.3 MB)
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

root       751     1  0 Jun16 ?        00:00:07 NetworkManager

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
    Speed:           6 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *Home-Farm:      Infra, <MAC 'Home-Farm' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 44

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
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:off
                    ESSID:"Home-Farm"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 92ms ago

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

[  137.683304] ERROR @wl_dev_intvar_get : error (-1) (repeated 2 times)
[63202.710606] ERROR @wl_dev_intvar_get : error (-1)

########## wireless info END ############

```

The laptop has a Broadcom bcm4352 802.11 network adapter, so I installed the dkms then bcmwl-kernel-source packages, and the WLAN worked sometimes. Then I discovered that people have been complaining for many years that this driver is unstable, and I'm getting the same symptoms. However, your post seems to be optimistic.

Below are plots showing that just over 50% of pings fail, because it toggles from working to not working and back again over periods of typically tens of minutes. These pings were run while the radio environent was otherwise quiet (I live 300m from the next nearest house). Other machines using the same WiFi subnet have no problems. 

[ATTACH=CONFIG]262661[/ATTACH]
[ATTACH=CONFIG]262663[/ATTACH]

I can force it to work for a while wiith a disconnect/reconnect, but that's not really a workable solution.

---

### Post by roma24ster on 2015-11-19
I have the same problem, did you ever fix it?

Also, the hybrid driver link above no longer works, does anyone know where the new link is now?

---

### Post by Maciek_Jedynak on 2016-03-16
I downloaded the Broadcomm driver from [here]("http://www.broadcom.com/support/802.11"). But it seems to be really crappy, I always get a few percent of packet loss during ping tests and user experience is very low due to frequent timeouts. 
Also somehow it gets much worse further from the router, although the signal strength drops only slightly. On the top of that, I don't see any errors in kernel logs. I don't know what to do with this card, perhaps indeed replacement is the way to go.

---

