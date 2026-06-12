---
title: "Netgear A6210 Not working right"
date: 2024-03-20
forum: Networking &amp; Wireless
---

### Post by wohk on 2024-03-20
I looked through some other solutions but they didn't work for me so im making a thread
My downloads and general speeds are about half of what they should be
(I just downloaded ubuntu as my first ever linux distro and im very lost)

---

### Post by jeremy31 on 2024-03-20
See the wireless script link in my signature and post results

---

### Post by wohk on 2024-03-20
[URL="https://pastebin.com/wUBw38GL"]https://pastebin.com/wUBw38GL
I configured safe boot so third party drivers and then i installed the generic headers, whenever i try to run make on kadukes's A6210 driver i get this error 

[/URL][LEFT]cp -f os/linux/Makefile.6 /home/wohk/Netgear-A6210/os/linux/Makefile make -C /lib/modules/6.5.0-26-generic/build DBGFLAGS=-DDBG SUBDIRS=/home/wohk/Netgear-A6210/os/linux modules make[1]: Entering directory '/usr/src/linux-headers-6.5.0-26-generic'   SYNC    include/config/auto.conf.cmd   HOSTCC  scripts/basic/fixdep /bin/sh: 1: gcc-12: not found make[4]: *** [scripts/Makefile.host:114: scripts/basic/fixdep] Error 127 make[3]: *** [Makefile:644: scripts_basic] Error 2 /usr/src/linux-headers-6.5.0-26-generic/Makefile:786: include/config/auto.conf.cmd: No such file or directory make[2]: *** [/usr/src/linux-headers-6.5.0-26-generic/Makefile:809: include/config/auto.conf.cmd] Error 2 make[1]: *** [Makefile:234: __sub-make] Error 2 make[1]: Leaving directory '/usr/src/linux-headers-6.5.0-26-generic' make: *** [Makefile:64: debug] Error 2[/LEFT]

---

### Post by TheFu on 2024-03-21
There are 2 sides to every download.  You have the client-side.  Someone else runs the server.  On my servers, I limit the bandwidth that each visitor can have, so that other users aren't stuck waiting or worse.

That isn't to say the system doesn't have some performance issues, but it is just something to consider.  Servers don't have unlimited bandwidth and they need to share it across hundreds of connections, not just yours.

I didn't look at the pastbin.

---

### Post by praseodym on 2024-03-22
```
sudo apt install linssid
```
Search a free channel with that tool

---

### Post by TheFu on 2024-03-22
```
SSID                 BSSID              MODE   CHAN  FREQ      RATE        SIGNAL  BARS  SECURITY   ACTIVE  IN-USE 
SockMonkey           <MAC 'SockMonkey' [AN1]>  Infra  6     2437 MHz  [COLOR="#FF0000"]54 Mbit/s[/COLOR]   74      &#9602;&#9604;&#9606;_  WPA1 WPA2  no             
House-Guest          <MAC 'House-Guest' [AN2]>  Infra  9     2452 MHz  [COLOR="#FF0000"]130 Mbit/s[/COLOR]  74      &#9602;&#9604;&#9606;_  WPA2       no             
MySpectrumWiFic2-2G  <MAC 'MySpectrumWiFic2-2G' [AN3]>  Infra  11    2462 MHz  [COLOR="#FF0000"]195 Mbit/s[/COLOR]  72      &#9602;&#9604;&#9606;_  WPA2       no             
--                   <MAC '--' [AN4]>  Infra  9     2452 MHz  130 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2       no             
House                <MAC 'House' [AN5]>  Infra  9     2452 MHz  130 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA2       no             
reyes                <MAC 'reyes' [AN6]>  Infra  2     2417 MHz  540 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       no             
--                   <MAC '--' [AN7]>  Infra  2     2417 MHz  130 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA2       no             
VR217-68D8           <MAC 'VR217-68D8' [AN8]>  Infra  3     2422 MHz  270 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA2       no             
The culdeSAC         <MAC 'The culdeSAC' [AN9]>  Infra  40    5200 MHz  270 Mbit/s  54      &#9602;&#9604;__  WPA2       no             
**MySpectrumWiFic2-5G  <MAC 'MySpectrumWiFic2-5G' [AN10]>  Infra  40    5200 MHz  [COLOR="#FF0000"]405 Mbit/s[/COLOR]  43      &#9602;&#9604;__  WPA2       [COLOR="#00FF00"]yes[/COLOR]     *  **
```

If your wifi connection is weak or cannot connect faster, look first at the local environment.

You claim: 
> My downloads and general speeds are about half of what they should be

Why do you believe that?  What do you think it should be and what are the real-world transfer rates on your LAN?  Forget the internet for now, that isn't something you or I can control.  Use **iperf3** between 2 systems on your LAN.  It would be best if both were wired ethernet first as a baseline.  Then one with wifi for a second test.  

I don't have any wifi devices here, but going between 2 GigE NICs with iperf3 returns about 930+ Mbps.  
```
[ ID] Interval           Transfer     Bitrate
[  5]   0.00-10.04  sec  1.09 GBytes   936 Mbits/sec                  receiver
```

My internet connection returns:
```
Download: 29.44 Mbit/s
Upload: 6.39 Mbit/s

```

Just ran both of those in the last few minutes.

When I had a fiber ISP, I was limited to about 300 Mbps symmetric.  My router doesn't go faster than about 500 Mbps per connection, though it has GigE capable hardware.  With 4 different connections, each gets a different thread on the router and it does get to 920 Mbps. My router has a low-power (12W) AMD CPU from 2014, so it isn't great at fast, single connection, throughput.  I tested the throughput between putting it in as my edge router.

Anyway, seems your router is only connecting at slower than expected speeds.  What 802.11? standards does it support?  Is the computer in the same room with the router? The there is a brick/cement wall between the computer and router, 5Ghz can't be used, only 2.4Ghz will go through that.  Different frequencies work better in different environments.  Also, for 2.4Ghz, there are only 3 channels that don't overlap 1, 6, 11. All others overlap and reduce bandwidth.

The "House-Guest" on channel 9 is a problem.  Make that channel 1.
The "VR217-68D8" is stronger than your selected channel. It is an overlapping channel too. Not great.
The signal level for MySpectrumWiFic2-5G on channel 40 is low. Get closer or remove obstructions.
_"The culdeSAC" is stronger AND on the same channel as your connected channel. That needs to be avoided completely._  Move to a channel that isn't anywhere in the list, off 40.

---

