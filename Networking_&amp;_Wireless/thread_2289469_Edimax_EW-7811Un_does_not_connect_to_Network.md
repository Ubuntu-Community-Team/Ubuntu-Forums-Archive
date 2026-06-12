---
title: "Edimax EW-7811Un does not connect to Network"
date: 2015-08-04
forum: Networking &amp; Wireless
---

### Post by chromo2 on 2015-08-04
Hello,
I'm running on an Odroid C1 ([http://www.hardkernel.com/main/products/prdt_info.php?g_code=G141578608433](http://www.hardkernel.com/main/products/prdt_info.php?g_code=G141578608433)) a minimum version of trusty thar ([http://forum.odroid.com/viewtopic.php?f=112&t=8075](http://forum.odroid.com/viewtopic.php?f=112&t=8075)).
My Problem is, that I tried to use my Edimax EW-7811Un WiFi-Stick on this system, but it didn't connect to my network.
I googled for days and tried many methods found in forms, but nothing worked.
I'm new to the Linux-World, so I don't know which information you need to help me. I show you the output of some commands, which I think are important.
Currently I'm connected with the Odroid via Ethernet, this works fine.

```
'lsusb'

[FONT=Menlo]Bus 001 Device 006: ID 7392:7811 Edimax Technology Co., Ltd EW-7811Un 802.11n Wireless Adapter [Realtek RTL8188CUS]
Bus 001 Device 005: ID 0781:5571 SanDisk Corp. Cruzer Fit[/FONT]
[FONT=Menlo]Bus 001 Device 004: ID 0781:5571 SanDisk Corp. Cruzer Fit[/FONT]
[FONT=Menlo]Bus 001 Device 003: ID 0781:5571 SanDisk Corp. Cruzer Fit[/FONT]
[FONT=Menlo]Bus 001 Device 002: ID 05e3:0610 Genesys Logic, Inc. 4-port hub[/FONT]
[FONT=Menlo]Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub[/FONT]
[FONT=Menlo]Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
[/FONT]
```

```
'lsmod'

[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]Module                  Size  Used by[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]8192cu                533775  0 [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]w1_gpio                 3287  0 [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]wire                   20827  1 w1_gpio[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]nls_cp437               5125  1 [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]btrfs                 759723  0 [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]xor                     4613  1 btrfs[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]raid6_pq               85392  1 btrfs[/COLOR][/FONT][/COLOR]

```

```
'iwconfig'

[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]wlan0     unassociated  Nickname:"<WIFI@REALTEK>"[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]          Mode:Auto  Frequency=2.412 GHz  Access Point: Not-Associated   [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]          Sensitivity:0/0  [/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]          Retry:off   RTS thr:off   Fragment thr:off[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]          Power Management:off[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]          Link Quality=0/100  Signal level=0 dBm  Noise level=0 dBm[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]          Tx excessive retries:0  Invalid misc:0   Missed beacon:0[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]sit0      no wireless extensions.[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]lo        no wireless extensions.[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]eth0      no wireless extensions.[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]
[/COLOR][/FONT][/COLOR]
[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]ip6tnl0   no wireless extensions.[/COLOR][/FONT][/COLOR]



```

```
'uname -r'

[COLOR=#FFFFFF][FONT=Menlo][COLOR=#000000]3.10.80-120[/COLOR][/FONT][/COLOR]

```

I hope, anyone can help me. Thank! :)

---

