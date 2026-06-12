---
title: "Slow WiFi Connection with Centrino Wireless-N 1000 and Ubuntu 18.04.4 LTS"
date: 2020-05-06
forum: Networking &amp; Wireless
---

### Post by unogold on 2020-05-06
Hi Forum Members,

I am experiencing continued intermittent wifi speeds with Centrino Wireless-N 1000 and Ubuntu 18.04.4 LTS. 

I implemented the suggestions of Chili555 [here]("https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520").

And configured /etc/modprobe.d/iwlwifi.conf with the following content:

```
options iwlwifi 11n_disable=1
options iwlwifi swcrypto=1
options iwlwifi 11n_disable=8
options iwlwifi bt_coex_active=0 
```

based on suggestions [here]("https://askubuntu.com/questions/1029723/slow-wifi-since-updating-to-18-04") and [here]("https://unix.stackexchange.com/questions/404287/wifi-suddenly-extremely-slow").

I updated the wifi drivers based upon the suggestion [here]("https://askubuntu.com/questions/1049307/slow-wifi-with-ubuntu-18-04-and-intel-dual-band-wireless-ac-3168/1063311#1063311").

Output of lspci -knn | grep Net -A2:

```
05:00.0 Network controller [0280]: Intel Corporation Centrino Wireless-N 1000 [Condor Peak] [8086:0084]
    Subsystem: Intel Corporation Centrino Wireless-N 1000 BGN [8086:1315]
    Kernel driver in use: iwlwifi
--
09:00.0 Ethernet controller [0200]: Broadcom Inc. and subsidiaries NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
    Subsystem: Lenovo NetLink BCM57780 Gigabit Ethernet PCIe [17aa:38cf]
    Kernel driver in use: tg3
    Kernel modules: tg3 
```

Output of iwconfig:

```
wlp5s0    IEEE 802.11  ESSID:"--------"  
          Mode:Managed  Frequency:2.422 GHz  Access Point: --:--:--:--:--:--   
          Bit Rate=65 Mb/s   Tx-Power=14 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=70/70  Signal level=-21 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:483   Missed beacon:0 
```
I haven't been able to identify what conditions slow the wifi. I have a Windows machine located next to this machine and I can confirm the Windows machine on the same network has appropriate wifi speeds when the Ubuntu machine slows.

Any help will be appreciated.

Thanks in advance!

---

### Post by unogold on 2020-05-19
Bump.

Any suggestions of paths to query. 

Download speed currently 0.46 Mbit/s.

I would greatly appreciate any suggestions.

Thanks!

---

### Post by miguelpires on 2020-05-20
Hi,
I've the same problem but with 20.04. 

Have you HWE kernels? 

If you an please subscribe to this bug report [URL="https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1878480"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1878480 
[/URL]
Regards
Miguel

---

### Post by tomdkat on 2020-05-20
I'm encountering a similar issue on Linux Mint 18.3.  The bit rate never goes above 65 Mbps *but* my download speeds are actually good.  I'm using the iwlwifi driver and the only change I made was to enable Tx AMPDU (11n_disable=8 driver setting).  I can get up to 80 Mbps download speeds, from various speed test sites (speedtest.net, Google Fiber speed test, DSL reports).   What's odd is, if I connect to a D-Link DAP-1650 access point, the bit rate can jump as high as 130 Mbps, but comes back down to 65 Mbps (eventually).   For the longest time, the bit rate would start at 65 Mbps and drop to 6 or 7.2.  When it would drop to those levels, I couldn't ping any websites.  I even replaced my wireless router (went from a TRENDNET TEW-824DRU to a TP-Link AC1750 Archer A7) and the adapter still won't connect at speeds faster than 65 Mbps.   I also changed my router to use 802.11n *only* and set the channel width back to 20/40 MHz (Auto) from being only 20 MHz.

Right now, these settings are what I currently have:

Wireless router broadcasting 802.11n (only) @ 2.4GHz on channel 11
Lenovo laptop running Linut Mint 18.3 with iwlwifi set to enable Tx AMPUD (11n_disable=8)

wireless bit rate: 65Mbps

I can boot Ubuntu 20.04 on this laptop (live USB) and can see how it behaves any differently.    I'm very interested in this discussion because I can't understand why I can't get any faster connection speeds to the wireless router.

Peace...

---

### Post by tomdkat on 2020-05-21
Well, I booted Ubuntu 20.04 on my Lenovo laptop and the wireless connection was stable.  The bit rate stayed at 65 Mbps, but I was able to achieve download speeds around 80Mbps.

Peace...

---

### Post by unogold on 2020-05-27
Download speed now 53.6 Mbps. So the WiFi speed fluctuates by 2 orders of magnitude.

@Miguel: I have not [COLOR=#333333][FONT=&amp]opted into the HWE Kernel stream.[/FONT][/COLOR]  

Can anyone suggest what to log to evaluate and further debug?

---

