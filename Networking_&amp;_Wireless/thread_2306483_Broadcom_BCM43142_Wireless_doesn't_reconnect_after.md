---
title: "Broadcom BCM43142 Wireless doesn't reconnect after overnight shutdown"
date: 2015-12-15
forum: Networking &amp; Wireless
---

### Post by HuaiDan on 2015-12-15
System Info: 
Asus fx550j laptop i7 8gb ram
Broadcom BCM43142 Wireless
Ubuntu 15.10 x86_64 / dual boot configuration with Windows 10

sudo lspci -nn -k -d  14e4:
```
davidh@davidh-X550JX:~$ sudo lspci -nn -k -d  14e4:
03:00.0 Network controller [0280]: Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)
	Subsystem: Lite-On Communications Inc Device [11ad:6605]
	Kernel driver in use: wl
```
Description of problem:
After connecting to a wpa-personal wi-fi at work and using that for the work day, I will return home and connect to my wpa-personal wifi at home. There seems to be no issue with this change. 
However, when I return to work the following day, the wireless connection will not re-establish, despite rebooting, modprobe-ing wl, deleting the connection in network manager, or cloning the mac address.
The only clue I currently have to this behavior is the following from dmesg:
```
error@wl_cfg80211_get_station : wrong mac address
```
followed by a couple of mac addresses that must belong to the router I'm trying to connect to, because they certainly don't belong to my wireless card. Sorry, I don't have that info now, as the wi-fi is currently connected.

The *only* thing that will allow me to connect is to boot into Windows 10 on the same laptop, connect to the wi-fi (happens automatically) in the Windows session, reboot back into Ubuntu, and let the wi-fi reconnect quickly and without issue.

Odd, isn't it? Anyway, I would like to connect to the wi-fi at work without having to boot into Windows first. Any suggestions?

---

### Post by HuaiDan on 2015-12-16
I was able to determine that connecting to my home network makes no difference to whether I am able to connect to the work network, as expected. It would be very odd if it did. 
I didn't connect to my home network yesterday evening. In fact, I didn't even turn on my laptop after I got home until I arrived at work again this morning.
However, the problem persists. I was unable to connect to the work wifi network, until I rebooted into Windows, and the restarted again int Ubuntu.
This time I was sure to get a bit more dmesg output.
Here is the dmesg output when I am unable to connect:
```
[    9.473444] wl: module license 'MIXED/Proprietary' taints kernel.
[    9.473447] Disabling lock debugging due to kernel taint
[    9.475118] wl: module verification failed: signature and/or required key missing - tainting kernel
[    9.609927] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[    9.684564] cfg80211: World regulatory domain updated:
[    9.684567] cfg80211:  DFS Master region: unset
[    9.684569] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[    9.684571] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    9.684572] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[    9.684573] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[    9.684574] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[    9.684576] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[    9.684577] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[    9.684578] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[    9.684579] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[    9.993714] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 1
[   67.477614] audit: type=1400 audit(1450311367.380:49): apparmor="DENIED" operation="open" profile="/usr/lib/telepathy/mission-control-5" name="/etc/ld.so.preload" pid=1637 comm="mission-control" requested_mask="r" denied_mask="r" fsuid=1000 ouid=0
[   85.188539] cfg80211: World regulatory domain updated:
[   85.188542] cfg80211:  DFS Master region: unset
[   85.188543] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   85.188544] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   85.188545] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   85.188546] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   85.188547] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   85.188548] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   85.188549] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   85.188550] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   85.188551] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   86.025107] cfg80211: Regulatory domain changed to country: CN
[   86.025110] cfg80211:  DFS Master region: FCC
[   86.025111] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   86.025113] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   86.025114] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (N/A)
[   86.025116] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[   86.025126] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[   86.025127] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[   86.025128] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
[   86.025129] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[   87.242565] audit: type=1400 audit(1450311387.132:50): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/etc/ld.so.preload" pid=1859 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   87.247792] audit: type=1400 audit(1450311387.140:51): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=1860 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   87.283629] audit: type=1400 audit(1450311387.176:52): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=1864 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   87.286496] audit: type=1400 audit(1450311387.176:53): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=1868 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[   87.961786] cfg80211: World regulatory domain updated:
[   87.961789] cfg80211:  DFS Master region: unset
[   87.961789] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   87.961791] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   87.961792] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   87.961793] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   87.961794] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   87.961795] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   87.961796] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   87.961797] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   87.961798] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   99.549431] cfg80211: Regulatory domain changed to country: CN
[   99.549433] cfg80211:  DFS Master region: FCC
[   99.549434] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   99.549436] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   99.549437] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (N/A)
[   99.549439] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[   99.549440] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[   99.549441] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[   99.549442] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
[   99.549443] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[  100.761160] audit: type=1400 audit(1450311400.644:54): apparmor="DENIED" operation="open" profile="/sbin/dhclient" name="/etc/ld.so.preload" pid=1949 comm="dhclient" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[  100.765981] audit: type=1400 audit(1450311400.648:55): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=1950 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[  100.801014] audit: type=1400 audit(1450311400.684:56): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=1954 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0
[  100.803513] audit: type=1400 audit(1450311400.684:57): apparmor="DENIED" operation="open" profile="/usr/lib/NetworkManager/nm-dhcp-helper" name="/etc/ld.so.preload" pid=1958 comm="nm-dhcp-helper" requested_mask="r" denied_mask="r" fsuid=0 ouid=0

```


And here is some dmesg output form when I am able to connect:

```
[    9.833567] wl: module license 'MIXED/Proprietary' taints kernel.
[    9.833569] Disabling lock debugging due to kernel taint
[    9.835196] wl: module verification failed: signature and/or required key missing - tainting kernel
[    9.965653] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   10.190142] intel_rapl: Found RAPL domain package
[   10.190146] intel_rapl: Found RAPL domain core
[   10.190149] intel_rapl: Found RAPL domain uncore
[   10.190151] intel_rapl: Found RAPL domain dram
[   10.531035] cfg80211: World regulatory domain updated:
[   10.531038] cfg80211:  DFS Master region: unset
[   10.531040] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   10.531043] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   10.531045] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   10.531047] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (N/A, 2000 mBm), (N/A)
[   10.531049] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (N/A)
[   10.531052] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2000 mBm), (0 s)
[   10.531054] cfg80211:   (5490000 KHz - 5730000 KHz @ 160000 KHz), (N/A, 2000 mBm), (0 s)
[   10.531056] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 2000 mBm), (N/A)
[   10.531059] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 0 mBm), (N/A)
[   25.975939] cfg80211: Regulatory domain changed to country: CN
[   25.975942] cfg80211:  DFS Master region: FCC
[   25.975943] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   25.975944] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm), (N/A)
[   25.975945] cfg80211:   (5170000 KHz - 5250000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (N/A)
[   25.975947] cfg80211:   (5250000 KHz - 5330000 KHz @ 80000 KHz, 160000 KHz AUTO), (N/A, 2300 mBm), (0 s)
[   25.975948] cfg80211:   (5735000 KHz - 5835000 KHz @ 80000 KHz), (N/A, 3000 mBm), (N/A)
[   25.975949] cfg80211:   (57240000 KHz - 59400000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)
[   25.975949] cfg80211:   (59400000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4400 mBm), (N/A)
[   25.975950] cfg80211:   (63720000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 2800 mBm), (N/A)


```

---

### Post by HuaiDan on 2015-12-17
So, is there any information I can provide that would help get to the bottom of this? The issue seems too consistent in its behavior to be just a random bug. Let me summarize what I know to be certain:
1. Broadcom wireless card won't connect to work wifi in the morning, unless I boot into Windows, then reboot back into Ubuntu.
2. Rebooting the system after a successful connect has no negative effect. The wifi will continue to connect successfully with each reboot.
3. Extended shutdowns (over an hour) has no negative effect.
4. An overnight shutdown is the only way I can replicate the problem, in which case the replication rate is 100%.
5. No other devices on the work wifi have this issue.
6. The issue only occurs on the work wifi.

I'm Googling this like a madman, but I can't find anything that matches. It seems like an oddly specific problem not to have a specific solution.

---

### Post by HuaiDan on 2016-01-05
I'd like to bump this, not only because it's still an issue , but also because I've managed a workaround that also might be an important clue.
I've mitigated having to boot into Windows with one simple trick: I go into time and date settings and set the date back to the last date I *could* connect( in this case, the previous day), and as soon as I do that, I am immediately able to connect to the office wi fi.
After that, I reset the date to the correct date, and I can disconnect and reconnect at leisure.

Any ideas on why this works, and how I can fix it permanently?

The next thing I'd like to troubleshoot, now that I have this information, is whether my BIOS time setting has anything to do with it. Because my system is dual-boot, I have to keep the BIOS set to local time rather than UTC, as with the latter case Windows and Ubuntu will, at best, display the incorrect times, and, at worst, change the BIOS time to something else. Ubuntu is set to recognize the system time as local rather than UTC, so Windows and Ubuntu can co-exist peacefully.

---

### Post by HuaiDan on 2016-01-07
Update:
I confirmed this morning that I was unable to connect. 
I changed /etc/default/rcS back to UTC=yes, then rebooted and changed the system clock in BIOS to UTC as well. 
Restarted Ubuntu, still unable to connect. Tried setting Ubuntu time back one day, as I had done before successfully, still unable to connect.
Reset everything back to local time, still unable to connect, and finally, set the clock back one day, still unable to connect.
I was back to square one, so I had to reboot into WIndows, connect there, then I was finally able to connect when I booted into Ubuntu.
It seems, at least for today, my clock-resetting trick is broken.

Any clues in iwlist scan? The router I'm trying to connect to is "qhfzcyxx".
```
wlan0     Scan completed :
          Cell 01 - Address: 76:14:4B:5D:CD:58
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=62/70  Signal level=-48 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 0706434E20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: DD0D001AA914144B5DCD550164FC18
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F20201018C0003A4000027A4000042435E0062322F00
          Cell 02 - Address: 2A:69:6C:52:AD:7B
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=37/70  Signal level=-73 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434E20010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AED0103FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD07001AA96B8B4567
          Cell 03 - Address: B6:14:4B:5D:C1:CC
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030106
                    IE: Unknown: 0706434E20010D14
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1606081500000000000000000000000000000000000000
                    IE: Unknown: DD0D001AA914144B5DC1C90164FC18
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101840003A4000027A4000042435E0062322F00
          Cell 04 - Address: 86:14:4B:5D:CD:59
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: 2D1A6C181BFF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D160B080400000000000000000000000000000000000000
                    IE: Unknown: DD0D001AA914144B5DCD550164FC18
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101880003A4000027A4000042435E0062322F00
          Cell 05 - Address: 2A:69:6C:50:B9:A0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434E20010D20
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AED011BFFFFFF0000000000000000000100000000000000000000
                    IE: Unknown: 3D160B000500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD07001AA96B8B4567
          Cell 06 - Address: 2A:69:6C:52:AC:BD
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434E20010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AED0103FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601080000000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD07001AA96B8B4567
          Cell 07 - Address: 2A:69:6C:52:AC:D1
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=44/70  Signal level=-66 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 0706434E20010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AED0103FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000500000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD07001AA96B8B4567
          Cell 08 - Address: 00:87:36:09:24:E2
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=27/70  Signal level=-83 dBm  
                    Encryption key:on
                    ESSID:"\xE4\xBA\x94\xE5\xB9\xB4\xE7\xBA\xA7"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 9 Mb/s
                              18 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 12 Mb/s; 24 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 0009E4BA94E5B9B4E7BAA7
                    IE: Unknown: 010882848B961224486C
                    IE: Unknown: 030106
                    IE: Unknown: 32040C183060
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 050400010020
                    IE: Unknown: 2A0104
                    IE: Unknown: DD07000C4306000000
                    IE: Unknown: 2D1A6E0102FF000000000000000000000000000000000E0000000000
                    IE: Unknown: 3D1606050000000000000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E0102FF000000000000000000000000000000000E0000000000
                    IE: Unknown: DD1A00904C3406050000000000000000000000000000000000000000
          Cell 09 - Address: 2A:69:6C:4F:62:DB
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=29/70  Signal level=-81 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 03010B
                    IE: Unknown: 050400010004
                    IE: Unknown: 0706434E20010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AED0103FFFF000000000000000000008000000000000000000000
                    IE: Unknown: 3D160B000100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD07001AA96B8B4567
          Cell 10 - Address: 2A:69:6C:52:AD:44
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=33/70  Signal level=-77 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434E20010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AED0103FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601080400000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD07001AA96B8B4567
          Cell 11 - Address: 2A:69:6C:52:AC:EA
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=30/70  Signal level=-80 dBm  
                    Encryption key:on
                    ESSID:"QHFZCYXX"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 00085148465A43595858
                    IE: Unknown: 010882848B0C12961824
                    IE: Unknown: 030101
                    IE: Unknown: 050400010000
                    IE: Unknown: 0706434E20010D1E
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1AED0103FFFF000000000000000000000100000000000000000000
                    IE: Unknown: 3D1601000100000000000000000000000000000000000000
                    IE: Unknown: 7F080000000000000040
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101080003A4000027A4000042435E0062322F00
                    IE: Unknown: DD0900037F01010000FF7F
                    IE: Unknown: DD07001AA96B8B4567
          Cell 12 - Address: BC:D1:77:45:6F:3A
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=25/70  Signal level=-85 dBm  
                    Encryption key:on
                    ESSID:"MERCURY_456F3A"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000000000000000
                    Extra: Last beacon: 68ms ago
                    IE: Unknown: 000E4D4552435552595F343536463341
                    IE: Unknown: 010882848B960C121824
                    IE: Unknown: 030101
                    IE: Unknown: 050700010000000000
                    IE: Unknown: 2A0100
                    IE: Unknown: 32043048606C
                    IE: Unknown: 2D1A6E1003FF00000000000000000000000000000000000000000000
                    IE: Unknown: 3D1601050200000000000000000000000000000000000000
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: DD05000AEB0100
                    IE: Unknown: DD310050F204104A00011010440001021047001000000000000010000000BCD177456F3A103C0001011049000600372A000120

```

---

### Post by HuaiDan on 2016-01-12
*bump*
Sometimes changing the date works, sometimes it doesn't.
Anyone?

---

### Post by HuaiDan on 2016-01-14
Here are the results of Verunendra's wireless troubleshooting script. This is while connected, so I doubt anything of interest will show up. I'll post the output of when it's unable to connect tomorrow, when I encounter the problem.

---

### Post by HuaiDan on 2016-01-14
..and as promised, here's the script output for when it can't connect.
One thing that immediately jumps out at me is this:
```
Booted last: 14 Jan 2016 00:00 CST +0800
```
..which is false. I'm not in the habit of starting my laptop at exactly midnight. This seems suspicious, considering I have to change my clock to before this time in order to connect.

---

### Post by byb3 on 2016-01-15
I've had a similar problem to you, but I could always re-connect after I had rebooted the laptop or used rfkill to disable and re-enable it.

It seems like you have a driver/hardware issue.  I would see if there is a newer version available in the latest kernel and try that.  Try a LiveCD with a newer kernel version and see if your wireless works on those.  Otherwise just forget about it and buy a USB wireless adapter or even better a PCI express half mini replacement (if possible) that is known to be compatible.  The amount of pain and stress I've had with 90% compatible wireless drivers that work for a week then fail randomnly for no apparent reason is not worth it and I wouldn't wish it on anyone else.

---

