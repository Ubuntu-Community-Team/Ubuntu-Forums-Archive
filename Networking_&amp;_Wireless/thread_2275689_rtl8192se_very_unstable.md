---
title: "rtl8192se very unstable"
date: 2015-04-27
forum: Networking &amp; Wireless
---

### Post by jean_bono2 on 2015-04-27
Hello,
Another issue with this dreaded driver...
I managed to stabilize my connection a few months ago but my landlady just changed the router and it's going crazy again...
I tried to follow some of my steps but without much success
I hope someone can see the light in this mess

Here's the wireless script result with the wifi connected and working ( a few minutes after it disconnected and I had to disable wifi and renable it to get back online)
```
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472
473
474
475
476
477
478
479
480
481
482
483
484
485
486
487
488
489
490
491
492
493
494
495
496
497
498
499
500
501
502
503
504
505
506
507
508
509
510
511
512
513
514
515
516
517
518
519
520
521
522
523
524
525
526
527
528
529
530
531
532
533
534
535
536
537
538
539
540
541
542
543
544
545
546
547
548
549
550
551
552
553
554
555
556
557
558
559
560
561
562
563
564
565
566
567
568
569
570
571
572
573
574
575
576
577
[/TD]
[TD="class: code"][COLOR=#000000]########## wireless info START ##########

Report from: 28 Apr 2015 00:48 BST +0100

Booted last: 28 Apr 2015 00:26 BST +0100

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 3.16.0-34-generic #47~14.04.1-Ubuntu SMP Fri Apr 10 17:49:16 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
	Kernel driver in use: rtl8192se

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Mitac Device [1071:9270]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 13d3:3249 IMC Networks Internal Bluetooth
Bus 002 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 002 Device 003: ID 040b:2013 Weltrend Semiconductor 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8192se              63162  0 
rtl_pci                26690  1 rtl8192se
rtlwifi                64255  2 rtl_pci,rtl8192se
mac80211              652718  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              494362  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.11  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:feea:a909/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11981 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8747 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11034019 (11.0 MB)  TX bytes:1768178 (1.7 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"VM572352-2G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'VM572352-2G' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:off
          Link Quality=50/70  Signal level=-60 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:13   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [Home-2G] -----------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    SKYCBC48:        Infra, <MAC 'SKYCBC48' [AC2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 27 WPA2
    virginmedia1706905: Infra, <MAC 'virginmedia1706905' [AC7]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 20 WPA WPA2
    networkwireless: Infra, <MAC 'networkwireless' [AC4]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AC5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2 Enterprise
    *VM572352-2G:    Infra, <MAC 'VM572352-2G' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 58 WPA2
    Weyland-Yutani:  Infra, <MAC 'Weyland-Yutani' [AC3]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    BTHub5-8538:     Infra, <MAC 'BTHub5-8538' [AN7]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AC6]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14

  IPv4 Settings:
    Address:         192.168.0.11
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/VM572352-2G]] (600 root)
[connection] id=Home-2G | type=802-11-wireless
[802-11-wireless] ssid=VM572352-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=dhcp

[[/etc/NetworkManager/system-connections/epson-setup-0000008e]] (600 root)
[connection] id=epson-setup-0000008e | type=802-11-wireless
[802-11-wireless] ssid=epson-setup-0000008e | mac-address=<MAC 'wlan0' [IF]>
[ipv6] method=auto
[ipv4] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      3   APs on   Frequency:2.412 GHz (Channel 1)
      1   APs on   Frequency:2.437 GHz (Channel 6)
      2   APs on   Frequency:2.462 GHz (Channel 11)
      1   APs on   Frequency:2.472 GHz (Channel 13)

eth0      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'VM572352-2G' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"VM572352-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=000000173f1e8c15
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'SKYCBC48' [AC2]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"SKYCBC48"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000005c80d56b454
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 03 - Address: <MAC 'Weyland-Yutani' [AC3]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"Weyland-Yutani"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000014604eda789
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
          Cell 04 - Address: <MAC 'networkwireless' [AC4]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"networkwireless"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000006e8eb94b
                    Extra: Last beacon: 44ms ago
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
          Cell 05 - Address: <MAC 'BTWifi-X' [AC5]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=18/70  Signal level=-92 dBm  
                    Encryption key:on
                    ESSID:"BTWifi-X"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008e45933e195
                    Extra: Last beacon: 796ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
                    IE: Unknlo        Interface doesn't support scanning.

own: 3D160B001300000000000000000000000000000000000000
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : 802.1x
          Cell 06 - Address: <MAC 'BTWifi-with-FON' [AC6]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=24/70  Signal level=-86 dBm  
                    Encryption key:off
                    ESSID:"BTWifi-with-FON"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000008e45933f25f
                    Extra: Last beacon: 792ms ago
          Cell 07 - Address: <MAC 'virginmedia1706905' [AC7]>
                    Channel:13
                    Frequency:2.472 GHz (Channel 13)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:on
                    ESSID:"virginmedia1706905"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000003ad82050122
                    Extra: Last beacon: 44ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : CCMP TKIP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192se]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     FF2890C4D22E859C393BF83
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     3273ECD6028617EFD27E4F4
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/3.16.0-34-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     8362106E96F806A9DBAE565
depends:        mac80211,cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     5410C94462FA26A0A3F256C
depends:        cfg80211
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/3.16.0-34-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     4A525D9D32B0C6D120CA547
depends:        
intree:         Y
vermagic:       3.16.0-34-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        80:21:14:84:DC:DA:08:06:05:39:31:B7:EE:AA:DE:22:EA:7E:C2:62
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192se]
debug: 0
fwlps: N
ips: N
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/rtl8192se.conf]
options rtl8192se ips=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[  635.144655] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 2/3)
[  635.248639] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 3/3)
[  635.352731] wlan0: authentication with <MAC 'VM572352-2G' [AC1]> timed out
[  636.706181] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[  636.726882] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  636.732564] wlan0: authenticated
[  636.736914] wlan0: associate with <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  636.743815] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC1]> (capab=0x411 status=0 aid=4)
[  636.746913] wlan0: associated
[  653.058236] wlan0: Connection to AP <MAC 'VM572352-2G' [AC1]> lost
[  654.027548] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[  654.048455] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  654.150735] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 2/3)
[  654.158021] wlan0: authenticated
[  654.158760] wlan0: associate with <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  654.262854] wlan0: associate with <MAC 'VM572352-2G' [AC1]> (try 2/3)
[  654.274906] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC1]> (capab=0x411 status=0 aid=4)
[  654.277597] wlan0: associated
[  659.067601] wlan0: Connection to AP <MAC 'VM572352-2G' [AC1]> lost
[  660.044437] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[  660.065803] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  660.167512] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 2/3)
[  660.271448] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 3/3)
[  660.375522] wlan0: authentication with <MAC 'VM572352-2G' [AC1]> timed out
[  662.228280] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[  662.249169] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  662.254641] wlan0: authenticated
[  662.255622] wlan0: associate with <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  662.262770] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC1]> (capab=0x411 status=0 aid=4)
[  662.265757] wlan0: associated

########## wireless info END ############[/COLOR]
[/TD]
[/TR]
[/TABLE]

```

Thanks

---

### Post by jean_bono2 on 2015-04-28
Hey there,
I fiddled a bit last night with some stuff
Installed a newer kernel 4.0 but still wasn't great
This morning I tried with my phone as a hotspot and it was surprinsingly good so I thought it was maybe something to do with the ESSID
I had given a name to my home connection so I deleted it and started fresh
It seems to work so far
I went through the wireless script and I notice that the power management is "on" now. Could that be it?
I'll let you know if it goes down again, or if you notice something unusual in my results let me know
Cheers

```

[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
408
409
410
411
412
413
414
415
416
417
418
419
420
421
422
423
424
425
426
427
428
429
430
431
432
433
434
435
436
437
438
439
440
441
442
443
444
445
446
447
448
449
450
451
452
453
454
455
456
457
458
459
460
461
462
463
464
465
466
467
468
469
470
471
472[/TD]
[TD="class: code"][COLOR=#000000]########## wireless info START ##########

Report from: 28 Apr 2015 10:30 BST +0100

Booted last: 28 Apr 2015 01:58 BST +0100

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.2 LTS
Release:    14.04
Codename:    trusty

##### kernel ############################

Linux 4.0.0-040000rc4-generic #201503152135 SMP Mon Mar 16 01:36:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
    Kernel driver in use: rtl8192se

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
    Subsystem: Mitac Device [1071:9270]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 007: ID 13d3:3249 IMC Networks Internal Bluetooth
Bus 002 Device 006: ID 05e3:0505 Genesys Logic, Inc. 
Bus 002 Device 003: ID 040b:2013 Weltrend Semiconductor 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

rtl8192se              65536  0 
rtl_pci                32768  1 rtl8192se
rtlwifi                77824  2 rtl_pci,rtl8192se
mac80211              774144  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              581632  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:feea:a909/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10000 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10729 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6144600 (6.1 MB)  TX bytes:3189112 (3.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"VM572352-2G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'VM572352-2G' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:92   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     9      0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### NetworkManager info ###############

NetworkManager Tool

State: connected (global)

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        <MAC 'eth0' [IF]>

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off

- Device: wlan0  [VM572352-2G] -------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rtl8192se
  State:             connected
  Default:           yes
  HW Address:        <MAC 'wlan0' [IF]>

  Capabilities:
    Speed:           72 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    virginmedia1706905: Infra, <MAC 'virginmedia1706905' [AN1]>, Freq 2472 MHz, Rate 54 Mb/s, Strength 30 WPA WPA2
    SKYCBC48:        Infra, <MAC 'SKYCBC48' [AN2]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA2
    BTWifi-X:        Infra, <MAC 'BTWifi-X' [AN3]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2 Enterprise
    BTHub5-8538:     Infra, <MAC 'BTHub5-8538' [AN4]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14 WPA2
    BTWifi-with-FON: Infra, <MAC 'BTWifi-with-FON' [AN5]>, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    networkwireless: Infra, <MAC 'networkwireless' [AN6]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 14 WPA
    Weyland-Yutani:  Infra, <MAC 'Weyland-Yutani' [AN7]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 14 WPA WPA2
    bono-mobile:     Infra, <MAC 'bono-mobile' [AN8]>, Freq 2437 MHz, Rate 54 Mb/s, Strength 89 WPA2
    *VM572352-2G:    Infra, <MAC 'VM572352-2G' [AC1]>, Freq 2412 MHz, Rate 54 Mb/s, Strength 62 WPA2

  IPv4 Settings:
    Address:         192.168.0.13
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=true

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/VM572352-2G]] (600 root)
[connection] id=VM572352-2G | type=802-11-wireless
[802-11-wireless] ssid=VM572352-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bono-mobile]] (600 root)
[connection] id=bono-mobile | type=802-11-wireless
[802-11-wireless] ssid=bono-mobile | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
    (2402 - 2482 @ 40), (N/A, 20)
    (5170 - 5250 @ 40), (N/A, 20)
    (5250 - 5330 @ 40), (N/A, 20), DFS
    (5490 - 5710 @ 40), (N/A, 27), DFS
    (57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'VM572352-2G' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=52/70  Signal level=-58 dBm  
                    Encryption key:on
                    ESSID:"VM572352-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001f5c86474a
                    Extra: Last beacon: 79512ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192se]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     E04FCB50CC184E09963A487
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     C37E3400EB03568EA817818
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger    <Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     B9F71EDCB05622E35ED2302
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     30B3B62942DA821463752CB
depends:        cfg80211
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     50F49B5647242701046959C
depends:        
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192se]
debug: 0
fwlps: N
ips: N
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/rtl8192se.conf]
options rtl8192se ips=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[  422.890923] wlan0: associated
[  422.890935] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  422.901961] wlan0: deauthenticating from <MAC 'VM572352-2G' [AC1]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[  422.912822] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[  422.923452] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  423.869430] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 2/3)
[  423.970186] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 3/3)
[  424.074293] wlan0: authentication with <MAC 'VM572352-2G' [AC1]> timed out
[ 1390.337325] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 1391.217682] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[ 1391.228302] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[ 1391.231955] wlan0: authenticated
[ 1391.236022] wlan0: associate with <MAC 'VM572352-2G' [AC1]> (try 1/3)
[ 1391.242383] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC1]> (capab=0x411 status=0 aid=3)
[ 1391.245264] wlan0: associated
[ 1391.245376] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 1749.019734] wlan0: deauthenticating from <MAC 'VM572352-2G' [AC1]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 1753.663402] wlan0: authenticate with <MAC 'bono-mobile' [AN8]>
[ 1753.674117] wlan0: send auth to <MAC 'bono-mobile' [AN8]> (try 1/3)
[ 1753.678541] wlan0: authenticated
[ 1753.681039] wlan0: associate with <MAC 'bono-mobile' [AN8]> (try 1/3)
[ 1753.694916] wlan0: RX AssocResp from <MAC 'bono-mobile' [AN8]> (capab=0x431 status=0 aid=1)
[ 1753.698144] wlan0: associated
[ 2012.762518] wlan0: deauthenticating from <MAC 'bono-mobile' [AN8]> by local choice (Reason: 3=DEAUTH_LEAVING)
[ 2026.892814] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[ 2026.913621] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[ 2026.917905] wlan0: authenticated
[ 2026.919619] wlan0: associate with <MAC 'VM572352-2G' [AC1]> (try 1/3)
[ 2026.926444] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC1]> (capab=0x411 status=0 aid=2)
[ 2026.929282] wlan0: associated

########## wireless info END ############[/COLOR][/TD]
[/TR]
[/TABLE]

```

edit : I also realise that the iwlist scan didn't see any other network even though I can see them in the nm applet...

---

### Post by jean_bono2 on 2015-04-28
I take it back... Got disconnected again
here is the dmesg
```

##### dmesg #############################

[ 6347.264782] wlan0: Connection to AP <MAC 'VM572352-2G' [AC7]> lost
[ 6348.342498] wlan0: authenticate with <MAC 'VM572352-2G' [AC7]>
[ 6348.353080] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6348.358179] wlan0: authenticated
[ 6348.361310] wlan0: associate with <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6348.373756] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC7]> (capab=0x411 status=0 aid=2)
[ 6348.376642] wlan0: associated
[ 6453.541649] wlan0: Connection to AP <MAC 'VM572352-2G' [AC7]> lost
[ 6454.586853] wlan0: authenticate with <MAC 'VM572352-2G' [AC7]>
[ 6454.608121] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6454.710135] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 2/3)
[ 6454.814297] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 3/3)
[ 6454.918315] wlan0: authentication with <MAC 'VM572352-2G' [AC7]> timed out
[ 6456.272025] wlan0: authenticate with <MAC 'VM572352-2G' [AC7]>
[ 6456.293458] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6456.395186] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 2/3)
[ 6456.499249] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 3/3)
[ 6456.603310] wlan0: authentication with <MAC 'VM572352-2G' [AC7]> timed out
[ 6458.457841] wlan0: authenticate with <MAC 'VM572352-2G' [AC7]>
[ 6458.478321] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6458.580481] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 2/3)
[ 6458.684644] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 3/3)
[ 6458.788712] wlan0: authentication with <MAC 'VM572352-2G' [AC7]> timed out
[ 6511.319967] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[ 6513.074369] wlan0: authenticate with <MAC 'VM572352-2G' [AC7]>
[ 6513.095536] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6513.101105] wlan0: authenticated
[ 6513.101776] wlan0: associate with <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6513.108899] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC7]> (capab=0x411 status=0 aid=2)
[ 6513.111995] wlan0: associated
[ 6513.112007] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[ 6513.139638] wlan0: deauthenticating from <MAC 'VM572352-2G' [AC7]> by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[ 6513.150757] wlan0: authenticate with <MAC 'VM572352-2G' [AC7]>
[ 6513.161346] wlan0: send auth to <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6513.167144] wlan0: authenticated
[ 6513.169802] wlan0: associate with <MAC 'VM572352-2G' [AC7]> (try 1/3)
[ 6513.179119] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC7]> (capab=0x411 status=0 aid=2)
[ 6513.182227] wlan0: associated

########## wireless info END ############

```

---

### Post by jean_bono2 on 2015-05-02
Bump
It's still very unstable
here is a wireless script after a reboot
```
 
[TABLE="class: pastetable"]
[TR]
[TD="class: linenos"]  1
  2
  3
  4
  5
  6
  7
  8
  9
 10
 11
 12
 13
 14
 15
 16
 17
 18
 19
 20
 21
 22
 23
 24
 25
 26
 27
 28
 29
 30
 31
 32
 33
 34
 35
 36
 37
 38
 39
 40
 41
 42
 43
 44
 45
 46
 47
 48
 49
 50
 51
 52
 53
 54
 55
 56
 57
 58
 59
 60
 61
 62
 63
 64
 65
 66
 67
 68
 69
 70
 71
 72
 73
 74
 75
 76
 77
 78
 79
 80
 81
 82
 83
 84
 85
 86
 87
 88
 89
 90
 91
 92
 93
 94
 95
 96
 97
 98
 99
100
101
102
103
104
105
106
107
108
109
110
111
112
113
114
115
116
117
118
119
120
121
122
123
124
125
126
127
128
129
130
131
132
133
134
135
136
137
138
139
140
141
142
143
144
145
146
147
148
149
150
151
152
153
154
155
156
157
158
159
160
161
162
163
164
165
166
167
168
169
170
171
172
173
174
175
176
177
178
179
180
181
182
183
184
185
186
187
188
189
190
191
192
193
194
195
196
197
198
199
200
201
202
203
204
205
206
207
208
209
210
211
212
213
214
215
216
217
218
219
220
221
222
223
224
225
226
227
228
229
230
231
232
233
234
235
236
237
238
239
240
241
242
243
244
245
246
247
248
249
250
251
252
253
254
255
256
257
258
259
260
261
262
263
264
265
266
267
268
269
270
271
272
273
274
275
276
277
278
279
280
281
282
283
284
285
286
287
288
289
290
291
292
293
294
295
296
297
298
299
300
301
302
303
304
305
306
307
308
309
310
311
312
313
314
315
316
317
318
319
320
321
322
323
324
325
326
327
328
329
330
331
332
333
334
335
336
337
338
339
340
341
342
343
344
345
346
347
348
349
350
351
352
353
354
355
356
357
358
359
360
361
362
363
364
365
366
367
368
369
370
371
372
373
374
375
376
377
378
379
380
381
382
383
384
385
386
387
388
389
390
391
392
393
394
395
396
397
398
399
400
401
402
403
404
405
406
407
[/TD]
[TD="class: code"][COLOR=#000000]########## wireless info START ##########

Report from: 02 May 2015 13:37 BST +0100

Booted last: 02 May 2015 13:29 BST +0100

Script from: 06 Apr 2015 17:23 UTC +0000

##### release ###########################

Distributor ID:	Ubuntu
Description:	Ubuntu 14.04.2 LTS
Release:	14.04
Codename:	trusty

##### kernel ############################

Linux 4.0.0-040000rc4-generic #201503152135 SMP Mon Mar 16 01:36:37 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Xubuntu

##### lspci #############################

03:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172] (rev 10)
	Subsystem: Realtek Semiconductor Co., Ltd. RTL8191SEvB Wireless LAN Controller [10ec:8172]
	Kernel driver in use: rtl8192se

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 03)
	Subsystem: Mitac Device [1071:9270]
	Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 005: ID 13d3:3249 IMC Networks Internal Bluetooth
Bus 002 Device 004: ID 05e3:0505 Genesys Logic, Inc. 
Bus 002 Device 003: ID 040b:2013 Weltrend Semiconductor 
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

##### lsmod #############################

rtl8192se              65536  0 
rtl_pci                32768  1 rtl8192se
rtlwifi                77824  2 rtl_pci,rtl8192se
mac80211              774144  3 rtl_pci,rtlwifi,rtl8192se
cfg80211              581632  2 mac80211,rtlwifi

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

eth0      Link encap:Ethernet  HWaddr <MAC 'eth0' [IF]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF]>  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::1e4b:d6ff:feea:a909/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10357 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7197 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11596668 (11.5 MB)  TX bytes:1173492 (1.1 MB)

##### iwconfig ##########################

eth0      no wireless extensions.

lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"VM572352-2G"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: <MAC 'VM572352-2G' [AC1]>   
          Bit Rate=72.2 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr=2347 B   Fragment thr:off
          Power Management:on
          Link Quality=52/70  Signal level=-58 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:138   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0
192.168.0.0     0.0.0.0         255.255.255.0   U     0      0        0 wlan0

##### resolv.conf #######################

nameserver 192.168.0.1

##### NetworkManager info ###############

/home/bono178/Desktop/wireless_script: line 201: nmcli: command not found

/home/bono178/Desktop/wireless_script: line 203: nmcli: command not found

##### NetworkManager.state ##############

cat: /var/lib/NetworkManager/NetworkManager.state: No such file or directory

##### NetworkManager.conf ###############

grep: /etc/NetworkManager/NetworkManager.conf: No such file or directory

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/VM572352-2G]] (600 root)
[connection] id=VM572352-2G | type=802-11-wireless
[802-11-wireless] ssid=VM572352-2G | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/bono-mobile]] (600 root)
[connection] id=bono-mobile | type=802-11-wireless
[802-11-wireless] ssid=bono-mobile | mac-address=<MAC 'wlan0' [IF]>
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Europe/London (based on set time zone)

country GB:
	(2402 - 2482 @ 40), (N/A, 20)
	(5170 - 5250 @ 40), (N/A, 20)
	(5250 - 5330 @ 40), (N/A, 20), DFS
	(5490 - 5710 @ 40), (N/A, 27), DFS
	(57240 - 65880 @ 2160), (N/A, 40), NO-OUTDOOR

##### iwlist channels ###################

eth0      no frequency information.

lo        no frequency information.

wlan0     13 channels in total; available frequencies :
          Channel 01 : 2.412 GHz
          Channel 02 : 2.417 GHz
          Channel 03 : 2.422 GHz
          Channel 04 : 2.427 GHz
          Channel 05 : 2.432 GHz
          Channel 06 : 2.437 GHz
          Channel 07 : 2.442 GHz
          Channel 08 : 2.447 GHz
          Channel 09 : 2.452 GHz
          Channel 10 : 2.457 GHz
          Channel 11 : 2.462 GHz
          Channel 12 : 2.467 GHz
          Channel 13 : 2.472 GHz
          Current Frequency:2.412 GHz (Channel 1)

##### iwlist scan #######################

Channel occupancy:

      1   APs on   Frequency:2.412 GHz (Channel 1)

eth0      Interface doesn't support scanning.

lo        Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: <MAC 'VM572352-2G' [AC1]>
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=50/70  Signal level=-60 dBm  
                    Encryption key:on
                    ESSID:"VM572352-2G"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000001514362d1
                    Extra: Last beacon: 372684ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[rtl8192se]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtl8192se/rtl8192se.ko
firmware:       rtlwifi/rtl8192sefw.bin
description:    Realtek 8192S/8191S 802.11n PCI wireless
license:        GPL
author:         Larry Finger	<Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     E04FCB50CC184E09963A487
depends:        rtlwifi,rtl_pci,mac80211
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512
parm:           swenc:Set to 1 for software crypto (default 0)
 (bool)
parm:           ips:Set to 0 to not use link power save (default 1)
 (bool)
parm:           swlps:Set to 1 to use SW control power save (default 0)
 (bool)
parm:           fwlps:Set to 1 to use FW control power save (default 1)
 (bool)
parm:           debug:Set debug level (0-5) (default 0) (int)

[rtl_pci]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtl_pci.ko
description:    PCI basic driver for rtlwifi
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     C37E3400EB03568EA817818
depends:        mac80211,rtlwifi
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512

[rtlwifi]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/drivers/net/wireless/rtlwifi/rtlwifi.ko
description:    Realtek 802.11n PCI wireless core
license:        GPL
author:         Larry Finger	<Larry.FInger@lwfinger.net>
author:         Realtek WlanFAE	<wlanfae@realtek.com>
author:         lizhaoming	<chaoming_li@realsil.com.cn>
srcversion:     B9F71EDCB05622E35ED2302
depends:        mac80211,cfg80211
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512

[mac80211]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     30B3B62942DA821463752CB
depends:        cfg80211
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.0.0-040000rc4-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     50F49B5647242701046959C
depends:        
intree:         Y
vermagic:       4.0.0-040000rc4-generic SMP mod_unload modversions 
signer:         Magrathea: Glacier signing key
sig_key:        FB:C6:3A:D1:87:69:EB:A8:28:0E:79:26:8C:23:A2:8E:9D:B7:70:1D
sig_hashalgo:   sha512
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[rtl8192se]
debug: 0
fwlps: N
ips: N
swenc: N
swlps: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[cfg80211]
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

lp
rtc

##### modprobe options ##################

[/etc/modprobe.d/blacklist-ath_pci.conf]
blacklist ath_pci

[/etc/modprobe.d/blacklist.conf]
blacklist evbug
blacklist usbmouse
blacklist usbkbd
blacklist eepro100
blacklist de4x5
blacklist eth1394
blacklist snd_intel8x0m
blacklist snd_aw2
blacklist i2c_i801
blacklist prism54
blacklist bcm43xx
blacklist garmin_gps
blacklist asus_acpi
blacklist snd_pcsp
blacklist pcspkr
blacklist amd76x_edac

[/etc/modprobe.d/blacklist-rare-network.conf]
alias net-pf-3 off
alias net-pf-6 off
alias net-pf-9 off
alias net-pf-11 off
alias net-pf-12 off
alias net-pf-19 off
alias net-pf-21 off
alias net-pf-36 off

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211
options iwlwifi 11n_disable=1

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/modesetting.conf]
options cirrus modeset=1
options mgag200 modeset=1

[/etc/modprobe.d/qemu-system-x86.conf]
options kvm_intel nested=1

[/etc/modprobe.d/rtl8192se.conf]
options rtl8192se ips=0

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

[/etc/udev/rules.d/70-persistent-net.rules]
# PCI device 0x10ec:0x8168 (r8169)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'eth0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="eth*", NAME="eth0"
# PCI device 0x10ec:0x8172 (rtl8192se)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC 'wlan0' [IF]>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
# USB device 0x:0x (rt2800usb)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="<MAC address>", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan1"

##### dmesg #############################

[   17.676156] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 3 times)
[   30.379774] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[   30.390278] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[   30.395915] wlan0: authenticated
[   30.398959] wlan0: associate with <MAC 'VM572352-2G' [AC1]> (try 1/3)
[   30.407212] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC1]> (capab=0x411 status=0 aid=4)
[   30.409895] wlan0: associated
[   30.409916] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  107.579051] wlan0: deauthenticated from <MAC 'VM572352-2G' [AC1]> (Reason: 6=CLASS2_FRAME_FROM_NONAUTH_STA)
[  108.660369] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready (repeated 4 times)
[  117.582551] wlan0: authenticate with <MAC 'VM572352-2G' [AC1]>
[  117.593579] wlan0: send auth to <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  117.598501] wlan0: authenticated
[  117.602091] wlan0: associate with <MAC 'VM572352-2G' [AC1]> (try 1/3)
[  117.608813] wlan0: RX AssocResp from <MAC 'VM572352-2G' [AC1]> (capab=0x411 status=0 aid=4)
[  117.611794] wlan0: associated
[  117.611812] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready

########## wireless info END ############



[/COLOR]
[/TD]
[/TR]
[/TABLE]

```

---

