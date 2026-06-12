---
title: "Wireless only works if I boot LIVE off USB. 12.04.3 LTS"
date: 2013-11-12
forum: Networking &amp; Wireless
---

### Post by gre.crss on 2013-11-12
If I try to activate Broadcom driver, it fails and suddenly appears that I have no wireless card at all. (or something).  Wireless also stops working if I boot the OS from the hard disc.  Currently booted from a USB.  HP-Compaq-mini-CQ-10.

---

### Post by chili555 on 2013-11-12
It seems obvious that you *shouldn't* activate the Broadcom driver as it's wrong for your particular device. Let's check:```
lspci -nn -d 14e4:
```

---

### Post by gre.crss on 2013-11-12
01:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)

---

### Post by chili555 on 2013-11-12
A very tricky device to get going! Let's see what's installed now:```
lsmod | grep -e wl -e brcm
```Whatever is installed, we are going the opposite!

---

### Post by gre.crss on 2013-11-12
brcmsmac              534541  0 
mac80211              541819  1 brcmsmac
brcmutil               14355  1 brcmsmac
cfg80211              453853  2 brcmsmac,mac80211
cordic                 12518  1 brcmsmac
bcma                   39810  1 brcmsmac

---

### Post by chili555 on 2013-11-12
That's actually the driver I would have suggested! Let's troubleshoot a bit:```
rfkill list all
dmesg | grep -e brcm -e wlan
sudo iwlist wlan0 scan
```

---

### Post by gre.crss on 2013-11-12
ubuntu@ubuntu:~$ rfkill list all
0: hp-wifi: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: hp-wwan: Wireless WAN
    Soft blocked: no
    Hard blocked: no
2: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
ubuntu@ubuntu:~$ dmesg | grep -e brcm -e wlan
[   41.778633] brcmsmac bcma0:0: mfg 4bf core 812 rev 24 class 0 irq 16
[   42.298756] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[   42.298786] brcmsmac bcma0:0: brcms_ops_config: change power-save mode: false (implement)
[   42.300717] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   42.302259] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[  159.945081] wlan0: authenticate with 00:21:55:b3:8b:00
[  159.945291] wlan0: send auth to 00:21:55:b3:8b:00 (try 1/3)
[  159.947158] wlan0: authenticated
[  159.952080] wlan0: associate with 00:21:55:b3:8b:00 (try 1/3)
[  159.954562] wlan0: RX AssocResp from 00:21:55:b3:8b:00 (capab=0x401 status=0 aid=173)
[  159.955772] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[  159.955790] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 0 (implement)
[  159.955800] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[  159.955836] wlan0: associated
[  159.955905] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  161.073461] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2266.032223] wlan0: deauthenticated from 00:21:55:b3:8b:00 (Reason: 2)
[ 2266.040267] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: disassociated
[ 2266.040288] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled false, count 1 (implement)
[ 2266.040299] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: false (implement)
[ 2267.006307] wlan0: authenticate with 00:21:55:b3:8b:00
[ 2267.006588] wlan0: send auth to 00:21:55:b3:8b:00 (try 1/3)
[ 2267.012249] wlan0: authenticated
[ 2267.016618] wlan0: associate with 00:21:55:b3:8b:00 (try 1/3)
[ 2267.019257] wlan0: RX AssocResp from 00:21:55:b3:8b:00 (capab=0x401 status=0 aid=205)
[ 2267.020990] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
[ 2267.021004] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
[ 2267.021011] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
[ 2267.021037] wlan0: associated

---

### Post by chili555 on 2013-11-12
> [ 2267.012249] wlan0: authenticated
 [ 2267.016618] wlan0: associate with 00:21:55:b3:8b:00 (try 1/3)
 [ 2267.019257] wlan0: RX AssocResp from 00:21:55:b3:8b:00 (capab=0x401 status=0 aid=205)
 [ 2267.020990] brcmsmac bcma0:0: brcmsmac: brcms_ops_bss_info_changed: associated
 [ 2267.021004] brcmsmac bcma0:0: brcms_ops_bss_info_changed: arp filtering: enabled true, count 1 (implement)
 [ 2267.021011] brcmsmac bcma0:0: brcms_ops_bss_info_changed: qos enabled: true (implement)
 [ 2267.021037] wlan0: associated Looks like you are connected to me. No??

---

### Post by praseodym on 2013-11-12
Did you install the package **linux-firmware-nonfree**?

---

### Post by gre.crss on 2013-11-12
I am connected, yes.  But only if I boot fron USB.  Hence, confusion.  As soon as I try to install I lose wireless capabilities.  I wish that I had another conputer to talk while I troubleshoot, but I only have this one.

---

### Post by gre.crss on 2013-11-12
Also, thank you for helping.  I'**m** new to Linux, if you couldn't tell.

---

### Post by gre.crss on 2013-11-12
where do I find? and what is it?

---

### Post by chili555 on 2013-11-12
It's not going to help us very much to troubleshoot the working setup, because there is no trouble to shoot! Please boot into your not-working harddrive install and open a terminal and do:```
sudo apt-get remove --purge bcmwl-kernel-source
sudo modprobe -r wl
sudo modprobe brcmsmac
```Jot down any errors or warnings only and come back here and post them.

---

