---
title: "Ubuntu 12.04 with D-link DSL 3680 from TalkTalk UK connected to network no internet"
date: 2013-10-07
forum: Networking &amp; Wireless
---

### Post by Beershaw on 2013-10-07
Hi All,

I have a home connection with TalkTalk UK using a D-link DSL3680 router on Ubuntu 12.04. Connection works fine on Android phones and windows laptops, but on my Acer Aspire laptop with Ubuntu it connects to the network but there's no actual internet access. Wired with ethernet cable straight into router works just fine. Other wifis (in work, etc.) work with this Ubuntu machine. Tried fix with modifying iwlwificonfig (or something like that), and a bunch of others I could find on forums, but no luck. Sometimes after a while of it being connected by ethernet, if I unplug the cable the wifi seems to work. Any help is much appreciated, getting desperate here!

---

### Post by sanderj on 2013-10-07
So wired it works, but wireless not. Correct?

If only wireless connected, do this:

mtr -nrc2 8.8.8.8

Post the output here.

PS: you have to install mtr first: sudo apt-get install mtr

---

### Post by Beershaw on 2013-10-07
So now the wireless is working again, so i'm connected to it, and this is the output I get from that command:
HOST: robert-Aspire-5732Z         Loss%   Snt   Last   Avg  Best  Wrst StDev
  1.|-- 192.168.1.1                0.0%     2    3.8   4.1   3.8   4.5   0.5
  2.|-- 92.22.128.1               50.0%     2   16.4  16.4  16.4  16.4   0.0
  3.|-- 78.151.225.23              0.0%     2   16.7  17.5  16.7  18.3   1.2
  4.|-- 78.151.229.24              0.0%     2   20.2  19.2  18.2  20.2   1.4
  5.|-- 78.144.8.111               0.0%     2   24.3  24.6  24.3  24.9   0.4
  6.|-- 72.14.242.127              0.0%     2   28.3  27.2  26.0  28.3   1.6
  7.|-- 209.85.255.76              0.0%     2   26.2  25.8  25.5  26.2   0.5
  8.|-- 209.85.253.92              0.0%     2   25.2  25.7  25.2  26.3   0.8
  9.|-- 72.14.242.166              0.0%     2   31.6  31.4  31.1  31.6   0.3
 10.|-- 72.14.238.215              0.0%     2   37.6  34.2  30.8  37.6   4.8
 11.|-- 92.22.128.1               50.0%     2  371.8 371.8 371.8 371.8   0.0
 12.|-- 8.8.8.8                    0.0%     2   30.1  31.3  30.1  32.4   1.6
Should I do it again when the wireless isn't working?
Thanks for the quick reply:)

---

### Post by Beershaw on 2013-10-08
And now when wifi isn't working again I get just:
HOST: robert-Aspire-5732Z         Loss%   Snt   Last   Avg  Best  Wrst StDev

---

### Post by sanderj on 2013-10-08
If mtr gives not a single IP address, type:

```

ifconfig  #### should show if you have an ip address on your wifi interface
iwconfig   #### shows the Wifi connection
dmesg | tail -20     #### shows the last 20 messages

```

HTH

---

### Post by Beershaw on 2013-10-09
Okay did these tasks in terminal and here's what I got:

> **sanderj said:**
> If mtr gives not a single IP address, type:

```

ifconfig  #### should show if you have an ip address on your wifi interface

eth0      Link encap:Ethernet  HWaddr 00:26:22:2d:53:88  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:507 errors:0 dropped:0 overruns:0 frame:0
          TX packets:507 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:37355 (37.3 KB)  TX bytes:37355 (37.3 KB)

wlan0     Link encap:Ethernet  HWaddr 0c:60:76:5a:ba:11  
          inet addr:192.168.1.3  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe5a:ba11/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:727399 errors:0 dropped:0 overruns:0 frame:0
          TX packets:36613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:263615663 (263.6 MB)  TX bytes:5690089 (5.6 MB)


iwconfig   #### shows the Wifi connection

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"TALKTALK-27EFDE"  
          Mode:Managed  Frequency:2.467 GHz  Access Point: 78:54:2E:27:EF:DE   
          Bit Rate=39 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-31 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:19   Missed beacon:0

eth0      no wireless extensions.

dmesg | tail -20     #### shows the last 20 messages

[ 6915.853259] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 6915.853262] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[ 6915.853265] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 6915.853268] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[ 6915.853271] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 6915.853273] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[ 6915.853276] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 6915.853279] cfg80211: Updating information on frequency 2467 MHz for a 20 MHz width channel with regulatory rule:
[ 6915.853282] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 6915.853285] cfg80211: Updating information on frequency 2472 MHz for a 20 MHz width channel with regulatory rule:
[ 6915.853288] cfg80211: 2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[ 6915.853291] cfg80211: Disabling freq 2484 MHz
[ 6915.853295] cfg80211: Regulatory domain changed to country: GB
[ 6915.853297] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 6915.853300] cfg80211:     (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6915.853303] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6915.853305] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 6915.853308] cfg80211:     (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[ 6917.599307] wlan0: IPv6 duplicate address fe80::e60:76ff:fe5a:ba11 detected!
[ 6933.464721] cfg80211: Found new beacon on frequency: 2467 MHz (Ch 12) on phy

```

HTH

Any thoughts?:-S

---

