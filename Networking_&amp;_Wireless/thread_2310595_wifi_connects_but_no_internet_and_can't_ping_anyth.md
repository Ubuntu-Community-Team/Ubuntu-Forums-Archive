---
title: "wifi connects but no internet and can't ping anything"
date: 2016-01-20
forum: Networking &amp; Wireless
---

### Post by wojciech8 on 2016-01-20
Hello
After more than week my laptop lost wifi :) I can see the wifi networks, can connect to them but can't really use it. can't ping any address in my network. What to do? 


```
cyborg@cyborg-Aspire-5750G:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=15.10
DISTRIB_CODENAME=wily
DISTRIB_DESCRIPTION="Ubuntu 15.10"
Linux cyborg-Aspire-5750G 4.2.0-23-lowlatency #28-Ubuntu SMP PREEMPT Sun Dec 27 18:28:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux
```
```
cyborg@cyborg-Aspire-5750G:~$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57785 Gigabit Ethernet PCIe [14e4:16b5] (rev 10)
	Subsystem: Acer Incorporated [ALI] Device [1025:0504]
	Kernel driver in use: tg3
--
03:00.0 Network controller [0280]: Qualcomm Atheros AR9287 Wireless Network Adapter (PCI-Express) [168c:002e] (rev 01)
	Subsystem: Foxconn International, Inc. T77H167.00 [105b:e034]
	Kernel driver in use: ath9k
cyborg@cyborg-Aspire-5750G:~$ iwconfig
enp2s0f0  no wireless extensions.


lo        no wireless extensions.


wlp3s0    IEEE 802.11bgn  ESSID:"u_wysockich"  
          Mode:Managed  Frequency:2.452 GHz  Access Point: 74:EA:3A:AB:EC:46   
          Bit Rate=1 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=39/70  Signal level=-71 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:85   Missed beacon:0
```


```
cyborg@cyborg-Aspire-5750G:~$ rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
```

---

### Post by slickymaster on 2016-01-20
*Moved to the ***Networking & Wireless*** sub-forum*

---

