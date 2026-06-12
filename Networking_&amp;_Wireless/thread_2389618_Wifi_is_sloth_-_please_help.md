---
title: "Wifi is sloth - please help"
date: 2018-04-19
forum: Networking &amp; Wireless
---

### Post by kim3 on 2018-04-19
Hi folks,

I recently moved to Mint which I quite liked other than the wifi connection was very poor.

I thought it was time to buy a new wifi adaptor so picked one up off ebay and installed. The same issue.So thought I would now try ubuntu 17.10

My 2014 macbook pro and xiaomi a1 phone both get speeds of around 15mbps when right next to my desktop which gets 1-2mbps, often slower.

The wireless interface is  description: Wireless interface
       product: Ultimate N WiFi Link 5300

I have tried a few tests seen elsewhere but to no avail.

Can you please help!

Or will I be forced, reluctantly, back to Windows!

---

### Post by kim3 on 2018-04-19
Can anyone offer me help here?

The efforts made on Mint are here>>

[https://forums.linuxmint.com/viewtopic.php?f=53&t=259452](https://forums.linuxmint.com/viewtopic.php?f=53&t=259452)

I was hopeful that the ubuntu community might be a little larger and more chance of success in seeking a solution!

---

### Post by jeremy31 on 2018-04-19
I would see [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
If that doesn't help try ```
echo "options iwlwifi 11n_disable=8 | sudo tee /etc/modprobe.d/iwlwifi-opt.conf
```
Reboot
If that doesn't help, there might be some issue with the wifi router that Linux doesn't like

---

### Post by kim3 on 2018-04-20
> **jeremy31 said:**
> I would see [https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520](https://ubuntuforums.org/showthread.php?t=2354328&p=13614520&#post13614520)
If that doesn't help try ```
echo "options iwlwifi 11n_disable=8 | sudo tee /etc/modprobe.d/iwlwifi-opt.conf
```
Reboot
If that doesn't help, there might be some issue with the wifi router that Linux doesn't like

Thank you Jeremy.

I have done a few of the steps. 
Couldnt open the file to edit due to this error>
[HTML]Error copying '/home/edmund/.Xauthority' to '/tmp/libgksu-Rca9ry': No such file or directory [/HTML]

Have changed to just 20Mhz instead of 20/40 and also set channel as 11.


Run the other commands also.

This didnt work>>
[HTML]
> echo "options iwlwifi 11n_disable=8 | sudodprobe.d/iwlwifi-opt.con
bash: sudodprobe.d/iwlwifi-opt.con: No such file or directory[/HTML]

Speed is up to 5-7mbps, whilst the macbook 2014 model next to it is 20mbps.

Any other ideas?

---

### Post by jeremy31 on 2018-04-20
```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi-opt.conf
```
That should work.  Then reboot

11n_disable=8 enables aggressive TX for the Intel wifi

---

### Post by slickymaster on 2018-04-20
Thread moved to **MINT** for a better fit

---

### Post by kim3 on 2018-04-20
> **slickymaster said:**
> Thread moved to **MINT** for a better fit
I am running the latest version of Ubuntu!

So should this not be in the Ubuntu forum?

---

### Post by kim3 on 2018-04-20
> **jeremy31 said:**
> ```
echo "options iwlwifi 11n_disable=8" | sudo tee /etc/modprobe.d/iwlwifi-opt.conf
```
That should work.  Then reboot

11n_disable=8 enables aggressive TX for the Intel wifi
[IMG]http://tinypic.com/r/34fl6v4/9[/IMG]

[http://tinypic.com/r/34fl6v4/9](http://tinypic.com/r/34fl6v4/9)[IMG]http://i65.tinypic.com/34fl6v4.png[/IMG]

Tried the above. No obvious major change though this morning, before using that code, and after the speed was around 1/3 to 1/4 of the signal received by my macbook right next to the desktop. Maybe the wireless adaptor is just that much weaker on the desktop, even the new one i bought? Or is there obviously a problem and I should be getting similar speeds on ubuntu desktop as I am on the mac and my phone from the same position in the house?

any other ideas?

---

### Post by slickymaster on 2018-04-21
> **kim3 said:**
> I am running the latest version of Ubuntu!

So should this not be in the Ubuntu forum?

Being so I'll move it back to the N&W forum.

---

### Post by jeremy31 on 2018-04-21
Are the antennas attached to the wifi card?

---

### Post by kim3 on 2018-04-22
> **jeremy31 said:**
> Are the antennas attached to the wifi card?

That amused me, Jeremy...yet I suppose worth asking.

yes, all three are connected.

It does make a little difference where they are pointed, And if they are the problem, on a new wifi card, then I am shocked at how spectacular my 14' macbook pro antenna must be to get double if not triple the speed from the exact same position in the house. Is this normal?

My wifi card>
2.4G/5Ghz Wireless 450Mbps PCI-E Card WiFi Network Antenna LAN Ethernet AC990

---

### Post by jeremy31 on 2018-04-22
It wouldn't have been the first time antennas weren't connected, see the wireless script link in my signature and post results

---

### Post by kim3 on 2018-04-28
> **jeremy31 said:**
> It wouldn't have been the first time antennas weren't connected, see the wireless script link in my signature and post results

```
[COLOR=#000]                                   **Ubuntu Pastebin**

           **Paste from edmund at Sun, 29 Apr 2018 00:17:38 +0000**

  [Download as text]("http://paste.ubuntu.com/p/bxdYChKXPq/plain/")  [TABLE="class: pastetable"]
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
578
579
580
581
582
583
584
585
586
587
588
589
590
591
592
593
594
595
596
597
598
599
600
601
602
603[/TD]
[TD="class: code"]########## wireless info START ##########

Report from: 29 Apr 2018 10:17 AEST +1000

Booted last: 29 Apr 2018 00:00 AEST +1000

Script from: 10 Jan 2018 20:04 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 17.10
Release:    17.10
Codename:    artful

##### kernel ############################

Linux 4.13.0-38-generic #43-Ubuntu SMP Wed Mar 14 15:20:44 UTC 2018 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu on Xorg

##### lspci #############################

01:00.0 Network controller [0280]: Intel Corporation Ultimate N WiFi Link 5300 [8086:4235]
    Subsystem: Intel Corporation Ultimate N WiFi Link 5300 [8086:1001]
    Kernel driver in use: iwlwifi

03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: Gigabyte Technology Co., Ltd Onboard Ethernet [1458:e000]
    Kernel driver in use: r8169

##### lsusb #############################

Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 002: ID 046d:c313 Logitech, Inc. Internet 350 Keyboard
Bus 003 Device 003: ID 1a2c:0042 China Resource Semico Co., Ltd 
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

iwldvm                229376  0
mac80211              782336  1 iwldvm
iwlwifi               253952  1 iwldvm
cfg80211              614400  3 iwlwifi,mac80211,iwldvm

##### interfaces ########################

[/etc/network/interfaces]
auto lo
iface lo inet loopback

##### ifconfig ##########################

1: lo: <LOOPBACK,UP,LOWER_UP> mtu 65536 qdisc noqueue state UNKNOWN group default qlen 1000
    link/loopback <MAC address> brd 00:00:00:00:00:00
    inet 127.0.0.1/8 scope host lo
       valid_lft forever preferred_lft forever
2: enp3s0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast state DOWN group default qlen 1000
    link/ether <MAC 'enp3s0' [IF1]> brd <MAC address>
3: wlp1s0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 qdisc mq state UP group default qlen 1000
    link/ether <MAC 'wlp1s0' [IF2]> brd <MAC address>
    inet 10.1.1.50/24 brd 10.1.1.255 scope global dynamic wlp1s0
       valid_lft 84237sec preferred_lft 84237sec

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp1s0    IEEE 802.11  ESSID:"iiNetB6B3B3"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: <MAC 'iiNetB6B3B3' [AC1]>   
          Bit Rate=39 Mb/s   Tx-Power=15 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=47/70  Signal level=-63 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:694   Missed beacon:0

##### route #############################

default via 10.1.1.1 dev wlp1s0 proto static metric 600 
10.1.1.0/24 dev wlp1s0 proto kernel scope link src 10.1.1.50 metric 600 
169.254.0.0/16 dev wlp1s0 scope link metric 1000 

##### resolv.conf #######################

nameserver 10.1.1.1
search lan

##### network managers ##################

Installed:

    NetworkManager

Running:

root       686     1  0 09:41 ?        00:00:00 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlp1s0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Intel Corporation
GENERAL.PRODUCT:                        Ultimate N WiFi Link 5300
GENERAL.DRIVER:                         iwlwifi
GENERAL.DRIVER-VERSION:                 4.13.0-38-generic
GENERAL.FIRMWARE-VERSION:               8.83.5.1 build 33692
GENERAL.HWADDR:                         <MAC 'wlp1s0' [IF2]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:01.0/0000:01:00.0/net/wlp1s0
GENERAL.IP-IFACE:                       wlp1s0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     iiNetB6B3B3
GENERAL.CON-UUID:                       4935be85-5258-4c35-90db-b854a880cf31
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/1
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     39 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     no
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   4935be85-5258-4c35-90db-b854a880cf31 | iiNetB6B3B3
IP4.ADDRESS[1]:                         10.1.1.50/24
IP4.GATEWAY:                            10.1.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             10.1.1.1
IP4.DOMAIN[1]:                          lan
DHCP4.OPTION[1]:                        requested_subnet_mask = 1
DHCP4.OPTION[2]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[3]:                        subnet_mask = 255.255.255.0
DHCP4.OPTION[4]:                        domain_name_servers = 10.1.1.1
DHCP4.OPTION[5]:                        ip_address = 10.1.1.50
DHCP4.OPTION[6]:                        requested_static_routes = 1
DHCP4.OPTION[7]:                        dhcp_server_identifier = 10.1.1.1
DHCP4.OPTION[8]:                        requested_time_offset = 1
DHCP4.OPTION[9]:                        broadcast_address = 10.1.1.255
DHCP4.OPTION[10]:                       requested_interface_mtu = 1
DHCP4.OPTION[11]:                       dhcp_rebinding_time = 75600
DHCP4.OPTION[12]:                       requested_domain_name_servers = 1
DHCP4.OPTION[13]:                       dhcp_message_type = 5
DHCP4.OPTION[14]:                       requested_broadcast_address = 1
DHCP4.OPTION[15]:                       routers = 10.1.1.1
DHCP4.OPTION[16]:                       dhcp_renewal_time = 43200
DHCP4.OPTION[17]:                       requested_domain_name = 1
DHCP4.OPTION[18]:                       domain_name = lan
DHCP4.OPTION[19]:                       requested_routers = 1
DHCP4.OPTION[20]:                       expiry = 1525045274
DHCP4.OPTION[21]:                       host_name = edmund-B85M-D3H
DHCP4.OPTION[22]:                       requested_netbios_scope = 1
DHCP4.OPTION[23]:                       requested_wpad = 1
DHCP4.OPTION[24]:                       requested_ms_classless_static_routes = 1
DHCP4.OPTION[25]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[26]:                       network_number = 10.1.1.0
DHCP4.OPTION[27]:                       requested_domain_search = 1
DHCP4.OPTION[28]:                       next_server = 10.1.1.1
DHCP4.OPTION[29]:                       requested_ntp_servers = 1
DHCP4.OPTION[30]:                       requested_host_name = 1
DHCP4.OPTION[31]:                       dhcp_lease_time = 86400

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Realtek Semiconductor Co., Ltd.
GENERAL.PRODUCT:                        RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (Onboard Ethernet)
GENERAL.DRIVER:                         r8169
GENERAL.DRIVER-VERSION:                 2.3LK-NAPI
GENERAL.FIRMWARE-VERSION:               --
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:1c.2/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       --
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     --
GENERAL.CON-UUID:                       --
GENERAL.CON-PATH:                       --
GENERAL.METERED:                        unknown
CAPABILITIES.CARRIER-DETECT:            yes
CAPABILITIES.SPEED:                     unknown
CAPABILITIES.IS-SOFTWARE:               no
CAPABILITIES.SRIOV:                     no
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: --

SSID            BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY  ACTIVE  * 
iiNet50905B     <MAC 'iiNet50905B' [AC2]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA2      no        
iiNetB6B3B3     <MAC 'iiNetB6B3B3' [AC1]>  Infra  11    2462 MHz  54 Mbit/s  57      &#9602;&#9604;&#9606;_  WPA2      yes     * 
Hark Guest 2.4  <MAC 'Hark Guest 2.4' [AN3]>  Infra  4     2427 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA2      no        
Schnitz 2.4     <MAC 'Schnitz 2.4' [AN4]>  Infra  4     2427 MHz  54 Mbit/s  50      &#9602;&#9604;__  WPA2      no        
TPG 9CD1        <MAC 'TPG 9CD1' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  40      &#9602;&#9604;__  WPA2      no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/iiNetB6B3B3]] (600 root)
[connection] id=iiNetB6B3B3 | type=wifi | permissions=
[wifi] mac-address=<MAC 'wlp1s0' [IF2]> | mac-address-blacklist= | ssid=iiNetB6B3B3
[ipv4] method=auto
[ipv6] method=ignore

##### Netplan config ####################

[/etc/netplan/01-network-manager-all.yaml]
network:
  version: 2
  renderer: NetworkManager

##### iw reg get ########################

Region: Australia/Melbourne (based on set time zone)

global
country 00: DFS-UNSET
    (2402 - 2472 @ 40), (N/A, 20), (N/A)
    (2457 - 2482 @ 20), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM, NO-IR
    (5170 - 5250 @ 80), (N/A, 20), (N/A), AUTO-BW, NO-IR
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS, AUTO-BW, NO-IR
    (5490 - 5730 @ 160), (N/A, 20), (0 ms), DFS, NO-IR
    (5735 - 5835 @ 80), (N/A, 20), (N/A), NO-IR
    (57240 - 63720 @ 2160), (N/A, 0), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

wlp1s0    32 channels in total; available frequencies :
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
          Channel 36 : 5.18 GHz
          Channel 40 : 5.2 GHz
          Channel 44 : 5.22 GHz
          Channel 48 : 5.24 GHz
          Channel 52 : 5.26 GHz
          Channel 56 : 5.28 GHz
          Channel 60 : 5.3 GHz
          Channel 64 : 5.32 GHz
          Channel 100 : 5.5 GHz
          Channel 104 : 5.52 GHz
          Channel 108 : 5.54 GHz
          Channel 112 : 5.56 GHz
          Channel 116 : 5.58 GHz
          Channel 120 : 5.6 GHz
          Channel 124 : 5.62 GHz
          Channel 128 : 5.64 GHz
          Channel 132 : 5.66 GHz
          Channel 136 : 5.68 GHz
          Channel 140 : 5.7 GHz
          Current Frequency:2.462 GHz (Channel 11)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

Channel occupancy:

      1   APs on   Frequency:2.437 GHz (Channel 6)
      1   APs on   Frequency:2.462 GHz (Channel 11)

wlp1s0    Scan completed :
          Cell 01 - Address: <MAC 'iiNetB6B3B3' [AC1]>
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=47/70  Signal level=-63 dBm  
                    Encryption key:on
                    ESSID:"iiNetB6B3B3"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000614e236b1a
                    Extra: Last beacon: 148ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
          Cell 02 - Address: <MAC 'iiNet50905B' [AC2]>
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=42/70  Signal level=-68 dBm  
                    Encryption key:on
                    ESSID:"iiNet50905B"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000002ca4270cdf0
                    Extra: Last beacon: 5952ms ago
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK

##### module infos ######################

[iwldvm]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/intel/iwlwifi/dvm/iwldvm.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi Link AGN driver for Linux
srcversion:     247533358E1675610AB8991
depends:        mac80211,iwlwifi,cfg80211
intree:         Y
name:           iwldvm
vermagic:       4.13.0-38-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           force_cam:force continuously aware mode (no power saving at all) (bool)

[mac80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     125925493BE4168AD62F1ED
depends:        cfg80211
intree:         Y
name:           mac80211
vermagic:       4.13.0-38-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[iwlwifi]
filename:       /lib/modules/4.13.0-38-generic/kernel/drivers/net/wireless/intel/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003- 2015 Intel Corporation <linuxwifi@intel.com>
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-6.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-6.ucode
firmware:       iwlwifi-7265D-29.ucode
firmware:       iwlwifi-7265-17.ucode
firmware:       iwlwifi-3168-29.ucode
firmware:       iwlwifi-3160-17.ucode
firmware:       iwlwifi-7260-17.ucode
firmware:       iwlwifi-8265-33.ucode
firmware:       iwlwifi-8000C-33.ucode
firmware:       iwlwifi-9260-th-b0-jf-b0--33.ucode
firmware:       iwlwifi-9260-th-a0-jf-a0--33.ucode
firmware:       iwlwifi-9000-pu-a0-jf-b0--33.ucode
firmware:       iwlwifi-9000-pu-a0-jf-a0--33.ucode
firmware:       iwlwifi-Qu-a0-jf-b0--33.ucode
firmware:       iwlwifi-Qu-a0-hr-a0--33.ucode
srcversion:     339D7D3BD0DD2A9C7FE616F
depends:        cfg80211
intree:         Y
name:           iwlwifi
vermagic:       4.13.0-38-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           swcrypto:using crypto in software (default 0 [hardware]) (int)
parm:           11n_disable:disable 11n functionality, bitmap: 1: full, 2: disable agg TX, 4: disable agg RX, 8 enable agg TX (uint)
parm:           amsdu_size:amsdu size 0: 12K for multi Rx queue devices, 4K for other devices 1:4K 2:8K 3:12K (default 0) (int)
parm:           fw_restart:restart firmware in case of error (default true) (bool)
parm:           antenna_coupling:specify antenna coupling in dB (default: 0 dB) (int)
parm:           nvm_file:NVM file name (charp)
parm:           d0i3_disable:disable d0i3 functionality (default: Y) (bool)
parm:           lar_disable:disable LAR functionality (default: N) (bool)
parm:           uapsd_disable:disable U-APSD functionality bitmap 1: BSS 2: P2P Client (default: 3) (uint)
parm:           bt_coex_active:enable wifi/bt co-exist (default: enable) (bool)
parm:           led_mode:0=system default, 1=On(RF On)/Off(RF Off), 2=blinking, 3=Off (default: 0) (int)
parm:           power_save:enable WiFi power management (default: disable) (bool)
parm:           power_level:default power save level (range from 1 - 5, default: 1) (int)
parm:           fw_monitor:firmware monitor - to debug FW (default: false - needs lots of memory) (bool)
parm:           d0i3_timeout:Timeout to D0i3 entry when idle (ms) (uint)
parm:           disable_11ac:Disable VHT capabilities (default: false) (bool)

[cfg80211]
filename:       /lib/modules/4.13.0-38-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     A5EDD7467E172A70410EBCD
depends:        
intree:         Y
name:           cfg80211
vermagic:       4.13.0-38-generic SMP mod_unload 
signat:         PKCS#7
signer:         
sig_key:        
sig_hashalgo:   md4
parm:           bss_entries_limit:limit to number of scan BSS entries (per wiphy, default 1000) (int)
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

##### module parameters #################

[iwldvm]
force_cam: Y

[mac80211]
beacon_loss_count: 7
ieee80211_default_rc_algo: minstrel_ht
max_nullfunc_tries: 2
max_probe_tries: 5
minstrel_vht_only: Y
probe_wait_ms: 500

[iwlwifi]
11n_disable: 8
amsdu_size: 0
antenna_coupling: 0
bt_coex_active: Y
d0i3_disable: Y
d0i3_timeout: 1000
disable_11ac: N
fw_monitor: N
fw_restart: Y
lar_disable: N
led_mode: 0
nvm_file: (null)
power_level: 0
power_save: N
swcrypto: 0
uapsd_disable: 3

[cfg80211]
bss_entries_limit: 1000
cfg80211_disable_40mhz_24ghz: N
ieee80211_regdom: 00

##### /etc/modules ######################

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

[/etc/modprobe.d/intel-microcode-blacklist.conf]
blacklist microcode

[/etc/modprobe.d/iwlwifi.conf]
remove iwlwifi \
(/sbin/lsmod | grep -o -e ^iwlmvm -e ^iwldvm -e ^iwlwifi | xargs /sbin/rmmod) \
&& /sbin/modprobe -r mac80211

[/etc/modprobe.d/iwlwifi-opt.conf]
options iwlwifi 11n_disable=8

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

[/etc/modprobe.d/rt2800.conf]
options rt2800pci nohwcrypt=1

[/etc/modprobe.d/rtl8723be.conf]
options rtl8723be swenc=1 fwlps=0 ips=0 ant_sel=1

##### rc.local ##########################

grep: /etc/rc.local: No such file or directory

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[    2.052645] iwlwifi 0000:01:00.0: enabling device (0000 -> 0002)
[    2.052711] iwlwifi 0000:01:00.0: can't disable ASPM; OS doesn't have ASPM control
[    2.090357] iwlwifi 0000:01:00.0: loaded firmware version 8.83.5.1 build 33692 op_mode iwldvm
[    2.104495] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUG disabled
[    2.104496] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[    2.104497] iwlwifi 0000:01:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[    2.104499] iwlwifi 0000:01:00.0: Detected Intel(R) Ultimate N WiFi Link 5300 AGN, REV=0x24
[    2.168534] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[    2.355391] iwlwifi 0000:01:00.0 wlp1s0: renamed from wlan0
[    3.051626] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    3.166077] r8169 0000:03:00.0 enp3s0: link down
[    3.166124] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready
[    3.168594] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready
[    3.177756] iwlwifi 0000:01:00.0: Radio type=0x0-0x2-0x0 (repeated 2 times)
[    3.372770] IPv6: ADDRCONF(NETDEV_UP): wlp1s0: link is not ready (repeated 2 times)
[    9.811527] wlp1s0: authenticate with <MAC 'iiNetB6B3B3' [AC1]>
[    9.816209] wlp1s0: send auth to <MAC 'iiNetB6B3B3' [AC1]> (try 1/3)
[    9.818981] wlp1s0: authenticated
[    9.820003] wlp1s0: associate with <MAC 'iiNetB6B3B3' [AC1]> (try 1/3)
[    9.823658] wlp1s0: RX AssocResp from <MAC 'iiNetB6B3B3' [AC1]> (capab=0x1411 status=0 aid=4)
[    9.828609] wlp1s0: associated
[    9.828633] IPv6: ADDRCONF(NETDEV_CHANGE): wlp1s0: link becomes ready

########## wireless info END ############
[/TD]
[/TR]
[/TABLE]
 
 [Download as text]("http://paste.ubuntu.com/p/bxdYChKXPq/plain/") 
                 
         
     [/COLOR]

```

[http://paste.ubuntu.com/p/bxdYChKXPq/](http://paste.ubuntu.com/p/bxdYChKXPq/)

---

### Post by kim3 on 2018-06-12
Coming back to ubuntu for another attempt to get the wifi sorted before trying Windows 7 again. Any ideas why the difference between the macbook and the desktop (running ubuntu) is so staggering?

---

### Post by jeremy31 on 2018-06-12
I would switch to Ubuntu 16.04 or 18.04 as support for 17.10 ends in 6 weeks
You have set the country code ```
sudo iw reg set AU
```

---

### Post by kim3 on 2018-06-12
I have updated to the latest version this evening. And just set the country code as advised. Will report back on any change. Though am starting to suspect it is the wifi adaptor?

---

