---
title: "Dropped Network Can't Connect"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by munkymac on 2013-10-29
I got a new laptop about three months ago, and have had a problem this whole time: When I connect to wireless networks, my connection will remain steady for a while (sometimes a few hours) but then will eventually drop out, and one of two things will happen: The network I was connected to will be listed, but the computer will no longer connect, or the network will not be listed (though surrounding networks will be). Either way, the only solution I have is to restart the computer. This happened both on 13.04 and now on 13.10 (clean install, so it's not a problem that carried over from a previous configuration). Any help would be appreciated. Here are the relevant details:

Acer V5-131
Ubuntu Gnome 13.10 64bit
Network controller: Qualcomm Atheros AR9485 Wireless Network Adapter (rev 01)

Output of ifconfig ```
wlan0     Link encap:Ethernet  HWaddr 0c:84:dc:0c:86:4e  
          inet addr:10.12.16.129  Bcast:10.12.255.255  Mask:255.255.0.0
          inet6 addr: fe80::e84:dcff:fe0c:864e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10243 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5804 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3732668 (3.7 MB)  TX bytes:1185217 (1.1 MB)
```

Output of iwconfig ```
wlan0     IEEE 802.11bgn  ESSID:"SFPL-WIRELESS"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:18:0A:36:4E:34   
          Bit Rate=11 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/70  Signal level=-49 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:1  Invalid misc:519   Missed beacon:0

```

Output of lsmod | grep "ath9k"
```
ath9k                 151173  0 
ath9k_common           13859  1 ath9k
ath9k_hw              444645  2 ath9k_common,ath9k
ath                    23827  3 ath9k_common,ath9k,ath9k_hw
mac80211              596969  1 ath9k
cfg80211              479757  3 ath,ath9k,mac80211

```

---

### Post by Hadaka on 2013-10-29
Hi,please do..
```
sudo gedit /etc/modprobe.d/ath9k.conf
```
enter this one line of code..
```
options ath9k nohwcrypt=1
```
save and close gedit...then do..
```
sudo modprobe -rfv ath9k
sudo modprobe ath9k
```
boot
disconnect the ethernet cable,connect to wireless
let it run for awhile and see how it holds.
thanks

---

### Post by munkymac on 2013-10-31
This seems to have done the trick, but I'll wait a day or two before marking it solved. Thanks!

---

