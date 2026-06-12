---
title: "When is Wireless in 8.10 going to work"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by colinpat on 2008-11-24
When are they going to fix the wireless driver in the latest kernel?
	
Re: went from 8.04 to 8.10 and it fixed my wifi, but its so slow.
I can only get wireless to work reliably by loading kernel 2.6.24-19.

Kernel 2.6.27.7 worked till I did a few updates and now it is so slow everything times out.

The iwl4965 driver is the only one that seems to work with the pro/wireless 4965 AG.

I thought wireless was a big priority in 8.10

Colin

---

### Post by lisati on 2008-11-24
It already works on my two laptops.....

---

### Post by halovivek on 2008-11-24
It is working fine in 8.10. 
i am using it and i have installed on my friends computer they are also doing great. 
please do a hardware testing and check.

---

### Post by colinpat on 2008-11-24
Have run hardware test using both kernel 2.6.24-19 and the latest kernel.  Can't connect with wireless in the latest kernel to upload the report.
For some reason the iwlagn driver dose not work with my Intel Pro/Wireless 4965 AGN (Kedron) card.
Load the 2.6.24-19 kernel with the iwl4965 driver and system works well
Are you using the Intel Pro/Wireless 4965 AGN card??

---

### Post by kojo on 2008-12-06
bump

Wireless is slow using the iwlagn driver and the Intel Pro/Wireless 4965 AG.  When I connect a LAN cable to the ethernet jack my speeds pickup tremendously.  I transferred 125 megabytes over lan cable in 3 minutes within my local network.  The same task took 1 hour and 30 minutes using this wireless driver.

Clearly iwlagn does not support full wireless speeds on the Intel Pro/Wireless 4965 AG.

Machine: SONY VIAO VGN-FZ145E
```
$ uname -mr
2.6.27-10-generic i686
```

```
$ sudo lshw -C network
[sudo] password for: 
  *-network               
       description: Wireless interface
       product: PRO/Wireless 4965 AG or AGN [Kedron] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wmaster0
       version: 61
       serial: 00:13:e8:0f:ff:e3
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.0.7 latency=0 module=iwlagn multicast=yes wireless=IEEE 802.11abgn
```

Hardware:
```
06:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
        Subsystem: Intel Corporation Device 1100
        Flags: bus master, fast devsel, latency 0, IRQ 217
        Memory at fa000000 (64-bit, non-prefetchable) [size=8K]
        Capabilities: <access denied>
        Kernel driver in use: iwlagn
        Kernel modules: iwlagn
```
```
$ iwconfig wlan0
wlan0     IEEE 802.11abgn  ESSID:"KG4OFW"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:50:F2:CC:DE:98   
          Bit Rate=11 Mb/s   Tx-Power=14 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=97/100  Signal level:-54 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```
```
$ lsmod | grep iwlagn
iwlagn                 99716  0 
iwlcore                94276  1 iwlagn
mac80211              216820  2 iwlagn,iwlcore
cfg80211               32392  3 iwlagn,iwlcore,mac80211
```
```
[   14.266654] sony-laptop: Sony Notebook Control Driver v0.6.
[   14.274912] input: Sony Vaio Keys as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:29/SNY5001:00/input/input6
[   14.301245] input: Sony Vaio Jogdial as /devices/virtual/input/input7
[   14.333122] sony-laptop: detected Sony Vaio FZ Series
[   14.721864] iwlagn: Intel(R) Wireless WiFi Link AGN driver for Linux, 1.3.27ks
[   14.721868] iwlagn: Copyright(c) 2003-2008 Intel Corporation
[   14.731192] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   14.731224] iwlagn 0000:06:00.0: setting latency timer to 64
[   14.731280] iwlagn: Detected Intel Wireless WiFi Link 4965AGN REV=0x4
[   14.781402] iwlagn: Tunable channels: 11 802.11bg, 13 802.11a channels
[   14.782131] iwlagn 0000:06:00.0: PCI INT A disabled
[   14.782583] phy0: Selected rate control algorithm 'iwl-agn-rs'
[   28.005382] sky2 eth0: enabling interface
[   28.018624] iwlagn 0000:06:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   28.018720] iwlagn 0000:06:00.0: restoring config space at offset 0x1 (was 0x40100102, writing 0x40100106)
[   28.018899] firmware: requesting iwlwifi-4965-2.ucode
[   28.438354] Registered led device: iwl-phy0:radio
[   28.438380] Registered led device: iwl-phy0:assoc
[   28.438397] Registered led device: iwl-phy0:RX
[   28.438413] Registered led device: iwl-phy0:TX
[   28.509622] NET: Registered protocol family 17
[   29.175587] [drm] Initialized drm 1.1.0 20060810
[   29.180482] pci 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   29.180492] pci 0000:00:02.0: setting latency timer to 64
[   29.180634] [drm] Initialized i915 1.6.0 20060119 on minor 0
[   30.177804] wlan0: authenticate with AP 00:12:17:ff:e3:f0
[   30.189186] wlan0: authenticated
[   30.189191] wlan0: associate with AP 00:12:17:ff:e3:f0
[   30.193521] wlan0: RX AssocResp from 00:12:17:ff:e3:f0 (capab=0x401 status=0 aid=7)
[   30.193528] wlan0: associated
[   30.202070] wlan0: disassociating by local choice (reason=3)
[   64.647266] lo: Disabled Privacy Extensions
[   64.648780] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   64.650638] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.700469] wlan0: authenticate with AP 00:50:f2:cc:de:98
[   82.707472] wlan0: authenticate with AP 00:50:f2:cc:de:98
[   82.718775] wlan0: authenticated
[   82.718788] wlan0: associate with AP 00:50:f2:cc:de:98
[   82.724729] wlan0: RX AssocResp from 00:50:f2:cc:de:98 (capab=0x11 status=0 aid=6)
[   82.724739] wlan0: associated
[   82.733835] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  314.548127] wlan0: disassociating by local choice (reason=3)
[  329.795143] wlan0: authenticate with AP 00:12:17:ff:e3:f0
[  329.802513] wlan0: authenticated
[  329.802525] wlan0: associate with AP 00:12:17:ff:e3:f0
[  330.000582] wlan0: associate with AP 00:12:17:ff:e3:f0
[  330.016431] wlan0: RX AssocResp from 00:12:17:ff:e3:f0 (capab=0x401 status=0 aid=7)
[  330.016442] wlan0: associated
[  330.035077] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  330.036972] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  375.249556] wlan0: disassociating by local choice (reason=3)
[  375.252680] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  375.257030] wlan0: deauthenticated
[  375.286511] wlan0: authenticate with AP 00:12:17:ff:e3:f0
[  375.484111] wlan0: authenticate with AP 00:12:17:ff:e3:f0
[  375.486082] wlan0: authenticated
[  375.486094] wlan0: associate with AP 00:12:17:ff:e3:f0
[  375.684137] wlan0: associate with AP 00:12:17:ff:e3:f0
[  375.688451] wlan0: RX AssocResp from 00:12:17:ff:e3:f0 (capab=0x401 status=0 aid=7)
[  375.688463] wlan0: associated
[  375.696590] wlan0: disassociating by local choice (reason=3)
[  382.523085] wlan0: authenticate with AP 00:12:17:ff:e3:f0
[  382.721068] wlan0: authenticate with AP 00:12:17:ff:e3:f0
[  382.724422] wlan0: authenticated
[  382.724437] wlan0: associate with AP 00:12:17:ff:e3:f0
[  382.920098] wlan0: associate with AP 00:12:17:ff:e3:f0
[  382.922903] wlan0: RX AssocResp from 00:12:17:ff:e3:f0 (capab=0x401 status=0 aid=7)
[  382.922916] wlan0: associated
[  382.930780] wlan0: disassociating by local choice (reason=3)
[  382.942662] wlan0: authenticate with AP 00:50:f2:cc:de:98
[  382.949866] wlan0: authenticate with AP 00:50:f2:cc:de:98
[  382.957269] wlan0: authenticate with AP 00:50:f2:cc:de:98
[  382.970510] wlan0: authenticated
[  382.970523] wlan0: associate with AP 00:50:f2:cc:de:98
[  382.973805] wlan0: RX AssocResp from 00:50:f2:cc:de:98 (capab=0x11 status=0 aid=6)
[  382.973815] wlan0: associated
[  382.981320] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  382.982659] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2581.810918] wlan0: disassociating by local choice (reason=3)
[ 2581.812830] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2581.854302] wlan0: authenticate with AP 00:50:f2:cc:de:98
[ 2581.861548] wlan0: authenticate with AP 00:50:f2:cc:de:98
[ 2581.869310] wlan0: authenticated
[ 2581.869327] wlan0: associate with AP 00:50:f2:cc:de:98
[ 2581.871815] wlan0: RX AssocResp from 00:50:f2:cc:de:98 (capab=0x11 status=0 aid=6)
[ 2581.871827] wlan0: associated
[ 2581.881262] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 2581.881779] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

```

---

### Post by kojo on 2008-12-08
I read about this driver in the bug reports.  It looks like it is associated with the linux kernel as mentioned in this thread.  After reinstalling 8.10 from cd, removing network manager and using wicd the problem remained.  I then tested the performance using my neighbor's open wlan on ch 6.  Speeds improved.  So I put a spare wireless router on my network using ch 11 and wep security.  Speeds were normal.  It appears that interference of 3 area routers on ch 6 might have been to blame.  The nic works fine now.  Resolved.

---

### Post by chifeatures on 2008-12-09
I'm unsure what has happened to make this work but last night for the first time in a year wireless worked - and consistently all night. It was the absolute bain of my life (life's tough huh).

I have a 4965 wireless card on a Dell XPS M1330. I've posted on a few threads here trying to diagnose the problem with no luck, as have 1000's of others, but I'm very keen to share any information I can to help others.

If you want me to run any commands let me know.

---

### Post by bolinec on 2008-12-11
I think it is resolved due to WEP.  I'm having these same issues and have WPA.  If I drop down to WEP everyone plays nice.  This could be an issue with wpa_supplicant.

---

### Post by chifeatures on 2008-12-11
The wireless network I was connecting to successfully was WPA.

---

### Post by sockrebel on 2008-12-20
I have a HP 2510p with Intel 4965 AG and am also experiencing a very slow wireless connection.  WEP security is already enabled.  Any other fix ideas?
thx!

---

### Post by kojo on 2008-12-20
> **sockrebel said:**
> I have a HP 2510p with Intel 4965 AG and am also experiencing a very slow wireless connection.  WEP security is already enabled.  Any other fix ideas?
thx!

After struggling with this issue myself I would suggest that you might try changing the channel of your wireless router (or try a router on a different channel).  I had one router on channel 6 and one on channel 11, both had the same WEP encryption but channel 11 worked faster.  Several nearby residences were all on channel 6 and possibly posing interference issues.

If this doesn't work you might find that reloading an older kernel might solve the problem.  I read this recently.  It seems that this is not an Ubuntu distro problem as much as a kernel issue.

---

