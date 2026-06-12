---
title: "[Ubuntu 14.04.1] RTL8111/8168 Either not connecting or dropping"
date: 2014-12-16
forum: Networking &amp; Wireless
---

### Post by Ersin Kandemir on 2014-12-16
Hi, i'm in an annoying trouble with wi-fi access to college's "eduroam" network for a few days.

I had been using Ubuntu 14.04 LTS which i could use the wireless though it was dropping at regular intervals but not too frequently. Then i decided to switch it up to 14.10 with clean install without upgrading. It began to raise issue to connect to network and keep usable. I've tried higher kernels on 14.10 and even 15.04 with built-in wireless device. (**Broadcom  BCM43142** with **bcmwl-kernel-source**) but problem never sorted out in spite of trying almost all the solution about this device on the internet. So i bought an USB wireless adapter named **Dark RangeMax (Realtek RTL8111/8168). **This adapter keeps similar issues with built-in device. It either never connects or connects but not keep usable over just two minutes (disconnects or no web access).

What i have tried:


[LIST]
[*]Bought new adapter. 8-[ 
[*]Since "eduroam" has WPA Enterprise / Tunneled TLS - PAP security, i've chosen many CA certs to connect. 
[*]Since "eduroam" has multiple APs, i've set the BSSID to single AP. 
[*]Fixed the MTU 1500 instead of automatic. 
[*]Ignored IPv6. 
[*]Disabled N mode for both device. (disclaimer built-in, i just want to use the new one.) 
[*]Set power management off. 
[*]... 
[/LIST]

I researched all the forums and see many people to have solved their problem with the solutions above but not mine. I reinstall the 14.04.1 LTS because i played so much with older. Now i have clean system with all the updates done. I just ignore the built-in device and not installed the bcmwl driver. 

Thanks for help, here is my script output: [ATTACH]258643[/ATTACH]

And dmesg while trying to connect; it doesn't always happen. I have many ways not to connect to damn network. :| 

```
[ 2671.512490] wlan1: authenticate with 20:37:06:12:24:f1
[ 2671.535904] wlan1: send auth to 20:37:06:12:24:f1 (try 1/3)
[ 2671.554278] wlan1: authenticated
[ 2671.555727] wlan1: associate with 20:37:06:12:24:f1 (try 1/3)
[ 2671.659841] wlan1: associate with 20:37:06:12:24:f1 (try 2/3)
[ 2671.763962] wlan1: associate with 20:37:06:12:24:f1 (try 3/3)
[ 2671.867992] wlan1: association with 20:37:06:12:24:f1 timed out
[ 2682.029086] wlan1: authenticate with 20:37:06:6c:90:31
[ 2682.053022] wlan1: send auth to 20:37:06:6c:90:31 (try 1/3)
[ 2682.144965] wlan1: authenticated
[ 2682.148767] wlan1: associate with 20:37:06:6c:90:31 (try 1/3)
[ 2682.252820] wlan1: associate with 20:37:06:6c:90:31 (try 2/3)
[ 2682.356995] wlan1: associate with 20:37:06:6c:90:31 (try 3/3)
[ 2682.461028] wlan1: association with 20:37:06:6c:90:31 timed out

```

Sorry for any missing information,

**Edit:** This is how it doesn't connect now:

```

[ 2780.684975] wlan1: authenticate with e8:ed:f3:ea:64:f1
[ 2780.710565] wlan1: send auth to e8:ed:f3:ea:64:f1 (try 1/3)
[ 2780.812577] wlan1: send auth to e8:ed:f3:ea:64:f1 (try 2/3)
[ 2780.890663] wlan1: authenticated
[ 2780.892677] wlan1: associate with e8:ed:f3:ea:64:f1 (try 1/3)
[ 2780.945289] wlan1: RX AssocResp from e8:ed:f3:ea:64:f1 (capab=0x431 status=0 aid=1)
[ 2780.945322] wlan1: associated
[ 2780.945503] IPv6: ADDRCONF(NETDEV_CHANGE): wlan1: link becomes ready
[ 2780.945565] cfg80211: Calling CRDA for country: TR
[ 2780.948461] cfg80211: Regulatory domain changed to country: TR
[ 2780.948465] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2780.948466] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2780.948467] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[ 2780.948469] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[ 2780.948470] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[ 2784.127346] wlan1: deauthenticating from e8:ed:f3:ea:64:f1 by local choice (reason=3)
[ 2784.140534] cfg80211: Calling CRDA to update world regulatory domain
[ 2784.143348] cfg80211: World regulatory domain updated:
[ 2784.143353] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2784.143354] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2784.143356] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2784.143357] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2784.143359] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2784.143360] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2796.382778] wlan1: authenticate with e8:ed:f3:ea:64:f1
[ 2796.422606] wlan1: send auth to e8:ed:f3:ea:64:f1 (try 1/3)
[ 2796.439416] wlan1: authenticated
[ 2796.441891] wlan1: associate with e8:ed:f3:ea:64:f1 (try 1/3)
[ 2796.469534] wlan1: RX AssocResp from e8:ed:f3:ea:64:f1 (capab=0x431 status=0 aid=1)
[ 2796.469584] wlan1: associated
[ 2796.469675] cfg80211: Calling CRDA for country: TR
[ 2796.474684] cfg80211: Regulatory domain changed to country: TR
[ 2796.474691] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2796.474694] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[ 2796.474697] cfg80211:   (5170000 KHz - 5250000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[ 2796.474699] cfg80211:   (5250000 KHz - 5330000 KHz @ 20000 KHz), (N/A, 2000 mBm)
[ 2796.474702] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[ 2799.635476] wlan1: deauthenticating from e8:ed:f3:ea:64:f1 by local choice (reason=3)
[ 2799.648351] cfg80211: Calling CRDA to update world regulatory domain
[ 2799.652255] cfg80211: World regulatory domain updated:
[ 2799.652261] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[ 2799.652265] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2799.652268] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2799.652270] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[ 2799.652273] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[ 2799.652275] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)



```

---

### Post by Ersin Kandemir on 2014-12-17
I'm sorry if it is disturbing to up the topic, but i need help. Anyone knows what i am supposed to do?

---

### Post by chili555 on 2014-12-17
I suggest you try this: [http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617](http://askubuntu.com/questions/425583/ubuntu-connect-drops-worked-for-a-while-then-started-dropping-again/425617#425617)

---

### Post by Ersin Kandemir on 2014-12-18
Thanks for your reply, i've already tried:

[QUOTE=Ersin Kandemir]
What i have tried:


[LIST]
[*]Bought new adapter. 8-[
[*]Since "eduroam" has WPA Enterprise / Tunneled TLS - PAP security, i've chosen many CA certs to connect.
[*]_**Since "eduroam" has multiple APs, i've set the BSSID to single AP.**_
[*]Fixed the MTU 1500 instead of automatic.
[*]Ignored IPv6.
[*]Disabled N mode for both device. (disclaimer built-in, i just want to use the new one.)
[*]Set power management off.
[*]...
[/LIST]
[/QUOTE]

---

### Post by Ersin Kandemir on 2014-12-19
Still not able to connect.:roll:

---

### Post by Ersin Kandemir on 2014-12-20
Any idea yet?

---

### Post by Ersin Kandemir on 2014-12-22
OK guys, this is the solution:

 [IMG]http://img3.wikia.nocookie.net/__cb20121109111615/glee/images/2/27/Burn_computer.gif[/IMG]

---

