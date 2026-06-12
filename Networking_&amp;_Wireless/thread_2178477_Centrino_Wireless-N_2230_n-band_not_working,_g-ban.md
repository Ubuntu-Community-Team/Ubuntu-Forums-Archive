---
title: "Centrino Wireless-N 2230: n-band not working, g-band crippled with n on"
date: 2013-10-03
forum: Networking &amp; Wireless
---

### Post by kc600 on 2013-10-03
1) My office has an 802.11n network available but it doesn't show up in the network manager. [edit]This is true for other networks, the card doesn't detect any N-band network.[/edit]
2) With N-band enabled, i see a lot of "Tx excessive retries" on the wlan0 (which can only use 802.11g). When i disable N-band functionality, this is fixed and i get a lot more kB/s from it. [edit]So the 802.11g seems to be a bit crippled with n-band enabled, but only then.[/edit]

I've found these threads which look related, but they don't describe my problem exactly. Still i'll follow up on them a little:

a) [http://askubuntu.com/questions/174472/how-to-get-intel-centrino-wireless-n-2230-to-work-on-11-10](http://askubuntu.com/questions/174472/how-to-get-intel-centrino-wireless-n-2230-to-work-on-11-10) 
This is about wlan0 not working at all, which is not the case.

b) [http://askubuntu.com/questions/304838/wifi-problems-with-intel-centrino-wireless-n-2230-on-ubuntu-12-04](http://askubuntu.com/questions/304838/wifi-problems-with-intel-centrino-wireless-n-2230-on-ubuntu-12-04)
This is not a well-defined problem, and there is no good answer. One comment says: "No proprietary drivers found when I go to additional drivers", this is also the case with me.

c) [http://ubuntuforums.org/showthread.php?t=2089512](http://ubuntuforums.org/showthread.php?t=2089512)
This is also about a coard that won't work at all, whereas mine works fine but just for G-band. The file /lib/firmware/iwlwifi-2030-6.ucode is present on my system.

I attach output from lspci and iwconfig. I currently have N-band disabled explicitly in /etc/modprobe.d/iwlwifi.conf, which is also attached.

This is on Ubuntu 13.04, on a Lenovo ThinkPad S430. 

Any hints on how to debug/fix this?

---

### Post by kc600 on 2013-10-04
Update: This thread [https://bbs.archlinux.org/viewtopic.php?id=163475](https://bbs.archlinux.org/viewtopic.php?id=163475) is for another card (Centrino Advanced-N 6230) but seems to have the same issues. They reference this kernel bug: [https://bugzilla.kernel.org/show_bug.cgi?id=58591](https://bugzilla.kernel.org/show_bug.cgi?id=58591)

---

### Post by kc600 on 2013-10-08
Filed this as [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1237051](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1237051)

---

### Post by mörgæs on 2013-10-09
Thanks for the bug report. However, it will carry more impact if you can confirm the bug in 13.10, as 13.04 has only a few months left anyway.
Have you tried 13.10 to see how it works?

---

### Post by kc600 on 2013-10-15
I did, on 2013-10-11 (so after your reply): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1237051/comments/4](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1237051/comments/4)

---

### Post by mörgæs on 2013-10-22
When the 14.04 development gets up to speed it's a good idea to discuss with the people in the [U+1]("http://ubuntuforums.org/forumdisplay.php?f=427") forum in order to get the bug fixed. I can move your thread if you want to.

---

### Post by chili555 on 2013-10-22
I assume we are discussing the driver iwlwifi and not necessarily the specific card. The card's capabilities are enabled in the Intel provided firmware. From *modinfo iwlwifi*:> chili@Think410:~$ modinfo iwlwifi
filename:       /lib/modules/3.11.0-12-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
license:        GPL
author:         Copyright(c) 2003-2013 Intel Corporation <ilw@linux.intel.com>
version:        in-tree:
description:    Intel(R) Wireless WiFi driver for Linux
firmware:       iwlwifi-100-5.ucode
firmware:       iwlwifi-1000-5.ucode
firmware:       iwlwifi-135-6.ucode
firmware:       iwlwifi-105-6.ucode
firmware:       iwlwifi-2030-6.ucode
firmware:       iwlwifi-2000-6.ucode
firmware:       iwlwifi-5150-2.ucode
firmware:       iwlwifi-5000-5.ucode
firmware:       iwlwifi-6000g2b-6.ucode
firmware:       iwlwifi-6000g2a-5.ucode
firmware:       iwlwifi-6050-5.ucode
firmware:       iwlwifi-6000-4.ucode
firmware:       iwlwifi-3160-7.ucode
firmware:       iwlwifi-7260-7.ucode
<snip>In my own experience, the bug still exixts in 13.10. Here, for example, is my *iwconfig*:```
wlan0     IEEE 802.11abgn  ESSID:"GBR1"  
          Mode:Managed  Frequency:5.745 GHz  Access Point: xx:D7:19:41:54:xx   
          Bit Rate=81 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=51/70  Signal level=-59 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:591  Invalid misc:105   Missed beacon:0
```As you can see, I am connected at N speeds and I have lots of excessive retries. As well, the link quality, aka signal strength is 51/70. If I turn off N in the router, it is more likely to be 65/70.> the card doesn't detect any N-band networkI think the card detects it, but Network Manager doesn't show it. Here is my redacted scan:> $ sudo iwlist wlan0 scan
[sudo] password for chili: 
wlan0     Scan completed :
          Cell 01 - Address: xx:D7:19:41:54:xx
                    [COLOR="#FF0000"]Channel:149
                    Frequency:5.745 GHz (Channel 149)
                    Quality=49/70  Signal level=-61 dBm  
                    Encryption key:on
                    ESSID:"GBR1"[/COLOR]
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master                    
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    
          Cell 02 - Address: xx:D7:19:41:54:xx
                    [COLOR="#FF0000"]Channel:5
                    Frequency:2.432 GHz (Channel 5)
                    Quality=63/70  Signal level=-47 dBm  
                    Encryption key:on
                    ESSID:"GBR1"[/COLOR]
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                        IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK Having said all that, do i know the solution? No. My objective here is simply to add data to the discussion.

I am suspicious that there is some finger pointing going on here between Intel and the router manufacturers about who is implementing N correctly and who is not. I must admit that some routers connect at N speeds to Intel cards with ease, excepting excessive retries. Other routers will not. Ever.

---

