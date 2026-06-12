---
title: "Can't login to network. denied association (code=18)"
date: 2019-12-29
forum: Networking &amp; Wireless
---

### Post by danielserrao on 2019-12-29
Hi,

I'm trying to login on a network on a Ubuntu 18.04.3 LTS. I can see the network available, but when I try to login it keeps asking for the password over and over again. I'm sure that the password is correct because I am able to login on the network using Windows 10 on the same laptop.

After executing the dmesg command I get:

```

[17463.062224] wlp0s20f3: authenticate with 50:c7:bf:3b:e0:57
[17463.066323] wlp0s20f3: send auth to 50:c7:bf:3b:e0:57 (try 1/3)
[17463.078164] wlp0s20f3: authenticated
[17463.082104] wlp0s20f3: associate with 50:c7:bf:3b:e0:57 (try 1/3)
[17463.089768] wlp0s20f3: RX AssocResp from 50:c7:bf:3b:e0:57 (capab=0x1431 status=18 aid=0)
[17463.089773] wlp0s20f3: 50:c7:bf:3b:e0:57 denied association (code=18)

```

Since I get code 18, I suppose the problem is > [COLOR=#24292E][FONT=SFMono-Regular]Association denied due to requesting station not supporting all of the data [/FONT][/COLOR][COLOR=#24292E][FONT=SFMono-Regular]rates in the BSSBasicRateSet parameter[/FONT][/COLOR]

When checking the NetworkManager status I get:

```

dec 29 15:16:36 daniel-HOST NetworkManager[14405]: <info> [1577628996.8569] device (wlp0s20f3): state change: failed -> disconnected (reason 'none', sys-iface-state: 'managed')
dec 29 15:19:43 daniel-HOST NetworkManager[14405]: <info> [1577629183.7388] device (wlp0s20f3): supplicant interface state: scanning -> associated
dec 29 15:19:43 daniel-HOST NetworkManager[14405]: <warn> [1577629183.7389] sup-iface[0x561a54343f00,wlp0s20f3]: connection disconnected (reason -3)
dec 29 15:19:43 daniel-HOST NetworkManager[14405]: <info> [1577629183.7440] device (wlp0s20f3): supplicant interface state: associated -> disconnected
dec 29 15:19:43 daniel-HOST NetworkManager[14405]: <info> [1577629183.8439] device (wlp0s20f3): supplicant interface state: disconnected -> inactive
dec 29 15:23:28 daniel-HOST NetworkManager[14405]: <info> [1577629408.9269] device (enp2s0f1): carrier: link connected
dec 29 15:25:22 daniel-HOST NetworkManager[14405]: <info> [1577629522.9351] device (wlp0s20f3): supplicant interface state: inactive -> associated
dec 29 15:25:22 daniel-HOST NetworkManager[14405]: <warn> [1577629522.9351] sup-iface[0x561a54343f00,wlp0s20f3]: connection disconnected (reason -3)
dec 29 15:25:22 daniel-HOST NetworkManager[14405]: <info> [1577629522.9403] device (wlp0s20f3): supplicant interface state: associated -> disconnected
dec 29 15:25:23 daniel-HOST NetworkManager[14405]: <info> [1577629523.0412] device (wlp0s20f3): supplicant interface state: disconnected -> inactive

```

When checking the wpa_supplicant I get:

```

dec 29 15:16:20 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: CTRL-EVENT-SSID-TEMP-DISABLED id=0 ssid="67-2.4" auth_failures=2 duration=20 reason=CONN_FAILED
dec 29 15:19:43 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: No network configuration found for the current AP
dec 29 15:19:43 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: CTRL-EVENT-DISCONNECTED bssid=38:d8:2f:11:f2:eb reason=3 locally_generated=1
dec 29 15:19:43 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
dec 29 15:25:22 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: No network configuration found for the current AP
dec 29 15:25:22 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: CTRL-EVENT-DISCONNECTED bssid=38:d8:2f:11:f2:eb reason=3 locally_generated=1
dec 29 15:25:22 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0
dec 29 15:28:51 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: No network configuration found for the current AP
dec 29 15:28:51 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: CTRL-EVENT-DISCONNECTED bssid=38:d8:2f:11:f2:eb reason=3 locally_generated=1
dec 29 15:28:51 daniel-HOST wpa_supplicant[14481]: wlp0s20f3: CTRL-EVENT-SUBNET-STATUS-UPDATE status=0

```


Some more useful information:

Kernel: 5.0.0-37-generic

Network controller/chipset: Intel Corporation Device 9df0 (rev 30)
Subsystem: Intel Corporation Device 0034
Kernel/wifi driver in use: iwlwifi
Kernel modules: iwlwifi

Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)

Router: TP-LINK Archer C9 V3

My laptop radio type/standard: 802.11ac

I spent a full day trying to find a solution that would work without success. Probably I'm missing something since I'm not experient with solving networking issues. I would be thankful if you could guide me on how to fix this.

Thanks

---

