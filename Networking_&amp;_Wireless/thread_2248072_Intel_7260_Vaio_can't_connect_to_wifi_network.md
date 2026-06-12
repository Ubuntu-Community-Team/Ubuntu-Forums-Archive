---
title: "Intel 7260 Vaio can't connect to wifi network"
date: 2014-10-12
forum: Networking &amp; Wireless
---

### Post by Damwdan on 2014-10-12
Hi there,

I must finally come to you, this problem is obviously beyond my understanding and even after all the time I spent looking for a solution, I still can't fix it.

First off, I have a Sony Vaio Pro 13 (hostname titanium, in the logs) which, despite the all the fine hardware it came with, caused me a lot of troubles when I was setting up Ubuntu (uefi wasn't very well supported at the time). So a lot of things could originate from this.

My problem is that I can't connect to the wifi. I have had some difficulties in the past with it, but most of the time restarting NetworkManager did the trick or, worst case scenario, turning wifi off and on again worked. But this time, nothing I have tried so far even showed the slightest change. About a week ago, it was working fine and I could connect to this open network (the one giving me troubles now, called ZyXEL) but then I restarted my computer because I had to check something on Windows and when I booted back on Ubuntu, it just wouldn't connect anymore.

The symptoms are always the same: I log in, I can see the nm-applet starting to connect, at some point it says "Connected" but I don't have an IP, I see the i3status wifi indicator saying it's down, then the nm-applet says I'm disconnected and the wifi network is actually gone.
Underlying, I have noticed a few more things: running dmesg (see below) shows the same message over and over again until the network is gone and on i3, the wifi indicator sometimes turn green saying I am connected (sometimes with an IP, sometimes without) for half a second then goes back red.

```
$ sudo dmesg | grep iwl
[    8.504518] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
[    8.504688] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[    8.504741] iwlwifi 0000:01:00.0: irq 62 for MSI/MSI-X
[    8.509733] iwlwifi 0000:01:00.0: loaded firmware version 22.1.7.0 op_mode iwlmvm
[    8.543044] iwlwifi 0000:01:00.0: Detected Intel(R) Dual Band Wireless N 7260, REV=0x144
[    8.543143] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[    8.543351] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[    8.751609] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    9.090794] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[    9.090999] iwlwifi 0000:01:00.0: L1 Disabled; Enabling L0S
[   16.824696] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   20.941093] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   25.062175] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   29.190767] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   33.306923] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   37.426013] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   41.545197] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   45.668880] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   49.793807] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   53.911716] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   58.030447] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
[   62.146646] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
```

```
$ cat /var/log/syslog | grep -e iwl -e 80211 | tail -n 60
Oct 11 18:45:01 titanium kernel: [ 1362.632556] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
Oct 11 18:45:01 titanium kernel: [ 1362.641409] cfg80211: Calling CRDA to update world regulatory domain
Oct 11 18:45:01 titanium kernel: [ 1362.646666] cfg80211: World regulatory domain updated:
Oct 11 18:45:01 titanium kernel: [ 1362.646673] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 11 18:45:01 titanium kernel: [ 1362.646679] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:01 titanium kernel: [ 1362.646683] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:01 titanium kernel: [ 1362.646686] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:01 titanium kernel: [ 1362.646689] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:01 titanium kernel: [ 1362.646693] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:04 titanium kernel: [ 1366.414932] cfg80211: Calling CRDA for country: AT
Oct 11 18:45:04 titanium kernel: [ 1366.421278] cfg80211: Regulatory domain changed to country: AT
Oct 11 18:45:04 titanium kernel: [ 1366.421288] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 11 18:45:04 titanium kernel: [ 1366.421295] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 11 18:45:04 titanium kernel: [ 1366.421300] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 11 18:45:04 titanium kernel: [ 1366.421305] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 11 18:45:04 titanium kernel: [ 1366.421309] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Oct 11 18:45:04 titanium kernel: [ 1366.421315] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Oct 11 18:45:05 titanium kernel: [ 1366.710358] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
Oct 11 18:45:05 titanium kernel: [ 1366.716651] cfg80211: Calling CRDA to update world regulatory domain
Oct 11 18:45:05 titanium kernel: [ 1366.721739] cfg80211: World regulatory domain updated:
Oct 11 18:45:05 titanium kernel: [ 1366.721746] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 11 18:45:05 titanium kernel: [ 1366.721752] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:05 titanium kernel: [ 1366.721756] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:05 titanium kernel: [ 1366.721759] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:05 titanium kernel: [ 1366.721763] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:05 titanium kernel: [ 1366.721766] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:08 titanium kernel: [ 1370.486093] cfg80211: Calling CRDA for country: AT
Oct 11 18:45:08 titanium kernel: [ 1370.491948] cfg80211: Regulatory domain changed to country: AT
Oct 11 18:45:08 titanium kernel: [ 1370.491959] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 11 18:45:08 titanium kernel: [ 1370.491966] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 11 18:45:08 titanium kernel: [ 1370.491972] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 11 18:45:08 titanium kernel: [ 1370.491977] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
Oct 11 18:45:08 titanium kernel: [ 1370.491983] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
Oct 11 18:45:08 titanium kernel: [ 1370.491989] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
Oct 11 18:45:09 titanium kernel: [ 1370.785509] iwlwifi 0000:01:00.0: No assocation and the time event is over already...
Oct 11 18:45:09 titanium kernel: [ 1370.792019] cfg80211: Calling CRDA to update world regulatory domain
Oct 11 18:45:09 titanium kernel: [ 1370.797199] cfg80211: World regulatory domain updated:
Oct 11 18:45:09 titanium kernel: [ 1370.797206] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
Oct 11 18:45:09 titanium kernel: [ 1370.797211] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:09 titanium kernel: [ 1370.797216] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:09 titanium kernel: [ 1370.797219] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:09 titanium kernel: [ 1370.797222] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
Oct 11 18:45:09 titanium kernel: [ 1370.797226] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
```

Since the problem first happened, I have tried a lot of things : rfkill-ing on and off, modprob-ing the iwlwifi on and off, killing NetworkManager, moving to wicd and back to nm, rebooting the computer (duh) and the box. I also tried to upgrade the intel firmware but I'm an unsure of how it actually had an impact. So i have to say, I don't really know what to do anymore. I should mention that it connects on my network at work which is protected (Netgear, in the logs), and ZyXEL isn't, but I don't know how that's relevant, especially since I could connect fine a few days ago.

I have attached the wireless_script output, it seems to me that iwlwifi does not use the latest firmware but I really can't say for sure.

Thank you!

---

### Post by jeremy31 on 2014-10-12
First thing to do is upgrade to 14.04 as 13.10 is no longer supported

---

### Post by LarryJ2 on 2014-10-21
Lenovo Y50-70 with Intel 7260.   14.04  currently has this problem.   Going to try  14.10

lj@lenovo:~$ uname -a
Linux lenovo 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

---

### Post by jeremy31 on 2014-10-21
> **LarryJ2 said:**
> Lenovo Y50-70 with Intel 7260.   14.04  currently has this problem.   Going to try  14.10

lj@lenovo:~$ uname -a
Linux lenovo 3.13.0-37-generic #64-Ubuntu SMP Mon Sep 22 21:28:38 UTC 2014 x86_64 x86_64 x86_64 GNU/Linux

Post the results of ```
lspci -nnk | grep -iA2 net
```
You may have a version that is not supported yet

Or boot back into windows to see if it is still enabled there

---

