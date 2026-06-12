---
title: "Wireless LED always orange on my dv6000 laptop"
date: 2008-04-14
forum: Networking &amp; Wireless
---

### Post by lotakoka on 2008-04-14
Hi
[SIZE="4"]I have hp dv6000 intell model. After many days hard work , i am able to connect using wireless. But speed is very slow and wireless LED always orange , never turns in blue. I have pasted some output below ...[/SIZE]
anil@sushma-laptop:~$ sudo iwconfig wlan0
[sudo] password for anil:
wlan0     IEEE 802.11g  ESSID:"tumerijanhai"  
          Mode:Managed  Frequency:2.437 GHz  Access Point:
          00:0F:66:22:A1:71   
          Bit Rate=11 Mb/s   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Encryption key:0006-3022-08
          Link Quality=85/100  Signal level=-19 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

anil@sushma-laptop:~$ sudo dmesg|grep wl
[   14.412000] iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for
Linux, 1.1.0
[   14.412000] iwl4965: Copyright(c) 2003-2007 Intel Corporation
[   14.412000] iwl4965: Detected Intel Wireless WiFi Link 4965AGN
[   14.752000] iwl4965: Tunable channels: 11 802.11bg, 13 802.11a
channels
[   14.752000] wmaster0: Selected rate control algorithm 'iwl-4965-rs'
[   46.100000] wlan0: Initial auth_alg=0
[   46.100000] wlan0: authenticate with AP 00:0f:66:22:a1:71
[   46.104000] wlan0: RX authentication from 00:0f:66:22:a1:71 (alg=0
transaction=2 status=0)
[   46.104000] wlan0: authenticated
[   46.104000] wlan0: associate with AP 00:0f:66:22:a1:71
[   46.108000] wlan0: RX AssocResp from 00:0f:66:22:a1:71 (capab=0x15
status=0 aid=720)
[   46.108000] wlan0: associated
[   62.908000] wlan0: no IPv6 routers present
anil@sushma-laptop:~$ 

**Can any body went thru this ?**:lolflag:

---

### Post by lotakoka on 2008-04-14
Any body and any idea ?

THX

---

### Post by lotakoka on 2008-04-15
Hi
Looks like no body knows how to turn LED light from orange to blue. 
Any body ...hello ..ubuntu support ?

---

