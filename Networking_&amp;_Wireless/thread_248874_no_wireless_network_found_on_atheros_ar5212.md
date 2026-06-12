---
title: "no wireless network found on atheros ar5212"
date: 2006-09-01
forum: Networking &amp; Wireless
---

### Post by kamilczauz on 2006-09-01
hey guys....

ive been on this for days now... and can not figure anything out.

I put a mini pci atheros ar5212 card in my thinkpad t23, heres a link to the card.

[http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ih=015&item=250019925135&rd=1&sspagename=STRK%3AMEWN%3AIT&rd=1](http://cgi.ebay.com/ws/eBayISAPI.dll?ViewItem&ih=015&item=250019925135&rd=1&sspagename=STRK%3AMEWN%3AIT&rd=1)


It just wont find me any networks.

Heres wat happens when i run a few commands...

```
kamil@kamil-laptop:~$ iwlist ath0 scan
ath0      Failed to read scan data : Resource temporarily unavailable



kamil@kamil-laptop:~$ iwconfig ath0 
ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Frequency:2.442 GHz  Access Point: Not-Associated   
          Bit Rate=11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0





kamil@kamil-laptop:~$ ifconfig ath0
ath0      Link encap:Ethernet  HWaddr 00:14:78:77:58:78  
          inet6 addr: fe80::214:78ff:fe77:5878/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:200 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:d8ac0000-d8ad0000 



kamil@kamil-laptop:~$ dmesg|less|grep 'ath
> '
[17179596.744000] ath_hal: module license 'Proprietary' taints kernel.
[17179596.748000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179596.832000] ath_rate_sample: 1.2
[17179596.844000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179597.788000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179597.788000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179597.788000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179597.788000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179597.788000] ath0: mac 7.9 phy 4.5 radio 5.6
[17179597.788000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179597.788000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179597.788000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179597.788000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179597.788000] ath0: Use hw queue 8 for CAB traffic
[17179597.788000] ath0: Use hw queue 9 for beacons
[17179597.788000] ath0: Atheros 5212: mem=0xc0200000, irq=11
[17179614.288000] ath0: no IPv6 routers present
[17179968.080000] ath0: no IPv6 routers present

```

please help... i really dont know what to do... ive tried several different AP, and no success

Thanks
Kamil

---

### Post by tturrisi on 2006-09-02
post the results of:

sudo iwlist ath0 scan

---

### Post by kamilczauz on 2006-09-02
its been posted above, here it is again

kamil@kamil-laptop:~$ sudo iwlist ath0 scan
Password:
ath0      Failed to read scan data : Resource temporarily unavailable

kamil@kamil-laptop:~$

---

### Post by kamilczauz on 2006-09-03
still no internet... please help:(

---

