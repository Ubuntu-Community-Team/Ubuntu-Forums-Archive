---
title: "wifi disconnected &amp; wlan0 no such device"
date: 2016-12-19
forum: Networking &amp; Wireless
---

### Post by smallcat9603 on 2016-12-19
Dear all,

I am new to ubuntu and this is my first mail in this forum.
The OS version is 16.04.01 on my macbook. 
After the installation, I have spent a whole day to use the wifi connection, but still not successful.

I have installed the wireless driver from the installation usb flash and also tried 
```
apt-get update
apt-get install bcm-kernel-source
```
still it does not work.

Enable Wifi checked, but no wifi network can be connected. Wired connection is totally fine.
Also, I get by iwconfig wlan0, and the result is
wlan0 No such device

Other outputs:

```
lspci -nn | grep 0280
02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)

lsusb
Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

Thanks very much for your help!!

Regards,
huyao

---

### Post by chili555 on 2016-12-19
I assume that you really meant:```
sudo apt-get install bcm**wl**-kernel-source
```Is that correct?

What is the result of these terminal commands?```
sudo modprobe wl
iwconfig
sudo iwlist scan
```

---

### Post by wildmanne39 on 2016-12-19
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by smallcat9603 on 2016-12-19
> **chili555 said:**
> I assume that you really meant:```
sudo apt-get install bcm**wl**-kernel-source
```Is that correct?

What is the result of these terminal commands?```
sudo modprobe wl
iwconfig
sudo iwlist scan
```


Thanks a lot for your reply.
Yes, I meant bcmwl-kernel-source. Sorry for my mistake.

Output:

```

sudo modprobe wl
[sudo] password for smallcat: 

iwconfig
lo        no wireless extensions.

enp3s0    no wireless extensions.

wlp2s0    IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
sudo iwlist scan
lo        Interface doesn't support scanning.

enp3s0    Interface doesn't support scanning.

wlp2s0    No scan results

```

I also tried your method two years ago, still does not work..
[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

Thanks very much!!

---

### Post by smallcat9603 on 2016-12-19
I see. Thanks!

---

### Post by chili555 on 2016-12-19
No scan results?? Let's also see: ```
rfkill list all
dmesg | grep wl
```Thanks.

---

### Post by smallcat9603 on 2016-12-19
> **chili555 said:**
> No scan results?? Let's also see: ```
rfkill list all
dmesg | grep wl
```Thanks.


Thanks very much.

Output:

```

rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
2: brcmwl-0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

dmesg | grep wl
[   17.276377] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.282890] wl: module verification failed: signature and/or required key missing - tainting kernel
[   17.345894] wlan0: Broadcom BCM432b 802.11 Hybrid Wireless Controller 6.30.223.248 (r487574)
[   17.347406] wl 0000:02:00.0 wlp2s0: renamed from wlan0
[   39.717786] IPv6: ADDRCONF(NETDEV_UP): wlp2s0: link is not ready
[   70.019506] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  103.023548] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  146.033911] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  199.020027] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  262.020063] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  325.027999] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  388.062583] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  451.073986] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  453.567039] ERROR @wl_dev_intvar_get : error (-1)
[  453.567044] ERROR @wl_cfg80211_get_tx_power : error (-1)
[  466.868139] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  514.059835] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  577.069614] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  640.064127] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  703.021636] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  766.064030] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  829.077655] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  892.077773] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[  955.019947] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1018.019552] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1081.079579] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1144.056520] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1207.076673] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1270.043851] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1333.081564] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1396.077928] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1459.021624] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1522.032062] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1585.031584] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1648.083332] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1711.075913] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1774.042030] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1837.075512] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1900.062019] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 1963.075569] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2026.072129] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2089.033800] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2152.021667] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2215.078132] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2278.077629] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2341.077732] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2404.068103] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2467.019653] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2530.080049] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2593.077679] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2656.081567] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2719.085823] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2782.064124] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2845.053702] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2908.073562] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 2971.076044] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3034.075481] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3097.073651] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3160.081931] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3223.018696] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3286.076230] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3349.025767] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3412.081562] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3475.025741] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3538.084163] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3601.080108] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3664.041653] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3727.028165] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3790.022054] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3853.047875] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3916.036197] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 3979.019592] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4042.028162] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4105.077873] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4168.060117] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4231.021655] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4294.023545] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4357.025474] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4420.045697] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4483.032167] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4546.024127] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4609.021807] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4672.076385] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4735.020085] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4798.064176] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4861.040128] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4924.024135] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 4987.021484] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5050.040166] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5113.076529] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5176.022023] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5239.048199] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5302.033250] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5365.077927] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5428.076529] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5491.021665] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5554.077908] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5617.029661] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5680.080107] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5743.024144] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5806.069783] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5869.058335] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5932.028253] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 5995.063783] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6058.033883] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6121.024146] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6184.081640] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6247.084149] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6310.052163] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6373.053571] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6436.081994] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6499.024152] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6562.069517] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6625.077801] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6688.068520] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6751.025944] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)
[ 6814.028099] ERROR @wl_notify_scan_status : wlp2s0 Scan_results error (-22)

```

---

### Post by chili555 on 2016-12-20
Wow! No wonder it doesn't scan. It is a very unhappy hardware and driver combination! I have Googled the error and, remarkably, it is always associated with your exact device, 14e4:432b. I suggest that we experiment with the other Broadcom driver. With a working internet connection:```
sudo apt-get purge bbcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```Reboot and let us hear your result.

---

### Post by smallcat9603 on 2016-12-21
> **chili555 said:**
> Wow! No wonder it doesn't scan. It is a very unhappy hardware and driver combination! I have Googled the error and, remarkably, it is always associated with your exact device, 14e4:432b. I suggest that we experiment with the other Broadcom driver. With a working internet connection:```
sudo apt-get purge bbcmwl-kernel-source
sudo apt-get install firmware-b43-installer
```Reboot and let us hear your result.


Hi chili555, thanks very much for your patience! You meant bcmwl not bbcmwl, right?

Output:
(It seemed I had purged bcmwl-kernel-source before I did the following operation..)

```

sudo apt-get purge bcmwl-kernel-source
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'bcmwl-kernel-source' is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.

sudo apt-get install firmware-b43-installer
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  b43-fwcutter
The following NEW packages will be installed:
  b43-fwcutter firmware-b43-installer
0 upgraded, 2 newly installed, 0 to remove and 11 not upgraded.
Need to get 27.4 kB of archives.
After this operation, 158 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
Get:1 http://archive.ubuntu.com/ubuntu xenial/main amd64 b43-fwcutter amd64 1:019-2 [23.3 kB]
Get:2 http://archive.ubuntu.com/ubuntu xenial/multiverse amd64 firmware-b43-installer all 1:019-2 [4,120 B]
Fetched 27.4 kB in 1s (19.7 kB/s)                 
Preconfiguring packages ...
Selecting previously unselected package b43-fwcutter.
(Reading database ... 200513 files and directories currently installed.)
Preparing to unpack .../b43-fwcutter_1%3a019-2_amd64.deb ...
Unpacking b43-fwcutter (1:019-2) ...
Selecting previously unselected package firmware-b43-installer.
Preparing to unpack .../firmware-b43-installer_1%3a019-2_all.deb ...
Unpacking firmware-b43-installer (1:019-2) ...
Processing triggers for man-db (2.7.5-1) ...
Setting up b43-fwcutter (1:019-2) ...
Setting up firmware-b43-installer (1:019-2) ...
No chroot environment found. Starting normal installation
--2016-12-21 14:48:52--  http://www.lwfinger.com/b43-firmware/broadcom-wl-5.100.138.tar.bz2
Resolving www.lwfinger.com (www.lwfinger.com)... 173.254.28.119
Connecting to www.lwfinger.com (www.lwfinger.com)|173.254.28.119|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 13514651 (13M) [application/x-bzip2]
Saving to: &#8216;broadcom-wl-5.100.138.tar.bz2&#8217;

broadcom-wl-5.100.1 100%[===================>]  12.89M   641KB/s    in 16s     

2016-12-21 14:49:09 (818 KB/s) - &#8216;broadcom-wl-5.100.138.tar.bz2&#8217; saved [13514651/13514651]

Deleting old extracted firmware...
broadcom-wl-5.100.138/
broadcom-wl-5.100.138/linux/
broadcom-wl-5.100.138/linux/wl_apsta.o
broadcom-wl-5.100.138/linux/wl_ap.o
broadcom-wl-5.100.138/linux/wl_sta.o
broadcom-wl-5.100.138/README
broadcom-wl-5.100.138/config/
broadcom-wl-5.100.138/config/wlconfig_lx_shared
broadcom-wl-5.100.138/config/wl.mk
broadcom-wl-5.100.138/config/wl_default
broadcom-wl-5.100.138/config/wl_hnd
broadcom-wl-5.100.138/config/wlconfig_nomimo
This file is recognised as:
  filename   :  wl_apsta.o
  version    :  666.2
  MD5        :  e1b05e268bcdbfef3560c28fc161f30e
Extracting b43/lp0initvals14.fw
Extracting b43/lcn0bsinitvals25.fw
Extracting b43/n0bsinitvals25.fw
Extracting b43/n0bsinitvals17.fw
Extracting b43/ucode17_mimo.fw
Extracting b43/ucode16_lp.fw
Extracting b43/sslpn1initvals27.fw
Extracting b43/lp2bsinitvals19.fw
Extracting b43/sslpn3bsinitvals21.fw
Extracting b43/ucode16_sslpn.fw
  ucode time:     01:15:07
Extracting b43/ucode25_lcn.fw
Extracting b43/ucode21_sslpn.fw
Extracting b43/lp0bsinitvals14.fw
Extracting b43/b0g0initvals9.fw
Extracting b43/ucode20_sslpn.fw
Extracting b43/a0g1bsinitvals9.fw
Extracting b43/lp1initvals20.fw
Extracting b43/b0g0bsinitvals13.fw
Extracting b43/lp2initvals19.fw
Extracting b43/n2bsinitvals19.fw
Extracting b43/sslpn4bsinitvals22.fw
Extracting b43/ucode16_sslpn_nobt.fw
  ucode date:     2011-02-23
Extracting b43/n1bsinitvals20.fw
Extracting b43/n1initvals20.fw
Extracting b43/b0g0bsinitvals5.fw
Extracting b43/ucode22_sslpn.fw
Extracting b43/b0g0initvals13.fw
Extracting b43/ht0initvals26.fw
Extracting b43/ucode33_lcn40.fw
Extracting b43/sslpn1bsinitvals20.fw
Extracting b43/lcn400bsinitvals33.fw
Extracting b43/ucode14.fw
Extracting b43/a0g0initvals5.fw
Extracting b43/lp1bsinitvals22.fw
Extracting b43/n16initvals30.fw
Extracting b43/lp0bsinitvals16.fw
Extracting b43/lcn1bsinitvals25.fw
Extracting b43/lcn400initvals33.fw
Extracting b43/n0bsinitvals24.fw
Extracting b43/lcn2bsinitvals26.fw
Extracting b43/lcn1initvals26.fw
Extracting b43/n0bsinitvals22.fw
Extracting b43/n18initvals32.fw
Extracting b43/lcn2initvals26.fw
Extracting b43/a0g1bsinitvals5.fw
Extracting b43/n0bsinitvals11.fw
Extracting b43/lcn2initvals24.fw
Extracting b43/lcn0initvals26.fw
Extracting b43/n0absinitvals11.fw
Extracting b43/ucode21_sslpn_nobt.fw
  ucode time:     01:15:07
Extracting b43/ucode26_mimo.fw
Extracting b43/n2initvals19.fw
Extracting b43/sslpn3initvals21.fw
Extracting b43/a0g1bsinitvals13.fw
Extracting b43/sslpn4initvals22.fw
Extracting b43/pcm5.fw
Extracting b43/ucode22_mimo.fw
Extracting b43/ucode9.fw
Extracting b43/lcn2initvals25.fw
Extracting b43/lp1initvals22.fw
Extracting b43/sslpn1bsinitvals27.fw
Extracting b43/lcn0initvals24.fw
Extracting b43/ucode32_mimo.fw
Extracting b43/a0g0bsinitvals9.fw
Extracting b43/n18bsinitvals32.fw
Extracting b43/n0initvals24.fw
Extracting b43/n0initvals25.fw
Extracting b43/a0g1initvals5.fw
Extracting b43/ucode24_lcn.fw
Extracting b43/n0initvals17.fw
Extracting b43/n0bsinitvals16.fw
Extracting b43/lp0initvals15.fw
Extracting b43/b0g0initvals5.fw
Extracting b43/ucode20_sslpn_nobt.fw
Extracting b43/lcn1initvals24.fw
Extracting b43/sslpn0initvals16.fw
Extracting b43/a0g1initvals13.fw
Extracting b43/lp1bsinitvals20.fw
Extracting b43/sslpn2initvals19.fw
Extracting b43/a0g1initvals9.fw
Extracting b43/lcn1bsinitvals24.fw
Extracting b43/ucode5.fw
Extracting b43/lcn2bsinitvals24.fw
Extracting b43/lp0bsinitvals13.fw
Extracting b43/n0initvals16.fw
Extracting b43/ucode19_sslpn_nobt.fw
Extracting b43/b0g0bsinitvals9.fw
Extracting b43/ucode11.fw
Extracting b43/lp0initvals16.fw
Extracting b43/ucode16_mimo.fw
Extracting b43/lcn0bsinitvals26.fw
Extracting b43/ht0initvals29.fw
Extracting b43/lcn2bsinitvals25.fw
Extracting b43/a0g0initvals9.fw
Extracting b43/ucode29_mimo.fw
Extracting b43/lcn0bsinitvals24.fw
Extracting b43/ucode19_sslpn.fw
Extracting b43/lcn1initvals25.fw
Extracting b43/ucode30_mimo.fw
Extracting b43/n16bsinitvals30.fw
Extracting b43/ucode25_mimo.fw
Extracting b43/ucode24_mimo.fw
Extracting b43/ucode27_sslpn.fw
Extracting b43/lp0initvals13.fw
Extracting b43/a0g0bsinitvals5.fw
Extracting b43/ht0bsinitvals26.fw
Extracting b43/ucode13.fw
Extracting b43/sslpn2bsinitvals19.fw
Extracting b43/ucode15.fw
Extracting b43/lp0bsinitvals15.fw
Extracting b43/n0initvals11.fw
Extracting b43/lcn0initvals25.fw
Extracting b43/sslpn0bsinitvals16.fw
Extracting b43/sslpn1initvals20.fw
Extracting b43/lcn1bsinitvals26.fw
Extracting b43/n0initvals22.fw
Extracting b43/ht0bsinitvals29.fw

```

Now I reboot...

Sadly, still no use...:(

---

### Post by chili555 on 2016-12-21
> **smallcat9603 said:**
> 
Now I reboot...

Sadly, still no use...:(Gakkk! Something is, obviously, still wrong here. Let's dig deeper:```
lsmod | grep -e b43 -e wl
sudo dpkg -s broadcom-sta-dkms
```If the latter is installed, please purge it:```
sudo apt-get purge broadcom-sta-dkms
```Reboot and show me:```
iwconfig
sudo modprobe b43 && dmesg | grep b43
```

---

### Post by smallcat9603 on 2016-12-22
> **chili555 said:**
> Gakkk! Something is, obviously, still wrong here. Let's dig deeper:```
lsmod | grep -e b43 -e wl
sudo dpkg -s broadcom-sta-dkms
```If the latter is installed, please purge it:```
sudo apt-get purge broadcom-sta-dkms
```Reboot and show me:```
iwconfig
sudo modprobe b43 && dmesg | grep b43
```

Thanks a lot!
Before I report the result, I say a strange thing. Several hours ago, I suddenly found my machine can be connected by wifi (SSIDs appear), and I tried to connect it and it was successfully done! To verify it really works I reboot (several times) the machine, then the wifi did not work again. Maybe a 10% chance to be connected? Or I should input some code to switch on the wifi driver?

Output:

```

lsmod | grep -e b43 -e wl
b43                   417792  0
bcma                   53248  1 b43
mac80211              737280  1 b43
cfg80211              565248  2 b43,mac80211
ssb                    65536  1 b43

sudo dpkg -s broadcom-sta-dkms
[sudo] password for smallcat: 
dpkg-query: package 'broadcom-sta-dkms' is not installed and no information is available
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.

iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          
enp3s0    no wireless extensions.

sudo modprobe b43 && dmesg | grep b43
[   19.117994] b43-phy0: Broadcom 4322 WLAN found (core revision 16)
[   19.148603] b43-phy0: Found PHY: Analog 8, Type 4 (N), Revision 4
[   19.148628] b43-phy0: Found Radio: Manuf 0x17F, ID 0x2056, Revision 3, Version 0
[   43.724233] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)

```


[update after two hours] 

After trying several times, I found that indeed the problem exists after each reboot, but when the machine goes to sleep and then is woken up, interestingly the wifi network works!! 

Now the problem maybe becomes how can I switch on wifi after each reboot, not by the sleep-wakeup way?

---

### Post by Hadaka on 2016-12-22
Hi please do..
This will automatically load the b43 module on boot or restart.
```
echo 'b43' | sudo tee -a /etc/modules
```
please also post the output of ..
```
nmcli nm
```
remove any wired and usb connections..boot and test wireless
Thanks.

---

### Post by smallcat9603 on 2016-12-22
> **Hadaka said:**
> Hi please do..
This will automatically load the b43 module on boot or restart.
```
echo 'b43' | sudo tee -a /etc/modules
```
please also post the output of ..
```
nmcli nm
```
remove any wired and usb connections..boot and test wireless
Thanks.

Hi, thanks for your attention.

Output:

```

echo 'b43' | sudo tee -a /etc/modules
[sudo] password for smallcat: 
b43

nmcli nm
Error: Object 'nm' is unknown, try 'nmcli help'.

```

Now reboot...

Ah...it seems the wifi problem has been solved after the restart...thanks very much!!!

---

### Post by Hadaka on 2016-12-22
Glad that  worked for you ! Just to humor me,
if you have the time, and now that your wifi is working
would you be so kind as to post the output of..
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
This will create a file in your home directory named **wireless-info.txt**
Please post that TEXT file. And if you are satisfied with your wireless now, please take the time to mark
your thread **Solved** by clicking **Thread tools** near the top of the page and then choose **Solved**.
Thanks

---

### Post by smallcat9603 on 2016-12-22
> **Hadaka said:**
> Glad that  worked for you ! Just to humor me,
if you have the time, and now that your wifi is working
would you be so kind as to post the output of..
```
wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
```
This will create a file in your home directory named **wireless-info.txt**
Please post that TEXT file. And if you are satisfied with your wireless now, please take the time to mark
your thread **Solved** by clicking **Thread tools** near the top of the page and then choose **Solved**.
Thanks

[B]
[update with a new problem] Sorry that I just confirmed a new problem. Now the wifi works well after each reboot, but if I close the lid and open it again, the wifi does not work. So I must reboot the machine again to make it connected. Is there a way to automatically connect the wifi networks after each system sleep-wakeup? Thanks very much![/B]


Thanks a lot for your help! I would like to post the result. Just one thing I noticed, today after a long sleep (10 hours?) the machine cannot connect to wifi networks again. But after rebooting the machine, it works. Maybe it is not a usual thing, I hope.

Output:

```

wget -N -t 5 -T 10 https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info && chmod +x wireless-info && ./wireless-info
--2016-12-23 11:15:21--  https://github.com/UbuntuForums/wireless-info/raw/master/wireless-info
Resolving github.com (github.com)... 192.30.253.112, 192.30.253.113
Connecting to github.com (github.com)|192.30.253.112|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info [following]
--2016-12-23 11:15:32--  https://raw.githubusercontent.com/UbuntuForums/wireless-info/master/wireless-info
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 151.101.100.133
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|151.101.100.133|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 16156 (16K) [text/plain]
Saving to: &#8216;wireless-info&#8217;

wireless-info       100%[===================>]  15.78K  30.3KB/s    in 0.5s    

Last-modified header missing -- time-stamps turned off.
2016-12-23 11:15:41 (30.3 KB/s) - &#8216;wireless-info&#8217; saved [16156/16156]

[sudo] password for smallcat: 

Results saved in "/home/smallcat/wireless-info.txt".

Results also archived in "/home/smallcat/wireless-info.tar.gz", as they exceed the 19.5 kB size limit for ".txt" attachments on the Ubuntu Forums.


```


wireless-info.txt:

```


########## wireless info START ##########

Report from: 23 Dec 2016 11:15 JST +0900

Booted last: 23 Dec 2016 00:00 JST +0900

Script from: 08 Jul 2016 02:16 UTC +0000

##### release ###########################

Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

##### kernel ############################

Linux 4.4.0-53-generic #74-Ubuntu SMP Fri Dec 2 15:59:10 UTC 2016 x86_64 x86_64 x86_64 GNU/Linux

Parameters: ro, quiet, splash, vt.handoff=7

##### desktop ###########################

Ubuntu

##### lspci #############################

02:00.0 Network controller [0280]: Broadcom Corporation BCM4322 802.11a/b/g/n Wireless LAN Controller [14e4:432b] (rev 01)
    Subsystem: Apple Inc. AirPort Extreme [106b:008d]
    Kernel driver in use: b43-pci-bridge

03:00.0 Ethernet controller [0200]: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684] (rev 10)
    Subsystem: Broadcom Corporation NetXtreme BCM5764M Gigabit Ethernet PCIe [14e4:1684]
    Kernel driver in use: tg3

##### lsusb #############################

Bus 002 Device 002: ID 05ac:8403 Apple, Inc. Internal Memory Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 005: ID 05ac:8213 Apple, Inc. Bluetooth Host Controller
Bus 004 Device 004: ID 0a5c:4500 Broadcom Corp. BCM2046B1 USB 2.0 Hub (part of BCM2046 Bluetooth)
Bus 004 Device 003: ID 05ac:8242 Apple, Inc. Built-in IR Receiver
Bus 004 Device 002: ID 05ac:0236 Apple, Inc. Internal Keyboard/Trackpad (ANSI)
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 05ac:8507 Apple, Inc. Built-in iSight
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

##### PCMCIA card info ##################

##### rfkill ############################

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

##### lsmod #############################

b43                   417792  0
bcma                   53248  1 b43
mac80211              737280  1 b43
cfg80211              565248  2 b43,mac80211
mxm_wmi                16384  1 nouveau
wmi                    20480  2 mxm_wmi,nouveau
ssb                    65536  1 b43

##### interfaces ########################

auto lo
iface lo inet loopback

##### ifconfig ##########################

enp3s0    Link encap:Ethernet  HWaddr <MAC 'enp3s0' [IF1]>  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:20 

wlan0     Link encap:Ethernet  HWaddr <MAC 'wlan0' [IF2]>  
          inet addr:192.168.1.12  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::8892:b84f:51a:48b0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1400  Metric:1
          RX packets:821 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1019 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:413691 (413.6 KB)  TX bytes:175477 (175.4 KB)

##### iwconfig ##########################

lo        no wireless extensions.

enp3s0    no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"(mobilecube)034658"  
          Mode:Managed  Frequency:2.442 GHz  Access Point: <MAC '(mobilecube)034658' [AN3]>   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=65/70  Signal level=-45 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:61   Missed beacon:0

##### route #############################

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
0.0.0.0         192.168.1.1     0.0.0.0         UG    600    0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
192.168.1.0     0.0.0.0         255.255.255.0   U     600    0        0 wlan0

##### resolv.conf #######################

nameserver 127.0.1.1

##### network managers ##################

Installed:

    NetworkManager

Running:

root       664     1  0 11:11 ?        00:00:01 /usr/sbin/NetworkManager --no-daemon

##### NetworkManager info ###############

GENERAL.DEVICE:                         wlan0
GENERAL.TYPE:                           wifi
GENERAL.NM-TYPE:                        NMDeviceWifi
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        BCM4322 802.11a/b/g/n Wireless LAN Controller (AirPort Extreme)
GENERAL.DRIVER:                         b43
GENERAL.DRIVER-VERSION:                 4.4.0-53-generic
GENERAL.FIRMWARE-VERSION:               N/A
GENERAL.HWADDR:                         <MAC 'wlan0' [IF2]>
GENERAL.MTU:                            0
GENERAL.STATE:                          100 (connected)
GENERAL.REASON:                         0 (No reason given)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:15.0/0000:02:00.0/ssb0:0/net/wlan0
GENERAL.IP-IFACE:                       wlan0
GENERAL.IS-SOFTWARE:                    no
GENERAL.NM-MANAGED:                     yes
GENERAL.AUTOCONNECT:                    yes
GENERAL.FIRMWARE-MISSING:               no
GENERAL.NM-PLUGIN-MISSING:              no
GENERAL.PHYS-PORT-ID:                   --
GENERAL.CONNECTION:                     (mobilecube)034658 2
GENERAL.CON-UUID:                       09f26368-318f-49a9-bb15-34e24028b82c
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveConnection/0
GENERAL.METERED:                        no (guessed)
CAPABILITIES.CARRIER-DETECT:            no
CAPABILITIES.SPEED:                     54 Mb/s
CAPABILITIES.IS-SOFTWARE:               no
WIFI-PROPERTIES.WEP:                    yes
WIFI-PROPERTIES.WPA:                    yes
WIFI-PROPERTIES.WPA2:                   yes
WIFI-PROPERTIES.TKIP:                   yes
WIFI-PROPERTIES.CCMP:                   yes
WIFI-PROPERTIES.AP:                     yes
WIFI-PROPERTIES.ADHOC:                  yes
WIFI-PROPERTIES.2GHZ:                   yes
WIFI-PROPERTIES.5GHZ:                   yes
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: /org/freedesktop/NetworkManager/Settings/{2,5,4,0,1}
CONNECTIONS.AVAILABLE-CONNECTIONS[1]:   bbd757c3-921c-43e4-a86e-caafbd3edbb1 | Soken
CONNECTIONS.AVAILABLE-CONNECTIONS[2]:   09f26368-318f-49a9-bb15-34e24028b82c | (mobilecube)034658 2
CONNECTIONS.AVAILABLE-CONNECTIONS[3]:   13c66457-0999-47f8-9b28-efacc763ebc7 | Soken 1
CONNECTIONS.AVAILABLE-CONNECTIONS[4]:   fd7d5724-f77c-4954-88e5-a62ec5b76e13 | (mobilecube)034658
CONNECTIONS.AVAILABLE-CONNECTIONS[5]:   4dc128b3-7ebf-47d2-a6bc-2e9141c0680b | (mobilecube)034658 1
IP4.ADDRESS[1]:                         192.168.1.12/24
IP4.GATEWAY:                            192.168.1.1
IP4.ROUTE[1]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt = 1000
IP4.DNS[1]:                             192.168.1.1
DHCP4.OPTION[1]:                        requested_ms_classless_static_routes = 1
DHCP4.OPTION[2]:                        requested_domain_search = 1
DHCP4.OPTION[3]:                        requested_host_name = 1
DHCP4.OPTION[4]:                        requested_time_offset = 1
DHCP4.OPTION[5]:                        requested_domain_name = 1
DHCP4.OPTION[6]:                        requested_rfc3442_classless_static_routes = 1
DHCP4.OPTION[7]:                        requested_broadcast_address = 1
DHCP4.OPTION[8]:                        requested_wpad = 1
DHCP4.OPTION[9]:                        requested_netbios_scope = 1
DHCP4.OPTION[10]:                       next_server = 0.0.0.0
DHCP4.OPTION[11]:                       expiry = 1482462691
DHCP4.OPTION[12]:                       requested_interface_mtu = 1
DHCP4.OPTION[13]:                       requested_subnet_mask = 1
DHCP4.OPTION[14]:                       dhcp_lease_time = 3600
DHCP4.OPTION[15]:                       dhcp_message_type = 5
DHCP4.OPTION[16]:                       ip_address = 192.168.1.12
DHCP4.OPTION[17]:                       requested_static_routes = 1
DHCP4.OPTION[18]:                       requested_domain_name_servers = 1
DHCP4.OPTION[19]:                       routers = 192.168.1.1
DHCP4.OPTION[20]:                       broadcast_address = 192.168.1.255
DHCP4.OPTION[21]:                       requested_ntp_servers = 1
DHCP4.OPTION[22]:                       requested_netbios_name_servers = 1
DHCP4.OPTION[23]:                       interface_mtu = 1400
DHCP4.OPTION[24]:                       domain_name_servers = 192.168.1.1
DHCP4.OPTION[25]:                       subnet_mask = 255.255.255.0
DHCP4.OPTION[26]:                       network_number = 192.168.1.0
DHCP4.OPTION[27]:                       requested_routers = 1
DHCP4.OPTION[28]:                       dhcp_server_identifier = 192.168.1.1
IP6.ADDRESS[1]:                         fe80::8892:b84f:51a:48b0/64
IP6.GATEWAY:                            

GENERAL.DEVICE:                         enp3s0
GENERAL.TYPE:                           ethernet
GENERAL.NM-TYPE:                        NMDeviceEthernet
GENERAL.VENDOR:                         Broadcom Corporation
GENERAL.PRODUCT:                        NetXtreme BCM5764M Gigabit Ethernet PCIe
GENERAL.DRIVER:                         tg3
GENERAL.DRIVER-VERSION:                 3.137
GENERAL.FIRMWARE-VERSION:               5764m-v3.38
GENERAL.HWADDR:                         <MAC 'enp3s0' [IF1]>
GENERAL.MTU:                            1500
GENERAL.STATE:                          20 (unavailable)
GENERAL.REASON:                         2 (Device is now managed)
GENERAL.UDI:                            /sys/devices/pci0000:00/0000:00:16.0/0000:03:00.0/net/enp3s0
GENERAL.IP-IFACE:                       
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
WIRED-PROPERTIES.CARRIER:               off
CONNECTIONS.AVAILABLE-CONNECTION-PATHS: 

SSID                BSSID              MODE   CHAN  FREQ      RATE       SIGNAL  BARS  SECURITY     ACTIVE  * 
HUMAX-EEC71         <MAC 'HUMAX-EEC71' [AN1]>  Infra  11    2462 MHz  54 Mbit/s  94      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
HUMAX-A0772         <MAC 'HUMAX-A0772' [AN2]>  Infra  11    2462 MHz  54 Mbit/s  92      &#9602;&#9604;&#9606;&#9608;  WPA1 WPA2    no        
(mobilecube)034658  <MAC '(mobilecube)034658' [AN3]>  Infra  7     2442 MHz  54 Mbit/s  75      &#9602;&#9604;&#9606;_  WPA1 WPA2    yes     * 
HUMAX-EEC71-A       <MAC 'HUMAX-EEC71-A' [AN4]>  Infra  48    5240 MHz  54 Mbit/s  72      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
Copy39918           <MAC 'Copy39918' [AN5]>  Infra  1     2412 MHz  54 Mbit/s  70      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
HUMAX-E0CAD         <MAC 'HUMAX-E0CAD' [AN6]>  Infra  11    2462 MHz  54 Mbit/s  69      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
FON_FREE_INTERNET   <MAC 'FON_FREE_INTERNET' [AN7]>  Infra  5     2432 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  --           no        
MyPlace             <MAC 'MyPlace' [AN8]>  Infra  5     2432 MHz  54 Mbit/s  67      &#9602;&#9604;&#9606;_  WPA1         no        
FON_FREE_EAP        <MAC 'FON_FREE_EAP' [AN9]>  Infra  5     2432 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA1 802.1X  no        
HUMAX-B99F1         <MAC 'HUMAX-B99F1' [AN10]>  Infra  11    2462 MHz  54 Mbit/s  65      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
AirPort39918        <MAC 'AirPort39918' [AN11]>  Infra  1     2412 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
HUMAX-B99F1-A       <MAC 'HUMAX-B99F1-A' [AN12]>  Infra  40    5200 MHz  54 Mbit/s  64      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
Guest39918          <MAC 'Guest39918' [AN13]>  Infra  1     2412 MHz  54 Mbit/s  62      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
aterm-3b6eb8-g      <MAC 'aterm-3b6eb8-g' [AN14]>  Infra  6     2437 MHz  54 Mbit/s  59      &#9602;&#9604;&#9606;_  WPA1 WPA2    no        
--                  <MAC '--' [AN15]>  Infra  6     2437 MHz  54 Mbit/s  55      &#9602;&#9604;__  WEP          no        
BCW710J-17196-G     <MAC 'BCW710J-17196-G' [AN16]>  Infra  11    2462 MHz  54 Mbit/s  54      &#9602;&#9604;__  WPA1 WPA2    no        
F660T-2jnY-G        <MAC 'F660T-2jnY-G' [AN17]>  Infra  11    2462 MHz  54 Mbit/s  52      &#9602;&#9604;__  WPA1 WPA2    no        
HUMAX-A0772-A       <MAC 'HUMAX-A0772-A' [AN18]>  Infra  48    5240 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
F660T-2jnY-A        <MAC 'F660T-2jnY-A' [AN19]>  Infra  116   5580 MHz  54 Mbit/s  47      &#9602;&#9604;__  WPA1 WPA2    no        
DC094C895708-2G     <MAC 'DC094C895708-2G' [AN20]>  Infra  2     2417 MHz  54 Mbit/s  44      &#9602;&#9604;__  WPA1 WPA2    no        
aterm-a4f945-g      <MAC 'aterm-a4f945-g' [AN21]>  Infra  7     2442 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2    no        
BCW710J-17196-A     <MAC 'BCW710J-17196-A' [AN22]>  Infra  136   5680 MHz  54 Mbit/s  37      &#9602;&#9604;__  WPA1 WPA2    no        
aterm-a4f945-gw     <MAC 'aterm-a4f945-gw' [AN23]>  Infra  7     2442 MHz  54 Mbit/s  35      &#9602;&#9604;__  WEP          no        
elecom2g-C9C694     <MAC 'elecom2g-C9C694' [AN24]>  Infra  4     2427 MHz  54 Mbit/s  32      &#9602;&#9604;__  WPA1 WPA2    no        
pr500k-8daac2-2     <MAC 'pr500k-8daac2-2' [AN25]>  Infra  1     2412 MHz  54 Mbit/s  30      &#9602;___  WPA2         no        
RVS340HI-E16D4F-2   <MAC 'RVS340HI-E16D4F-2' [AN26]>  Infra  5     2432 MHz  54 Mbit/s  30      &#9602;___  WEP          no        
My ASUS             <MAC 'My ASUS' [AN27]>  Infra  6     2437 MHz  54 Mbit/s  27      &#9602;___  WPA2         no        
FON_FREE_EAP        <MAC 'FON_FREE_EAP' [AN28]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA1 802.1X  no        
MyPlace_3C7688      <MAC 'MyPlace_3C7688' [AN29]>  Infra  6     2437 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
e-timer-D5A664      <MAC 'e-timer-D5A664' [AN30]>  Infra  9     2452 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
Buffalo-G-3060      <MAC 'Buffalo-G-3060' [AN31]>  Infra  11    2462 MHz  54 Mbit/s  25      &#9602;___  WPA2         no        
pr500k-f5d067-2     <MAC 'pr500k-f5d067-2' [AN32]>  Infra  1     2412 MHz  54 Mbit/s  24      &#9602;___  WEP          no        
FON_FREE_INTERNET   <MAC 'FON_FREE_INTERNET' [AN33]>  Infra  6     2437 MHz  54 Mbit/s  22      &#9602;___  --           no        
W01_94FE2204FCFE    <MAC 'W01_94FE2204FCFE' [AN34]>  Infra  10    2457 MHz  54 Mbit/s  22      &#9602;___  WPA1 WPA2    no        
YS002               <MAC 'YS002' [AN35]>  Infra  7     2442 MHz  54 Mbit/s  17      &#9602;___  WPA1 WPA2    no        
planexuser          <MAC 'planexuser' [AN36]>  Infra  12    2467 MHz  54 Mbit/s  15      &#9602;___  WEP          no        

##### NetworkManager.state ##############

[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

##### NetworkManager.conf ###############

[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq

[ifupdown]
managed=false

##### NetworkManager profiles ###########

[[/etc/NetworkManager/system-connections/(mobilecube)034658 2]] (600 root)
[connection] id=(mobilecube)034658 2 | type=wifi | permissions=user:smallcat:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=(mobilecube)034658
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/(mobilecube)034658 1]] (600 root)
[connection] id=(mobilecube)034658 1 | type=wifi | permissions=user:smallcat:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=(mobilecube)034658
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/(mobilecube)034658]] (600 root)
[connection] id=(mobilecube)034658 | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=(mobilecube)034658
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Soken]] (600 root)
[connection] id=Soken | type=wifi | autoconnect=false | permissions=
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Soken
[ipv4] method=shared
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/soken]] (600 root)
[connection] id=soken | type=wifi | permissions=user:smallcat:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=soken
[ipv4] method=auto
[ipv6] method=auto

[[/etc/NetworkManager/system-connections/Soken 1]] (600 root)
[connection] id=Soken 1 | type=wifi | permissions=user:smallcat:;
[wifi] mac-address=<MAC 'wlan0' [IF2]> | mac-address-blacklist= | ssid=Soken
[ipv4] method=auto
[ipv6] method=auto

##### iw reg get ########################

Region: Asia/Tokyo (based on set time zone)

country JP: DFS-JP
    (2402 - 2482 @ 40), (N/A, 20), (N/A)
    (2474 - 2494 @ 20), (N/A, 20), (N/A), NO-OFDM
    (4910 - 4990 @ 40), (N/A, 23), (N/A)
    (5030 - 5090 @ 40), (N/A, 23), (N/A)
    (5170 - 5250 @ 80), (N/A, 20), (N/A)
    (5250 - 5330 @ 80), (N/A, 20), (0 ms), DFS
    (5490 - 5710 @ 160), (N/A, 23), (0 ms), DFS
    (59000 - 66000 @ 2160), (N/A, 10), (N/A)

##### iwlist channels ###################

lo        no frequency information.

enp3s0    no frequency information.

wlan0     32 channels in total; available frequencies :
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
          Channel 14 : 2.484 GHz
          Channel 184 : 4.92 GHz
          Channel 186 : 4.93 GHz
          Channel 188 : 4.94 GHz
          Channel 190 : 4.95 GHz
          Channel 192 : 4.96 GHz
          Channel 194 : 4.97 GHz
          Channel 196 : 4.98 GHz
          Channel 08 : 5.04 GHz
          Channel 10 : 5.05 GHz
          Channel 12 : 5.06 GHz
          Channel 14 : 5.07 GHz
          Channel 16 : 5.08 GHz
          Channel 36 : 5.18 GHz
          Channel 38 : 5.19 GHz
          Channel 40 : 5.2 GHz
          Channel 42 : 5.21 GHz
          Channel 44 : 5.22 GHz
          Channel 46 : 5.23 GHz
          Current Frequency:2.442 GHz (Channel 7)

##### iwlist scan #######################

lo        Interface doesn't support scanning.

wlan0     Failed to read scan data : Resource temporarily unavailable

enp3s0    Interface doesn't support scanning.

##### module infos ######################

[b43]
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/net/wireless/b43/b43.ko
firmware:       b43/ucode9.fw
firmware:       b43/ucode5.fw
firmware:       b43/ucode16_mimo.fw
firmware:       b43/ucode15.fw
firmware:       b43/ucode14.fw
firmware:       b43/ucode13.fw
firmware:       b43/ucode11.fw
license:        GPL
author:         Rafa&#322; Mi&#322;ecki
author:         Gábor Stefanik
author:         Michael Buesch
author:         Stefano Brivio
author:         Martin Langer
description:    Broadcom B43 wireless driver
srcversion:     6046FCC9190ABD5D296D2D2
depends:        mac80211,ssb,bcma,cfg80211
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 
parm:           bad_frames_preempt:enable(1) / disable(0) Bad Frames Preemption (int)
parm:           fwpostfix:Postfix for the .fw files to load. (string)
parm:           hwpctl:Enable hardware-side power control (default off) (int)
parm:           nohwcrypt:Disable hardware encryption. (int)
parm:           hwtkip:Enable hardware tkip. (int)
parm:           qos:Enable QOS support (default on) (int)
parm:           btcoex:Enable Bluetooth coexistence (default on) (int)
parm:           verbose:Log message verbosity: 0=error, 1=warn, 2=info(default), 3=debug (int)
parm:           pio:Use PIO accesses by default: 0=DMA, 1=PIO (int)
parm:           allhwsupport:Enable support for all hardware (even it if overlaps with the brcmsmac driver) (int)

[bcma]
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/bcma/bcma.ko
license:        GPL
description:    Broadcom's specific AMBA driver
srcversion:     B8F81D53A09CD1D43DDE810
depends:        
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 

[mac80211]
filename:       /lib/modules/4.4.0-53-generic/kernel/net/mac80211/mac80211.ko
license:        GPL
description:    IEEE 802.11 subsystem
srcversion:     F1176862D12ECD05A1066CF
depends:        cfg80211
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 
parm:           minstrel_vht_only:Use only VHT rates when VHT is supported by sta. (bool)
parm:           max_nullfunc_tries:Maximum nullfunc tx tries before disconnecting (reason 4). (int)
parm:           max_probe_tries:Maximum probe tries before disconnecting (reason 4). (int)
parm:           beacon_loss_count:Number of beacon intervals before we decide beacon was lost. (int)
parm:           probe_wait_ms:Maximum time(ms) to wait for probe response before disconnecting (reason 4). (int)
parm:           ieee80211_default_rc_algo:Default rate control algorithm for mac80211 to use (charp)

[cfg80211]
filename:       /lib/modules/4.4.0-53-generic/kernel/net/wireless/cfg80211.ko
description:    wireless configuration support
license:        GPL
author:         Johannes Berg
srcversion:     FD4B9DA2F385F0531B5CB0B
depends:        
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 
parm:           ieee80211_regdom:IEEE 802.11 regulatory domain code (charp)
parm:           cfg80211_disable_40mhz_24ghz:Disable 40MHz support in the 2.4GHz band (bool)

[ssb]
filename:       /lib/modules/4.4.0-53-generic/kernel/drivers/ssb/ssb.ko
license:        GPL
description:    Sonics Silicon Backplane driver
srcversion:     E5F0C2CF8244682FABB35A4
depends:        
intree:         Y
vermagic:       4.4.0-53-generic SMP mod_unload modversions 

##### module parameters #################

[b43]
allhwsupport: 0
bad_frames_preempt: 0
btcoex: 1
hwpctl: 0
hwtkip: 0
nohwcrypt: 0
pio: 0
qos: 1
verbose: 2

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

b43

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

[/etc/modprobe.d/mlx4.conf]
softdep mlx4_core post: mlx4_en

##### rc.local ##########################

exit 0

##### pm-utils ##########################

##### udev rules ########################

##### dmesg #############################

[   41.592495] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   41.780205] b43-phy0: Loading firmware version 666.2 (2011-02-23 01:15:07)
[   42.112501] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.117673] IPv6: ADDRCONF(NETDEV_UP): enp3s0: link is not ready (repeated 2 times)
[   43.244961] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   56.733097] wlan0: authenticate with <MAC '(mobilecube)034658' [AN3]>
[   56.760857] wlan0: send auth to <MAC '(mobilecube)034658' [AN3]> (try 1/3)
[   56.964039] wlan0: send auth to <MAC '(mobilecube)034658' [AN3]> (try 2/3)
[   57.168073] wlan0: send auth to <MAC '(mobilecube)034658' [AN3]> (try 3/3)
[   57.172143] wlan0: authenticated
[   57.172348] b43 ssb0:0 wlan0: disabling HT as WMM/QoS is not supported by the AP
[   57.172351] b43 ssb0:0 wlan0: disabling VHT as WMM/QoS is not supported by the AP
[   57.176084] wlan0: associate with <MAC '(mobilecube)034658' [AN3]> (try 1/3)
[   57.178695] wlan0: RX AssocResp from <MAC '(mobilecube)034658' [AN3]> (capab=0x431 status=0 aid=4)
[   57.179147] wlan0: associated
[   57.179187] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   86.656221] b43-phy0 ERROR: PHY init: Channel switch to default failed
[   86.668231] b43-phy0: Radio turned on by software
[   87.404274] b43-phy0 ERROR: PHY init: Channel switch to default failed
[   87.412274] b43-phy0: Radio turned on by software
[   88.120218] b43-phy0 ERROR: PHY init: Channel switch to default failed
[   88.128279] b43-phy0: Radio turned on by software
[   88.836238] b43-phy0 ERROR: PHY init: Channel switch to default failed
[   88.844243] b43-phy0: Radio turned on by software
[   89.544217] b43-phy0 ERROR: PHY init: Channel switch to default failed
[   89.552227] b43-phy0: Radio turned on by software
[  130.724422] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  130.732327] b43-phy0: Radio turned on by software
[  131.440284] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  131.448333] b43-phy0: Radio turned on by software
[  132.152212] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  132.160233] b43-phy0: Radio turned on by software
[  132.892251] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  132.900244] b43-phy0: Radio turned on by software
[  133.604198] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  133.612240] b43-phy0: Radio turned on by software
[  192.520301] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  192.528320] b43-phy0: Radio turned on by software
[  193.228432] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  193.236348] b43-phy0: Radio turned on by software
[  193.928320] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  193.936304] b43-phy0: Radio turned on by software
[  194.636377] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  194.644338] b43-phy0: Radio turned on by software
[  195.340270] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  195.348254] b43-phy0: Radio turned on by software
[  275.600378] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  275.608446] b43-phy0: Radio turned on by software
[  276.324302] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  276.332300] b43-phy0: Radio turned on by software
[  277.024315] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  277.032291] b43-phy0: Radio turned on by software
[  277.732302] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  277.740300] b43-phy0: Radio turned on by software
[  278.444500] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  278.452284] b43-phy0: Radio turned on by software
[  329.008370] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  329.016256] b43-phy0: Radio turned on by software
[  329.740236] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  329.748227] b43-phy0: Radio turned on by software
[  330.468245] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  330.476271] b43-phy0: Radio turned on by software
[  331.180253] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  331.188269] b43-phy0: Radio turned on by software
[  331.928253] b43-phy0 ERROR: PHY init: Channel switch to default failed
[  331.936278] b43-phy0: Radio turned on by software

########## wireless info END ############


```

---

### Post by Hadaka on 2016-12-24
Hi, your dmesg section in your wireless report is showing..
```
b43-phy0 ERROR: PHY init: Channel switch to default failed
```
you are currently on channel 7..
```
Current Frequency:2.442 GHz (Channel 7)
```
and using a japanese mobilecube type router..
```
ESSID:"(mobilecube)034658" 
```
with your basic region..
```
Region: Asia/Tokyo (based on set time zone)
```
Is it possible to change the channel in your "mobilecube" ?
*If yes..then change to channel 1 or 11...wpa2 ccmp
Is it possible to change the ESSID in the "mobilecube" ?
*If yes..then change to something with no "("  ")" in the name.
Next to Connect Automatically...click your wifi icon then click
Edit Connections, Edit your connection and check the box marked
Connect Automatically...see attached
[ATTACH=CONFIG]272825[/ATTACH]
save your changes...boot and test.
thanks.

---

### Post by smallcat9603 on 2016-12-24
> **Hadaka said:**
> Hi, your dmesg section in your wireless report is showing..
```
b43-phy0 ERROR: PHY init: Channel switch to default failed
```
you are currently on channel 7..
```
Current Frequency:2.442 GHz (Channel 7)
```
and using a japanese mobilecube type router..
```
ESSID:"(mobilecube)034658" 
```
with your basic region..
```
Region: Asia/Tokyo (based on set time zone)
```
Is it possible to change the channel in your "mobilecube" ?
*If yes..then change to channel 1 or 11...wpa2 ccmp
Is it possible to change the ESSID in the "mobilecube" ?
*If yes..then change to something with no "("  ")" in the name.
Next to Connect Automatically...click your wifi icon then click
Edit Connections, Edit your connection and check the box marked
Connect Automatically...see attached
[ATTACH=CONFIG]272825[/ATTACH]
save your changes...boot and test.
thanks.


Hi&#65292;thanks very much for your time and patience&#65281; I have learnt lot and known how to do next. Thanks a lot for your solution.

I will mark this thread as SOLVED shortly.

---

