---
title: "Broadcom-wl 19.04"
date: 2019-05-15
forum: Networking &amp; Wireless
---

### Post by kc1di on 2019-05-15
Still haven't got broacom-wl to work on 19.04, anyone got it working? If so mind sharing what you have done.
TIA.

---

### Post by chili555 on 2019-05-16
> Still haven't got broacom-wl to work on 19.04Meaning what? That it won't install? That it installs but won't modprobe?  That it installs and loads but doesn't drive your device? That it drives your device but doesn't connect? Or...what?

Please run and post:```
lspci -nnk | grep 0280 -A3
lsmod | grep wl
sudo modprobe wl && dmesg | grep wl
```

---

### Post by kc1di on 2019-05-16
Hello Chili555 and thanks for the response,

It means that wireless card is not found by system here are the outputs. 

```
sudo modprobe wl && dmesg | grep wl
[  126.958401] wl: loading out-of-tree module taints kernel.
[  126.958408] wl: module license 'MIXED/Proprietary' taints kernel.
[  126.962100] wl: module verification failed: signature and/or required key missing - tainting kernel
ubuntu@ubuntu:~$ 
```

```
lsmod | grep wl
wl                   6451200  0
cfg80211              671744  2 wl,mac80211

```

```
lspci -nnk | grep 0280 -A3
03:00.0 Network controller [0280]: Broadcom Inc. and subsidiaries BCM4312 802.11b/g LP-PHY [14e4:4315] (rev 01)
	Subsystem: Dell Wireless 1397 WLAN Mini-Card [1028:000c]
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb, wl

``` (Note I tried removing ssb module already made no difference.) 

Also rfkill return nothing.

here's the wireless script [pastebin ]("http://paste.ubuntu.com/p/Gk37J734PV/")

---

### Post by chili555 on 2019-05-16
With a working internet connection by ethernet, tethering or whatever means possible, open a terminal and do:```
sudo apt install firmware-b43-installer
sudo apt purge bcmwl-kernel-source
```Reboot and let us see:```
iwconfig
dmesg | grep b43
rfkill list all
```

---

### Post by kc1di on 2019-05-16
Here it is.  After reboot wireless is working. 

```
lo        no wireless extensions.

enp4s0    no wireless extensions.

wlp3s0    IEEE 802.11  ESSID:"PastorR"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: C0:3F:0E:C7:95:E4   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

dmesg | grep b43
Returns nothing. 

```
[rfkill list all
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

according to driver tool broadcome-sta is installed. 

Not sure why but it's now working :) 
thanks for the help

---

### Post by chili555 on 2019-05-16
> Not sure why but it's now working Quite simply, we removed the incorrect driver and installed the firmware required by the correct driver.

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

