---
title: "Ralink 5370 USB dongle not connecting, Ubuntu 14.04 Trusty"
date: 2014-12-04
forum: Networking &amp; Wireless
---

### Post by koplette on 2014-12-04
Hi,

I have the following problem with my external USB dongle: it gets recognized, the drivers are loaded, but **it can see no wireless networks** (the built-in wireless card can).
The card is always displayed as **disconnected** by **nm-cli**.

```

$ lsusb
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 011: ID 148f:5370 Ralink Technology, Corp. RT5370 Wireless Adapter
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 003: ID 0483:2016 STMicroelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

```

$ lsmod | grep rt2
rt2800usb              27034  0 
rt2x00usb              20742  1 rt2800usb
rt2800lib              89076  1 rt2800usb
rt2x00lib              55307  3 rt2x00usb,rt2800lib,rt2800usb
crc_ccitt              12707  1 rt2800lib
mac80211              626557  5 iwl4965,iwlegacy,rt2x00lib,rt2x00usb,rt2800lib
cfg80211              484040  4 iwl4965,iwlegacy,mac80211,rt2x00lib

```

```

$iwconfig
wlan1     IEEE 802.11bgn  ESSID:off/any  
             Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
             Retry  long limit:7   RTS thr:off   Fragment thr:off
             Power Management:off

```

```

$ nm-tool
- Device: wlan1 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            rt2800usb
  State:             disconnected
  Default:           no
  HW Address:        00:0F:54:0D:AE:26

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 

```

What should I do? Should I load different drivers? Is the dongle broken?

Thanks.

---

### Post by chili555 on 2014-12-04
Why is iwl4965 loaded? Do you have an internal wireless? What is wrong with it?

---

### Post by koplette on 2014-12-05
Yes, as briefly mentioned above, I have an internal wireless card, I have edited the output of the above commands to only show the problematic card.

I'm trying to use an external card with a large antenna to increase bandwidth.

---

### Post by chili555 on 2014-12-05
I recommend, as a start, that you blacklist the driver for the internal card so the driver suites don't conflict:```
sudo -i
echo "blacklist iwl4965"  >>  /etc/modprobe.d/blacklist.conf
modprobe -r iwl4965
exit
```Any improvement? If not, please let us see:```
nm-tool
dmesg | grep rt2
```Thanks.

---

### Post by koplette on 2014-12-30
Thank you for the help, but in the end it turned out that the dongle was probably broken.

---

