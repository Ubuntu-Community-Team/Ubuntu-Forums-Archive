---
title: "Fiesty: Roaming Mode + NetworkManager broken?"
date: 2007-09-13
forum: Networking &amp; Wireless
---

### Post by spyder0080 on 2007-09-13
Hello all,

I have had Ubuntu Fiesty Fawn since this summer. I had a wireless network at home, so I used network-admin to connect to the network by entering the information for my network. However, since I've came to school, I've used roaming mode and NetworkManager to find the network I want to connect to. 

I've never had problems when using network-admin and connecting to the network I specified, but when I used roaming mode and NetworkManager to find and connect to my school's wireless network, I've gotten disconnected many times. Also, the icon would freeze up when trying to connect and then the keyboard wouldn't work. My laptop wouldn't even shut down properly when this happened.

Ever since I went back to using the old way things have gone smoothly. This leads me to believe that either roaming mode or NetworkManager(or both) are broken.

I'm just curious, anyone else having these problems? Will there be another app to handle roaming networks in the next release?

Thanks!

---

### Post by diepruis on 2007-09-14
> **spyder0080 said:**
> Hello all,

I have had Ubuntu Fiesty Fawn since this summer. I had a wireless network at home, so I used network-admin to connect to the network by entering the information for my network. However, since I've came to school, I've used roaming mode and NetworkManager to find the network I want to connect to. 

I've never had problems when using network-admin and connecting to the network I specified, but when I used roaming mode and NetworkManager to find and connect to my school's wireless network, I've gotten disconnected many times. Also, the icon would freeze up when trying to connect and then the keyboard wouldn't work. My laptop wouldn't even shut down properly when this happened.

Ever since I went back to using the old way things have gone smoothly. This leads me to believe that either roaming mode or NetworkManager(or both) are broken.

I'm just curious, anyone else having these problems? Will there be another app to handle roaming networks in the next release?

Thanks!

To my knowledge, some drivers are non-standard and don't support NetworkManager. I know for a fact that the legacy RaLink drivers have this problem. Others might as well.

---

### Post by rocketship on 2007-09-14
Yes!

I've been having the same problem, with my university's wireless network.  I filed a bug, but I don't think anybody's even looked at it.

I wonder if it may have something to do with multiple access points with the same name.  I've been killing NetWorkManager at startup and running ```
sudo NetworkManager --no-daemon
``` 
which will give you debugging feedback.  It looks like it keeps flopping between access points - though I haven't seen a clear sign of what happens when it crashes.

RS

ps - out of curiousity, what school?  I'm at Pratt Institute in New York.  Academic computing is pretty Linux-unfriendly...

---

### Post by rocketship on 2007-10-12
*bump*
I can't imagine that nobody else has run into this problem...?

---

### Post by noob12 on 2007-10-13
If you think there is a bug, you really should file a bug report on launchpad ([https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)) with information about your specific machine configuration and the APs.  It might be an actual bug that is triggered by specific circumstances that are less than common.

---

### Post by DrIdiot on 2007-10-19
> **spyder0080 said:**
> Hello all,

I have had Ubuntu Fiesty Fawn since this summer. I had a wireless network at home, so I used network-admin to connect to the network by entering the information for my network. However, since I've came to school, I've used roaming mode and NetworkManager to find the network I want to connect to. 

I've never had problems when using network-admin and connecting to the network I specified, but when I used roaming mode and NetworkManager to find and connect to my school's wireless network, I've gotten disconnected many times. Also, the icon would freeze up when trying to connect and then the keyboard wouldn't work. My laptop wouldn't even shut down properly when this happened.

Ever since I went back to using the old way things have gone smoothly. This leads me to believe that either roaming mode or NetworkManager(or both) are broken.

I'm just curious, anyone else having these problems? Will there be another app to handle roaming networks in the next release?

Thanks!

Hi,

I've been having a problem where my internet randomly drops if NetworkManager is on roaming mode, and when I try to change between roaming/nonroaming, it will crash (someoen told me that restart dbus will help - however, I have to restart to connect to the network).  I am using a network card that uses a rt61 driver.  Is the driver that is shipped with ubuntu the legacy driver?  Do you have a wireless card you'd recommend for Linux>?

Thanks,
-Harrison

---

### Post by diepruis on 2007-10-20
> **DrIdiot said:**
> Hi,

I've been having a problem where my internet randomly drops if NetworkManager is on roaming mode, and when I try to change between roaming/nonroaming, it will crash (someoen told me that restart dbus will help - however, I have to restart to connect to the network).  I am using a network card that uses a rt61 driver.  Is the driver that is shipped with ubuntu the legacy driver?  Do you have a wireless card you'd recommend for Linux>?

Thanks,
-Harrison

No, the driver Ubuntu ships with is the rt2x00 driver, which is still highly experimental and very beta. However, it shouldn't have problems with network manager.

---

### Post by eckmann on 2007-12-29
I have the exact same problem --- roaming mode with Network Manager on a school wireless network worked only for short periods of time (minutes) and then stopped working.  Also had the problem of keyboard not functioning while Netwrok Manager seemed to be trying to connect to my school's wireless network --- only choice I had then was to hard POWER off my machine --- not good.

I have had roaming in Network Manager on my home network working fine.  It sure sounds like I have the same exact situation as the original poster.  

I am running an Acer Aspire with a Broadcom 4318 Ubuntu Gutsy, not Feisty.

Mike

---

### Post by ugm6hr on 2007-12-29
Network Manager In Feisty was buggy with WPA encrypted networks, and dropped and reconnected every few mintues (particularly with Intel and Atheros chipsets).  Apparently it still is a bit buggy in Gutsy (although I have stuck with it and had no problems).

If this is a problem - try Wicd instead of NM: [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

---

### Post by s3raphim on 2008-02-11
EVERYONE has this problem.  There is, in fact, a bur report.  My co-worker and I have the problem on our Broadcom cards - one Dell on HP.

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/129908](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/129908)

It comes from having many access points with the same SSID.  I think if you specify manually and encrypted network's SSID with a specific channel, it should work (I will test it tomorrow).  Then Network Manager will remember this as a preferred network for your location.  The caveat is, I don't know what will happen if you then walk around the building from access point to access point ....  My building has 60-some points.

Let me know if it works better....

---

