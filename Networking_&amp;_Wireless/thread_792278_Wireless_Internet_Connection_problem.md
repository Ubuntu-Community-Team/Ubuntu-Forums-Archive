---
title: "Wireless Internet Connection problem"
date: 2008-05-12
forum: Networking &amp; Wireless
---

### Post by Chacon-66 on 2008-05-12
Let me state this early I am very new to Linux, first installed it 3 days ago.

I have been busting my brains for a total of 24 hours not including sleep nonstop trying to find a solution to my PCI Adapter problem. I have looked through google intensively and tried all how-to's that I could find and I cannot find a solution.

I have installed Ubuntu 8.04 on my old Gateway desktop which is pentium 3 and has 512mb of Ram. It does not have a Ethernet Adapter so a while back my dad bought a Linksys Wireless - G PCI Adapter with Speedbooster and it worked fine on Windows ME. So right now the computer running Ubuntu has no internet connectivity at all, not even dial up. Once I installed Ubuntu there was no going back to Windows ME because I cannot find the OS CD.

I am looking for a how-to that does not include any connectivity with the internet. I can download stuff on this PC(windows XP) and do have a USB to transfer files to my other computer running ubuntu.

When I type in lspci in the terminal this shows up =
"Broadcom corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller" so I guess it does know it is there. Also if any use to know I am using a WRT54GS Wireless-G Broadband Router.

---

### Post by superprash2003 on 2008-05-12
could you go to the terminal and type iwconfig and post output here

---

### Post by Chacon-66 on 2008-05-12
Yes the output of iwconfig are =

lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11g  ESSID:""
          Mode:Managed  Channel:0  Access Point: Not-Associated
          Tx-Power=0  dBm
          Retry min limit:7   RTS thr:off   Fragment thr=2346  B
          Link Quality:0  Signal Level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0  Missed beacon:0



(Sorry if something is misspelled, I cannot Copy/Paste)

---

### Post by Chacon-66 on 2008-05-12
Need help please

---

### Post by Ayuthia on 2008-05-13
> **Chacon-66 said:**
> Let me state this early I am very new to Linux, first installed it 3 days ago.

I have been busting my brains for a total of 24 hours not including sleep nonstop trying to find a solution to my PCI Adapter problem. I have looked through google intensively and tried all how-to's that I could find and I cannot find a solution.

I have installed Ubuntu 8.04 on my old Gateway desktop which is pentium 3 and has 512mb of Ram. It does not have a Ethernet Adapter so a while back my dad bought a Linksys Wireless - G PCI Adapter with Speedbooster and it worked fine on Windows ME. So right now the computer running Ubuntu has no internet connectivity at all, not even dial up. Once I installed Ubuntu there was no going back to Windows ME because I cannot find the OS CD.

I am looking for a how-to that does not include any connectivity with the internet. I can download stuff on this PC(windows XP) and do have a USB to transfer files to my other computer running ubuntu.

When I type in lspci in the terminal this shows up =
"Broadcom corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller" so I guess it does know it is there. Also if any use to know I am using a WRT54GS Wireless-G Broadband Router.

I am not sure about which version of the 4318 you have (you can check by typing lspci -nn at the Terminal), but it looks like the best bet is to try NDISwrapper.  You can install NDISwrapper from the liveCD.  Just install ndiswrapper-common and ndiswrapper-utils-1.9.  Here is a guide that can help: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Chacon-66 on 2008-05-13
Ok so I installed NDISwrapper, and now the computer recognizes the Driver but every time I go to System > Administration > Hardware Drivers I find "Broadcom B43 wireless driver" and every time I try to click on the enable box my computer crashes and I have to turn it off by pressing its power button. What should I do?

---

### Post by Ayuthia on 2008-05-13
> **Chacon-66 said:**
> Ok so I installed NDISwrapper, and now the computer recognizes the Driver but every time I go to System > Administration > Hardware Drivers I find "Broadcom B43 wireless driver" and every time I try to click on the enable box my computer crashes and I have to turn it off by pressing its power button. What should I do?You don't want to enable the driver if you are using NDISwrapper.  The Hardware Drivers will try to load the native linux Broadcom driver and that will create conflicts with NDISwrapper.

I am not for sure about where you are in the ndiswrapper isntall.  Does ndiswrapper -l show the device (14e4:4318) present statement?  If so, have you done:
```
sudo modprobe -r b43 ssb
sudo modprobe ndiswrapper
```

---

### Post by Chacon-66 on 2008-05-14
When I type in sudo ndiswrapper -l it shows "bcmwl5 : driver installed" but nothing else. What do I do to get the device to show up?

---

### Post by Ayuthia on 2008-05-14
> **Chacon-66 said:**
> When I type in sudo ndiswrapper -l it shows "bcmwl5 : driver installed" but nothing else. What do I do to get the device to show up?You need to try another driver until it say device (14e4:43XX) present.  You might try another driver in the No-Fluff list.

---

### Post by Chacon-66 on 2008-05-14
Where can I find the No-Fluff list?

---

### Post by Chacon-66 on 2008-05-14
Help please.

---

### Post by Ayuthia on 2008-05-14
> **Chacon-66 said:**
> Where can I find the No-Fluff list?

Sorry, the link was in post #5.  Here it is again: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by Chacon-66 on 2008-05-15
So I followed directions and I started to do 2a but problem is I don't have cabextract, where can I get it?

and also when I try to follow his guide to adding the Universe and Multiverse Repositories I end up not being able to find "Software Properties" under System > Administration.

---

### Post by Ayuthia on 2008-05-15
> **Chacon-66 said:**
> So I followed directions and I started to do 2a but problem is I don't have cabextract, where can I get it?

and also when I try to follow his guide to adding the Universe and Multiverse Repositories I end up not being able to find "Software Properties" under System > Administration.

Here is the [link]("http://packages.ubuntu.com/hardy/utils/cabextract").  You will need to pick either the i386 version (32-bit) or the amd64(64-bit) version.  Once you have it in Ubuntu, go to the directory on where it is located and click on the icon.  Or you can do in the terminal:
32-bit:
```
sudo dpkg -i cabextract_1.2-2_i386.deb 
```

64-bit:
```
sudo dpkg -i cabextract_1.2-2_amd64.deb
```

---

