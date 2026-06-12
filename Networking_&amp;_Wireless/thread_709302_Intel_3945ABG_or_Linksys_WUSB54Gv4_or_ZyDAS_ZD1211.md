---
title: "Intel 3945ABG or Linksys WUSB54Gv4 or ZyDAS ZD1211 as an AP - possible? :/"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by misiekf-pl on 2008-02-27
Hello everyone.

I have got three wireless cards:
wlan0 - Intel 3945ABG, built into my laptop (I tried both ipw3945 and iwl3945 drivers)
wlan1 - Linksys WUSB54g version 4, USB (I use rt2500usb)
wlan2 - some no-name (but probably "CC&C") USB dongle with ZyDAS ZD1211 inside (driver is zd1211rw).

The problem is that I need to settle an AP using any of these cards.. but:
```
root@mfnotebook:~ # iwconfig wlan0 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
root@mfnotebook:~ # iwconfig wlan1 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan1 ; Invalid argument.
root@mfnotebook:~ # iwconfig wlan2 mode master
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan2 ; Invalid argument.
```

I searched the web but I didn't find a solution. I would be grateful for any advice.

lspci (fragment):
```
02:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
```

lsusb (fragment):
```
Bus 005 Device 003: ID 0ace:1215 ZyDAS
Bus 005 Device 002: ID 13b1:000d Linksys
```

iwconfig:
```
wmaster0_rename  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:"xxxx" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: xxxx
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key: xxxx
          Link Quality=56/100  Signal level=-60 dBm  Noise level=-84 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wmaster0  no wireless extensions. [COLOR="Red"]this loads with wlan0 together. what is it?[/COLOR]

wlan1     IEEE 802.11g  ESSID:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

wlan2     IEEE 802.11b/g  ESSID:off/any  Nickname:"zd1211"
          Mode:Managed  Frequency:2.472 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          Encryption key:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

uname -a
```
Linux mfnotebook 2.6.22-14-generic #1 SMP Tue Feb 12 07:42:25 UTC 2008 i686 GNU/Linux

```

---

