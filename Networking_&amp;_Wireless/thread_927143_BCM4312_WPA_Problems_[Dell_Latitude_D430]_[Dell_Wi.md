---
title: "BCM4312 WPA Problems [Dell Latitude D430] [Dell Wireless 1390]"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by EvilNemesis on 2008-09-22
[FONT=Arial][SIZE=3]The Basics First:

System: Dell Latitude D430
Wireless: Dell Wireless 1390 [BCM4312]
LSPCI = 0c:00.0 Network Controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
OS: Ubuntu 8.04 (Hardy Heron)
Kernel: 2.6.24-19-generic

Problem:
I have been working for the past week, trying to get the internal wireless to work on this system. I didn't have a choice on wireless adapters so I'm stuck troubleshooting the BC4312. This is all being tested on a freshly loaded Ubuntu 8.04 system with the latest updates. After all the updates are installed I reboot and the 'Restricted Drivers' window pops up. From the list I can see 'wl' is enabled and being used. 

If I left-click the network manager it shows me the nearby wireless networks, indicating that the driver is indeed working. I click on my wireless network and it immediately recognizes that we are using WPA Personal, which is correct. I enter the password and click 'Connect'. At this point it just keeps trying to authenticate until it eventually times out. 

I have gone through dozens of threads, blogs, and HowTo's... There are so many "solutions" but I'm not sure which one fixes my problem. I've gone from compiling new broadcom FW to enabling ndiswrapper. None of them have completely solved the issue. From my diagnoses the Network Manager is not accepting WPA correctly. Is there a fix for this? I've searched and read that there is but can't seem to find the solution.

Any help is very much appreciated. I apoligize in advance for adding another thread to an already abundant issue. Thanks in advance!


[/SIZE][/FONT]

---

### Post by roro100 on 2008-09-26
> **EvilNemesis said:**
> [FONT=Arial][SIZE=3]The Basics First:



[/SIZE][/FONT]

I have exactly the same problem. I have dell studio 15 with BCM4312 and Hardy. I have no problem connecting to my router in Vista, or connecting to my neighbours routers (unsecured), but not to my own WPA secured. Strange. I think I will try to install Ubuntu 7.10, which I had before and it worked pretty well for me (but with a SigmaTel card.

---

### Post by willca on 2008-09-26
Give this a try. That gui network manager never worked well in my experience.

sudo apt-get install wpa_supplicant

Edit /etc/wpa_supplicant.conf

Replace the ssid and psk.

ctrl_interface=/var/run/wpa_supplicant
 network={
   ssid="YourWiFiSSID"
   psk="YourWiFiPassword"
   key_mgmt=WPA-PSK
   proto=WPA
   pairwise=TKIP
 }

Then test it.

sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd

If it goes well...then edit /etc/network/interfaces

auto wlan0
iface wlan0 inet dhcp
pre-up wpa_supplicant -Bw -Dwext -iwlan0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

Lastly,

sudo /etc/init.d/networking restart

Check if you are indeed connected.

sudo iwconfig

---

### Post by heykenen on 2008-10-03
I have the same problem, but I don't have problems with my own secured WPA but neighbors unsecured router I can't connect.  I have installed wpasupplicant but I don't have the file called /etc/wpa_supplicant.conf

I've used gusty, Dell D430.

---

### Post by mohtasham1983 on 2008-10-05
I have same exact problem with my dell latitude d630 and broadcom bcm4312 rev (01) wireless card.

I'm able to connect to my work's wireless network which is wpa and university which is open; however, having trouble connecting to my home wpa network. I can see everything, but can't connect to it.

I tried to install wifi-radar, but even using wifi-radar can't connect to the internet :(

---

### Post by mohtasham1983 on 2008-10-15
Today, at work, I noticed a new kernel update available for Hardy. I installed the new update, and hoped it would solve my problem of connecting to the internet at home. Just got back home, turned my laptop on, entered the wpa password, and boom, it connected. 

Thanks to Linus Torvalds and his teams for their great contribution. :)

---

