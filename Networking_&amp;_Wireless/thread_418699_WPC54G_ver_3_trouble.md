---
title: "WPC54G ver 3 trouble"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by rosalinethemarauder on 2007-04-22
So, I recently commandeered an old laptop from my parents (it used to be mine) and proceeded to install feisty on it. It works like a dream, compiz and beryl work, etc. Wired network works fine. Now, I have a WPC54G ver.3 card that I would like to get working. I looked at the supported cards wiki, and unfortunately, I no longer have the disc that came with the card.  I got the drivers from the linksys website, ndiswrapper shows them as being present and installed. 

clu@flynn:/etc/ndiswrapper/linksys$ ndiswrapper -l
linksys : driver installed
        device (14E4:4318) present (alternate driver: bcm43xx)


when I modprobe the first time, it gives me:

[  113.184000] ndiswrapper version 1.38 loaded (preempt=no,smp=yes)
[  113.224000] usbcore: registered new interface driver ndiswrapper

Then when I go back and look at my dmesg afterword, I see a lot of:

[  918.076000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.


Now, I have no idea what that means. My iwconfig gives me:

clu@flynn:/etc/ndiswrapper/linksys$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:""  Nickname:"Broadcom 4318"
          Mode:Managed  Access Point: Invalid   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Any help would be appreciated. Normally I wouldn't care if the wireless works or not, being as the router is in my room, however, my parents would still like to use this laptop, and I want to try to turn them onto Linux. Thanks in advance

---

