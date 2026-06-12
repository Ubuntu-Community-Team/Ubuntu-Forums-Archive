---
title: "ASUS M2N32-SLI Deluxe WiFi On Linux"
date: 2007-04-17
forum: Networking &amp; Wireless
---

### Post by cactusbin on 2007-04-17
I've been using linux for a while on my old machines, and I love it. But when I got my new computer (custom) Linux didn't seem to love my new hardware. Right now I have wireless built into my motherboard: [http://www.newegg.com/Product/Product.asp?item=N82E16813131011](http://www.newegg.com/Product/Product.asp?item=N82E16813131011) . Realtek released linux drivers for their products and I compiled them. In the network manager it can detect my wireless network and supposedly conenct to it, but when i run 'iwconfig wlan0' it only has the correct essid and it is on channel 12 (is really on channel 6) and has no mac address, I manually connect to the mac address using iwconfig it still doesn't work! (I'm not using any encryption or mac filtering btw)

---

### Post by devkelso on 2007-04-17
scuttle the downloaded driver you compiled.  This applies to anyone useing a Linksys wpc11 v4 (version 4) wireless card.  Feisty already comes with the right driver.  No need to use ndiswrapper or an old driver that was last synced with the kernel over two years ago.
```
sudo modprobe r818x
```This driver is said to be flakey with RaLink chipsets but my Realtek 8180 works hunky dory.

---

### Post by cactusbin on 2007-04-17
thanks man, for trying to help me. I removed the drivers from the blacklist, restarted, and modprobed it. Still didn't associate with the ap. In the system log it showed that for 11 minutes straight it was trying to connect to purpl (my essid) (or something similar to that). The ap works perfectly fine on my friend's mac and my other friend's linux laptop (ubuntu as well). It also works with my laptop and my windows partition. My ap is a WRT54G with 'Firmware: DD-WRT v23 (12/25/05)'. Please help. (btw it is 8187 chipset version thing) (btw again i got an official CD from ShipIt 'Version 6.06 LTS for your PC')

Thanks,
DJ

---

### Post by dbott67 on 2007-04-17
Also, check this thread here about some wireless Realtek issues and a workaround.

[http://ubuntuforums.org/showthread.php?p=2444014#post2444014](http://ubuntuforums.org/showthread.php?p=2444014#post2444014)

-Dave

---

### Post by chili555 on 2007-04-17
Saw you on IRC. Can I please see sudo iwlist wlan0 scan? Might take 2-3 tries.

---

### Post by cactusbin on 2007-04-17
I'm not using fiesta though... But I did try adding an 'x' (dummy char.) to the end of the essid in my interfaces file, and it thought that my essid was 'purplx' so I changed it back.

---

### Post by cactusbin on 2007-04-17
cactusbin@cactusbin-desktop:~$ sudo iwlist wlan0 scan
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39: D0:48:2D
                    ESSID:"purpl"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key: off
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality:15  Signal level:0  Noise level:16
                    Extra: Last beacon: 5ms ago


(I just noticed the signal level was 0...) (It's IRC btw :) )

---

### Post by chili555 on 2007-04-17
Yeah, IRC, I edited.

Please try:```
sudo iwconfig wlan0 essid purpl
sudo iwconfig wlan0 ap 00:18:39:D0:48:2D
sudo dhclient wlan0
```Let me know.

---

### Post by cactusbin on 2007-04-17
I already tried all that, but I will try it again and post exactly what I get. "I manually connect to the mac address using iwconfig it still doesn't work!"

---

### Post by cactusbin on 2007-04-17
cactusbin@cactusbin-desktop:~$ sudo iwconfig wlan0 essid purpl
cactusbin@cactusbin-desktop:~$ sudo iwconfig wlan0 ap 00:18:39: D0:48:2D
cactusbin@cactusbin-desktop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

Listening on LPF/wlan0/00:15:af:08:57:15
Sending on   LPF/wlan0/00:15:af:08:57:15
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
cactusbin@cactusbin-desktop:~$ iwconfig wlan0
wlan0     802.11b/g link..  ESSID:"purpl"
          Mode:Managed  Channel=6 Access Point: 00:18:39: D0:48:2D
          Bit Rate=11 Mb/s (<---???)
          Retry: on   Fragment thr: off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

cactusbin@cactusbin-desktop:~$

---

### Post by cactusbin on 2007-04-17
Please help? (bump)

---

### Post by chili555 on 2007-04-18
Well, in the kernel, there are two r818* modules, r8187 and r818x. I'd be interested to know which module is loaded versus which is needed. May I please see:```
sudo lshw -C network
lsmod | grep 818
cat /etc/modprobe.d/blacklist
```

Perhaps we need r8187 and we have loaded r818x. There is a difference: ```
$ diff -u /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rtl818x/r818x.ko /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rtl8187/r8187.ko
Binary files /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rtl818x/r818x.ko and /lib/modules/2.6.17-11-generic/kernel/drivers/net/wireless/rtl8187/r8187.ko **differ**
```

---

### Post by cactusbin on 2007-04-18
cactusbin@cactusbin-desktop:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:15:af:08:57:15
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=192.168.1.140 multicast=yes wireless=802.11b/g link..
cactusbin@cactusbin-desktop:~$ lsmod | grep 818
r8187                  41860  0
ieee80211_rtl          83464  1 r8187
usbcore               130692  8 usb_storage,r8187,usbhid,usblp,uhci_hcd,ehci_hcd,ohci_hcd
cactusbin@cactusbin-desktop:~$ cat /etc/modprobe.d/blacklist
# This file lists those modules which we don't want to be loaded by
# alias expansion, usually so some other driver will be loaded for the
# device instead.

# evbug is a debug tool that should be loaded explicitly
blacklist evbug

# these drivers are very simple, the HID drivers are usually preferred
blacklist usbmouse
blacklist usbkbd

# replaced by e100
blacklist eepro100

# replaced by tulip
blacklist de4x5

# causes no end of confusion by creating unexpected network interfaces
blacklist eth1394

# snd_intel8x0m can interfere with snd_intel8x0, doesn't seem to support much
# hardware on its own (Ubuntu bug #2011, #6810)
blacklist snd_intel8x0m

# causes failure to suspend on HP compaq nc6000 (Ubuntu: #10306)
blacklist i2c_i801
cactusbin@cactusbin-desktop:~$

---

### Post by chili555 on 2007-04-19
Doesn't look like the news is better in Feisty. Here is part of the default blacklist file:```
# buggy driver causes kernel BUG on load (Ubuntu: #78255, #88430)
blacklist r818x
blacklist r8187
```However, if you study the bug reports, quite a few people report the workaround of adding an extra character to the ESSID works! If you decide to try Feisty, try this technique after you un-blacklist r8187.

---

### Post by bluefightingcat on 2007-11-19
Hi,

Has anybody looked into the sound system of this board. The sound works automatically but I am not entirely sure that the "surround sound" works. I have 5.1 surround connected to my board. 

Does anybody have any experience with this?

BFC

---

### Post by bluefightingcat on 2007-11-20
Hi,

I found the solution to my problem. I just had to turn on the correct settings in the sound mixer! :oops:

BFC

---

