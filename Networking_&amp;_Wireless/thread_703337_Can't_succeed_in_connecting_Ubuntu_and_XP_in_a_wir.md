---
title: "Can't succeed in connecting Ubuntu and XP in a wireless network"
date: 2008-02-21
forum: Networking &amp; Wireless
---

### Post by Silviya on 2008-02-21
Ok, probably thousands of people asked same question but believe me I have tried everything that is in forums everywhere and still can't make it.
I'm trying to connect two computers, one using Ubuntu 7.10 GG, the other one, running on XP. One of them will get Internet through wired connection and will share it vie wireless network. It doesn't really matter which one will be the server. Here is what happened last days:
1 case: i'm making the network from Ubuntu. After many tries, i realise that the problem is with the Ad-Hoc command, it's giving me error. Here it is:
> Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.

This is coming about ath0. Ok? But here is what is coming after lshw -C network:
> *-network:0             
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications, Inc.
       physical id: 5
       bus info: pci@0000:06:05.0
       logical name: wifi0
       version: 01
       serial: 00:14:a4:50:70:d9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci latency=168 maxlatency=28 mingnt=10 module=ath_pci multicast=yes wireless=IEEE 802.11g


And here is iwconfig:
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:""  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:9 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/70  Signal level=-91 dBm  Noise level=-91 dBm
          Rx invalid nwid:330  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Looks as I'm not connected to it now...but the nwm is showing everything right...The XP is finding the network but not being able to connect to it. 

The other case that I tried last night:
I installed ndiswrapper, found the drivers for my card and Windows Wireless Drivers is saying to both of them: Hardware Present: NO.

Please, give me a hand about this.

---

