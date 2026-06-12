---
title: "Card capable of 801.11ac, connects only on 801.11abg"
date: 2016-12-15
forum: Networking &amp; Wireless
---

### Post by antouank on 2016-12-15
Hi.

I got today a new wifi card, [TP-LINK Archer T6E]("https://www.amazon.co.uk/gp/product/B013HCNTZU/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1") .
After some help I found in this forum, I got the 'bcmwl-kernel-source' package, and the card got recognized.

My issue is that even though it's capable of 802.11ac, I can see it connects on 802.11abg.
And having a 200Mbit connection, that's a bummer.

Same PC on windows, I get 802.11ac. So it's not a hardware issue.

I'll paste some info from the diagnose script you have on this forum.

```

##### kernel ############################

Linux 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

04:00.0 Network controller [0280]: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:43a0] (rev 03)
    Subsystem: Broadcom Corporation BCM4360 802.11ac Wireless Network Adapter [14e4:0619] [COLOR=#000000] Kernel driver in use: wl

[/COLOR]##### lsmod #############################

wl                   6365184  0
cfg80211              565248  1 wl
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau


##### ifconfig ##########################

br-fef0c5d7169c Link encap:Ethernet  HWaddr <MAC 'br-fef0c5d7169c' [IF1]>  
          inet addr:172.18.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

docker0   Link encap:Ethernet  HWaddr <MAC 'docker0' [IF2]>  
          inet addr:172.17.0.1  Bcast:0.0.0.0  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enp5s0    Link encap:Ethernet  HWaddr <MAC 'enp5s0' [IF3]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlp4s0    Link encap:Ethernet  HWaddr <MAC 'wlp4s0' [IF4]>  
          inet addr:192.168.0.23  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f994:e317:acec:c694/64 Scope:Link
          inet6 addr: fdb4:1f03:5ce9:1:a24f:67ac:3bfc:aa73/64 Scope:Global
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:265821 errors:0 dropped:0 overruns:0 frame:72138
          TX packets:167959 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:139785121 (139.7 MB)  TX bytes:70645706 (70.6 MB)
          Interrupt:16 Base address:0x8000 

##### iwconfig ##########################

lo        no wireless extensions.

br-fef0c5d7169c  no wireless extensions.

enp5s0    no wireless extensions.

docker0   no wireless extensions.

wlp4s0    IEEE 802.11abg  ESSID:"VM9373953"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'VM9373953' [AC1]>   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```

Any idea on how I can enable 802.11ac?

Thanks.

---

### Post by Hadaka on 2016-12-15
Hi, Broadcom Corporation does not support unix/linux and while you have
the correct driver "wl" that allows it to function. It is a known issue and the 
best advice is to get a known linux supported highspeed wifi card for your
type computer. Intel,think penguin and a few others. also in the future when
you post the wireless script, please post the entire script output. I see one issue
you have with power management on that can slow things down, but i would guess
there are likely other items adding to a sluggish connection.
thanks and good luck to you.

---

### Post by antouank on 2016-12-16
Thanks for the response.

I just got the card yesterday, so I guess I can return it.
Is there another 802.11ac PCI-express card you can suggest?

I don't think the connection is sluggish. 
Right now on speedtests I get ~54Mbps. Which is what 802.11abg supports from what I understand. So it's the protocol limit, not the wifi. Correct?
If I switch to windows I immediately get 200Mbps.

I didn't post the whole output because a) it's long, b) there were many details in there, like my IP, username, etc, so I don't know if that's a good idea. 
But the link is public anyway, so here you go : paste.ubuntu.com/23635472


edit: Maybe this one would do? [https://www.amazon.co.uk/Intel-Wireless-AC-802-11ac-Bluetooth-Brackets/dp/B00HATR6IS/](https://www.amazon.co.uk/Intel-Wireless-AC-802-11ac-Bluetooth-Brackets/dp/B00HATR6IS/)
or this one : [https://www.dlink-direct.co.uk/dwa-582](https://www.dlink-direct.co.uk/dwa-582)

---

### Post by chili555 on 2016-12-16
Here is a speed test from my Intel 7260: [http://www.dslreports.com/speedtest/7373978](http://www.dslreports.com/speedtest/7373978) It is somewhat limited by my AC1750 router that is not the latest, greatest $400+ unit bristling with antennae like a porcupine.

---

### Post by antouank on 2016-12-16
> **chili555 said:**
> Here is a speed test from my Intel 7260: [http://www.dslreports.com/speedtest/7373978](http://www.dslreports.com/speedtest/7373978) It is somewhat limited by my AC1750 router that is not the latest, greatest $400+ unit bristling with antennae like a porcupine.
Is this one ([https://www.amazon.co.uk/Intel-Wireless-AC-802-11ac-Bluetooth-Brackets/dp/B00HATR6IS/](https://www.amazon.co.uk/Intel-Wireless-AC-802-11ac-Bluetooth-Brackets/dp/B00HATR6IS/)) using that chipset?

---

### Post by chili555 on 2016-12-16
I haven't that exact device so I haven't tested it, but I'm very confident that it is. I suggest the latest driver; that is, kernel 4.8 and the latest firmware. I found big, big improvement when I got the -17 firmware. It is included in linux-firmware-1.160 and later.

Please see: [https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_7260_(7260HMWDTX1)](https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_7260_(7260HMWDTX1)) This says the pci.id is 8086:08b2. Indeed, I have:```
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [[COLOR="#FF0000"]8086:08b2[/COLOR]] (rev 83)

```For what it's worth, mine is the laptop version; about as big as a postage stamp!

---

### Post by antouank on 2016-12-17
> **chili555 said:**
> I haven't that exact device so I haven't tested it, but I'm very confident that it is. I suggest the latest driver; that is, kernel 4.8 and the latest firmware. I found big, big improvement when I got the -17 firmware. It is included in linux-firmware-1.160 and later.

Please see: [https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_7260_(7260HMWDTX1)](https://wikidevi.com/wiki/Intel_Dual_Band_Wireless-AC_7260_(7260HMWDTX1)) This says the pci.id is 8086:08b2. Indeed, I have:```
03:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [[COLOR=#FF0000]8086:08b2[/COLOR]] (rev 83)

```For what it's worth, mine is the laptop version; about as big as a postage stamp!
I went ahead and ordered that Intel card. Thanks for the help.

---

### Post by chili555 on 2016-12-17
> **antouank said:**
> I went ahead and ordered that Intel card. Thanks for the help.Good luck and keep us posted!

---

### Post by antouank on 2016-12-21
The Intel card solved the problem instantly.
I didn't need to install drivers or anything.

[http://www.dslreports.com/speedtest/7659118](http://www.dslreports.com/speedtest/7659118)
[IMG]http://www.dslreports.com/speedtest/7659118.png[/IMG]


( on a 200Mbit line )

---

### Post by chili555 on 2016-12-21
Awesome! Glad it's working as expected.

---

### Post by antouank on 2016-12-21
*Small note:* although I can see speeds that should be in 802.11ac, I can now see the interface reporting 802.11abgn as the protocol.
So I'm still not getting 802.11ac? I guess the "n" addition bumped the speeds up?

It's a bit confusing.

I got the drivers from Intel as well, but after rebooting, and doing also modprobe, I see the same.

[ATTACH=CONFIG]272800[/ATTACH]

---

### Post by chili555 on 2016-12-21
I suspect you got the firmware, not the actual driver, from Intel. I also doubt that it's the latest available, remarkably enough. Which firmware loads?```
dmesg | grep iwl
```We hope it is:```
iwlwifi 0000:03:00.0: loaded firmware version[COLOR="#FF0000"] 17[/COLOR].352738.0 op_mode iwlmvm

```In your attachment, we clearly see VHT and 468 Mbps which suggest that, if there is little RF interference, the channel is not too crowded, the distance between you and the router is short and uncluttered (unlike the rat's nest in my closet) and you squint your eyes just right, that AC is working.

---

### Post by antouank on 2016-12-21
> **chili555 said:**
> I suspect you got the firmware, not the actual driver, from Intel. I also doubt that it's the latest available, remarkably enough. Which firmware loads?```
dmesg | grep iwl
```We hope it is:```
iwlwifi 0000:03:00.0: loaded firmware version[COLOR=#FF0000] 17[/COLOR].352738.0 op_mode iwlmvm

```In your attachment, we clearly see VHT and 468 Mbps which suggest that, if there is little RF interference, the channel is not too crowded, the distance between you and the router is short and uncluttered (unlike the rat's nest in my closet) and you squint your eyes just right, that AC is working.

```

-> % dmesg | grep iwl
[    4.999257] iwlwifi 0000:04:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[    5.069247] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[    5.069295] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[    5.069503] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[    5.274548] ieee80211 phy0: Selected rate control algorithm 'iwl-mvm-rs'
[    5.279799] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
[    5.607498] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[    5.607711] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[    5.800022] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[    5.800236] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2488.296325] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2488.428423] iwlwifi 0000:04:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[ 2488.448034] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[ 2488.448082] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2488.448280] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2488.656563] ieee80211 phy1: Selected rate control algorithm 'iwl-mvm-rs'
[ 2488.658042] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
[ 2488.680310] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2488.680521] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2488.885410] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2488.885619] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2524.303620] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2524.426169] iwlwifi: unknown parameter '11nc_disable' ignored
[ 2524.427051] iwlwifi 0000:04:00.0: loaded firmware version 17.352738.0 op_mode iwlmvm
[ 2524.447223] iwlwifi 0000:04:00.0: Detected Intel(R) Dual Band Wireless AC 7260, REV=0x144
[ 2524.447271] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2524.447506] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2524.642554] ieee80211 phy2: Selected rate control algorithm 'iwl-mvm-rs'
[ 2524.645895] iwlwifi 0000:04:00.0 wlp4s0: renamed from wlan0
[ 2524.672385] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2524.672598] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2524.866759] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled
[ 2524.866967] iwlwifi 0000:04:00.0: L1 Disabled - LTR Disabled

```

The screenshot before is from "wavemon". So you think it's actually on ac mode or not? If it is, shouldn't it say ac instead of abgn?

The router is in my house. We only have a handful of devices ( I think only my laptop and my phone gets on 5GHz ).
And the distance is really small. less than 6m with only one floor between the router and the antena.

---

### Post by chili555 on 2016-12-21
I think it is on AC mode and I think the 'abgn' is meaningless. Here is my wavemon. See what it says about my card? No a, b, g, n or ac at all. However, it suggests a possible transmission rate of 867 Mbps; clearly AC territory.

[ATTACH=CONFIG]272805[/ATTACH]

---

### Post by antouank on 2016-12-21
> **chili555 said:**
> I think it is on AC mode and I think the 'abgn' is meaningless. Here is my wavemon. See what it says about my card? No a, b, g, n or ac at all. However, it suggests a possible transmission rate of 867 Mbps; clearly AC territory.

[ATTACH=CONFIG]272805[/ATTACH]
I see.
I did move my router a bit, it was behind the TV, and got the signal to 87%. Now it's stable above 600Mbit/s so I guess, like you say, it's at ac.
I see it at 866Mbit/s at times as well.

Thanks for all the help.

---

### Post by chili555 on 2016-12-21
> **antouank said:**
> I see.
I did move my router a bit, it was behind the TV, and got the signal to 87%. Now it's stable above 600Mbit/s so I guess, like you say, it's at ac.
I see it at 866Mbit/s at times as well.

Thanks for all the help.Awesome! Have fun! You have probably also helped a few searchers, as well, with Amazon links and all!

---

