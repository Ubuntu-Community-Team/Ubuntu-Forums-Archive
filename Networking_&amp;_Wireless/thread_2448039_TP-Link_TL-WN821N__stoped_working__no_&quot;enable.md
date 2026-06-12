---
title: "TP-Link TL-WN821N  stoped working  no &quot;enable WiFi&quot; in networking pop down"
date: 2020-07-31
forum: Networking &amp; Wireless
---

### Post by ibod on 2020-07-31
Hi All,

I have a problem with a TP-Link TL-WN821N on a DEL VOSTRO-260 running Ubuntu 16.04.

This has been working well for years and a couple of days ago on longer works 
No WiFi connection.

The Device shows up in lsusb but in the networking pop down there is no "Enable WiFi" 
line usually directly under the "Enable Networking" line and no list of router SSID's to connect to.

This device works on my other computer a DELL VOSTRO-230 also running Ubuntu 16.04

Thanks for and help or guidance you can provide.

---

### Post by chili555 on 2020-07-31
What exactly does lsusb say about it? Please post the output.

---

### Post by ibod on 2020-07-31
Hi Chili555,

From lsusb

```


$ lsusb Bus 002 Device 004: ID 413c:2003 Dell Computer Corp. Keyboard
Bus 002 Device 003: ID 046d:c077 Logitech, Inc. M105 Optical Mouse
Bus 002 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 007: ID 0cf3:7015 Atheros Communications, Inc. TP-Link TL-WN821N
v3 / TL-WN822N v2 802.11n (Atheros AR7010+AR9287)
Bus 001 Device 004: ID 03f0:4417 Hewlett-Packard EWS UPD
Bus 001 Device 003: ID 046d:0825 Logitech, Inc. Webcam C270
Bus 001 Device 002: ID 8087:0024 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
$


```

hope this helps

---

### Post by chili555 on 2020-07-31
> ID [COLOR="#FF0000"]0cf3:7015[/COLOR] Atheros Communications, Inc. TP-Link TL-WN821N
v3 / TL-WN822N v2 802.11n (Atheros AR7010+AR9287)Your device uses the driver ath9k_htc. Did the driver load?

```
lsmod | grep ath
```

Please load it and check for clues in the message log:

```
sudo modprobe ath9k_htc
dmesg | grep ath
```Let's also be certain that the required firmware is available:

```
ls -al /lib/firmware/ath9k_htc
```

We hope we see:

```
-rw-r--r--  1 root root 72812 Jul 15 09:11 htc_7010-1.4.0.fw
-rw-r--r--  1 root root 51008 Jul 15 09:11 htc_9271-1.4.0.fw

```

---

### Post by ibod on 2020-08-01
Hi Chili555,

Thanks for your help so far :-)

"Your device uses the driver ath9k_htc. Did the driver load?"

```


$
$ lsmod | grep ath
ath9k_htc            69632  1
ath9k_common         36864  1 ath9k_htc
ath9k_hw            471040  2 ath9k_common,ath9k_htc
ath                  24576  3 ath9k_common,ath9k_htc,ath9k_hw
mac80211            667648  1 ath9k_htc
cfg80211            499712  4 ath,ath9k_common,mac80211,ath9k_htc
$

```

I'm assuming this means it did load. 
So I skipped the the load instruction.
Hope I am correct with that ?
If not I will go back and load it.


"Let's also be certain that the required firmware is available:"

```


$
$ ls -al /lib/firmware/ath9k_htc
total 164
drwxr-xr-x    2 root root  4096 May   8 09:54 .
drwxr-xr-x  134 root root 36864 Jul  29 09:43 ..
-rw-r--r--    1 root root 72812 Apr  14 08:21 htc_7010-1.4.0.fw
-rw-r--r--    1 root root 51008 Apr  14 08:21 htc_9271-1.4.0.fw
$

```

Ok so this matches what you were expecting apart from the exact date / time.
Not sure what the date and time refer to...

Sorry about any wonky layout.
I am helping an elderly friend remotely to fix their connection over the phone.
He is sending me photos and I am typing them in.

---

### Post by chili555 on 2020-08-01
Your formatting is understood very well; no worries.

How about:

```
dmesg | grep ath
```That's where the good stuff will likely be found.

---

### Post by ibod on 2020-08-03
Hi Chili555,

Ok here is the good stuff.

Had to orgnise a better route to transfer the data this time, too much to type out from a photo lol.

```


$ dmesg | grep ath
[   14.113663] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[   14.113724] usbcore: registered new interface driver ath9k_htc
[   14.498243] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[   14.568566] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[   41.595626] ath: phy0: Reading Magic # failed
[   41.595913] ath9k_htc: Failed to initialize the device
[   41.595928] usb 1-1.4: ath9k_htc: USB layer deinitialized
[   41.893289] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[   42.001882] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[   42.072575] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[   69.045503] ath: phy1: Reading Magic # failed
[   69.045705] ath9k_htc: Failed to initialize the device
[   69.045749] usb 1-1.4: ath9k_htc: USB layer deinitialized
[   69.338324] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[   69.449563] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[   69.519972] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[   96.497050] ath: phy2: Reading Magic # failed
[   96.497273] ath9k_htc: Failed to initialize the device
[   96.497287] usb 1-1.4: ath9k_htc: USB layer deinitialized
[   96.788356] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[   96.897681] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[   96.968033] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  123.946009] ath: phy3: Reading Magic # failed
[  123.946232] ath9k_htc: Failed to initialize the device
[  123.946246] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  124.241666] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  124.350617] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  124.420968] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  151.399184] ath: phy4: Reading Magic # failed
[  151.399407] ath9k_htc: Failed to initialize the device
[  151.399421] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  151.694591] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  151.803553] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  151.873901] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  178.852284] ath: phy5: Reading Magic # failed
[  178.852508] ath9k_htc: Failed to initialize the device
[  178.852522] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  179.143470] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  179.252366] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  179.322712] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  206.301439] ath: phy6: Reading Magic # failed
[  206.301664] ath9k_htc: Failed to initialize the device
[  206.301682] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  206.592715] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  206.701294] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  206.771643] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  233.750476] ath: phy7: Reading Magic # failed
[  233.750700] ath9k_htc: Failed to initialize the device
[  233.750713] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  234.042147] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  234.155577] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  234.226079] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  261.203262] ath: phy8: Reading Magic # failed
[  261.203478] ath9k_htc: Failed to initialize the device
[  261.203491] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  261.499208] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  261.608408] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  261.678762] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  288.657052] ath: phy9: Reading Magic # failed
[  288.657277] ath9k_htc: Failed to initialize the device
[  288.657290] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  288.956390] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  289.069459] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  289.139946] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  316.117905] ath: phy10: Reading Magic # failed
[  316.118130] ath9k_htc: Failed to initialize the device
[  316.118144] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  316.413431] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  316.523025] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  316.593506] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  343.571887] ath: phy11: Reading Magic # failed
[  343.572104] ath9k_htc: Failed to initialize the device
[  343.572117] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  343.865742] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  343.974901] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  344.045272] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  371.024644] ath: phy12: Reading Magic # failed
[  371.024857] ath9k_htc: Failed to initialize the device
[  371.024872] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  371.318765] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  371.425358] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  371.495747] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  398.476966] ath: phy13: Reading Magic # failed
[  398.477174] ath9k_htc: Failed to initialize the device
[  398.477188] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  398.772161] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  398.879570] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  398.950061] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  425.931231] ath: phy14: Reading Magic # failed
[  425.931459] ath9k_htc: Failed to initialize the device
[  425.931475] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  426.233434] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  426.348618] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  426.419093] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  453.402785] ath: phy15: Reading Magic # failed
[  453.402987] ath9k_htc: Failed to initialize the device
[  453.402999] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  453.694687] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  453.855134] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  453.925511] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  480.904710] ath: phy16: Reading Magic # failed
[  480.904923] ath9k_htc: Failed to initialize the device
[  480.904937] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  481.196190] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  481.302357] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  481.372862] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  508.349964] ath: phy17: Reading Magic # failed
[  508.350185] ath9k_htc: Failed to initialize the device
[  508.350199] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  508.645192] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  508.755251] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  508.825628] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  535.806854] ath: phy18: Reading Magic # failed
[  535.807080] ath9k_htc: Failed to initialize the device
[  535.807094] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  536.106401] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  536.218876] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  536.289229] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  563.268045] ath: phy19: Reading Magic # failed
[  563.268273] ath9k_htc: Failed to initialize the device
[  563.268286] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  563.559535] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  563.673162] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  563.743663] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  590.721222] ath: phy20: Reading Magic # failed
[  590.721448] ath9k_htc: Failed to initialize the device
[  590.721464] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  591.016159] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  591.129743] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  591.200097] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  618.178216] ath: phy21: Reading Magic # failed
[  618.178442] ath9k_htc: Failed to initialize the device
[  618.178456] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  618.473468] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  618.582431] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  618.652782] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  645.631367] ath: phy22: Reading Magic # failed
[  645.631592] ath9k_htc: Failed to initialize the device
[  645.631606] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  645.922775] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  646.031608] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  646.102091] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  673.081217] ath: phy23: Reading Magic # failed
[  673.081455] ath9k_htc: Failed to initialize the device
[  673.081468] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  673.375659] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  673.489546] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  673.559898] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  700.537620] ath: phy24: Reading Magic # failed
[  700.537846] ath9k_htc: Failed to initialize the device
[  700.537859] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  700.836886] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  700.951105] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  701.021460] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  727.999205] ath: phy25: Reading Magic # failed
[  727.999425] ath9k_htc: Failed to initialize the device
[  727.999439] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  728.293954] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  728.407299] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  728.477517] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  755.467872] ath: phy26: Reading Magic # failed
[  755.468098] ath9k_htc: Failed to initialize the device
[  755.468113] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  755.762973] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  755.873081] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  755.943574] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  782.925592] ath: phy27: Reading Magic # failed
[  782.925809] ath9k_htc: Failed to initialize the device
[  782.925821] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  783.220584] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  783.332791] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  783.403098] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  810.382102] ath: phy28: Reading Magic # failed
[  810.382328] ath9k_htc: Failed to initialize the device
[  810.382344] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  810.677257] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  810.791325] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  810.861820] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  837.839593] ath: phy29: Reading Magic # failed
[  837.839822] ath9k_htc: Failed to initialize the device
[  837.839838] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  838.134839] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  838.244130] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  838.314560] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  865.292426] ath: phy30: Reading Magic # failed
[  865.292652] ath9k_htc: Failed to initialize the device
[  865.292666] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  865.583376] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  865.692094] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  865.762434] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  892.741484] ath: phy31: Reading Magic # failed
[  892.741709] ath9k_htc: Failed to initialize the device
[  892.741722] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  893.032809] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  893.141638] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  893.212122] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  920.190610] ath: phy32: Reading Magic # failed
[  920.190835] ath9k_htc: Failed to initialize the device
[  920.190849] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  920.481718] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  920.590827] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  920.661305] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  947.639718] ath: phy33: Reading Magic # failed
[  947.639944] ath9k_htc: Failed to initialize the device
[  947.639958] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  947.939052] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  948.047764] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  948.118115] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[  975.100587] ath: phy34: Reading Magic # failed
[  975.100809] ath9k_htc: Failed to initialize the device
[  975.100822] usb 1-1.4: ath9k_htc: USB layer deinitialized
[  975.391944] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[  975.501454] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[  975.571798] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1002.549934] ath: phy35: Reading Magic # failed
[ 1002.550159] ath9k_htc: Failed to initialize the device
[ 1002.550172] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1002.841296] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1002.952382] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1003.022733] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1030.003158] ath: phy36: Reading Magic # failed
[ 1030.003386] ath9k_htc: Failed to initialize the device
[ 1030.003400] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1030.294230] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1030.403690] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1030.474041] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1057.452232] ath: phy37: Reading Magic # failed
[ 1057.452457] ath9k_htc: Failed to initialize the device
[ 1057.452473] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1057.743492] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1057.855872] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1057.926224] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1084.905312] ath: phy38: Reading Magic # failed
[ 1084.905540] ath9k_htc: Failed to initialize the device
[ 1084.905555] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1085.200428] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1085.309934] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1085.380284] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1112.357913] ath: phy39: Reading Magic # failed
[ 1112.358121] ath9k_htc: Failed to initialize the device
[ 1112.358133] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1112.653737] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1112.762992] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1112.833343] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1139.811543] ath: phy40: Reading Magic # failed
[ 1139.811768] ath9k_htc: Failed to initialize the device
[ 1139.811781] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1140.102589] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1140.211683] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1140.282027] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1167.260651] ath: phy41: Reading Magic # failed
[ 1167.260875] ath9k_htc: Failed to initialize the device
[ 1167.260889] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1167.551971] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1167.661358] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1167.731711] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1194.713913] ath: phy42: Reading Magic # failed
[ 1194.714138] ath9k_htc: Failed to initialize the device
[ 1194.714151] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1195.004956] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1195.118901] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1195.189395] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1222.166535] ath: phy43: Reading Magic # failed
[ 1222.166752] ath9k_htc: Failed to initialize the device
[ 1222.166767] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1222.462266] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1222.571103] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1222.641454] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1249.620153] ath: phy44: Reading Magic # failed
[ 1249.620381] ath9k_htc: Failed to initialize the device
[ 1249.620394] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1249.915157] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1250.029903] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1250.100387] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1277.077418] ath: phy45: Reading Magic # failed
[ 1277.077643] ath9k_htc: Failed to initialize the device
[ 1277.077656] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1277.372467] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1277.485718] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1277.556073] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1304.534400] ath: phy46: Reading Magic # failed
[ 1304.534626] ath9k_htc: Failed to initialize the device
[ 1304.534639] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1304.829682] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1304.939529] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1305.009880] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1331.987524] ath: phy47: Reading Magic # failed
[ 1331.987753] ath9k_htc: Failed to initialize the device
[ 1331.987767] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1332.282710] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1332.391712] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1332.462064] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1359.440519] ath: phy48: Reading Magic # failed
[ 1359.440746] ath9k_htc: Failed to initialize the device
[ 1359.440760] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1359.735635] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1359.845267] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1359.915749] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1386.897664] ath: phy49: Reading Magic # failed
[ 1386.897889] ath9k_htc: Failed to initialize the device
[ 1386.897903] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1387.189004] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1387.298207] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1387.368559] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1414.350468] ath: phy50: Reading Magic # failed
[ 1414.350687] ath9k_htc: Failed to initialize the device
[ 1414.350705] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1414.645886] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1414.759756] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1414.830242] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1441.808022] ath: phy51: Reading Magic # failed
[ 1441.808246] ath9k_htc: Failed to initialize the device
[ 1441.808260] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1442.099498] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1442.208329] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1442.278800] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
[ 1469.256492] ath: phy52: Reading Magic # failed
[ 1469.256702] ath9k_htc: Failed to initialize the device
[ 1469.256715] usb 1-1.4: ath9k_htc: USB layer deinitialized
[ 1469.548172] usb 1-1.4: ath9k_htc: Firmware ath9k_htc/htc_7010-1.4.0.fw requested
[ 1469.658008] usb 1-1.4: ath9k_htc: Transferred FW: ath9k_htc/htc_7010-1.4.0.fw, size: 72812
[ 1469.728360] ath9k_htc 1-1.4:1.0: ath9k_htc: HTC initialized with 45 credits
$ 

```

Thanks for all your help.

---

### Post by chili555 on 2020-08-03
> This device works on my other computer a DELL VOSTRO-230 also running Ubuntu 16.04


What are the kernel versions for the working and not working installations?

```
uname -r
```

Possibly clues: [https://lkml.org/lkml/2020/6/27/140](https://lkml.org/lkml/2020/6/27/140) and: [https://bugzilla.kernel.org/show_bug.cgi?id=208251](https://bugzilla.kernel.org/show_bug.cgi?id=208251) 

If you interrupt the boot process at the GRUB menu and select the earliest kernel version you have, does the wireless work?

I actually have an ath9k_htc device and I'll be testing a bit later.

---

### Post by ibod on 2020-08-04
Hi Chili555

What are the kernel versions for the working and not working installations?


Working Vostro 230  = 
```


$ uname -r
4.15.0-112-generic
$

```

Not Working Vostro 260  = 

```


$ uname -r
4.4.0-186-generic
$

```

Hope this helps

---

### Post by chili555 on 2020-08-04
My similar device, using the same chipset, driver and firware, works perfectly:

```
[181410.289000] usbcore: registered new interface driver ath9k_htc
[181410.582745] usb 3-1: ath9k_htc: Transferred FW: ath9k_htc/htc_9271-1.4.0.fw, size: 51008
[181410.834809] ath9k_htc 3-1:1.0: ath9k_htc: HTC initialized with 33 credits
[181411.101752] ath9k_htc 3-1:1.0: ath9k_htc: FW Version: 1.4
[181411.101756] ath9k_htc 3-1:1.0: FW RMW support: On
[181411.101759] ath: EEPROM regdomain: 0x809c
[181411.101760] ath: EEPROM indicates we should expect a country code
[181411.101761] ath: doing EEPROM country->regdmn map search
[181411.101762] ath: country maps to regdmn code: 0x52
[181411.101763] ath: Country alpha2 being used: CN
[181411.101764] ath: Regpair used: 0x52
[181411.113021] ieee80211 phy1: Atheros AR9271 Rev:1
[181411.133699] ath9k_htc 3-1:1.0 wlx30b5c2120f20: renamed from wlan0
[181459.209782] wlp3s0: authenticate with a4:2b:b0:dc:45:85
[181459.212264] wlp3s0: send auth to a4:2b:b0:dc:45:85 (try 1/3)
[181459.213305] wlp3s0: authenticated
[181459.213589] wlp3s0: associate with a4:2b:b0:dc:45:85 (try 1/3)
[181459.223776] wlp3s0: RX AssocResp from a4:2b:b0:dc:45:85 (capab=0x411 status=0 aid=3)
[181459.225972] wlp3s0: associated
[181459.229156] wlp3s0: Limiting TX power to 27 (30 - 3) dBm as advertised by a4:2b:b0:dc:45:85
[181459.240366] IPv6: ADDRCONF(NETDEV_CHANGE): wlp3s0: link becomes ready
```

So kernel version 4.4 doesn't work and kernel version 4.15 does work. Is there any reason not to upgrade the Vostro 260? You could certainly try a live CD or USB of Ubuntu 18.04 LTS or 20.04 LTS to be sure before you install.

---

