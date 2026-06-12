---
title: "new install of 14.04, hp laptop, Wireless can't seem to see correct network"
date: 2016-04-16
forum: Networking &amp; Wireless
---

### Post by Hachi-Roku on 2016-04-16
Hello world! 

I'm having some wireless issues after installing Ubuntu Studio 14.04 on my new HP laptop. 

**Problem: ** Wireless adapter can't seem to see or connect to my network. This is where it gets weird... it seems to see my neighbors' wlan, but when i try to connect to that i get: "(32) Connection could not be found."

**Solutions tried:** Tried manually via the gui to put in a 'hidden network' using all the wifi credentials, when I do that it just hangs while trying to connect and then just fails.

I had wifi issues on my last laptop install (about 8 years ago!!) I don't think the wireless script was around then... **big props** to who put it together!!! A great tool!

I've researched and tried several bit and pieces from the forums without success. _So now i need some help_... here's the output from the wireless script;
As far as i can tell i have the driver and it seems to be loaded in lsmod... am i doubling up with a conflicting driver somewhere?? 

Any help appreciated!

```

########## wireless info START ##########

Report from: 16 Apr 2016 15:53 BST +0100

Booted last: 16 Apr 2016 14:10 BST +0100

Script from: 27 Sep 2015 00:34 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.4 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 4.2.0-35-lowlatency #40~14.04.1-Ubuntu SMP PREEMPT Fri Mar 18 17:28:07 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu Studio

##### lspci #############################

01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 15)
	Subsystem: Hewlett-Packard Company Device [103c:8135]
	Kernel driver in use: r8169

02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter [10ec:b723]
	Subsystem: Hewlett-Packard Company Device [103c:804c]
	Kernel driver in use: rtl8723be

##### lsusb #############################

Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 003: ID 0c45:651b Microdia 
Bus 001 Device 002: ID 0bda:b006 Realtek Semiconductor Corp. 
Bus 001 Device 004: ID 046d:c01a Logitech, Inc. M-BQ85 Optical Wheel Mouse
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: yes
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

hp_wmi                 16384  0 
sparse_keymap          16384  1 hp_wmi
rtl8723be              86016  0 
btcoexist              53248  1 rtl8723be
rtl8723_common         24576  1 rtl8723be
rtl_pci                28672  1 rtl8723be
rtlwifi                77824  2 rtl_pci,rtl8723be
mac80211              753664  3 rtl_pci,rtlwifi,rtl8723be
cfg80211              561152  2 mac80211,rtlwifi
wmi                    20480  1 hp_wmi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:80674 errors:0 dropped:0 overruns:0 frame:0
          TX packets:27643 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:109882112 (109.8 MB)  TX bytes:2350170 (2.3 MB)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 eth0
192.168.0.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

	NetworkManager

Running:

root       731     1  0 14:10 ?        00:00:01 NetworkManager

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8723be
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
    virginmedia4414622: Infra, <MAC 'virginmedia4414622' [AC1]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 24 WPA WPA2

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             connected
  Default:           yes
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes
    Speed:           1000 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.168.0.6
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             194.168.4.100
    DNS:             194.168.8.100

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
[802-11-wireless] ssid=virginmedia6152371
[ipv4] method=auto
[ipv6] method=ignore

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country 00:
	(2402 - 2472 @ 40), (3, 20)
	(2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
	(5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
	(5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
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

##### iwlist scan #######################

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'virginmedia4414622' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"virginmedia4414622"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=00000079ae6288ec
                    Extra: Last beacon: 15ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8723be]
filename:       /lib/modules/4.2.0-35-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8723be/rtl8723be.ko
firmware:       rtlwifi/rtl8723befw.bin
description:    Realtek 8723BE 802.11n PCI wireless
license:        GPL
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         PageHe	<page_he@realsil.com.cn>
srcversion:     0EB6BE33DFAD6AEFD4D63AE
depends:        rtlwifi,rtl8723-common,rtl_pci,btcoexist,mac80211
intree:         Y
vermagic:       4.2.0-35-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        14:88:F6:69:98:BE:F3:C3:7D:72:B8:3C:B7:F7:30:75:C9:F3:B3:44
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           msi:Set to 1 to use MSI interrupts mode (default 0)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)
parm:           disable_watchdog:Set to 1 to disable the watchdog (default 0)
 (bool)

[rtl8723_common]
filename:       /lib/modules/4.2.0-35-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl8723com/rtl8723-common.ko
description:    Realtek RTL8723AE/RTL8723BE 802.11n PCI wireless common routines
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
srcversion:     251C540A2D3AD38CCA85ED9
depends:        
intree:         Y
vermagic:       4.2.0-35-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        14:88:F6:69:98:BE:F3:C3:7D:72:B8:3C:B7:F7:30:75:C9:F3:B3:44
sig_hashalgo:   sha512

[rtl_pci]
filename:       /lib/modules/4.2.0-35-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     2E1C688267DE11E1F26A728
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.2.0-35-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        14:88:F6:69:98:BE:F3:C3:7D:72:B8:3C:B7:F7:30:75:C9:F3:B3:44
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.2.0-35-lowlatency/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     867B4080247A86ABBA59D17
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.2.0-35-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        14:88:F6:69:98:BE:F3:C3:7D:72:B8:3C:B7:F7:30:75:C9:F3:B3:44
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.2.0-35-lowlatency/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     1E79C1BE23A29358B904F24
depends:        cfg80211
intree:         Y
vermagic:       4.2.0-35-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        14:88:F6:69:98:BE:F3:C3:7D:72:B8:3C:B7:F7:30:75:C9:F3:B3:44
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.2.0-35-lowlatency/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     7982686FBE8064A87E02753
depends:        
intree:         Y
vermagic:       4.2.0-35-lowlatency SMP preempt mod_unload modversions 
signer:         Build time autogenerated kernel key
sig_key:        14:88:F6:69:98:BE:F3:C3:7D:72:B8:3C:B7:F7:30:75:C9:F3:B3:44
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8723be]
debug: 0
disable_watchdog: N
fwlps: Y
ips: Y
msi: N
swenc: N
swlps: N

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/osspd.conf]
blacklist snd-pcm-oss
blacklist snd-mixer-oss
blacklist snd-seq-oss

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0xb723 (rtl8723be)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

##### dmesg #############################

[    2.372045] r8169 0000:01:00.0 eth0: link down
[    2.372192] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.948391] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   95.656001] r8169 0000:01:00.0 eth0: link up
[   95.656011] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready

########## wireless info END ############
```

---

### Post by Hadaka on 2016-04-16
Hi please try this guide...*Note. The "rtl8723be ant_sel=2" is usually the best choice.
 [http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
Then open a terminal ctrl/alt/t Please copy and paste copy and paste..
```
sudo iw reg set GB
sudo sed -i 's/^REG.*=$/&GB/' /etc/default/crda
```
Next,access your router's internal configuration set up 
and remove the setting TKIP and chose WPA2 AES
Thanks.

---

### Post by Hachi-Roku on 2016-04-17
Thanks for the reply Hadaka :)

This seems to have half solved it. I went through the material suggested. Now i can see the available wireless networks  in the networking drop down menu. But it still hangs and then fails when i try to connect to a wlan.
Unfortunately I'm in a communal apartment block and don't have access to the routers' admin config.

I included the last command in Larrys' guide but still find i have to redo the modprobe command each time i boot.

What other diagnostics can I run/post to give better information?


Thanks!!
HR

---

### Post by Hadaka on 2016-04-17
Hi, If you copied and pasted every line from this guide..
[http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904](http://askubuntu.com/questions/717685/realtek-wifi-card-rtl8723be-not-working-properly/722904#722904)
your current load of rtl8723be should be correct as this is a recent ,tested and accurate guide.
to load your driver on start up or boot...please open a terminal and do..
```
echo "rtl8723be" | sudo tee -a /etc/modules
```
Next I suggest you go in and delete any entries to your access connection point.
click. the wifi icon > edit connections > wireless  then delete and re-add your connection.
Like the attached...
[ATTACH=CONFIG]268432[/ATTACH][ATTACH=CONFIG]268433[/ATTACH][ATTACH=CONFIG]268434[/ATTACH]
Boot and test wireless.

---

### Post by Hachi-Roku on 2016-04-17
Thanks for the reply.

I went back and re-did all the material from that link (great guide from Larry!). I noticed half way through the wireless started working. I carried on through the rest of the commands and then it stopped connecting and again just hanged if i tried to connect manually.
So i went back through the page for a third time and this time it started work after the sudo make install command, so I just stopped there and it seems to be working now. We'll see
 in the next few boots if it's connecting reliably now.

I'll post the outcome in a day or so.

---

### Post by Hachi-Roku on 2016-04-17
wrote too soon!
picked up my laptop, moved across the room... and the connection drops out and can't see the network anymore (note my phone is next to it and it connects, so its not a location problem).

I rebooted and it connected to the wlan, was slow then disconnected and disappeared from the network list.

Rebooted and a did the last section of commands. Now the network appears in the list, but just hangs when i try to connect.

any more ideas?

Thanks people!

---

### Post by Hadaka on 2016-04-17
Hi, to begin,,the driver rtl8723be is a larry finger dirver, but the guide
is from Ubuntu member Jermy31, and is accurate and correct.
If you are losing connection moving away from the router then one of 2 things
are  likely.
1. you did not load the rtl8723be driver correctly
2. you did not write the correct antenna selection command.

your phone may connect just fine, it has its own software, and is not linux.

here is your connection point, the signal Quality is very very weak, which means
the antenna select is not correct or the antenna connection on the card is not making
good contact.
```
wlan0     Scan completed :
          Cell 01 - Address: <MAC 'virginmedia4414622' [AC1]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=**[COLOR=#ff0000]28/70[/COLOR]**  Signal level=-82 dBm  
```
Please read carefully the guide for installing your driver and do again
also check your antenna connections on the router and if easily accesable
on the computer;s internal wifi card.
thanks.

---

### Post by Hachi-Roku on 2016-04-17
Even moving back to the same spot it doesn't work. My phone is not Linux, correct. My old laptop runs 10.04 and connects fine.
The weak signal in that snippet is my neighbours router.
Are the only options for antenna select numbers:1 & 2 ? I've tried both.

---

### Post by Hadaka on 2016-04-17
Let's see what might have changed, please post a fresh diagnostic report
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info 
```
thanks.

---

### Post by Hachi-Roku on 2016-04-21
Strangely... I booted up yesterday, wireless hanging and not connecting. Then after using the Ethernet cable for a while my wireless started working. I didn't change anything during this time.
I've since shut down and restarted many times over the last day (as i was skeptical it was robustly fixed) but it seems robust.
I don't really know what happened, but it's been working the last day quite well.
Thanks for the help

---

### Post by Hadaka on 2016-04-21
That great ! glad you got it working. Please mark your thread solved
by going to your first post of this thread,clicking Thread Tools and chooose Solved.
thanks,

---

### Post by jeremy31 on 2016-04-21
Larry Finger and his friends at Realtek do good work for us using Linux based OS.  The people at Realtek are working on code to make the ant_sel parameter automatic

---

### Post by Hachi-Roku on 2016-05-02
Thanks guys.
I left it for a while to see how robust it was over time. It seems to connect well. Sometimes there are speed issues. I also notice other problems of sites containing media (youtube/Udemy etc) don't work as soon as I've used Jack. But this would be a problem for another thread. I'll get back to this once I've noticed the proper pattern of occurrence etc.

Thanks for the help Hadaka!

---

### Post by Hachi-Roku on 2016-10-15
Just a quick post for the sake of anyone searching...

Lost all the wireless goodness that was done when I did the standard software update and again had nno wireless connections.

Something that helped was switching off the 5gHz band on my dual band router. I set it to 2.4 gHz only and it worked straight away.

---

