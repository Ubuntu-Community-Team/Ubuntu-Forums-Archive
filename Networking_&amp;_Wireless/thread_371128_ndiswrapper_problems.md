---
title: "ndiswrapper problems"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by -wake- on 2007-02-26
Hi,

I'm new to ubuntu so if anybody can help me please give detailed solutions.

The wired network is up and running without problems, so I thought I'd try to setup the wireless connection. I have a broadcom bcm4306 device and followed this guide: 

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Windows_Wireless_Drivers_.28Ndiswrapper.29)

I then installed the wifi-radar and even got the connection working! Jeee.. but then I noticed some other problems. The normal wired connection began to behave very strangely (I disconnected from the wireless network, so only wired was connected). It only receives a few packets at a time and rapidly changes between idle and receiving. Only web page I was able to connect to was google and make searches, but could not open any link, just got "unavailable to connect to"... This has something to do with that google loads so quickly, and searches are fast too. No other web page was loading fast enough to pass through my crazy on-off network connection... huh, what is going on here...? :confused: 

I then uninstalled ndiswrapper and wifi-radar from syn. packet man. and the connection works without problems. Everytime I install ndiswrapper as described above the same thing happens. What should I do, I'd need to have both network connections working??

Any help is appreciated, thanks. :)

---

### Post by Metaljaz on 2007-02-27
Try this wiki. Pick the version of Ubuntu that you are using.

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

