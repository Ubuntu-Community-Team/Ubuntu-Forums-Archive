---
title: "wlan0 oddity - works 13.10, fails 14.04"
date: 2014-05-15
forum: Networking &amp; Wireless
---

### Post by reh2 on 2014-05-15
have a laptop with Intel centrino advanced-n 6235. while it was running 13.10 (64bit), had zero problems connecting to a particular AP (Netgear) using wpa2 personal. Did upgrade to 14.04 lts and lost the ability to connect to just this AP (out of four we use here). this one gets us offsite and is used for troubleshooting issues. Also of note, i have an att router at home that uses wpa2 personal and have no problems connecting with 14.04.

Wiped the laptop and did a fresh install of 14.04 lts but the problem persists. On a hunch, i booted with 13.10 live cd and was able to connect to the AP with no problems. Booting on the 14.04 live cd brings the problem back. I've read that kernel changes could be responsible for this issue. 

I've tried disabling n mode, extending time out value but no luck. dmesg shows three associate attempts back to back and then a timed out message. Again, this is only in 14.04. Haven't tried other distributions on this laptop just yet. Kernel version is 3.13.0-24-generic #47-Ubuntu SMP dated 05/02/2014. 

To make this more fun, we don't have access to the access point...it's Comcast I think...so I can't modify the thing. 

I don't doubt that there is some characteristic of the router that is causing this. Are there commands to "probe" features of the access point to try and pinpoint what the issue is? 

Thanks for any information.

---

### Post by reh2 on 2014-05-16
The router is a Netgear WGT624. 

Works with ubuntu 13.10, Fedora 20 live (kernel 3.11.10) on the same laptop.

---

### Post by smss on 2014-05-16
Please paste the output of these commands here:
```

lspci | grep Network
lshw
ifconfig
iwlist $YOUR_DRIVER_NAME scan | grep ESSID

```
Note that you have to change "$YOUR_DRIVER_NAME" with your wireless driver name.( you can get it from "ifconfig", ok? )

---

### Post by reh2 on 2014-05-16
just tried it from the 14.04 live on a different laptop with a Qualcom Atheros AR9285 wireless card with the same results. 13.10 works find on this 2nd laptop also. I will post the command output when I can get my hands on the original laptop. 
Appreciate it.

---

### Post by varunendra on 2014-05-17
A detailed diagnostics report can be created by 'wireless_script' suggested in this post : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

### Post by reh2 on 2014-05-19
Here's partial information. Notice in the DMESG output it authenticates okay and the fails to associate. Note the ifconfig output is while connected to another AP (cisco). I have to fall back to 13.10 to facilitate connecting to this AP since it's needed. Appreciate your replies.

02:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6235 [8086:088e] (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    Kernel driver in use: iwlwifi


wlan0     IEEE 802.11abg  ESSID:"guest"  
          Mode:Managed  Frequency:5.18 GHz  Access Point: 00:21:D8:93:31:1C   
          Bit Rate=6 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-70 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


[ 2763.757419] wlan0: send auth to 00:0f:b5:e9:65:e0 (try 1/3)
[ 2763.766228] wlan0: authenticated
[ 2763.766440] iwlwifi 0000:02:00.0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 2763.766447] iwlwifi 0000:02:00.0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 2763.766453] wlan0: waiting for beacon from 00:0f:b5:e9:65:e0
[ 2763.864570] wlan0: associate with 00:0f:b5:e9:65:e0 (try 1/3)
[ 2763.972637] wlan0: associate with 00:0f:b5:e9:65:e0 (try 2/3)
[ 2764.080729] wlan0: associate with 00:0f:b5:e9:65:e0 (try 3/3)
[ 2764.188860] wlan0: association with 00:0f:b5:e9:65:e0 timed out

---

### Post by smss on 2014-05-19
Please use of CODE tag in your posts.
You have to find the name of your wireless card, which doesn't matter whats the version of ubuntu or linux. So, with these code you should be able to find it:
```

lspci | grep Wireless
lshw

```
The search it in google, Most common drivers for installing is : linux-backports
Also you can install windows drivers( if you have those ) with : ndiswrapper
To install ndiswrapper type this code interminal : 
```

$ sudo apt-get install ndisgtk

```
ndisgtk mannual:
```

NDISGTK(8)           Ndiswrapper driver installation tool           NDISGTK(8)

NAME
       ndisgtk - load Windows wireless drivers with ndiswrapper

SYNOPSIS
       ndisgtk

DESCRIPTION
       ndisgtk  is  a  program  for installing Windows wireless drivers from a
       graphical user interface.

OPTIONS
       ndisgtk has no options.

AUTHOR
       ndisgtk was written by Sam Pohlenz  <retrix@internode.on.net>.   It  is
       now developed by Julian Andres Klode <jak@jak-linux.org>

       This manual page was written by Julian Andres Klode <jak@jak-linux.org>
       based on and older  ndisgtk  manpage  by  Sam  Pohlenz  <retrix@intern&#8208;
       ode.on.net>.

0.7                               2007-05-13                        NDISGTK(8)

```

---

### Post by varunendra on 2014-05-20
> **smss said:**
> Please use of CODE tag in your posts.+1
> **smss said:**
> Also you can install windows drivers( if you have those ) with : ndiswrapper
I appreciate your interest in troubleshooting the problem, BUT ndiswrapper is and should always be the Last Resort, when no native Linux drivers are available. The OP has an Intel card and a suitable driver - iwlwifi is already present and loaded for it -
> **reh2 said:**
> 02:00.0 Network controller [0280]: **Intel Corporation Centrino Advanced-N 6235 [8086:088e]** (rev 24)
    Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN [8086:4060]
    **Kernel driver in use: [COLOR="#0000CD"]iwlwifi[/COLOR]**
ndiswrapper would only play the role of an added problem here, requiring us to revert back before being able to fix anything else. A friendly advice for you, considering you a learner (hopefully, an interested one) - There is no justification for passing misinformation, so please be careful and do some research before suggesting fixes/workarounds to others.


**@reh2,**
The driver/firmware combination for some of the Intel cards in Ubuntu 14.04 is being frequently reported to be problematic. I am not much active on the forums these days, so can't suggest a sure-shot fix, but there certainly are fixes for the problem. I wanted to see the script report just to be sure that everything else is as it should be.

**PS:**
In case you post back and nobody replies to your post in time, please PM chili555 to take a look at your problem. His knowledge and experience with Intel cards is more than the combined experience of all of us other wifi troubleshooters.

---

### Post by manuelortiz480 on 2014-05-26
I have a similar problem.  Upgraded from 12.04 to 14.04.  I am able to connect to other access points but not the WGT624.  The upgrade left kernel version 3.2.0-61 in the GRUB list.  If I select 3.2.0-61 I can connect to the WGT624 but I can't with the latest kernel. I can't remember the version and since then I have restored 12.04 from  backup.

Also, if I boot from the 14.04 live cd I can't connect.

Any thoughts ?

I can try upgrading again if any log files would be helpful.

---

### Post by varunendra on 2014-05-26
Welcome to the forums manuelortiz480 !

Please post the report of 'wireless_script' as asked in post #5. It may give us hints on the problem. You can run it from a live session of Ubuntu 14.04.

---

### Post by manuelortiz480 on 2014-05-26
Here you go:

```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ubuntu 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz
Memory : 5768 MB
Uptime : 17:52:45 up 32 min,  9 users,  load average: 0.17, 0.14, 0.14


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0570]
    Kernel driver in use: bcma-pci-bridge
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:2aa7]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 005: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 004: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:217d Broadcom Corp. HP Bluethunder
Bus 001 Device 004: ID 04ca:0055 Lite-On Technology Corp. 
Bus 001 Device 003: ID 04f2:b1e7 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface        Soft blocked  Hard blocked
0: hci0: Bluetooth         no            no
1: phy0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
b43                   387371  0 
mac80211              626489  2 b43,brcmsmac
cfg80211              484040  3 b43,brcmsmac,mac80211
ssb                    62379  1 b43
bcma                   52096  3 b43,brcmsmac


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connecting
================o=============o==========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver   | State        | Default | Speed     | Support      | HW Addr   
================o=============o==========o==============o=========o===========o==============o===========
 eth0           | Wired       | r8169    | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+----------+--------------+---------+-----------+--------------+-----------
 wlan0  [chuy]  | 802.11 WiFi | brcmsmac | connecting (configuring)| no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    Bortizzz:        Infra, <MAC C-02 Bortizzz>, Freq 2412 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    linksys:         Infra, <MAC C-01 linksys>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    CenturyLink7977: Infra, <MAC C-NA CenturyLink7977 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 34 WPA WPA2
    Samsung Galaxy Note3 6772: Infra, <MAC C-NA Samsung Galaxy Note3 6772 1>, Freq 2437 MHz, Rate 54 Mb/s, Strength 25 WPA2
    lapdog:          Infra, <MAC C-NA lapdog 1>, Freq 2462 MHz, Rate 54 Mb/s, Strength 51 WPA2
    chuy:            Infra, <MAC C-03 chuy>, Freq 2437 MHz, Rate 54 Mb/s, Strength 69 WPA WPA2
----------------+-------------+----------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

chuy                 : ssid=chuy | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     13 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 13 (2.472 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 linksys>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000a4ac61ed82
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Bortizzz>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"Bortizzz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000063ec56ad09
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 chuy>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"chuy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000031fbf5ee23
                    Extra: Last beacon: 12ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[brcmsmac]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
firmware:       brcm/bcm43xx_hdr-0.fw
firmware:       brcm/bcm43xx-0.fw
srcversion:     43D6897F7EB716081DF69BE
depends:        bcma,mac80211,brcmutil,cfg80211,cordic

[cordic]
filename:       /lib/modules/3.13.0-24-generic/kernel/lib/cordic.ko
srcversion:     810E6E73D80DD7F75AC5B42
depends:        

[brcmutil]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko
srcversion:     E81EE4CBB6A7A689150D93D
depends:        

[b43]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     BED87D210887FFC71A4BDE0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        

[bcma]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4357 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

file=/cdrom/preseed/ubuntu.seed boot=casper cdrom-detect/try-usb=true persistent noprompt floppy.allowed_drive_mask=0 ignore_uuid initrd=/casper/initrd.lz quiet splash --


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.587074] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.587379] audit: initializing netlink socket (disabled)
[    3.722004] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   24.043403] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   24.102427] bcma: bus0: Found chip with id 0xA8D9, rev 0x01 and package 0x08
[   24.102451] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[   24.102470] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[   24.102506] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[   24.120703] bcma: bus0: Bus registered
[   24.541504] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   24.541511] b43: probe of bcma0:0 failed with error -524
[   24.655365] brcmsmac bcma0:0: mfg 4bf core 812 rev 23 class 0 irq 16
[   24.675486] ieee80211 phy0: registered radio enabled led device: brcmsmac-phy0:radio gpio: 241
[   25.139605] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   25.139617] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   25.140631] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.141008] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  102.959261] wlan0: authenticate with <MAC C-03 chuy>
[  102.962660] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  102.964171] wlan0: authenticated
[  102.964434] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  102.964442] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  102.966669] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  103.070755] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  103.174789] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  103.278884] wlan0: association with <MAC C-03 chuy> timed out
[  103.999972] wlan0: authenticate with <MAC C-03 chuy>
[  104.001202] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  104.002773] wlan0: authenticated
[  104.002995] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  104.003003] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  104.003272] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  104.107391] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  104.211475] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  104.315515] wlan0: association with <MAC C-03 chuy> timed out
[  105.436886] wlan0: authenticate with <MAC C-03 chuy>
[  105.437996] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  105.439474] wlan0: authenticated
[  105.439689] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  105.439697] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  105.440150] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  105.544165] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  105.648325] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  105.760386] wlan0: association with <MAC C-03 chuy> timed out
[  107.386522] wlan0: authenticate with <MAC C-03 chuy>
[  107.387336] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  107.388864] wlan0: authenticated
[  107.389063] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  107.389070] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  107.389338] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  107.493455] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  107.597518] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  107.701572] wlan0: association with <MAC C-03 chuy> timed out
[  118.961032] wlan0: authenticate with <MAC C-03 chuy>
[  118.962653] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  118.964496] wlan0: authenticated
[  118.964719] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  118.964726] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  118.968411] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  119.072512] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  119.180571] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  119.284637] wlan0: association with <MAC C-03 chuy> timed out
[  188.819860] wlan0: authenticate with <MAC C-03 chuy>
[  188.820841] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  188.822423] wlan0: authenticated
[  188.822617] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  188.822623] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  188.822940] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  188.931051] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  189.035074] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  189.139104] wlan0: association with <MAC C-03 chuy> timed out
[  199.774179] wlan0: authenticate with <MAC C-03 chuy>
[  199.775806] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  199.777275] wlan0: authenticated
[  199.777463] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  199.777471] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  199.777611] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  199.881725] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  199.985794] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  200.101827] wlan0: association with <MAC C-03 chuy> timed out
[  218.433468] wlan0: authenticate with <MAC C-03 chuy>
[  218.435182] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  218.445407] wlan0: authenticated
[  218.445607] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  218.445612] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  218.449024] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  218.553064] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  218.657087] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  218.761228] wlan0: association with <MAC C-03 chuy> timed out
[  229.400302] wlan0: authenticate with <MAC C-03 chuy>
[  229.401899] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  229.403403] wlan0: authenticated
[  229.403670] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  229.403678] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  229.407657] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  229.511730] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  229.615805] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  229.719928] wlan0: association with <MAC C-03 chuy> timed out
[  356.517708] wlan0: authenticate with <MAC C-NA lapdog 1>
[  356.521013] wlan0: send auth to <MAC C-NA lapdog 1> (try 1/3)
[  356.522800] wlan0: authenticated
[  356.525103] wlan0: associate with <MAC C-NA lapdog 1> (try 1/3)
[  356.529016] wlan0: RX AssocResp from <MAC C-NA lapdog 1> (capab=0x411 status=0 aid=1)
[  356.529639] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  356.529650] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  356.529666] wlan0: associated
[  356.529680] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  359.228874] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  543.373651] wlan0: deauthenticated from <MAC C-NA lapdog 1> (Reason: 1)
[  543.387125] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[  543.387137] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[  543.387140] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[  544.320078] wlan0: authenticate with <MAC C-NA lapdog 1>
[  544.321703] wlan0: send auth to <MAC C-NA lapdog 1> (try 1/3)
[  544.339610] wlan0: send auth to <MAC C-NA lapdog 1> (try 2/3)
[  544.432437] wlan0: send auth to <MAC C-NA lapdog 1> (try 3/3)
[  544.508863] wlan0: authentication with <MAC C-NA lapdog 1> timed out
[  551.686181] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  555.453625] wlan0: authenticate with <MAC C-03 chuy>
[  555.455483] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  555.456927] wlan0: authenticated
[  555.457059] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  555.457067] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  555.458263] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  555.562365] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  555.666483] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  555.770543] wlan0: association with <MAC C-03 chuy> timed out
[  557.608425] wlan0: authenticate with <MAC C-03 chuy>
[  557.609493] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  557.610986] wlan0: authenticated
[  557.611186] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  557.611193] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  557.611620] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  557.715762] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  557.819799] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  557.923800] wlan0: association with <MAC C-03 chuy> timed out
[  569.611628] wlan0: authenticate with <MAC C-03 chuy>
[  569.612824] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  569.614328] wlan0: authenticated
[  569.614519] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  569.614527] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  569.614930] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  569.719011] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  569.823110] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  569.927166] wlan0: association with <MAC C-03 chuy> timed out
[  585.655627] wlan0: authenticate with <MAC C-03 chuy>
[  585.655703] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  585.657130] wlan0: authenticated
[  585.657236] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  585.657238] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  585.660778] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  585.764788] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  585.876804] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  585.980916] wlan0: association with <MAC C-03 chuy> timed out
[  596.844780] wlan0: authenticate with <MAC C-03 chuy>
[  596.845534] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  596.847018] wlan0: authenticated
[  596.847219] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  596.847225] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  596.847584] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  596.951632] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  597.055696] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  597.159662] wlan0: association with <MAC C-03 chuy> timed out
[  644.269165] wlan0: authenticate with <MAC C-03 chuy>
[  644.269262] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  644.270709] wlan0: authenticated
[  644.270870] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  644.270873] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  644.272387] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  644.376488] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  644.480532] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  644.588684] wlan0: association with <MAC C-03 chuy> timed out
[  655.444003] wlan0: authenticate with <MAC C-03 chuy>
[  655.445138] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[  655.448323] wlan0: authenticated
[  655.448541] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[  655.448549] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[  655.451266] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[  655.555327] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[  655.659346] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[  655.763490] wlan0: association with <MAC C-03 chuy> timed out
[  677.393442] wlan0: authenticate with <MAC C-NA lapdog 1>
[  677.397131] wlan0: send auth to <MAC C-NA lapdog 1> (try 1/3)
[  677.398946] wlan0: authenticated
[  677.400561] wlan0: associate with <MAC C-NA lapdog 1> (try 1/3)
[  677.404483] wlan0: RX AssocResp from <MAC C-NA lapdog 1> (capab=0x411 status=0 aid=1)
[  677.405088] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  677.405097] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  677.405107] wlan0: associated
[  677.405158] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  677.479924] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1649.716303] wlan0: deauthenticated from <MAC C-NA lapdog 1> (Reason: 1)
[ 1649.728650] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 1649.728661] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: 1 addresses (implement)
[ 1649.728665] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 1650.661607] wlan0: authenticate with <MAC C-NA lapdog 1>
[ 1650.663353] wlan0: send auth to <MAC C-NA lapdog 1> (try 1/3)
[ 1650.702806] wlan0: send auth to <MAC C-NA lapdog 1> (try 2/3)
[ 1650.777536] wlan0: send auth to <MAC C-NA lapdog 1> (try 3/3)
[ 1650.857735] wlan0: authentication with <MAC C-NA lapdog 1> timed out
[ 1657.112068] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1662.209562] wlan0: authenticate with <MAC C-03 chuy>
[ 1662.211377] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[ 1662.212794] wlan0: authenticated
[ 1662.212911] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1662.212914] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1662.216005] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[ 1662.320052] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[ 1662.424134] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[ 1662.532259] wlan0: association with <MAC C-03 chuy> timed out
[ 1664.370055] wlan0: authenticate with <MAC C-03 chuy>
[ 1664.371657] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[ 1664.374237] wlan0: authenticated
[ 1664.374513] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1664.374520] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1664.377380] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[ 1664.481482] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[ 1664.585543] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[ 1664.689536] wlan0: association with <MAC C-03 chuy> timed out
[ 1676.377948] wlan0: authenticate with <MAC C-03 chuy>
[ 1676.378654] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[ 1676.387602] wlan0: authenticated
[ 1676.387894] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1676.387903] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1676.388655] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[ 1676.492766] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[ 1676.600749] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[ 1676.704832] wlan0: association with <MAC C-03 chuy> timed out
[ 1690.639920] wlan0: authenticate with <MAC C-03 chuy>
[ 1690.640029] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[ 1690.642394] wlan0: authenticated
[ 1690.642620] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1690.642622] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1690.645379] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[ 1690.749481] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[ 1690.853486] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[ 1690.957575] wlan0: association with <MAC C-03 chuy> timed out
[ 1701.808820] wlan0: authenticate with <MAC C-03 chuy>
[ 1701.809987] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[ 1701.811626] wlan0: authenticated
[ 1701.811842] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1701.811850] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1701.812145] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[ 1701.916262] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[ 1702.020316] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[ 1702.124360] wlan0: association with <MAC C-03 chuy> timed out
[ 1959.469743] wlan0: authenticate with <MAC C-03 chuy>
[ 1959.470957] wlan0: send auth to <MAC C-03 chuy> (try 1/3)
[ 1959.472441] wlan0: authenticated
[ 1959.472684] brcmsmac bcma0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[ 1959.472692] brcmsmac bcma0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[ 1959.473116] wlan0: associate with <MAC C-03 chuy> (try 1/3)
[ 1959.581235] wlan0: associate with <MAC C-03 chuy> (try 2/3)
[ 1959.689237] wlan0: associate with <MAC C-03 chuy> (try 3/3)
[ 1959.793322] wlan0: association with <MAC C-03 chuy> timed out

    ======== Done ========

```

---

### Post by varunendra on 2014-05-27
> **manuelortiz480 said:**
> ```
01:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n **[14e4:4357]** (rev 01)
....
....
lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[COLOR="#FF0000"]brcmsmac[/COLOR]              563041  0 
cordic                 12574  1 [COLOR="#FF0000"]brcmsmac[/COLOR]
brcmutil               15618  1 [COLOR="#FF0000"]brcmsmac[/COLOR]
[COLOR="#0000CD"]b43[/COLOR]                   387371  0 
mac80211              626489  2 [COLOR="#0000CD"]b43[/COLOR],[COLOR="#FF0000"]brcmsmac[/COLOR]
cfg80211              484040  3 [COLOR="#0000CD"]b43[/COLOR],[COLOR="#FF0000"]brcmsmac[/COLOR],mac80211
ssb                    62379  1 b43
bcma                   52096  3 [COLOR="#0000CD"]b43[/COLOR],[COLOR="#FF0000"]brcmsmac[/COLOR]

```
The drivers "b43" and "brcmsmac" highlighted above are in conflict with each other. Both support your card, but only one should claim it at a given time.

So here's what we can try -

[INDENT]**1)** Try "brcmsmac" first, since everything it needs is already available in the default installation. To let it work without conflicts, we need to prevent b43 from loading. If you are doing it on a Live session, we can do this only temporarily, since everything will be reset to defaults on a Live session. So.. Open a terminal (Ctrl-Alt-T) and run the following commands in it -
```
sudo modprobe -rv b43 ssb brcmsmac
sudo modprobe -v brcmsmac
```

Then check -
```
lsmod | egrep 'b43|ssb'
```
You should see only brcmsmac (and some other supporting drivers), and no "b43" or "ssb" in the output. If so, can you connect to the AP in question now? Does wifi work nicely? If yes, stop here, post back your report and I'll post how to make this permanent. If not, try the next solution -

**2)** Try "b43" instead. But the "b43" driver needs a proprietary firmware that has to be installed manually. So if you can connect to internet via cable or other means, simply run the following command in a terminal -
```
sudo apt-get install linux-firmware-nonfree
```
If you can't connect to internet and need to install the above package offline, follow steps 1, 2 of this post : [http://ubuntuforums.org/showpost.php?p=13026042](http://ubuntuforums.org/showpost.php?p=13026042)

Once the firmware is installed, run the following commands in a terminal -
```
sudo modprobe -rv b43 ssb brcmsmac
sudo modprobe -v b43
```
Does it make things better? If yes, let me know to make it permanent. If not, there is yet another possible solution - the proprietary 'STA' (aka "wl") driver, but I'll leave it out for now, hoping one of the above would work.[/INDENT]

---

### Post by manuelortiz480 on 2014-05-27
Here are my results

```

ubuntu@ubuntu:~$ sudo modprobe -rv b43 ssb brcmsmac
rmmod b43
rmmod ssb
rmmod brcmsmac
rmmod mac80211
rmmod bcma
rmmod brcmutil
rmmod cordic
ubuntu@ubuntu:~$ sudo modprobe -v brcmsmac
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/lib/cordic.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko
ubuntu@ubuntu:~$ lsmod | egrep 'b43|ssb'
b43                   387371  0 
ssb                    62379  1 b43
bcma                   52096  3 b43,brcmsmac
mac80211              626489  2 b43,brcmsmac
cfg80211              484040  4 b43,brcmsmac,mac80211,rndis_wlan
ubuntu@ubuntu:~$ 

```

You can see b43 and ssb are still there and it will not connect.  Not even to my phone's WIFI access point which did work before I executed the commands.

As I continue
```

ubuntu@ubuntu:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ sudo modprobe -rv b43 ssb brcmsmac
rmmod b43
rmmod ssb
rmmod brcmsmac
rmmod mac80211
rmmod bcma
rmmod brcmutil
rmmod cordic
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ sudo modprobe -v b43
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lsmod | egrep 'b43|ssb'
b43                   387371  0 
bcma                   52096  3 b43,brcmsmac
mac80211              626489  2 b43,brcmsmac
ssb                    62379  1 b43
cfg80211              484040  4 b43,brcmsmac,mac80211,rndis_wlan
ubuntu@ubuntu:~$ 

```

Neither scenario allows me to connect.  Not even to my phone's wifi hot spot.

---

### Post by varunendra on 2014-05-27
..And neither scenario gets rid of the driver(s) we intend to remove. Were the 'lsmod..' output from the same session or after a reboot? Because this is weird, if they are from the same session.

In an installed instance of Ubuntu, we can certainly prevent the offending drivers from loading, but in a Live session, the commands I suggested are the only way unless it is a "Persistent" Live USB where changes can be retained on next boot.

---

### Post by manuelortiz480 on 2014-05-27
The lsmod output was from the same session. I did not reboot.  Yes, this was from a Live USB stick.  I will try it later today from a DVD.

---

### Post by manuelortiz480 on 2014-05-27
This time I booted from a live DVD.  It reacted exactly the same.
```

ubuntu@ubuntu:~$ sudo modprobe -rv b43 ssb brcmsmac
rmmod b43
rmmod ssb
rmmod brcmsmac
rmmod mac80211
rmmod bcma
rmmod brcmutil
rmmod cordic
ubuntu@ubuntu:~$ sudo modprobe -v brcmsmac
insmod /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmutil/brcmutil.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/lib/cordic.ko 
insmod /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/brcm80211/brcmsmac/brcmsmac.ko 
ubuntu@ubuntu:~$ 
ubuntu@ubuntu:~$ lsmod | egrep 'b43|ssb'
b43                   387371  0 
ssb                    62379  1 b43
bcma                   52096  3 b43,brcmsmac
mac80211              626489  2 b43,brcmsmac
cfg80211              484040  4 b43,brcmsmac,mac80211,rndis_wlan
ubuntu@ubuntu:~$ 

```

You can see that b43 is still there.  It must be loaded by brcmsmac?  So I tried it a little differently.

```

ubuntu@ubuntu:~$ sudo modprobe -rv b43 ssb
rmmod b43
rmmod ssb
ubuntu@ubuntu:~$ lsmod | egrep 'b43|ssb'
ubuntu@ubuntu:~$ lsmod | egrep brc
brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
bcma                   52096  2 brcmsmac
mac80211              626489  1 brcmsmac
cfg80211              484040  3 brcmsmac,mac80211,rndis_wlan

```

I still could not connect.

The second scenario gave me the same results.  I even tried ...
```

ubuntu@ubuntu:~$ sudo modprobe -rv brcmsmac
rmmod brcmsmac
rmmod brcmutil
rmmod cordic
ubuntu@ubuntu:~$ 

ubuntu@ubuntu:~$ lsmod | egrep b43
b43                   387371  0 
bcma                   52096  1 b43
mac80211              626489  1 b43
ssb                    62379  1 b43
cfg80211              484040  3 b43,mac80211,rndis_wlan
ubuntu@ubuntu:~$ 

```

When I removed brcmsmac I lost all wireless networking.

I am able to connect to other access points just not the WGT624.  If I reboot back to 12.04 everything works fine.

---

### Post by varunendra on 2014-05-28
If your Live USB is 'Persistent' (can retain changes across reboot), we can try the same thing that we'd try on a permanently installed instance of Ubuntu. If unsure, just create some bland file or directory on the Desktop > Reboot > see if the file/directory is still there. If it is, the USB is persistent and we are good to go.

To prevent "b43" and "ssb" from loading at startup, they can be blacklisted with the following command -
```
echo -e "blacklist b43\nblacklist ssb" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
On next boot, check -
```
lsmod | egrep 'b43|ssb|brcm'
```
You should see only brcmsmac.

This is different than what you tried to get rid of b43, since brcmsmac won't have any conflicts from the beginning when the drivers load. In your approach (remove only b43, ssb, leave brcmsmac), there is a possibility for the brcmsmac to remain in a confused/failed state, needing to be reloaded (what I was trying).

By the way, it is really weird that b43 is loading while trying brcmsmac alone.

If this doesn't work, we'll try removing "b43" and "ssb" from blacklist, and add "brcmsmac" to it instead. But as mentioned earlier, the firmware would also need to be installed for b43 to work, unless you have already done that on the persistent live usb.

---

### Post by manuelortiz480 on 2014-05-30
Again, let me make myself clear.  My WIFI works fine except that I can't connect to a WGT624 router.  I can connect just fine to other access points. I will give your latest idea a try tomorrow.

---

### Post by manuelortiz480 on 2014-06-01
Blacklisted b43 then rebooted.  lsmod returned:
```
ubuntu@ubuntu:~$ lsmod | egrep 'b43|ssb|brcm'
brcmsmac              563041  0 
cordic                 12574  1 brcmsmac
brcmutil               15618  1 brcmsmac
mac80211              626489  1 brcmsmac
cfg80211              484040  2 brcmsmac,mac80211
bcma                   52096  2 brcmsmac
ubuntu@ubuntu:~$ 

```

Still unable to connect to the WGT624, but I can connect to other access points.

I will blacklist brcmcmac now

---

### Post by manuelortiz480 on 2014-06-01
I un-blacklisted b43 and ssb and then blacklisted brcmsmac.  When I rebooted and look at lsmod I get 

```

ubuntu@ubuntu:~$ lsmod | egrep 'b43|ssb|brcm'
b43                   387371  0 
mac80211              626489  1 b43
ssb                    62379  1 b43
cfg80211              484040  3 b43,mac80211,rndis_wlan
bcma                   52096  1 b43
ubuntu@ubuntu:~$ 

```

but the is no wireless networking.  None.  When I click on the network manager dropdown there is no option for wireless networking and no access points listed.

---

### Post by varunendra on 2014-06-01
> **manuelortiz480 said:**
> I un-blacklisted b43 and ssb and then blacklisted brcmsmac....
....but the is no wireless networking.  None.  When I click on the network manager dropdown there is no option for wireless networking and no access points listed.
Did you install the firmware correctly? It didn't install as per your last attempt we have seen here -
> **manuelortiz480 said:**
> ```
ubuntu@ubuntu:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: **[COLOR="#FF0000"]Unable to locate package linux-firmware-nonfree[/COLOR]**

```

..which means either you were not connected to internet, or the software cache was not updated. The package can be installed with above method only when you are connected to internet. So please connect to internet via Ethernet cable or other means, then try again -
```
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
```
The 'b43' driver will work only when the firmware is installed correctly.

If you can't connect to internet at all, please manually download the firmware package from this link : [http://packages.ubuntu.com/trusty/all/linux-firmware-nonfree/download](http://packages.ubuntu.com/trusty/all/linux-firmware-nonfree/download)

Copy the downloaded file onto your Desktop, then open a terminal, and run the following commands to manually install it -
```
cd Desktop
sudo dpkg -i linux-firmware*.deb
```
Reboot, and try the b43 driver again.

---

### Post by WinEunuchs2Unix on 2014-06-02
I found Intel's Microcode Data File (google it) upgrade for Debian Linux Kernel > 3.1 most helpful in Ubuntu 14.04 (besides the CPU's and ICH8 chipset's microcode had not be updated in 7 years).  An Intel update for the GME965 chipset in Vista 32 blew my mind a few weeks ago with Clear View technology.  I would apply the Intel Microcode update as Intel is really playing professionally in the Open Source arena.

I ran Varun's Wireless Script it's most ingenious.  However "iwlist channel" has a bug where wlan1 is reported as wlan2, wlan0 is reported as wlan1 and wlan2 is reported as wlan0.  The same bug appears in "iwlist frequency" which reports the same as "iwlist currency".  I tried "iwlist bitrate" and parameters where wlan0, wlan1 and wlan2 were all reported correctly.  I also tried iwconfig which was correct.  I looked for a place to report this bug but...

---

### Post by manuelortiz480 on 2014-06-02
I did sudo apt-get update then ....
```

ubuntu@ubuntu:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-firmware-nonfree
ubuntu@ubuntu:~$ 

```

Is there a repos I need to install to get it ?

Downloaded manual.  Coming back after reboot.

---

### Post by manuelortiz480 on 2014-06-02
Added the repos to sources.list, sudo apt-get update, rebooted.  Verified linux-firmware-nonfree is installed
```

ubuntu@ubuntu:~$ sudo apt-get install linux-firmware-nonfree
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-firmware-nonfree is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 197 not upgraded.
ubuntu@ubuntu:~$ 

```

rebooted, still no wireless networking.

---

### Post by varunendra on 2014-06-02
> **manuelortiz480 said:**
> Added the repos to sources.list, sudo apt-get update, rebooted.  Verified linux-firmware-nonfree is installed
...
rebooted, still no wireless networking.
Please post a fresh report of the wireless_script.

> **WinEunuchs2Unix said:**
> I ran Varun's Wireless Script it's most ingenious.  However "iwlist channel" has a bug where wlan1 is reported as wlan2, wlan0 is reported as wlan1 and wlan2 is reported as wlan0.  The same bug appears in "iwlist frequency" which reports the same as "iwlist currency".  I tried "iwlist bitrate" and parameters where wlan0, wlan1 and wlan2 were all reported correctly.  I also tried iwconfig which was correct.  I looked for a place to report this bug but...
Can you show us the report which shows the discrepancy/bug you mentioned above please?

By the way, the original author of the wireless_script is one of the forum moderators "Wild Man". I have only recently modified it a bit and that version is experimental so far (I have already noticed a few minor bugs, but not this one you mentioned). The 'experimental' version of the script has been mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

..and a sample of the report it generates is here : [http://ubuntuforums.org/showpost.php?p=13033804](http://ubuntuforums.org/showpost.php?p=13033804)

So if the report you are referring to looks different (style and sequence of sections), it means you have used the original script of Wild Man.

For reporting bug in the script, you can PM him, if using the original script, or PM me, if the bug is in the codes that I have added.

---

### Post by WinEunuchs2Unix on 2014-06-02
> **varunendra said:**
> Please post a fresh report of the wireless_script.


Can you show us the report which shows the discrepancy/bug you mentioned above please?

By the way, the original author of the wireless_script is one of the forum moderators "Wild Man". I have only recently modified it a bit and that version is experimental so far (I have already noticed a few minor bugs, but not this one you mentioned). The 'experimental' version of the script has been mentioned here : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

..and a sample of the report it generates is here : [http://ubuntuforums.org/showpost.php?p=13033804](http://ubuntuforums.org/showpost.php?p=13033804)

So if the report you are referring to looks different (style and sequence of sections), it means you have used the original script of Wild Man.

For reporting bug in the script, you can PM him, if using the original script, or PM me, if the bug is in the codes that I have added.

The script calls a Kernel command "iwlist" passing the parameter "channel".  It is the command "iwlist" which has the bug not Wild man's script.  The same bug appears when you use the parameter "frequency" instead of "channel".  When I looked both parameters seem to have identical output.  Other parameters such as "bitrate" worked fine and wlan0, wlan1 and wlan2 were all reported correctly.

After work today I stumbled across the right forum for posting Ubuntu/Debian/Linux/Unix bugs.  It really doesn't bug me that much just pointing it out for those that review "iwlist" output when the "channel" parameter or "frequency" parameter is used when more than one wifi adapters are attached.

---

### Post by WinEunuchs2Unix on 2014-06-02
Script output from last night's wireless script is attached. :popcorn:

---

### Post by manuelortiz480 on 2014-06-03
Here is the output of wireless_script with brcmsmac blacklisted
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ubuntu 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz
Memory : 5768 MB
Uptime : 07:51:45 up 9 min,  8 users,  load average: 5.28, 4.64, 2.37


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0570]
    Kernel driver in use: bcma-pci-bridge
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:2aa7]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 006: ID 0bb4:0ffe HTC (High Tech Computer Corp.) Desire HD (modem mode)
Bus 002 Device 005: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 004: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:217d Broadcom Corp. HP Bluethunder
Bus 001 Device 004: ID 04ca:0055 Lite-On Technology Corp. 
Bus 001 Device 003: ID 04f2:b1e7 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface     Soft blocked  Hard blocked
0: hci0: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

b43                   387371  0 
mac80211              626489  1 b43
rndis_wlan             50281  0 
rndis_host             14503  1 rndis_wlan
usbnet                 43877  3 rndis_host,rndis_wlan,cdc_ether
ssb                    62379  1 b43
cfg80211              484040  3 b43,mac80211,rndis_wlan
bcma                   52096  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500
rndis_wlan    (8): afterburner=0 | country=EU | frameburst=1 | power_output=3 | power_save=0 | roamdelta=1 | roamtrigger=-70 | workaround_interval=0


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: connected (global)
============================o=======o============o==============o=========o===========o==============o===========
 Interface & ID             | Type  | Driver     | State        | Default | Speed     | Support      | HW Addr   
============================o=======o============o==============o=========o===========o==============o===========
 usb0  [Wired connection 2] | Wired | rndis_host | connected    | yes     |           |              | <MAC ID removed>

    Address:         192.168.42.192
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.42.129
    DNS:             192.168.42.129
----------------------------+-------+------------+--------------+---------+-----------+--------------+-----------
 eth0                       | Wired | r8169      | unavailable  | no      |           |              | <MAC eth0>
----------------------------+-------+------------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

chuy                 : ssid=chuy | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~

nameserver 127.0.1.1


Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.42.129  0.0.0.0         UG    0      0        0 usb0
192.168.42.0    0.0.0.0         255.255.255.0   U     1      0        0 usb0

--- 192.168.42.129 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 1001ms
rtt min/avg/max/mdev = 1.631/1.650/1.670/0.045 ms

--- 127.0.1.1 ping statistics ---
2 packets transmitted, 2 received, 0% packet loss, time 999ms
rtt min/avg/max/mdev = 0.022/0.022/0.023/0.004 ms


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist brcmsmac


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[b43]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     BED87D210887FFC71A4BDE0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[rndis_wlan]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/rndis_wlan.ko
srcversion:     A7CD7CEAA3F9E7A58B7FBAB
depends:        usbnet,rndis_host,cfg80211
parm:           country:Country code (ISO 3166-1 alpha-2), default: EU (string)
parm:           frameburst:enable frame bursting (default: on) (int)
parm:           afterburner:enable afterburner aka '125 High Speed Mode' (default: off) (int)
parm:           power_save:set power save mode: 0=off, 1=on, 2=fast (default: off) (int)
parm:           power_output:set power output: 0=25%, 1=50%, 2=75%, 3=100% (default: 100%) (int)
parm:           roamtrigger:set roaming dBm trigger: -80=optimize for distance, -60=bandwidth (default: -70) (int)
parm:           roamdelta:set roaming tendency: 0=aggressive, 1=moderate, 2=conservative (default: moderate) (int)
parm:           workaround_interval:set stall workaround interval in msecs (0=disabled) (default: 0) (int)

[rndis_host]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/usb/rndis_host.ko
srcversion:     5500F047782325557430406
depends:        usbnet,cdc_ether

[usbnet]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/usb/usbnet.ko
srcversion:     FBB0307A56163715BCACCFA
depends:        mii
parm:           msg_level:Override default message level (int)

[ssb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[bcma]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4357 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.557517] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.557825] audit: initializing netlink socket (disabled)
[    3.699740] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   38.066209] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   38.117820] bcma: bus0: Found chip with id 0xA8D9, rev 0x01 and package 0x08
[   38.117849] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[   38.117867] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[   38.117902] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[   38.136080] bcma: bus0: Bus registered
[   41.313528] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   41.313536] b43: probe of bcma0:0 failed with error -524

    ======== Done ========

```

---

### Post by varunendra on 2014-06-03
Could you try it without plugging in the USB adapter? Keep it unplugged, reboot, and try the native PCI adapter once more with "b43" driver. If it still fails to connect, the last shot is the proprietary driver "wl". To try the proprietary driver, run the following command in a terminal, while being connected to internet -
```
sudo apt-get install bcmwl-kernel-source
```
..followed by a reboot. This driver will blacklist both b43 and brcmsmac, along with their supporting drivers. On next boot, you would see only "wl" in the lsmod instead of b43, brcmsmac or their supporting drivers.

Probably there is not much left to try beyond this.

---

### Post by manuelortiz480 on 2014-06-03
Here is the wireless-info.txt with the USB adapter disconnected
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ubuntu 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz
Memory : 5768 MB
Uptime : 08:50:57 up 7 min,  8 users,  load average: 1.23, 1.81, 1.00


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0570]
    Kernel driver in use: bcma-pci-bridge
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:2aa7]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 005: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 004: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:217d Broadcom Corp. HP Bluethunder
Bus 001 Device 004: ID 04ca:0055 Lite-On Technology Corp. 
Bus 001 Device 003: ID 04f2:b1e7 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~



rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface     Soft blocked  Hard blocked
0: hci0: Bluetooth      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

b43                   387371  0 
mac80211              626489  1 b43
cfg80211              484040  2 b43,mac80211
ssb                    62379  1 b43
bcma                   52096  1 b43


module parameters ~~~~~~~~~~~~~~~~~~

b43          (10): allhwsupport=0 | bad_frames_preempt=0 | btcoex=1 | hwpctl=0 | hwtkip=0 | nohwcrypt=0 | pio=0 | qos=1 | verbose=2
cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00
mac80211      (5): beacon_loss_count=7 | ieee80211_default_rc_algo=minstrel_ht | max_nullfunc_tries=2 | max_probe_tries=5 | probe_wait_ms=500


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=======o========o==============o=========o===========o==============o===========
 Interface & ID | Type  | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=======o========o==============o=========o===========o==============o===========
 eth0           | Wired | r8169  | unavailable  | no      |           |              | <MAC eth0>
----------------+-------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

chuy                 : ssid=chuy | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

           - 


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~



blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist brcmsmac


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[b43]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
srcversion:     BED87D210887FFC71A4BDE0
depends:        bcma,ssb,mac80211,cfg80211
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[mac80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/mac80211/mac80211.ko
srcversion:     C0F95BBF832E05DEFD722F4
depends:        cfg80211
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/ssb/ssb.ko
srcversion:     3DE188310F77C566C2E8CB3
depends:        

[bcma]
filename:       /lib/modules/3.13.0-24-generic/kernel/drivers/bcma/bcma.ko
srcversion:     E41B811D88783DD5BC38565
depends:        


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4357 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.555583] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.555889] audit: initializing netlink socket (disabled)
[    3.691453] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   35.119885] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   35.141451] bcma: bus0: Found chip with id 0xA8D9, rev 0x01 and package 0x08
[   35.141476] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x22, class 0x0)
[   35.141520] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x17, class 0x0)
[   35.141699] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x0F, class 0x0)
[   35.157413] bcma: bus0: Bus registered
[   38.776504] Support for cores revisions 0x17 and 0x18 disabled by module param allhwsupport=0. Try b43.allhwsupport=1
[   38.776512] b43: probe of bcma0:0 failed with error -524

    ======== Done ========

```

Here it is after installing the proprietary 'wl' driver (after reboot)
```


    ======== Wireless-Info START ========

System-Info ~~~~~~~~~~~~~~~~~~~~~~~~

ubuntu 3.13.0-24-generic x86_64,  Ubuntu 14.04 LTS, trusty

CPU    : Intel(R) Core(TM) i5 CPU         650  @ 3.20GHz
Memory : 5768 MB
Uptime : 09:25:43 up 10 min,  8 users,  load average: 0.51, 1.00, 0.83


lspci ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

01:00.0 Network controller [0280]: Broadcom Corporation BCM43225 802.11b/g/n [14e4:4357] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0570]
    Kernel driver in use: wl
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Hewlett-Packard Company Device [103c:2aa7]
    Kernel driver in use: r8169


lsusb ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Bus 002 Device 005: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive
Bus 002 Device 004: ID 413c:2105 Dell Computer Corp. Model L100 Keyboard
Bus 002 Device 003: ID 0461:4d22 Primax Electronics, Ltd 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 005: ID 0a5c:217d Broadcom Corp. HP Bluethunder
Bus 001 Device 004: ID 04ca:0055 Lite-On Technology Corp. 
Bus 001 Device 003: ID 04f2:b1e7 Chicony Electronics Co., Ltd 
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


PCMCIA Card Info ~~~~~~~~~~~~~~~~~~~



iwconfig ~~~~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          


rfkill ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

      Interface            Soft blocked  Hard blocked
0: hci0: Bluetooth             no            no
1: phy0: Wireless LAN          no            no
2: brcmwl-0: Wireless LAN      no            no


lsmod ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

wl                   4207846  0 
lib80211               14381  2 wl,lib80211_crypt_tkip
cfg80211              484040  1 wl


module parameters ~~~~~~~~~~~~~~~~~~

cfg80211      (2): cfg80211_disable_40mhz_24ghz=N | ieee80211_regdom=00


nm-tool ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

State: disconnected
================o=============o========o==============o=========o===========o==============o===========
 Interface & ID | Type        | Driver | State        | Default | Speed     | Support      | HW Addr   
================o=============o========o==============o=========o===========o==============o===========
 eth0           | Wired       | r8169  | unavailable  | no      |           |              | <MAC eth0>
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------
 wlan0          | 802.11 WiFi | wl     | disconnected | no      |           | WEP/WPA/WPA2 | <MAC wlan0>

    linksys:         Infra, <MAC C-03 linksys>, Freq 2437 MHz, Rate 54 Mb/s, Strength 42 WPA WPA2
    Bortizzz:        Infra, <MAC C-02 Bortizzz>, Freq 2412 MHz, Rate 54 Mb/s, Strength 39 WPA WPA2
    chuy:            Infra, <MAC C-01 chuy>, Freq 2437 MHz, Rate 54 Mb/s, Strength 79 WPA WPA2
----------------+-------------+--------+--------------+---------+-----------+--------------+-----------


NetworkManager.state ~~~~~~~~~~~~~~~
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true


NetworkManager.conf ~~~~~~~~~~~~~~~~

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false


NM WiFi Profiles ~~~~~~~~~~~~~~~~~~~

chuy                 : ssid=chuy | mac-address=<MAC wlan0> | ipv4=auto | ipv6=auto 


interfaces ~~~~~~~~~~~~~~~~~~~~~~~~~

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

resolv.conf ~~~~~~~~~~~~~~~~~~~~~~~~



Routes & Ping ~~~~~~~~~~~~~~~~~~~~~~

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


iw reg get ~~~~~~~~~~~~~~~~~~~~~~~~~

(Region : "en_US.UTF-8")
country 00:
    (2402 - 2472 @ 40), (3, 20)
    (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
    (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
    (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS


iwlist chan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     32 channels in total; available frequencies :
          Channel 01 (2.412 GHz) - 14 (2.484 GHz)
          Channel 32 (5.16 GHz)
          Channel 34 (5.17 GHz)
          Channel 36 (5.18 GHz)
          Channel 38 (5.19 GHz)
          Channel 40 (5.2 GHz)
          Channel 42 (5.21 GHz)
          Channel 44 (5.22 GHz)
          Channel 46 (5.23 GHz)
          Channel 48 (5.24 GHz)
          Channel 50 (5.25 GHz)
          Channel 52 (5.26 GHz)
          Channel 54 (5.27 GHz)
          Channel 56 (5.28 GHz)
          Channel 58 (5.29 GHz)
          Channel 60 (5.3 GHz)
          Channel 62 (5.31 GHz)
          Channel 64 (5.32 GHz)
          Channel 66 (5.33 GHz) - 14 (2.484 GHz)


iwlist scan ~~~~~~~~~~~~~~~~~~~~~~~~

wlan0     Scan completed :
          Cell 01 - Address: <MAC C-01 chuy>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:on
                    ESSID:"chuy"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              12 Mb/s; 24 Mb/s; 36 Mb/s
                    Bit Rates:9 Mb/s; 18 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                       Preauthentication Supported
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC C-02 Bortizzz>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=32/70  Signal level=-78 dBm  
                    Encryption key:on
                    ESSID:"Bortizzz"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC C-03 linksys>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=35/70  Signal level=-75 dBm  
                    Encryption key:on
                    ESSID:"linksys"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 4ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK


blacklist ~~~~~~~~~~~~~~~~~~~~~~~~~~

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist-bcm43.conf]
blacklist b43
blacklist b43legacy
blacklist ssb
blacklist brcm80211
blacklist brcmfmac
blacklist brcmsmac
blacklist bcma

[/etc/modprobe.d/blacklist.conf]
blacklist brcmsmac


modinfo ~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[wl]
filename:       /lib/modules/3.13.0-24-generic/updates/dkms/wl.ko
srcversion:     FF25FE784DC6BDFF69DAFCB
depends:        cfg80211,lib80211
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[lib80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/lib80211.ko
srcversion:     84DEF767F03D28E373F18E5
depends:        

[cfg80211]
filename:       /lib/modules/3.13.0-24-generic/kernel/net/wireless/cfg80211.ko
srcversion:     8B3D642D1F2E6406EF33F74
depends:        
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


udev rules ~~~~~~~~~~~~~~~~~~~~~~~~~

# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC eth0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"

# PCI device 0x14e4:0x4357 (brcmsmac)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC wlan0>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"


Custom files/entries ~~~~~~~~~~~~~~~

/etc/modules        : Default
/etc/rc.local       : Default
/etc/modprobe.d     : Not Default
/etc/pm/(cnf|pw|sl) : Default

[/etc/modprobe.d]
iwlwifi.conf      : remove iwlwifi \
                    (/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
                    && /sbin/modprobe -r mac80211
mlx4.conf         : softdep mlx4_core post: mlx4_en


Kernel boot line ~~~~~~~~~~~~~~~~~~~

noprompt cdrom-detect/try-usb=true persistent file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash -- maybe-ubiquity


dmesg ~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

[    3.548793] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    3.549100] audit: initializing netlink socket (disabled)
[    3.686897] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   40.379611] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   47.858497] wl: module license 'MIXED/Proprietary' taints kernel.
[   47.860949] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   47.899532] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   47.952115] wlan0: Broadcom BCM4357 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[  608.089674] ERROR @wl_dev_intvar_get : error (-1)
[  608.089682] ERROR @wl_cfg80211_get_tx_power : error (-1)

    ======== Done ========

```

I still can't connect to the WGT624 but I can to other access points.

I see some lines in syslog about secrets, don't know if that helps.
```

Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) starting connection 'chuy'
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> (wlan0): device state change: disconnected -> prepare (reason 'none') [30 40 0]
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> NetworkManager state is now CONNECTING
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0/wireless): access point 'chuy' has security, but secrets are required.
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> (wlan0): device state change: need-auth -> prepare (reason 'none') [60 40 0]
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> (wlan0): device state change: prepare -> config (reason 'none') [40 50 0]
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0/wireless): connection 'chuy' has security, and secrets exist.  No new secrets needed.
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Config: added 'ssid' value 'chuy'
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Config: added 'scan_ssid' value '1'
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Config: added 'key_mgmt' value 'WPA-PSK'
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Config: added 'auth_alg' value 'OPEN'
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Config: added 'psk' value '<omitted>'
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> Config: set interface ap_scan to 1
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> (wlan0): supplicant interface state: inactive -> scanning
Jun  3 09:24:30 ubuntu wpa_supplicant[3387]: message repeated 6 times: [ wlan0: CTRL-EVENT-SCAN-STARTED ]
Jun  3 09:24:30 ubuntu wpa_supplicant[3387]: wlan0: Trying to associate with 00:14:6c:3d:21:84 (SSID='chuy' freq=2437 MHz)
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> (wlan0): supplicant interface state: scanning -> associating
Jun  3 09:24:30 ubuntu wpa_supplicant[3387]: wlan0: CTRL-EVENT-ASSOC-REJECT status_code=16
Jun  3 09:24:30 ubuntu wpa_supplicant[3387]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="chuy" auth_failures=1 duration=10
Jun  3 09:24:30 ubuntu NetworkManager[3072]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  3 09:24:40 ubuntu wpa_supplicant[3387]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun  3 09:24:40 ubuntu NetworkManager[3072]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  3 09:24:41 ubuntu wpa_supplicant[3387]: wlan0: CTRL-EVENT-SSID-REENABLED id=0 ssid="chuy"
Jun  3 09:24:41 ubuntu wpa_supplicant[3387]: wlan0: Trying to associate with 00:14:6c:3d:21:84 (SSID='chuy' freq=2437 MHz)
Jun  3 09:24:41 ubuntu NetworkManager[3072]: <info> (wlan0): supplicant interface state: scanning -> associating
Jun  3 09:24:41 ubuntu wpa_supplicant[3387]: wlan0: CTRL-EVENT-ASSOC-REJECT status_code=16
Jun  3 09:24:41 ubuntu wpa_supplicant[3387]: wlan0: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="chuy" auth_failures=2 duration=20
Jun  3 09:24:41 ubuntu NetworkManager[3072]: <info> (wlan0): supplicant interface state: associating -> disconnected
Jun  3 09:24:51 ubuntu wpa_supplicant[3387]: wlan0: CTRL-EVENT-SCAN-STARTED 
Jun  3 09:24:51 ubuntu NetworkManager[3072]: <info> (wlan0): supplicant interface state: disconnected -> scanning
Jun  3 09:24:54 ubuntu NetworkManager[3072]: <warn> Activation (wlan0/wireless): association took too long.
Jun  3 09:24:54 ubuntu NetworkManager[3072]: <info> (wlan0): device state change: config -> need-auth (reason 'none') [50 60 0]
Jun  3 09:24:54 ubuntu NetworkManager[3072]: <warn> Activation (wlan0/wireless): asking for new secrets
Jun  3 09:24:54 ubuntu NetworkManager[3072]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun  3 09:24:54 ubuntu NetworkManager[3072]: <warn> Couldn't disconnect supplicant interface: This interface is not connected.
Jun  3 09:24:56 ubuntu NetworkManager[3072]: <info> (wlan0): supplicant interface state: scanning -> inactive
Jun  3 09:24:57 ubuntu NetworkManager[3072]: <warn> No agents were available for this request.
Jun  3 09:24:57 ubuntu NetworkManager[3072]: <info> (wlan0): device state change: need-auth -> failed (reason 'no-secrets') [60 120 7]
Jun  3 09:24:57 ubuntu NetworkManager[3072]: <info> NetworkManager state is now DISCONNECTED
Jun  3 09:24:57 ubuntu NetworkManager[3072]: <info> Marking connection 'chuy' invalid.
Jun  3 09:24:57 ubuntu NetworkManager[3072]: <warn> Activation (wlan0) failed for connection 'chuy'
Jun  3 09:24:57 ubuntu NetworkManager[3072]: <info> (wlan0): device state change: failed -> disconnected (reason 'none') [120 30 0]
Jun  3 09:24:57 ubuntu NetworkManager[3072]: <info> (wlan0): deactivating device (reason 'none') [0]

```

---

### Post by WinEunuchs2Unix on 2014-06-03
Well ok this thread is rather muddy. 

reh2 cannot connect to his WGT624 router with his intel 6235 wifi or his Atheros AR9285 wifi.  Presumably he can connect to other routers though.

manuelortiz480 cannot connect to his WGT624 router with his broadcom wifi but he can connect to 3 or 4 other routers (aka access points or AP's).
manuelortiz480 cannot download "linux-nonfree" but I was able to download it two nights ago.  It primarily contains audio and video processing technology that is illegal in some countries and I assume manuel resides in one of those countries (his profile doesn't list a nation).

Varun suggests reh2 scraps his native linux intel driver and use an ndiswrapper driver generated off a windows driver in order to connect to the WGT624. reh2 wants to vomit on this idea.

Varun suggests manueloftiz480 remove the b43 driver through all kinds of boot from CD or USB for kernel persistency.  But since manuel can connect to the net through other routers he can get drivers on line anyway?

OK the problem appears to be the WGT624 router.  Doing a quick check it was introduced in 2004 and it's a 108 Mbps firewalled router (although under Linux Kernel 3.13 there are warnings about user name/password security holes).  There are actually four versions of this router and the current firmware versions found at [http://support.netgear.com/product/WGT624V1#wrapper](http://support.netgear.com/product/WGT624V1#wrapper) are:

WGT624v1: # 4.2.11
WGT624v2: # 4.2.11
WGT624v3: # 2.0.26_1.01 (North America only)
WGT624v4: # 2.0.13_2.0.15

If manuel has version 3 of the router and doesn't live in North America (as I suspect) then he won't be able to get the most current router firmware upgrade.

To recap all indicators are a problem with the NetGear WGT624v(?) router and it would have been helpful to know what router version(s) the two gentlemen were using and what firmware versions within the router version they were using.  

- WE2U ([[COLOR=#000000]WinEunuchs2Unix[/COLOR]]("http://ubuntuforums.org/member.php?u=1925810")[COLOR=#000000] )[/COLOR]

PS - Netgear should give her head a shake for having four different routers (see the pictures @ website) with the same model number followed by a version suffix.

---

### Post by manuelortiz480 on 2014-06-04
I agree that there is somekind of incompatibility with the WGT624.  I do have the v3 and it is at 2.0.26_1.01.

I think my solution is that Fry's electronics has a router on sale for $14.  I'll give that a try.

Thanks

---

### Post by varunendra on 2014-06-04
I think WinEunuchs2Unix already added some info that maybe the most useful info at this point. Just wanted to clarify/correct two points of his post -
> **WinEunuchs2Unix said:**
> ....manuelortiz480 cannot download "**linux-nonfree**" but I was able to download it two nights ago.  **[COLOR="#FF0000"]It primarily contains audio and video processing technology that is illegal in some countries[/COLOR]** and I assume manuel resides in one of those countries (his profile doesn't list a nation).
Not super-sure about the audio/video device firmware files, but the one we want from the "linux-firmware-nonfree" package (the broadcom wifi card firmware) is **definitely not illegal for 'ANY' user across the world** to download and use for their personal use. It is only a problem for the distributors ('Canonical' in our case, who develop and distribute 'Ubuntu' OS) to distribute the firmware with their OS (Ubuntu) due to Licencing restrictions. **But it is entirely free and legal for a user** to download and use it. I *believe* the same or similar is the case with all the other firmware files included in that package, but I don't have any authentic sources to support my assumption about those other contents.

> **WinEunuchs2Unix said:**
> **[COLOR="#FF0000"]Varun suggests reh2 scraps his native linux intel driver and use an ndiswrapper[/COLOR]** driver generated off a windows driver in order to connect to the WGT624. reh2 wants to vomit on this idea.
Eh? 'Varun' (me :p) 'Never' advocates ndiswrapper! You certainly confused me with 'smss'. Please read post #8 again.. :)

**@manuelortiz480,**
I too agree that the router/AP may the culprit, but right now I am seeing at least one more problem that can be easily removed. In your router, the encryption type is WPA/WPA2 mixed mode with **[COLOR="#FF0000"]TKIP[/COLOR]**. Please change it to pure **WPA2-PSK** with **AES (CCMP)**. No mixed mode, no TKIP. Reboot the router after saving the change. If this doesn't solve the problem, go ahead with your different router plan.

---

### Post by manuelortiz480 on 2014-06-05
I tried WPA-PSK with AES before I started posting here.  It didn't make a difference.

Purchased a cheapy $14 router from Fry's (On Networks N300R)  Reset the changes I had made as far as blacklisting the drivers.  Set up the router encryption the same as the old router and I was able to connect to it the first time with no problems.

So as far as I can tell there appears to be a comptability problem with 14.04 and the WGT624.  I also tried 14.04 on a gateway laptop with an atheros (?) wifi chip and it could't authenticate with the WGT624 either.

I don't think it's a driver issue I think it's some other problem with the authentication.  But I have no idea how to prove this.

So for now I will be using the new N300R.

If there is anything else you would like me to try with the WGT624 let me know and I'll hook it back up.

Manuel

---

### Post by WinEunuchs2Unix on 2014-06-05
> **varunendra said:**
> I think WinEunuchs2Unix already added some info that maybe the most useful info at this point. Just wanted to clarify/correct two points of his post -

Not super-sure about the audio/video device firmware files, but the one we want from the "linux-firmware-nonfree" package (the broadcom wifi card firmware) is **definitely not illegal for 'ANY' user across the world** to download and use for their personal use. It is only a problem for the distributors ('Canonical' in our case, who develop and distribute 'Ubuntu' OS) to distribute the firmware with their OS (Ubuntu) due to Licencing restrictions. **But it is entirely free and legal for a user** to download and use it. I *believe* the same or similar is the case with all the other firmware files included in that package, but I don't have any authentic sources to support my assumption about those other contents.


Eh? 'Varun' (me :p) 'Never' advocates ndiswrapper! You certainly confused me with 'smss'. Please read post #8 again.. :)


I probably mislead myself on "nonfree" because I thought I read something about "your conscience" and "in your country" or something like that.  I just get this weird feeling google (or someone) is playing big brother and blocking stuff all around the world for Hollywood... In any case there is a reason why he couldn't download "nonfree" and I could???

Sorry about the ndiswrapper false allegation :D  I notice you post extensively throughout the wireless forum and bend over backwards to help everyone out with determination that I could never live up to.  Please keep up the great volunteering!

---

### Post by chili555 on 2014-06-05
> In any case there is a reason why he couldn't download "nonfree" and I could???It's hard to tell; perhaps the repository was off-line for a while. > (the broadcom wifi card firmware) is definitely not illegal for 'ANY' user across the world to download and use for their personal use. It is only a problem for the distributors ('Canonical' in our case, who develop and distribute 'Ubuntu' OS) to distribute the firmware with their OS (Ubuntu) due to Licencing restrictions. Quite correct. Broadcom won't allow their firmware to be examined, changed, redistributed freely, etc. That's their right and their choice. But that means it's not GPLed* open source and can't be provided with Ubuntu on the iso/DVD/USB. 

Once the operating system is installed, it's yours to do with as you please. If you want to change the desktop wallpaper to a picture of your cat, feel free. If you want to amend some /etc file to meet your particular needs, go right ahead. If you want to install non-free firmware, have at it. 

In this context, I believe 'nonfree' means not free and open source. It does not mean not free to be used in some jurisdictions.

*[https://en.wikipedia.org/wiki/Gpl](https://en.wikipedia.org/wiki/Gpl)> The GNU General Public License (GNU GPL or GPL) is the most widely used free software license, which guarantees end users (individuals, organizations, companies) the freedoms to use, study, share (copy), and modify the software. Software that allows these rights is called free software 

---

### Post by reh2 on 2014-07-29
Well, since I started this thread, I'll "end" it. The Netgear device is not my property and I don't have access to it so I can't get firmware versions, etc. I completely understand that it's old and that eventually wouldn't be supported. I've been connecting to it at work to use in troubleshooting access issues using Ubuntu since 12.04 without problems and was just aghast that with 14.04 it was no longer possible, and was hoping that there was a modification that I could make to allow it to work. As is apparent by the heroic efforts on this thread, that's not possible.   

I ended up installing Fedora 20 on the laptop and "tweaked" gnome3 with extensions so that I could use it, rather than run an older version of Ubuntu.

Windows has spoiled me with backwards compatibility, as Win 8.1 on this laptop still works with this old Netgear.

So be it.

Thanks for all the useful information provided in this thread.

---

### Post by varunendra on 2014-07-29
Thanks for letting us know that Fedora works. It is always good to know that at least one Linux distro works - giving us hope that whatever the problem is - should be fixed in other too sooner or later.

Can you also confirm the kernel and driver versions being used in Fedora please? That would be the outputs of -
```
uname -mr
sudo lshw -C network
```

And if you have time and desire to make Ubuntu better, may I recommend to submit a bug report at launchpad, also mentioning that fedora on the same system works. If confirmed by enough users, it will attract the developers (they almost never look at forum posts) and the issue will hopefully be fixed via updates.

How to submit an effective bug report : [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs)

---

### Post by WinEunuchs2Unix on 2014-07-30
Since this thread started Ubuntu went from Kernel 3.13.0-24, 3.13.0-29, 3.13.0-30, 3.15.0, 3.15.1, 3.15.2, 3.15.3, 3.15.4, 3.15.5 and 3.15.6 on my machine.  Linux Kernel 3.15.7 is now out but for some strange reason Ubuntu didn't release an update within 24 hours like normal.

My point is each update fixes bugs.  I wonder if the Fedora version is more up-to-date than the Ubuntu version 3.13.0-24 or whatever was being used on May 14th, 2014.  Varun doesn't state this question but he alludes to it I think.

Also since this thread is "ending" I should confess to a boo-boo where I thought wlan0 and wlan1 were misreported in the wireless script.  They are not.  The inferior Intel 3945 abg (golan) really does have more frequencies than the modern Ralink and NetGear USB adapters.  FTR I'm now on wlan3 (Intel 6235) and hope to get wlan4 (Atheros) into the pipeline soon :D

---

### Post by reh2 on 2014-08-05
I think that OpenSuse 13 was also able to connect on this laptop. As I said, Ubuntu 14.04 also failed on a completely different laptop trying to connect to the same AP. But, using 13.10 livecd connects fine. That laptop was using a Realtek controller I believe. I've also tried other dist flavors that are based on 14.04 LTS and they all fail. I even downloaded the recent 14.04.1 the other day...same issue. Maybe a driver developer deleted one too many lines of code. ;-)

Uname -mr on Fedora 20 shows 3.15.6-200.fc20.x86_64 x86_64. lshw command not found. Here's output of lspci if that helps:

Network controller: Intel Corporation Centrino Advanced-N 6235 (rev 24)
	Subsystem: Intel Corporation Centrino Advanced-N 6235 AGN
	Flags: bus master, fast devsel, latency 0, IRQ 48
	Memory at 62600000 (64-bit, non-prefetchable) [size=8K]
	Capabilities: [c8] Power Management version 3
	Capabilities: [d0] MSI: Enable+ Count=1/1 Maskable- 64bit+
	Capabilities: [e0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting
	Capabilities: [140] Device Serial Number b4-b6-76-ff-ff-25-32-30
	Kernel driver in use: iwlwifi
	Kernel modules: iwlwifi

Thanks

---

### Post by WinEunuchs2Unix on 2014-08-05
When I first started with Ubuntu it was Kernel 3.13.0-24 or something like that.  The last couple of months I've been on Kernel version 3.15.x.  Like yourself today under Fedora I was on 3.15.6 two weeks ago but still running Ubuntu 14.04.  3.15 Kernel upgrades have been coming out every week so now I'm on 3.15.8.

There have been many bug fixes under 3.15.x each week.  I have no idea if theses are included in 14.04.1 which I burned to DVD last weekend but have not yet tried out.

It would be interesting to see if you can boot Ubuntu 14.04, install the Kernel 3.15.8 update over it and see if your problems get fixed.  

That said I had to yank out my recent Intel 6235 purchase from the laptop and put back the old Intel 3945 from 7 years ago.  My beefs with the 6235 are unrelated to your problems as I could connect to the internet at great speeds and reliability.  I've ordered a fifth Wifi Adapter with a RTL3072 chipset, 1 Amp amplifier, and two 5 dBi antenna's to try out now (fingers crossed).

---

