---
title: "Wifi constantly disconnects, network disappears - nm-applet memory leak?"
date: 2016-11-16
forum: Networking &amp; Wireless
---

### Post by Re4mRpR on 2016-11-16
Hey all, asus n76 machine, same issue over the last few years of using various editions of ubuntu.  Currently using 16.04.  On certain networks, unfortunately my home networks :/, my wifi connection is quite unstable, with the network vanishing, only to eventually reappear and connect.  Not an issue with my phone and network is on a different channel than my neighbors.

atheros 9k adapter, nm-applet stuff doesnt do anything, but it does have a memory leak (currently 600 megabytes of memory)

any ideas, thx

---

### Post by TheFu on 2016-11-16
I had an issue - different chips tho.  Got a Ubuquiti AP and the issue has gone away.  Plus got to put the AP centrally in the house, not where the router was convenient. Don't know if this is an option for you or not.  Not all wifi APs are created equal. Had issues with netgear, belkin and tp-link wifi APs.

BTW, being on a different channel isn't really enough. Need to be on a non-overlapping-channel. For 2.4Ghz devices that is 1, 6, or 11. All the others overlap with one of those channels.  In a dense wifi place (apartment/townhouse), there might not be any choice.

You can also try a different wifi manager like wicd instead of NM, but the issue is probably in a driver/driver-setting. That would be my guess.

Is this device running on battery? Could battery saving be enabled that turns off the wifi automatically?

---

### Post by Re4mRpR on 2016-11-16
I'm a subletter in a shared 2 floor apartment, so hte AP is kinda staying where it is, and what it is, unfortunately.  It has been thrown around to try to run another AP from it using a LAN extension.

We're on channel 2, 2.4Ghz.  There are about 40 networks that my wifi radar can find.  Most are on channels 1,6,11.  We used to be on one of those

As NM has a memory leak, I'm willing to look at wicd.  Although a laptop, I always have it plugged into mains power and actually have power saving features turned off.

---

### Post by wildmanne39 on 2016-11-16
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by TheFu on 2016-11-16
Just throwing out some ideas ... 

Wicd isn't without problems, but it is what I've used the last few years - actually **wicd-curses**.  I run a minimal GUI - no panel, no launcher. Last time I used NM, it was often confused by my non-standard networking. 

Sounds like a difficult location.  Wired isn't an option? Perhaps subsidized with powerline to get through the different levels?  Powerline can suck and the performance I see is about 10% of the advertised-on-the-box speeds (600Mbs on the box --> 40-60Mbps downstairs). Not all wiring works with it, but solid networking is important to me.  Wifi will always be flaky in a place like yours, I'm sorry to say. Actually, if you watch wifi bandwidth, it fluctuates all the time and computers see this and are impacted by it easily.

I suppose 5Ghz probably isn't an option. It doesn't like walls, but there are many more frequencies so the interference should be less.

To find the best channel (strength and location), you could use a wifi mapping tool to see what the weakest of channels 1, 6, 11 are where you work. I've seen them for a few OSes.  Use one on Android myself. Then pick an unused channel of the overlapping kind for that location. If you are sharing wifi with others in the apartment, finding the happy medium for all locations can be challenging.  A $90 [Ubiquiti AC AP]("https://www.amazon.com/dp/B015PR20GY/") will do wonders, however.

---

### Post by Re4mRpR on 2016-11-16
> **Wild Man said:**
> Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

i cut out the details of the other networks in the area.  Before seeing your reply, I also switched to wicd, which also disconnects

```


########## wireless info START ##########


Report from: 16 Nov 2016 20:45 CET +0100


Booted last: 16 Nov 2016 00:00 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave AR9485 Wireless Network Adapter [1a3b:2c97]
	Kernel driver in use: ath9k


04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)
	Subsystem: ASUSTeK Computer Inc. N56VZ [1043:1477]
	Kernel driver in use: alx


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 006: ID 13d3:3362 IMC Networks Atheros AR3012 Bluetooth 4.0 Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 004: ID 0582:0074 Roland Corp. EDIROL UA-25
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


0: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
4: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath3k                  20480  0
ath9k                 143360  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
mac80211              737280  1 ath9k
bluetooth             520192  30 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
asus_nb_wmi            24576  0
asus_wmi               28672  1 asus_nb_wmi
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


auto wlp3s0
iface wlp3s0 inet dhcp


iface wlp3s0 inet static
wireless-essid Underwater
wireless-key rosenkohlISThohl
address 192.168.2.101
netmask 255.255.255.0
gateway 192.168.2.1


##### ifconfig ##########################


enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.2.101  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp3s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:72141 errors:0 dropped:0 overruns:0 frame:0
          TX packets:45755 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:95850997 (95.8 MB)  TX bytes:5838203 (5.8 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp4s0    no wireless extensions.


wlp3s0    IEEE 802.11bgn  ESSID:"Underwater"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Underwater' [AC2]>   
          Bit Rate=135 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=24/70  Signal level=-86 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:109   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 wlp3s0
192.168.2.0     0.0.0.0         255.255.255.0   U     0      0        0 wlp3s0


##### resolv.conf #######################


nameserver 192.168.2.1
search Speedport_W_921V_1_39_000


##### network managers ##################


Installed:


	Wicd


Running:


	None found.


##### NetworkManager info ###############


NetworkManager is not installed (package "network-manager").


##### NetworkManager.state ##############


cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory


##### NetworkManager.conf ###############


grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory


##### NetworkManager profiles ###########


[[/etc/NetworkManager/system-connections/Underwater]] (600 root)
[connection] id=Underwater | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=Underwater
[ipv4] method=auto
[ipv6] method=auto


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 20), (N/A)
	(5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
	(5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp4s0    no frequency information.


wlp3s0    13 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp4s0    Interface doesn't support scanning.


Channel occupancy:


      7   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      5   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      5   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)


wlp3s0    Scan completed :
          
          Cell 02 - Address: <MAC 'Underwater' [AC2]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Underwater"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000008675103dd1
                    Extra: Last beacon: 52ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          
##### module infos ######################


[ath3k]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     2B85DCB887D9376A61652DD
depends:        bluetooth
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[ath9k]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1B84AD8C53440158CD581F2
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath9k_common]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     FA7ECFBA5761A5B3ED96BB2
depends:        ath
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 0
ps_enable: 0
use_chanctx: 0


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


##### modprobe options ##################


[/etc/modprobe.d/AR9485.conf]
options AR9485 fwlps=N


[/etc/modprobe.d/ath5k.conf]
options ath5k nohwcrypt=Y
options ath5k nohwcrypt=N
options ath5k nohwcrypt=Y


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


exit 0


##### pm-utils ##########################


[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="AR9485"


##### udev rules ########################


##### dmesg #############################


[ 2597.473324] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[ 2617.190751] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 2617.326856] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[ 2617.507249] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2619.658135] wlp3s0: authenticate with <MAC 'Underwater' [AC2]>
[ 2619.672545] wlp3s0: send auth to <MAC 'Underwater' [AC2]> (try 1/3)
[ 2619.674219] wlp3s0: authenticated
[ 2619.677553] wlp3s0: associate with <MAC 'Underwater' [AC2]> (try 1/3)
[ 2619.683442] wlp3s0: RX AssocResp from <MAC 'Underwater' [AC2]> (capab=0x431 status=0 aid=8)
[ 2619.683526] wlp3s0: associated
[ 2619.683569] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 2619.687093] ath: EEPROM regdomain: 0x8114
[ 2619.687097] ath: EEPROM indicates we should expect a country code
[ 2619.687098] ath: doing EEPROM country->regdmn map search
[ 2619.687100] ath: country maps to regdmn code: 0x37
[ 2619.687101] ath: Country alpha2 being used: DE
[ 2619.687103] ath: Regpair used: 0x37
[ 2619.687104] ath: regdomain 0x8114 dynamically updated by country IE
[ 2703.605169] wlp3s0: deauthenticating from <MAC 'Underwater' [AC2]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2703.642038] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2703.761667] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[ 2703.915331] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready (repeated 2 times)
[ 2708.912520] IPv6: ADDRCONF(NETDEV_UP): enp4s0: link is not ready
[ 2709.061172] IPv6: ADDRCONF(NETDEV_UP): wlp3s0: link is not ready
[ 2711.227559] wlp3s0: authenticate with <MAC 'Underwater' [AC2]>
[ 2711.241786] wlp3s0: send auth to <MAC 'Underwater' [AC2]> (try 1/3)
[ 2711.244238] wlp3s0: authenticated
[ 2711.247137] wlp3s0: associate with <MAC 'Underwater' [AC2]> (try 1/3)
[ 2711.254928] wlp3s0: RX AssocResp from <MAC 'Underwater' [AC2]> (capab=0x431 status=0 aid=8)
[ 2711.255023] wlp3s0: associated
[ 2711.255060] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[ 2711.258217] ath: EEPROM regdomain: 0x8114
[ 2711.258221] ath: EEPROM indicates we should expect a country code
[ 2711.258222] ath: doing EEPROM country->regdmn map search
[ 2711.258224] ath: country maps to regdmn code: 0x37
[ 2711.258225] ath: Country alpha2 being used: DE
[ 2711.258227] ath: Regpair used: 0x37
[ 2711.258228] ath: regdomain 0x8114 dynamically updated by country IE


########## wireless info END ############



```

---

### Post by TheFu on 2016-11-16
[https://ubuntuforums.org/showthread.php?t=2321894](https://ubuntuforums.org/showthread.php?t=2321894) says to disable HW encryption.
I searched on "Atheros AR9485 ubuntu" - lots of other results as well appear to say the same thing.

---

### Post by Hadaka on 2016-11-16
Hi, one possible reason you are having difficulties may be because of the current
configuration of your /etc/network/interfaces file. The way you have it is for a manual
management without using any network manager type configuration. You are currently
using "wcid" and it is managing your network. please copy and paste to allow wcid to
manage your network and remove the conflict,please do...
```
echo -e "auto lo\niface lo inet loopback" | sudo tee /etc/network/interfaces
```
You do not have a device that requires "ath5k" so let's remove that file to avoid possible conflict. 
```
sudo rm -rf /etc/modprobe.d/ath5k.conf
```
To further help with drop outs please do..
```
echo "options ath9k nohwcrypt=1" sudo tee -a /etc/modprobe.d/ath9k.conf
```
Finally edit your "Underwater" connection and set Ipv6 to  IGNORE...see attached
[ATTACH=CONFIG]272171[/ATTACH]

---

### Post by Re4mRpR on 2016-11-17
Ive tried the edits from #8, with the wifi still freezing.  In fact, wicd would still indicate that I am connected.  I just switched back to nm to see if there will be a difference.  at the very least, the system tray icon is standard.

Oh, and I never found any option in wicd to do anything about ipv6

---

### Post by TheFu on 2016-11-17
I blacklist ipv6, so don't care if anything supports it or not.
Wicd is older and may not have IPv6 support. I dunno.

I thought blacklisting ipv6 was a normal, 1st step, to troubleshooting ipv4 connection issues?  Could be wrong.  I blacklist it in the kernel module, not some GUI. Don't remember the exact steps, just know it is disabled here.

If I were switching between NM and WICD, I'd be removing all the programs whenever I swapped between them. Some things just seem to interfere with each other.

---

### Post by Hadaka on 2016-11-17
Hi,looking at your wireless diagnostic printout it indicates a weak signal received
from your computer to the router.
```
wlp3s0    IEEE 802.11bgn  ESSID:"Underwater"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Underwater' [AC2]>   
          Bit Rate=135 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=[COLOR=#ff0000]24/70[/COLOR]  Signal level=-86 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:109   Missed beacon:0
```
*If possible check your internal antenna/card connection and reseat the card as well.
be sure to power off and remove the battery prior,and to take care with the antenna wire.
then power down your router and check all connections and verify the antenna is free of
corrosion and making good contact. and of course remove any wired connection and usb's
you might also try changing wifi channel to 1,6,or11.
 Your report also indicates your wifi eprom chip does not have the correct country code.0x8117
the reports shows your country code location as,,,0x037 = DE ...Is this correct ?
```
##### iw reg get ########################
# Region: Europe/Berlin (based on set time zone)# DE    +5230+01322
# Europe/Berlin    Germany (most areas)
```
*IF country is Europe/Berlin DE then copy and paste.
```
sudo iw reg set DE
sudo cp /etc/default/crda /etc/default/crda.old
sudo sed -i '/^REGDOMAIN=/ d' /etc/default/crda
echo 'REGDOMAIN=DE' | sudo tee -a /etc/default/crda
```
To insure it loads at startup ..
```
sudo sed -i '/^exit/ d' /etc/rc.local
echo -e 'sudo iw reg set DE\nexit 0' | sudo tee -a /etc/rc.local
```
*BOOT remove any wired connection and usb's and test.
* you might also try selecting 80211 b/g and no N connection in the router.

---

### Post by TheFu on 2016-11-17
Link Quality=24/70 is a real issue.  Extremely low signal.  Look at my other posts for alternatives.

Is this issue just when at home?  If you go to a cafe with wifi, does it connect and work?

---

### Post by Re4mRpR on 2016-11-18
I've brought up the signal quality issue with my roommate before and he said that he went ahead and boosted the signal.  Looks like i need to hound him again.

I do live in Germany, so the country code is correct.  DEspite being a laptop, I never bring it outside much, and when I do, I don't have problems.  MY android phone doenst have the same connection issues, however.

---

### Post by TheFu on 2016-11-18
Increasing the signal isn't always useful. Sometimes it does more harm. It is about "S/N" not "power."  Doesn't hurt to try, but maybe the better answer is to work with the neighbors and see if they can turn theirs down just to cover their apartments? 

If the issue is only happening at home, it is an environmental issue. If it happens elsewhere too, then it is probably the laptop / antenna / chip. If it ever worked well, look for changes to the environment - like someone else nearby has their channel set to 1.  Try ch 8.  Really, you should look at the RF in the places you like to work and look for channels that don't have much traffic, then move your's over.  The clients don't need to be updated - this is a wifi AP thing, only.

The easy fix is to add an AP for downstairs wired back to the main router. See my link above for a link and suggested device. Even placing it in the stairs hanging on the wall halfway down would be amazing. You'll see.  BTW, the layout of the apartment, where the router-wifi is would all matter for a proper placement design.  If the router-wifi is in a corner upstairs (bldg corner, not just some room corner), then placing the other AP on the opposite side of the apartment downstairs would help.  I've done high-rise deployments this way - every other floor on opposite sides (center was unavailable) of the bldg.

Did you load up that wifi survey app on your phone? It is free.

---

### Post by Re4mRpR on 2016-11-19
We've talked about adding another AP or changing the channel.  The current AP is aimed as best as possible in my direction.  i dont have the hardware password and my roommate is a lil slow to act.

My connection is still disconnecting, and the wireless didnt load at all (not mine nor any of hte other networks visible) once after coming out of sleep, but the last registry tweak suggestions do seem to have stabilized things a bit.

yea, i have wifi scanner app for my phone.  i also have wifi radar and wireshark installed on my laptop.  channel 8 looks like a good candidate

---

### Post by Hadaka on 2016-11-19
Hi,I agree with the "Fu" about the low signal of 24/70
Hopefully you are able to find a way to a stronger signal.
Mean time let's look again and see if we can find anything that
may further help after you have made changes. Please post the output of..
```
cat /etc/rc.local
```
```
cat /sys/class/dmi/id/bios_date
cat /sys/class/dmi/id/power/runtime_suspended_time
```
and a fresh wireless diagnostic report.
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
Thanks.

---

### Post by Re4mRpR on 2016-11-20
[COLOR=#000000]cat /etc/rc.local

#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


sudo iw reg set DE
exit 0


cat /sys/class/dmi/id/bios_date
07/09/2013

cat /sys/class/dmi/id/power/runtime_suspended_time
0

```
[/COLOR]

########## wireless info START ##########


Report from: 20 Nov 2016 16:45 CET +0100


Booted last: 20 Nov 2016 00:00 CET +0100


Script from: 08 Jul 2016 02:16 UTC +0000


##### release ###########################


Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.1 LTS
Release:	16.04
Codename:	xenial


##### kernel ############################


Linux 4.4.0-47-generic #68-Ubuntu SMP Wed Oct 26 19:39:52 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux


Parameters: ro, noprompt, persistent, quiet, splash, vt.handoff=7


##### desktop ###########################


Ubuntu


##### lspci #############################


03:00.0 Network controller [0280]: Qualcomm Atheros AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: AzureWave AR9485 Wireless Network Adapter [1a3b:2c97]
	Kernel driver in use: ath9k


04:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8161 Gigabit Ethernet [1969:1091] (rev 08)
	Subsystem: ASUSTeK Computer Inc. N56VZ [1043:1477]
	Kernel driver in use: alx


##### lsusb #############################


Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 011: ID 13d3:3362 IMC Networks Atheros AR3012 Bluetooth 4.0 Adapter
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 003: ID 045e:0084 Microsoft Corp. Basic Optical Mouse
Bus 003 Device 007: ID 0582:0074 Roland Corp. EDIROL UA-25
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub


##### PCMCIA card info ##################


##### rfkill ############################


1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
2: asus-wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: asus-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
7: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no


##### lsmod #############################


ath9k                 143360  0
asus_nb_wmi            24576  0
ath3k                  20480  0
ath9k_common           36864  1 ath9k
ath9k_hw              466944  2 ath9k_common,ath9k
ath                    32768  3 ath9k_common,ath9k,ath9k_hw
asus_wmi               28672  1 asus_nb_wmi
mac80211              737280  1 ath9k
sparse_keymap          16384  1 asus_wmi
mxm_wmi                16384  0
bluetooth             520192  14 bnep,ath3k,btbcm,btrtl,btusb,rfcomm,btintel
cfg80211              565248  4 ath,ath9k_common,ath9k,mac80211
wmi                    20480  2 mxm_wmi,asus_wmi
video                  40960  2 i915,asus_wmi


##### interfaces ########################


auto lo
iface lo inet loopback


##### ifconfig ##########################


enp4s0    Link encap:Ethernet  HWaddr <MAC 'enp4s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 


wlp3s0    Link encap:Ethernet  HWaddr <MAC 'wlp3s0' [IF2]>  
          inet addr:192.168.2.104  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::<IP6 'wlp3s0' [IF2]>/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3618995 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2046354 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:4980507481 (4.9 GB)  TX bytes:223428315 (223.4 MB)


##### iwconfig ##########################


lo        no wireless extensions.


enp4s0    no wireless extensions.


wlp3s0    IEEE 802.11bgn  ESSID:"Underwater"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Underwater' [AC1]>   
          Bit Rate=45 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=25/70  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:35   Missed beacon:0


##### route #############################


Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    600    0        0 wlp3s0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlp3s0
192.168.2.0     0.0.0.0         255.255.255.0   U     600    0        0 wlp3s0


##### resolv.conf #######################


nameserver 127.0.1.1
search Speedport_W_921V_1_39_000


##### network managers ##################


Installed:


	NetworkManager


Running:


root       935     1  0 Nov19 ?        00:00:17 /usr/sbin/NetworkManager --no-daemon


##### NetworkManager info ###############


GENERAL.DEVICE:                         wlp3s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR9485 Wireless Network Adapter
GENERAL.DRIVER:                         ath9k
GENERAL.DRIVER-VERSION:                 4.4.0-47-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlp3s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0/net/wlp3s0
GENERAL.IP-IFACE:                       wlp3s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     Underwater
GENERAL.CON-UUID:                       2c180556-23df-424e-a910-85b0aaf5626a
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/13
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     27 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   no
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{0}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   2c180556-23df-424e-a910-85b0aaf5626a | Underwater
IP4.ADDRESS[1]:                         192.168.2.104/24
IP4.GATEWAY:                            192.168.2.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.2.1
IP4.DOMAIN[1]:                          Speedport_W_921V_1_39_000
DHCP4.OPTION[1]:                        requested_routers = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_time_offset = 1
DHCP4.OPTION[4]:                        requested_domain_name = 1
DHCP4.OPTION[5]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[6]:                        requested_broadcast_address = 1
DHCP4.OPTION[7]:                        requested_netbios_scope = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        next_server = 192.168.2.1
DHCP4.OPTION[10]:                       expiry = 1481470968
DHCP4.OPTION[11]:                       requested_interface_mtu = 1
DHCP4.OPTION[12]:                       requested_subnet_mask = 1
DHCP4.OPTION[13]:                       routers = 192.168.2.1
DHCP4.OPTION[14]:                       dhcp_message_type = 5
DHCP4.OPTION[15]:                       ip_address = 192.168.2.104
DHCP4.OPTION[16]:                       requested_static_routes = 1
DHCP4.OPTION[17]:                       domain_name = Speedport_W_921V_1_39_000
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       broadcast_address = 192.168.2.255
DHCP4.OPTION[20]:                       requested_ntp_servers = 1
DHCP4.OPTION[21]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[22]:                       dhcp_lease_time = 1814400
DHCP4.OPTION[23]:                       domain_name_servers = 192.168.2.1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.2.0
DHCP4.OPTION[27]:                       requested_host_name = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.2.1
IP6.ADDRESS[1]:                         fe80::<IP6 'wlp3s0' [IF2]>/64
IP6.GATEWAY:                            


GENERAL.DEVICE:                         enp4s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Qualcomm Atheros
GENERAL.PRODUCT:                        AR8161 Gigabit Ethernet (N56VZ)
GENERAL.DRIVER:                         alx
GENERAL.DRIVER-VERSION:                 
GENERAL.FIRMWARE-VERSION:               
GENERAL.HWADDR:                         <MAC 'enp4s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.3/0000:04:00.0/net/enp4s0
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
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 


SSID               BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY   ACTIVE  * 
Vodafone Homespot  <MAC 'Vodafone Homespot' [AC17]>  Infra  11    2462 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  --         no        
HITRON-C5C0        <MAC 'HITRON-C5C0' [AC15]>  Infra  11    2462 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2  no        
Vodafone Hotspot   <MAC 'Vodafone Hotspot' [AC16]>  Infra  11    2462 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  --         no        
Vodafone Hotspot   <MAC 'Vodafone Hotspot' [AC12]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  --         no        
Chromecast5843.b   <MAC 'Chromecast5843.b' [AC8]>  Infra  6     2437 MHz  54 Mbit/s  47      &#9602;&#9604;__  --         no        
Vodafone Homespot  <MAC 'Vodafone Homespot' [AC9]>  Infra  6     2437 MHz  54 Mbit/s  45      &#9602;&#9604;__  --         no        
EasyBox-903681     <MAC 'EasyBox-903681' [AC4]>  Infra  1     2412 MHz  54 Mbit/s  42      &#9602;&#9604;__  WPA1 WPA2  no        
Melix              <MAC 'Melix' [AC11]>  Infra  6     2437 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2       no        
KDG-CF76C          <MAC 'KDG-CF76C' [AC7]>  Infra  6     2437 MHz  54 Mbit/s  39      &#9602;&#9604;__  WPA1 WPA2  no        
KDG-A5AE8          <MAC 'KDG-A5AE8' [AC3]>  Infra  1     2412 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA1 WPA2  no        
Underwater         <MAC 'Underwater' [AC1]>  Infra  2     2417 MHz  54 Mbit/s  35      &#9602;&#9604;__  WPA2       yes     * 
Vodafone Hotspot   <MAC 'Vodafone Hotspot' [AC5]>  Infra  1     2412 MHz  54 Mbit/s  34      &#9602;&#9604;__  --         no        
HITRON-5C40        <MAC 'HITRON-5C40' [AN13]>  Infra  11    2462 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA2       no        
o2-WLAN14          <MAC 'o2-WLAN14' [AC14]>  Infra  7     2442 MHz  54 Mbit/s  30      &#9602;___  WPA2       no        
Vodafone Hotspot   <MAC 'Vodafone Hotspot' [AN15]>  Infra  1     2412 MHz  54 Mbit/s  29      &#9602;___  --         no        
HITRON-9E10        <MAC 'HITRON-9E10' [AN16]>  Infra  1     2412 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
o2-WLAN54          <MAC 'o2-WLAN54' [AC6]>  Infra  3     2422 MHz  54 Mbit/s  25      &#9602;___  WPA2       no        
Vodafone Homespot  <MAC 'Vodafone Homespot' [AN18]>  Infra  6     2437 MHz  54 Mbit/s  20      &#9602;___  --         no        
WLAN-8D7714        <MAC 'WLAN-8D7714' [AN19]>  Infra  11    2462 MHz  54 Mbit/s  20      &#9602;___  WPA1 WPA2  no        
WLAN-ABAE12        <MAC 'WLAN-ABAE12' [AC10]>  Infra  6     2437 MHz  54 Mbit/s  19      &#9602;___  WPA1 WPA2  no        
Vodafone Homespot  <MAC 'Vodafone Homespot' [AN21]>  Infra  1     2412 MHz  54 Mbit/s  15      &#9602;___  --         no        
JM_NETZWERK        <MAC 'JM_NETZWERK' [AN22]>  Infra  1     2412 MHz  54 Mbit/s  9       &#9602;___  WPA2       no        
HITRON-2CC0        <MAC 'HITRON-2CC0' [AC18]>  Infra  11    2462 MHz  54 Mbit/s  5       ____  WPA1 WPA2  no        


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


[[/etc/NetworkManager/system-connections/Underwater]] (600 root)
[connection] id=Underwater | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp3s0' [IF2]> | mac-address-blacklist= | ssid=Underwater
[ipv4] method=auto
[ipv6] method=ignore


##### iw reg get ########################


Region: Europe/Berlin (based on set time zone)


country DE: DFS-ETSI
	(2400 - 2483 @ 40), (N/A, 20), (N/A)
	(5150 - 5250 @ 80), (N/A, 20), (N/A), NO-OUTDOOR
	(5250 - 5350 @ 80), (N/A, 20), (0 ms), NO-OUTDOOR, DFS
	(5470 - 5725 @ 160), (N/A, 26), (0 ms), DFS
	(57000 - 66000 @ 2160), (N/A, 40), (N/A)


##### iwlist channels ###################


lo        no frequency information.


enp4s0    no frequency information.


wlp3s0    13 channels in total; available frequencies :
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
          Current Frequency:2.417 GHz (Channel 2)


##### iwlist scan #######################


lo        Interface doesn't support scanning.


enp4s0    Interface doesn't support scanning.


Channel occupancy:


      5   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.417 GHz (Channel 2)
      1   APs on   Frequency:2.422 GHz (Channel 3)
      6   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.442 GHz (Channel 7)
      4   APs on   Frequency:2.462 GHz (Channel 11)


wlp3s0    Scan completed :
          Cell 01 - Address: <MAC 'Underwater' [AC1]>
                    Channel:2
                    Frequency:2.417 GHz (Channel 2)
                    Quality=26/70  Signal level=-84 dBm  
                    Encryption key:on
                    ESSID:"Underwater"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000d3927678c7
                    Extra: Last beacon: 40ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          


##### module infos ######################


[ath9k]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     1B84AD8C53440158CD581F2
depends:        mac80211,ath9k_hw,ath9k_common,cfg80211,ath
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           debug:Debugging mask (uint)
parm:           nohwcrypt:Disable hardware encryption (int)
parm:           blink:Enable LED blink on activity (int)
parm:           led_active_high:Invert LED polarity (int)
parm:           btcoex_enable:Enable wifi-BT coexistence (int)
parm:           bt_ant_diversity:Enable WLAN/BT RX antenna diversity (int)
parm:           ps_enable:Enable WLAN PowerSave (int)
parm:           use_chanctx:Enable channel context for concurrency (int)


[ath3k]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/bluetooth/ath3k.ko
firmware:       ath3k-1.fw
license:        GPL
version:        1.0
description:    Atheros AR30xx firmware driver
author:         Atheros Communications
srcversion:     2B85DCB887D9376A61652DD
depends:        bluetooth
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[ath9k_common]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_common.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless 802.11n LAN cards.
author:         Atheros Communications
srcversion:     6FBD9F8A613FDFA282AB4FE
depends:        ath9k_hw,cfg80211,ath
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[ath9k_hw]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath9k/ath9k_hw.ko
license:        Dual BSD/GPL
description:    Support for Atheros 802.11n wireless LAN cards.
author:         Atheros Communications
srcversion:     FA7ECFBA5761A5B3ED96BB2
depends:        ath
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[ath]
filename:       /lib/modules/4.4.0-47-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     3FCDBF7CE71CB8FB980D59D
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 


[mac80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)


[cfg80211]
filename:       /lib/modules/4.4.0-47-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-47-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)


##### module parameters #################


[ath9k]
blink: 0
bt_ant_diversity: 0
btcoex_enable: 0
led_active_high: -1
nohwcrypt: 1
ps_enable: 0
use_chanctx: 0


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


##### modprobe options ##################


[/etc/modprobe.d/AR9485.conf]
options AR9485 fwlps=N


[/etc/modprobe.d/ath9k.conf]
options ath9k nohwcrypt=1


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


[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode


[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211


[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en


[/etc/modprobe.d/vmware-fuse.conf]
alias char-major-10-229 fuse


##### rc.local ##########################


sudo iw reg set DE
exit 0


##### pm-utils ##########################


[/etc/pm/config.d/config] (644 root)
SUSPEND_MODULES="AR9485"


##### udev rules ########################


##### dmesg #############################


[33847.738375] wlp3s0: authenticated
[33847.742470] wlp3s0: associate with <MAC 'Underwater' [AC1]> (try 1/3)
[33847.748348] wlp3s0: RX AssocResp from <MAC 'Underwater' [AC1]> (capab=0x431 status=0 aid=8)
[33847.748456] wlp3s0: associated
[33847.748471] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
[33847.752351] ath: EEPROM regdomain: 0x8114
[33847.752355] ath: EEPROM indicates we should expect a country code
[33847.752356] ath: doing EEPROM country->regdmn map search
[33847.752358] ath: country maps to regdmn code: 0x37
[33847.752359] ath: Country alpha2 being used: DE
[33847.752361] ath: Regpair used: 0x37
[33847.752363] ath: regdomain 0x8114 dynamically updated by country IE
[33987.662254] wlp3s0: authenticate with <MAC 'Underwater' [AC1]>
[33987.683132] wlp3s0: send auth to <MAC 'Underwater' [AC1]> (try 1/3)
[33987.688000] wlp3s0: authenticated
[33987.689042] wlp3s0: associate with <MAC 'Underwater' [AC1]> (try 1/3)
[33987.697497] wlp3s0: RX AssocResp from <MAC 'Underwater' [AC1]> (capab=0x431 status=0 aid=8)
[33987.697587] wlp3s0: associated
[33987.699866] ath: EEPROM regdomain: 0x8114
[33987.699868] ath: EEPROM indicates we should expect a country code
[33987.699868] ath: doing EEPROM country->regdmn map search
[33987.699869] ath: country maps to regdmn code: 0x37
[33987.699870] ath: Country alpha2 being used: DE
[33987.699871] ath: Regpair used: 0x37
[33987.699872] ath: regdomain 0x8114 dynamically updated by country IE
[33991.670887] wlp3s0: authenticate with <MAC 'Underwater' [AC1]>
[33991.691119] wlp3s0: send auth to <MAC 'Underwater' [AC1]> (try 1/3)
[33991.692806] wlp3s0: authenticated
[33991.696898] wlp3s0: associate with <MAC 'Underwater' [AC1]> (try 1/3)
[33991.700612] wlp3s0: RX AssocResp from <MAC 'Underwater' [AC1]> (capab=0x431 status=0 aid=8)
[33991.700710] wlp3s0: associated
[33991.704411] ath: EEPROM regdomain: 0x8114
[33991.704415] ath: EEPROM indicates we should expect a country code
[33991.704417] ath: doing EEPROM country->regdmn map search
[33991.704418] ath: country maps to regdmn code: 0x37
[33991.704420] ath: Country alpha2 being used: DE
[33991.704421] ath: Regpair used: 0x37
[33991.704424] ath: regdomain 0x8114 dynamically updated by country IE


########## wireless info END ############


[COLOR=#000000]
```




[/COLOR]

---

### Post by Hadaka on 2016-11-20
Thanks for the new report.
The only thing that stands out is the still low signal..
```
wlp3s0    IEEE 802.11bgn  ESSID:"Underwater"  
          Mode:Managed  Frequency:2.417 GHz  Access Point: <MAC 'Underwater' [AC1]>   
          Bit Rate=45 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=[COLOR=#ff0000]25/70[/COLOR]  Signal level=-85 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:35   Missed beacon:0
```
since you have a laptop, try getting as close to the router as possible,like
in the same room. and then do..
```
iwconfig
```
*If the signal is still low just a short distance from the router then it is likely
a corroded connection of card/pci antenna connection or antenna connection or router fault.
Another option is to acquire a repeater or a used router with repeater abilities and put it
between you and the router. Untill you find a way to a stronger signal you will continue to
have connection issues.

---

### Post by jeremy31 on 2016-11-20
Changing the orientation of the router might make a big difference, if it is lying flat on a surface change it to laying on it's side as antenna polarization is important

---

### Post by Hadaka on 2016-11-20
In addition to jermy31's suggestion, research shows your card..
 Qualcomm Atheros AR9485 has 2 antenna connections, please swap them
carefully...get a you-tube if you need to know how, and see if that makes an
improvement in the signal when you do...
```
iwconfig
```
 
 Qualcomm Atheros AR9485 card...see attached
[ATTACH=CONFIG]272270[/ATTACH]

---

### Post by Re4mRpR on 2016-11-23
Access to the card in my my model is somewhat complicated, so before I get out the screw drivers, does the fact that i get strong signal from other networks make a difference?

> **Hadaka said:**
> In addition to jermy31's suggestion, research shows your card..
 Qualcomm Atheros AR9485 has 2 antenna connections, please swap them
carefully...get a you-tube if you need to know how, and see if that makes an
improvement in the signal when you do...
```
iwconfig
```
 
 Qualcomm Atheros AR9485 card...see attached
[ATTACH=CONFIG]272270[/ATTACH]

---

### Post by TheFu on 2016-11-23
YES!!!! It is called "interference."    I find it doubtful to be an issue with the card in the environment you've described. Plus since it isn't an issue anywhere else, the issue isn't with the laptop, it is the environment.

Fix that.

The wifi-AP you want connected to the laptop needs to have a better connection, on a channel that isn't interfered with, than with other nearby wifi-APs.  This is normal RF stuff.  Even nearby channels impact the ability to receive. That's why we said to use non-overlapping channels initially.  As it is, if you cannot convince the neighbors to turn down their wifi power output, then someone in your apartment will need to make the AP you want a connection with have with a higher S/N than other APs nearby.

In short, if you want to solve this, add another AP to the network. If money is more important than time, keep troubleshooting to eliminate all the other possibilities, but **$65-$90 solves this, depending on the wifi standard you want to use.**  For most people, 802.11G is fine, since their internet connection isn't faster.  If you move large files around the LAN (not the internet), then going with faster, more expensive, wifi standards could make sense. The only real trick is that walls are an issue for 5Ghz bands and that whatever the box says, expect in a best-case situation, to get 30% of that.  For example, I have a properly setup wifi-N300 router, but only get 65Mbps out of it.  That's fine. iperf is "best case", not real world transfers.
```
$ iperf -c hadar
------------------------------------------------------------
Client connecting to hadar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.16 port 52766 connected with 172.22.22.6 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  76.1 MBytes  63.7 Mbits/sec
``` That's 76MB transferred in 10 seconds.
My internet is only 16/3 Mbps and I only use wifi for typical stuff. 

When I need to move files around on the LAN, I plug in with wired ethernet (920Mbps). Give me a second to change the network connection and rerun the bandwidth test.  Need to get some videos for the holidays on this box anyway.
```
$ iperf -c hadar
------------------------------------------------------------
Client connecting to hadar, TCP port 5001
TCP window size: 85.0 KByte (default)
------------------------------------------------------------
[  3] local 172.22.22.13 port 47032 connected with 172.22.22.6 port 5001
[ ID] Interval       Transfer     Bandwidth
[  3]  0.0-10.0 sec  1.07 GBytes   921 Mbits/sec
```  That's GB transferred in 10 seconds. Not shabby.
There's the wired connection.  64Mbps vs 921Mbps.  No comparison. Wired is 14x faster for the same chromebook, connecting to the same, internal, server.  Plus I had to make the wifi-AP N-only and use 40Mhz channels to even get that speed. Before, it would only get about 48Mbps - basically wifi-G standard.  I live in a single family house with average amounts of land around it.  Can see about 5 other APs from my neighbors, but their S/N is fairly weak and we don't use the same channels.  I spoke with them to ensure we didn't.  1 neighbor works for IBM and I used to work for a well-known telecom/ISP, so it wasn't hard to convince them what would be best for channels so we'd all have the optimal settings within limits.

---

### Post by Re4mRpR on 2017-01-10
So, been a while.  We are using ch 4 now, and because of the signal quality, the obvious rf issues persist.  I don't really have the money to drop on an AP right now.

An interesting change is that I recently connected to a friends wifi and although the device is currently many kilometers away and obviously not being detected, my network manager will sometimes list it in the available wireless list and attempt to connect to it

---

### Post by TheFu on 2017-01-10
There are only 2.4Ghz 3 channels that don't overlap - 1, 6, 11.  Only use any other channels if you are in an apartment or otherwise dense wifi area. The interference will lower the available bandwidth.  If you live in Japan, you can use ch13 too.

5.8Ghz channels are mostly empty, but that frequency doesn't work well through any walls.

Life is really easier if people would just get wired ethernet connections.  Wifi sucks. Wifi will always suck.  More wifi will suck more.  That is the nature of RF when more than 1 device anywhere nearby uses it.

I did some reading on new wifi standards coming out.  They offer more speed, but don't do anything about interference.  The really high-speed version at 4.7Gbps won't work through walls.  What use is that?  If we're in the same room with the AP, then we can plug in a cable, right?  At least for most people.  I have an open floorplan house, so putting a wifi AP in the center of the ceiling on the 2nd floor actually does cover the den, living room, half the kitchen and upstairs playroom without any walls in the way.  Alas, my area doesn't have interference from outside our home. The neighbors are far enough away that connecting to their wifi requires extra effort (pringles can or other directional antenna). ;)

---

