---
title: "can't connect to wireless network"
date: 2009-03-02
forum: New to Ubuntu
---

### Post by Rumtscho on 2009-03-02
I started using Linux two days ago. With some effort, I sucessfully installed the driver for my wireless dongle. I got a working Internet connection, which fell apart after 10 minutes and I couldn't bring it back to working state. I reinstalled the driver, and again I had a working connection for a very short time, now I cannot connect again. 

The Connection Icon in my panel says "no network connection" and right-clicking doesn't offer a network to connect to. Running iwconfig gives following information: 

```

ra0     RT2870 Wireless ESSID="11n-AP" Nickname:"RT2870STA"
        Mode:Auto Frequency=2.412 GHz Access-Point: Not-Associated
        Bit Rate: 1 Mb/s
        RTS thr:off    Fragment thr:off
        Link Quality=100/100 Signal level:0 dBm Noise level:-97 dBm
        Rx invalid nwid:0  Rx invalid crypt:0 Rx invalid frag:0 
        TX excessive retries:0  Invalid misc:0 Missed beacon:0 

```

I don't know if this is a driver problem (by the way, I used the native drivers provided by the chipset's producer Ralink). If the driver doesn't function, why was I able to make a working connection directly after install? and besides, a Wiki I used for starting with Ubuntu suggests that there wouldn't be an entry under ESSID if the driver didn't work. They have some examples of iwconfig outputs and say that one like mine, with "Access-Point:Not-Associated" means there isn't a wireless modem working nearby. But my modem works 100%, I tried downloading something on my boyfriend's PC that's connected to the same modem (Windows XP), and there were no troubles with that download while Linux stubbornly insisted that there is no wireless network nearby. I tried pulling the dongle out and sticking it again, I tried restarting the modem, but it didn't help. 

My modem can only use WPA encryption, there is no way to switch to another encryption method or an unsecured network. I've found some pages on the Internet where people complain about Linux having trouble with WPA, but no solutions so far. Could that be the source of my trouble? Why should encryption have an influence on whether a network is detected at all? 

Perhaps you've got an idea what I am doing wrong? 

P.S. I have installed Ubuntu 8.10 and done no changes to it except for installing the wireless driver.

My handheld detects 3 different access points nearby (2 must be my neighbour's modems).

---

### Post by Rumtscho on 2009-03-02
All right, I found out it was the wpa after all. It seems the Network manager just can't handle it, so a manual configuration for the wpa_supplicant is needed. 

Problem solved, anyway.

---

