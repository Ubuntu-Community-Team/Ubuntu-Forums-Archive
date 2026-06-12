---
title: "TL-WN823N-TL-WN823N-v2 vs Lubuntu 17.04"
date: 2017-10-04
forum: Networking &amp; Wireless
---

### Post by AuroraSCII on 2017-10-04
Greetings,

I am using the wifi dongle TL-WN823N-v2 with lubuntu 17.04 and having trouble to connect to my wifi.

ifconfig
```
wlx18a6f714b6e7: flags=4099<UP,BROADCAST,MULTICAST>  mtu 1500
        ether 18:a6:f7:14:b6:e7  txqueuelen 1000  (Ethernet)
        RX packets 0  bytes 0 (0.0 B)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 0  bytes 0 (0.0 B)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

lsusb
```
Bus 002 Device 003: ID 2357:0109  
Bus 002 Device 002: ID 04e8:6863 Samsung Electronics Co., Ltd GT-I9500 [Galaxy S4] / GT-I9250 [Galaxy Nexus] (network tethering)
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 046d:c52b Logitech, Inc. Unifying Receiver
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

modinfo 
[h=1]rtl8xxxu[/h]
```

filename:       /lib/modules/4.10.0-35-generic/kernel/drivers/net/wireless/realtek/rtl8xxxu/rtl8xxxu.ko
firmware:       rtlwifi/rtl8723bu_bt.bin
firmware:       rtlwifi/rtl8723bu_nic.bin
firmware:       rtlwifi/rtl8192eu_nic.bin
firmware:       rtlwifi/rtl8192cufw_TMSC.bin
firmware:       rtlwifi/rtl8192cufw_B.bin
firmware:       rtlwifi/rtl8192cufw_A.bin
firmware:       rtlwifi/rtl8723aufw_B_NoBT.bin
firmware:       rtlwifi/rtl8723aufw_B.bin
firmware:       rtlwifi/rtl8723aufw_A.bin
license:        GPL
description:    RTL8XXXu USB mac80211 Wireless LAN Driver
author:         Jes Sorensen <Jes.Sorensen@redhat.com>
srcversion:     4579E6203C3D3D3D7D7B53E
alias:          usb:v7392p7822d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v4855p0091d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p0100d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v20F4p624Dd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pAB2Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p330Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p3309d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p3307d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E66p0020d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0E66p0019d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp2E2Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0846pF001d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0846p9021d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v07B8p8178d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v07AAp0056d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0789p016Dd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0DF6p0070d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0DF6p0061d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p17ABd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v06F8pE035d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0586p341Fd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v050Dp2103d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v050Dp2102d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04BBp0950d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019p1201d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFFCd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFFBd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFF8d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFFAd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFF9d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04F2pAFF7d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:vCDABp8010d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v4856p0091d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v4855p0090d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pED17d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pAB2Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019pAB2Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2019p4902d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p330Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v13D3p3357d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v103Cp1629d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0EB0p9071d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0DF6p005Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0DF6p0052d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp5088d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp1E1Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0B05p17BAd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0846p9041d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v07B8p8189d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v06F8pE033d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v050Dp1102d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v04BBp094Cd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v1058p0631d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp317Fd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp818Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Ed*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Dd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Ad*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8177d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8170d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8191d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2001p3308d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v20F4p648Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v050Dp1004d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v7392p7811d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp817Fd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8178d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8176d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDApB720d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v2357p0109d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp818Bd*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp0724d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp1724d*dc*dsc*dp*icFFiscFFipFFin*
alias:          usb:v0BDAp8724d*dc*dsc*dp*icFFiscFFipFFin*
depends:        mac80211
intree:         Y
vermagic:       4.10.0-35-generic SMP mod_unload 
parm:           debug:Set debug mask (int)
parm:           ht40_2g:Enable HT40 support on the 2.4GHz band (bool)
parm:           dma_aggregation:Enable DMA packet aggregation (bool)
parm:           dma_agg_timeout:Set DMA aggregation timeout (range 1-127) (int)
parm:           dma_agg_pages:Set DMA aggregation pages (range 1-127, 0 to disable) (int)


```

I don't get why it fails to connect to my Wifi even though they are showing up in my network manager.
Here's my /etc/NetworkManager/NetworkManager.conf:

```
[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

[device]
wifi.scan-rand-mac-address=no
```

Any help would be greatly appreciated.

Regards

---

### Post by wildmanne39 on 2017-10-04
Hi, please click on the wireless script in my signature, follow the directions for running it and posting the results back here using code tags.

---

### Post by AuroraSCII on 2017-10-05
Hi, thank you.

Pastebin: [http://paste.ubuntu.com/25678667/](http://paste.ubuntu.com/25678667/)

regards

---

### Post by wildmanne39 on 2017-10-05
Please do:
```
echo "blacklist rtl8xxxu" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
Then do:
```
sudo add-apt-repository ppa:hanipouspilot/rtlwifi
sudo apt-get update
sudo apt-get install rtl8192eu-dkms
```
Reboot

Found in post 8 here.

[https://ubuntuforums.org/showthread.php?t=2348667](https://ubuntuforums.org/showthread.php?t=2348667)

---

