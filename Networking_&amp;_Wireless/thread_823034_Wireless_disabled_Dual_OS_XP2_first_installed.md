---
title: "Wireless disabled_Dual OS_XP2 first installed"
date: 2008-06-08
forum: Networking &amp; Wireless
---

### Post by taodongwang on 2008-06-08
Hi everyone.I recently installed Ubuntu 8.04 after I first installed xp2. Now the problem is wireless disabled(However my wired network works well,because my network package is well installed). My wireless chip set is Broadcom BCM94311MCG. What I have done is:
FIRST I used the method(almost EXACTLY the same,except my ndiswrapper version is 1.53) in the website below to install ndiswrapper and driver.
[http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/]("http://invaleed.wordpress.com/2007/11/20/install-bcm94311mcg-wlan-mini-pci-ubuntu-710/")
SECOND I useed lshw to look at my wireless network and the result was:*-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1d:d9:35:af:91
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes 
By the way the WiFi light is NOT blue.
So I am not sure the problem is driver installation or something else.
Please.

---

### Post by taodongwang on 2008-06-08
After I typed iwconfig, I got this information:
 iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2346 B   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by pytheas22 on 2008-06-08
What is the output of:
```

iwconfig
ifconfig
iwlist wlan0 scan
```

---

