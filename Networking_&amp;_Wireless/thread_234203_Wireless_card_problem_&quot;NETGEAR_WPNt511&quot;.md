---
title: "Wireless card problem &quot;NETGEAR WPNt511&quot;"
date: 2006-08-11
forum: Networking &amp; Wireless
---

### Post by freeborn on 2006-08-11
Hi, am new to Linux.

 I have problem to get a “Netgear WPNt511 (pciid: 17cb:0002 )” wireless card to work on Xubuntu. Been searching the net, but haven’t found anything really, regarding this card.

I wonder if someone knows how to make this card work under Xubuntu or Ubuntu?

I have tried Ndiswrapper (synaptic) (The WPNt511 is supported on [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List) but not with pciid: 17cb:002) with the Windows driver from [http://kbserver.netgear.com/products/wpnt511.asp](http://kbserver.netgear.com/products/wpnt511.asp). Don’t get any errors in terminal on installing the driver, but get following error message in "dmesg".

<command> sudo dmesg

[  314.477374] ndiswrapper version 1.8 loaded (preempt=yes,smp=no)
[  342.899205] pccard: CardBus card inserted into slot 0
[  343.031970] ndiswrapper: driver tmimo3p (NETGEAR Networks, Inc.,10/28/2005, 2.0.1.19) loaded
[  343.033897] PCI: Enabling device 0000:02:00.0 (0000 -> 0002)
[  343.039193] ndiswrapper: using irq 9
[  343.344284] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.344350] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1349280104
[  343.344366] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1868984933
[  343.344381] ndiswrapper (NdisWriteErrorLogEntry:233): code: 2035510642
[  343.344396] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1835365491
[  343.344411] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1702061394
[  343.344426] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1631789172
[  343.344441] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1684368492
[  343.344456] ndiswrapper (NdisWriteErrorLogEntry:233): code: 3238461450
[  343.359816] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.359875] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1667462515
[  343.359891] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1718842213
[  343.359906] ndiswrapper (NdisWriteErrorLogEntry:233): code: 2037148789
[  343.359921] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1768843552
[  343.359936] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1818323316
[  343.359951] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1684372073
[  343.359966] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1818322976
[  343.359980] ndiswrapper (NdisWriteErrorLogEntry:233): code: 6517280
[  343.360020] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.360038] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1349280104
[  343.360053] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1868984933
[  343.360068] ndiswrapper (NdisWriteErrorLogEntry:233): code: 2035510642
[  343.360083] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1835365491
[  343.360098] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1702061394
[  343.360112] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1631789172
[  343.360127] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1684368492
[  343.360141] ndiswrapper (NdisWriteErrorLogEntry:233): code: 10
[  343.909873] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.909898] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1702127169
[  343.909914] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1634214002
[  343.909929] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1667321196
[  343.909944] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1850308424
[  343.909959] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1679848553
[  343.909974] ndiswrapper (NdisWriteErrorLogEntry:233): code: 174419567
[  343.909988] ndiswrapper (NdisWriteErrorLogEntry:233): code: 0
[  343.910003] ndiswrapper (NdisWriteErrorLogEntry:233): code: 3502205168
[  343.910401] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.910423] ndiswrapper (NdisWriteErrorLogEntry:233): code: 543647299
[  343.910438] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1634886000
[  343.910453] ndiswrapper (NdisWriteErrorLogEntry:233): code: 858923117
[  343.910469] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1852383281
[  343.910484] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1633904996
[  343.910499] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1852795252
[  343.910515] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1953459744
[  343.910529] ndiswrapper (NdisWriteErrorLogEntry:233): code: 6383648
[  343.912025] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.912053] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1701012818
[  343.912069] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1684371049
[  343.912084] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1397051936
[  343.912100] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1598377301
[  343.912115] ndiswrapper (NdisWriteErrorLogEntry:233): code: 541480014
[  343.912130] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1394634345
[  343.912145] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1702125940
[  343.912160] ndiswrapper (NdisWriteErrorLogEntry:233): code: 2109984
[  343.912408] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.912427] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1919773036
[  343.912442] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1836413797
[  343.912457] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1952670053
[  343.912473] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1953068649
[  343.912488] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1718906489
[  343.912503] ndiswrapper (NdisWriteErrorLogEntry:233): code: 544434464
[  343.912518] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1953391987
[  343.912533] ndiswrapper (NdisWriteErrorLogEntry:233): code: 7497248
[  343.914014] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.914046] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1349280104
[  343.914061] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1701015410
[  343.914077] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1951626099
[  343.914092] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1165259361
[  343.914178] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1953391990
[  343.914193] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1866670138
[  343.914208] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1701605485
[  343.914223] ndiswrapper (NdisWriteErrorLogEntry:233): code: 6579572
[  343.914245] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a
[  343.914263] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1349280104
[  343.914279] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1701015410
[  343.914294] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1951626099
[  343.914309] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1165259361
[  343.914324] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1953391990
[  343.914340] ndiswrapper (NdisWriteErrorLogEntry:233): code: 1866735674
[  343.914355] ndiswrapper (NdisWriteErrorLogEntry:233): code: 758801774
[  343.914369] ndiswrapper (NdisWriteErrorLogEntry:233): code: 6375456
[  344.939619] wlan0: vendor: 'Airgo Networks True MIMO (tm) Wireless Adapter'
[  344.939658] wlan0: ndiswrapper ethernet device 00:14:6c:60:e3:9b using driver tmimo3p, 17CB:0002:1385:6D00.5.conf
[  344.939754] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

What I can understand that:
[  343.344284] ndiswrapper (NdisWriteErrorLogEntry:230): log: C000138A, count: 8, return_address: d0bd984a

indicate some kind of hardware/driver problem.

/freeborn

---

### Post by x-tomek on 2006-12-29
Hi, try [http://ubuntuforums.org/showthread.php?t=262465](http://ubuntuforums.org/showthread.php?t=262465) (different card but same chipset)

---

