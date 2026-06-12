---
title: "Slow Wifi Connection - Rosewill RNX-AC1300 (Broadcom 4360)"
date: 2018-12-03
forum: Networking &amp; Wireless
---

### Post by nasbit on 2018-12-03
Hello,

I recently installed Ubuntu Server 18.04 LTS and I am trying to use it as a file server. I am trying to stream some video files from the server but the local wifi connection to my router is not providing a good enough connection to play the files without buffering. I have tested this with a wired connection, it works fine, over wifi it buffers.

I am using a Rosewill RNX-AC1300 and I installed the bcmwl-kernel-source according to the sticky. I am connected however my suspicion is that I am not using the AC connection, probably N or even G...My router is broadcasting 5Ghz in mixed n/ac mode since my laptop only has N, I would like the server to connect in AC mode though.

How can I force the server to connect in AC mode? Do the current drivers even support AC? See below the relevant output of the script:

```

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 18.04.1 LTS
Release:    18.04
Codename:    bionic

##### kernel ############################

Linux 4.15.0-42-generic #45-Ubuntu SMP Thu Nov 15 19:32:57 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, noapic

##### desktop ###########################

Ubuntu

##### lspci #############################

00:0a.0 Bridge [0680]: NVIDIA Corporation CK804 Ethernet Controller [10de:0057] (rev f3)
    Subsystem: ASUSTeK Computer Inc. K8N4/A8N Series Mainboard [1043:8141]
    Kernel driver in use: forcedeth

04:00.0 Network controller [0280]: Broadcom Limited BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Broadcom Limited BCM4360 802.11ac Wireless Network Adapter [14e4:0619]
    Kernel driver in use: wl
##### ifconfig ##########################

3: wlp4s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc fq_codel state UP group default qlen 1000
    link/ether <MAC 'wlp4s0' [IF1]> brd <MAC address>
    inet 192.168.1.150/24 brd 192.168.1.255 scope global wlp4s0
       valid_lft forever preferred_lft forever
    inet6 fe80::<IP6 'wlp4s0' [IF1]>/64 scope link 
       valid_lft forever preferred_lft forever

##### iwconfig ##########################

enp0s10   no wireless extensions.

lo        no wireless extensions.

wlp4s0    IEEE 802.11  ESSID:"****"  
          Mode:Managed  Frequency:5.2 GHz  Access Point: <MAC '****' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

##### network managers ##################

Installed:

    None found.

Running:

    None found.

##### iwlist scan #######################

wlp4s0    Scan completed :
          Cell 01 - Address: <MAC '****' [AC1]>
                    Channel:40
                    Frequency:5.2 GHz (Channel 40)
                    Quality=34/70  Signal level=-76 dBm  
                    Encryption key:on
                    ESSID:"****"
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 84ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[wl]
filename:       /lib/modules/4.15.0-42-generic/updates/dkms/wl.ko
license:        MIXED/Proprietary
srcversion:     00D38A27B7E3C7B97C238FC
depends:        cfg80211
retpoline:      Y
name:           wl
vermagic:       4.15.0-42-generic SMP mod_unload 
parm:           passivemode:int
parm:           wl_txq_thresh:int
parm:           oneonly:int
parm:           piomode:int
parm:           instance_base:int
parm:           nompc:int
parm:           intf_name:string

[cfg80211]
filename:       /lib/modules/4.15.0-42-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     62FD05DCC5AEEA290640C3D
depends:        
retpoline:      Y
intree:         Y
name:           cfg80211
vermagic:       4.15.0-42-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
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

[/etc/modprobe.d/amd64-microcode-blacklist.conf]
blacklist microcode

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

[/etc/modprobe.d/mdadm.conf]
options md_mod start_ro=1


```

I am concerned because in the iwlist scan my network is showing a maximum of 54Mb/s, shouldn't this be 300Mb/s for N and 867 Mb/s for AC?

Is there a way to see the actual speed (server --> router) of my current wifi connection? In other peoples logs I see the link speed but can't seem to see what mine is.

Thanks in advance!

---

### Post by nasbit on 2018-12-04
So after some searching in the forum it seems to be somewhat well documented that the broadcom driver does not support AC mode, see:

[https://ubuntuforums.org/showthread.php?t=2407411](https://ubuntuforums.org/showthread.php?t=2407411)
[https://ubuntuforums.org/showthread.php?t=2220007](https://ubuntuforums.org/showthread.php?t=2220007)
[https://ubuntuforums.org/showthread.php?t=2346510](https://ubuntuforums.org/showthread.php?t=2346510)

These threads are old so it seems possible that the drivers have been updated since, does anyone know? I will do some testing this evening by broadcasting only AC from my router.

If this is the case I will likely return this card (black friday deal) and get something more linux friendly. The Intel 7260 desktop seems like it would work for me.

---

### Post by nasbit on 2018-12-04
So I decided to setup iperf in order to see what I was dealing with. I used an old macbook as the "server" and my actual new file server as the "client".

Here both client and server were wireless:
```
   	 	 	 	   [ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
 [  4]   0.00-1.00   sec  2.85 MBytes  23.9 Mbits/sec    0   80.6 KBytes        
 [  4]   1.00-2.00   sec  2.92 MBytes  24.5 Mbits/sec    0   97.6 KBytes        
 [  4]   2.00-3.00   sec  2.94 MBytes  24.7 Mbits/sec    0    107 KBytes        
 [  4]   3.00-4.00   sec  2.73 MBytes  22.9 Mbits/sec    0    107 KBytes        
 [  4]   4.00-5.00   sec  3.11 MBytes  26.1 Mbits/sec    0    129 KBytes        
 [  4]   5.00-6.00   sec  3.21 MBytes  26.9 Mbits/sec    0    141 KBytes        
 [  4]   6.00-7.00   sec  3.35 MBytes  28.1 Mbits/sec    0    209 KBytes        
 [  4]   7.00-8.00   sec  3.04 MBytes  25.5 Mbits/sec    0    209 KBytes        
 [  4]   8.00-9.00   sec  3.49 MBytes  29.3 Mbits/sec    0    209 KBytes        
 [  4]   9.00-10.00  sec  3.55 MBytes  29.8 Mbits/sec    0    209 KBytes        
 - - - - - - - - - - - - - - - - - - - - - - - - -
 [ ID] Interval           Transfer     Bandwidth       Retr
 [  4]   0.00-10.00  sec  31.2 MBytes  26.2 Mbits/sec    0             sender
 [  4]   0.00-10.00  sec  30.8 MBytes  25.9 Mbits/sec                  receiver
  
```

~26 Mbits/s

Knowing the wireless server may be a bottleneck (2011 macbook limited to N) I plugged it in, here are the results with the client being wireless and the server being wired:

```
[ ID] Interval           Transfer     Bandwidth       Retr  Cwnd
[  4]   0.00-1.00   sec  7.85 MBytes  65.9 Mbits/sec    0   94.7 KBytes       
[  4]   1.00-2.00   sec  9.30 MBytes  78.0 Mbits/sec    0    113 KBytes       
[  4]   2.00-3.00   sec  9.09 MBytes  76.2 Mbits/sec    0    113 KBytes       
[  4]   3.00-4.00   sec  9.42 MBytes  79.0 Mbits/sec    0    113 KBytes       
[  4]   4.00-5.00   sec  9.74 MBytes  81.7 Mbits/sec    0    119 KBytes       
[  4]   5.00-6.00   sec  9.55 MBytes  80.1 Mbits/sec    0    160 KBytes       
[  4]   6.00-7.00   sec  10.6 MBytes  88.7 Mbits/sec    0    160 KBytes       
[  4]   7.00-8.00   sec  10.9 MBytes  91.5 Mbits/sec    0    165 KBytes       
[  4]   8.00-9.00   sec  9.35 MBytes  78.5 Mbits/sec    0    165 KBytes       
[  4]   9.00-10.00  sec  11.0 MBytes  92.0 Mbits/sec    0    165 KBytes       
- - - - - - - - - - - - - - - - - - - - - - - - -
[ ID] Interval           Transfer     Bandwidth       Retr
[  4]   0.00-10.00  sec  96.8 MBytes  81.2 Mbits/sec    0             sender
[  4]   0.00-10.00  sec  96.5 MBytes  80.9 Mbits/sec                  receiver

iperf Done.

```

~80 Mbits/s

The good news is this is above G speed (54 Mbits/s), seems most likely to be using N...

I decided to force my router to broadcast only AC mode @ 80 Hz in order to see if the BCM4360 would connect, to my surprise, it connected! I re-ran the iperf test and obtained similar results (~80 Mbits/s).

This leaves me slightly confused as even on AC I am only seeing ~80 Mbits/s when I should be able to get up to 867 Mbit/s (in a perfect environment).

Any ideas how I can squeeze some more juice out of this sucker?

---

### Post by nasbit on 2018-12-04
I decided to reverse the roles, server hard wired and the macbook over wireless, got ~130 Mbits/s which seems about right for the N wireless it is limited to. Also tried wired + wired which got ~940 Mbits/s as expected.

Clearly the BCM4360 is not living up to AC speeds, though it will connect to an AC network. It isn't even reaching N speeds so there definitely seems to be an issue.

I am thinking of testing out some of the other drivers, brcmfmac seems to be the newer one although it does not list the BCM4360 as being supported. 

Any help is appreciated!

---

