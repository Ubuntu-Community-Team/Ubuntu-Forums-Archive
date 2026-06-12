---
title: "slow wifi, loosing many packets - Ubuntu 16.04"
date: 2018-04-22
forum: Networking &amp; Wireless
---

### Post by pusiux on 2018-04-22
Hi!

I have problem with wifi connection on my Thinkpad X1 Carbon gen2 with Ubuntu 16.04 LTS. Connection is really slow, works good only when I'm sitting near to router. I am also loosing around 25% of packages.

iwconfig shows:

```
lo        no wireless extensions.


wlp3s0    IEEE 802.11  ESSID:"xxx"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 60:45:CB:10:1D:A0   
          Bit Rate=144.4 Mb/s   Tx-Power=22 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=59/70  Signal level=-51 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:2  Invalid misc:230   Missed beacon:0

enp0s25   no wireless extensions.

```

lspci | egrep -i --color 'wifi|wlan|wireless' shows:

```
03:00.0 Network controller: Intel Corporation Wireless 7260 (rev 83)
```

I am already travelling  and I have the same problem  in many places. Also second notebook with Windows 10 is working fine with the same networks, so it is probably problem with my drivers or wifi card maybe.

---

### Post by chili555 on 2018-04-22
May we see:```
dmesg | grep iwl
uname -r
```Thanks.

---

### Post by pusiux on 2018-04-24
outputs:

```
dmesg | grep iwl
[    2.526270] iwlwifi 0000:03:00.0: loaded firmware version 17.608620.0 op_mode iwlmvm
[    2.572307] iwlwifi 0000:03:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    2.612158] iwlwifi 0000:03:00.0: base HW address: e8:2a:ea:1f:0d:42
[    2.828175] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    2.829627] iwlwifi 0000:03:00.0 wlp3s0: renamed from wlan0

``````

uname -a
Linux pusiux-ThinkPad 4.13.0-38-generic #43~16.04.1-Ubuntu SMP Wed Mar 14 17:48:43 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

```

Connection looks good only when I am near to the router, when there is no wall etc.

---

### Post by chili555 on 2018-04-25
Frankly, your readings look just perfect and, in fact, identical to the readings I get on my own Intel 7260!

When I read this:> Connection looks good only when I am near to the router, when there is no wall etc.And this:> Connection is really slow, works good only when I'm sitting near to router. I then wonder if the antenna connections are secure. Can you open the computer and check?

[IMG]https://ae01.alicdn.com/kf/HTB1qHlYQXXXXXXcXFXXq6xXFXXXs/IPEX-MHF4-Internal-Antenna-Laptop-NGFF-for-Intel-7260-3160-8260-Wifi-WLAN-Card-3G-N5321.jpg[/IMG]

---

