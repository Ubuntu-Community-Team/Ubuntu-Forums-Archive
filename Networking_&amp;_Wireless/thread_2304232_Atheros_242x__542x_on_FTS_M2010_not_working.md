---
title: "Atheros 242x / 542x on FTS M2010 not working"
date: 2015-11-25
forum: Networking &amp; Wireless
---

### Post by david466 on 2015-11-25
Hello everybody, I am a Linux/Ubuntu Newbie and could use some of your help getting my wireless Adapter to work. 

System Information: 
I recently installed Ubuntu 14.04. 32 Bit on a Fujitsu M2010 Netbook that comes with a Qualcomm Atheros 242x / 524x wifi Card. 

Problem: 
No WiFi Networks are shown 

What I tried: 
A lot of People seem to have run into Trouble using the Aetheros Card so I found a thing or two to check on while googling. 

1. No Softblock / No Hardblock

```
david@FTS-ubuntu:~$ sudo rfkill list
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no

```
2. Tried to scan WiFi Networks

```
david@FTS-ubuntu:~$ sudo iwlist wlan0 scan
wlan0     No scan results
```

3. Tried to activate wlan0 via ifconfig

```
david@FTS-ubuntu:~$ sudo ifconfig wlan0 up

```
4. Blacklist? 

This is my modprobe.d content: 

```
david@FTS-ubuntu:/etc/modprobe.d$ ls -l
insgesamt 52
-rw-r--r-- 1 root root 2507 Feb 13  2013 alsa-base.conf
-rw-r--r-- 1 root root  327 Nov 24 22:28 blacklist-ath_pci.conf
-rw-r--r-- 1 root root  325 Apr 10  2014 blacklist-ath_pci.conf~
-rw-r--r-- 1 root root 1603 Apr 10  2014 blacklist.conf
-rw-r--r-- 1 root root  210 Apr 10  2014 blacklist-firewire.conf
-rw-r--r-- 1 root root  677 Apr 10  2014 blacklist-framebuffer.conf
-rw-r--r-- 1 root root  156 Feb 13  2013 blacklist-modem.conf
lrwxrwxrwx 1 root root   41 Nov 23 13:20 blacklist-oss.conf -> /lib/linux-sound-base/noOSS.modprobe.conf
-rw-r--r-- 1 root root  583 Apr 10  2014 blacklist-rare-network.conf
-rw-r--r-- 1 root root 1077 Apr 10  2014 blacklist-watchdog.conf
-rw-r--r-- 1 root root  456 Apr 14  2014 fbdev-blacklist.conf
-rw-r--r-- 1 root root  347 Apr 10  2014 iwlwifi.conf
-rw-r--r-- 1 root root  104 Apr 10  2014 mlx4.conf
-rw-r--r-- 1 root root   30 Jun 11 01:26 vmwgfx-fbdev.conf

```
I opened "blacklist-ath_pci.conf" and uncommented the line "blacklist ath_pci", even did a restart of the System afterwards. But still no wireless Action. 

This is the Output from the wireless script mentioned at [http://ubuntuforums.org/showthread.php?p=12350385#post12350385](http://ubuntuforums.org/showthread.php?p=12350385#post12350385): 


```
########## wireless info START ##########
Report from: 25 Nov 2015 11:20 CET +0100
Booted last: 25 Nov 2015 10:00 CET +0100
Script from: 27 Sep 2015 00:34 UTC +0000
##### release ###########################
Distributor ID: Ubuntu
Description: Ubuntu 14.04.3 LTS
Release: 14.04
Codename: trusty
##### kernel ############################
Linux 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:18:00 UTC 2015 i686 i686 i686 GNU/Linux
Parameters: ro, quiet, splash, vt.handoff=7
##### desktop ###########################
Ubuntu
##### lspci #############################
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
 Subsystem: Fujitsu Limited. Device [10cf:1534]
 Kernel driver in use: r8169
03:00.0 Ethernet controller [0200]: Qualcomm Atheros AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
 Subsystem: Quanta Microsystems, Inc Device [1a32:0108]
 Kernel driver in use: ath5k
##### lsusb #############################
Bus 001 Device 003: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 002: ID 0408:13e0 Quanta Computer, Inc. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
##### PCMCIA card info ##################
##### rfkill ############################
0: phy0: Wireless LAN
 Soft blocked: no
 Hard blocked: no
##### lsmod #############################
ath5k                 135168  0 
ath                    24576  1 ath5k
mac80211              618496  1 ath5k
cfg80211              450560  3 ath,ath5k,mac80211
##### interfaces ########################
auto lo
iface lo inet loopback
##### ifconfig ##########################
eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          inet addr:192.168.2.125  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: 2003:81:6e18:f7d:<IP6 'eth0' [IF]>/64 Scope:Global
          inet6 addr: fe80::<IP6 'eth0' [IF]>/64 Scope:Link
          inet6 addr: 2003:81:6e18:f7d:5d9e:c3d5:34fe:3c2c/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:149530 errors:0 dropped:0 overruns:0 frame:0
          TX packets:291388 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:48417579 (48.4 MB)  TX bytes:313266299 (313.2 MB)
wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
##### iwconfig ##########################
lo        no wireless extensions.
eth0      no wireless extensions.
wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
##### route #############################
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.2.1     0.0.0.0         UG    0      0        0 eth0
192.168.2.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
##### resolv.conf #######################
nameserver 127.0.1.1
search Speedport_W_921V_1_39_000
##### network managers ##################
Installed:
 NetworkManager
Running:
root       664     1  0 08:59 ?        00:00:01 NetworkManager
##### NetworkManager info ###############
NetworkManager Tool
State: connected (global)
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             disconnected
  Default:           no
  HW Address:        <MAC 'wlan0' [IF]>
  Capabilities:
  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes
  Wireless Access Points 
- Device: eth0  [Kabelnetzwerkverbindung 1] ------------------------------------
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
    Address:         192.168.2.125
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.2.1
    DNS:             192.168.2.1
  IPv6 Settings:
    Address:         2003:81:6e18:f7d:5d9e:c3d5:34fe:3c2c
    Prefix:          64
    Gateway:         fe80::1
    Address:         2003:81:6e18:f7d:<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::1
    Address:         fe80::<IP6 'eth0' [IF]>
    Prefix:          64
    Gateway:         fe80::1
    DNS:             fe80::1
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
##### iw reg get ########################
Region: Europe/Berlin (based on set time zone)
country 00:
 (2402 - 2472 @ 40), (3, 20)
 (2457 - 2482 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
 (2474 - 2494 @ 20), (3, 20), NO-OFDM, PASSIVE-SCAN, NO-IBSS
 (5170 - 5250 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
 (5735 - 5835 @ 40), (3, 20), PASSIVE-SCAN, NO-IBSS
##### iwlist channels ###################
lo        no frequency information.
eth0      no frequency information.
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
Sorry, try again.
lo        Interface doesn't support scanning.
eth0      Interface doesn't support scanning.
wlan0     No scan results
##### module infos ######################
[ath5k]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/ath/ath5k/ath5k.ko
license:        Dual BSD/GPL
description:    Support for 5xxx series of Atheros 802.11 wireless LAN cards.
author:         Nick Kossifidis
author:         Jiri Slaby
srcversion:     AB33EFF88AF59F8CCF40484
depends:        mac80211,cfg80211,ath
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        BB:26:8D:6D:EE:CB:ED:52:27:34:75:F8:CB:66:1B:D2:CA:20:8A:1B
sig_hashalgo:   sha512
parm:           nohwcrypt:Disable hardware encryption. (bool)
parm:           fastchanswitch:Enable fast channel switching for AR2413/AR5413 radios. (bool)
parm:           no_hw_rfkill_switch:Ignore the GPIO RFKill switch state (bool)
[ath]
filename:       /lib/modules/3.19.0-25-generic/kernel/drivers/net/wireless/ath/ath.ko
license:        Dual BSD/GPL
description:    Shared library for Atheros wireless LAN cards.
author:         Atheros Communications
srcversion:     D89F916A5E804AF040C4D29
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        BB:26:8D:6D:EE:CB:ED:52:27:34:75:F8:CB:66:1B:D2:CA:20:8A:1B
sig_hashalgo:   sha512
[mac80211]
filename:
       /lib/modules/3.19.0-25-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     B23264F074A7D27F8B691A2
depends:        cfg80211
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        BB:26:8D:6D:EE:CB:ED:52:27:34:75:F8:CB:66:1B:D2:CA:20:8A:1B
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)
[cfg80211]
filename:       /lib/modules/3.19.0-25-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     E61EB836E1B33C2A2918485
depends:        
intree:         Y
vermagic:       3.19.0-25-generic SMP mod_unload modversions 686 
signer:         Magrathea: Glacier signing key
sig_key:        BB:26:8D:6D:EE:CB:ED:52:27:34:75:F8:CB:66:1B:D2:CA:20:8A:1B
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)
##### module parameters #################
[ath5k]
fastchanswitch: N
nohwcrypt: N
no_hw_rfkill_switch: N
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
##### modprobe options ##################
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
[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8136 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x168c:0x001c (ath5k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
##### dmesg #############################
[   14.075692] ath5k 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   14.075971] ath5k 0000:03:00.0: registered as 'phy0'
[   15.720066] ath: EEPROM regdomain: 0x65
[   15.720077] ath: EEPROM indicates we should expect a direct regpair map
[   15.720085] ath: Country alpha2 being used: 00
[   15.720090] ath: Regpair used: 0x65
[   15.836009] ath5k: phy0: Atheros AR2425 chip found (MAC: 0xe2, PHY: 0x70)
[   16.259859] r8169 0000:02:00.0 eth0: link down
[   16.266053] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.343732] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1877.950093] r8169 0000:02:00.0 eth0: link up
[ 1877.950123] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
########## wireless info END ############

```

As I already mentioned I am absolutely new to the Linux world so any Kind of help is much much much appreciated :-) 

Thank you!

David

---

