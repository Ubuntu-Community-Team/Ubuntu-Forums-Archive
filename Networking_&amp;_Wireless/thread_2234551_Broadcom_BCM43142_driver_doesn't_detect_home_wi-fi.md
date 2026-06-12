---
title: "Broadcom BCM43142 driver doesn't detect home wi-fi, detects neighbours"
date: 2014-07-15
forum: Networking &amp; Wireless
---

### Post by roho2 on 2014-07-15
Request your help to resolve issues with my wireless connection. 


I'm using a dell vostro 2520 with Ubuntu 12.04 and the following wireless driver:


Broadcom Corporation BCM43142 802.11b/g/n [14e4:4365] (rev 01)


The issue is, my laptop recognizes my home wi-fi sometimes, but more often than not, it doesn't. For example, it connected automatically on boot-up the last 2 days, today, it doesn't even show up on the list of available connections.


It's showing me the wireless connections of all my neighbours though.


BTW, my brothers laptop, running a windows detects the wireless so I know it's not the router to blame.

I'm new to Ubuntu, a complete non-techie. I have gone through multiple threads on multiple forums. Tried all possible commands, installing kernels, purging kernels etc but nothing's worked. 


Request you to help me with this.

---

### Post by grahammechanical on 2014-07-15
If the WiFi adapter is detecting wireless access points in range, then Ubuntu is doing what it is supposed to do. There is a driver for the WiFi adapter and it is working and Network manager is listing available networks/wireless access points.

If Network Manager sometimes automatically makes a connection. Then Network Manager is doing it job. Thinking logically there can only be a small number of reasons for this problem.

1) the router/wireless access point is switched off
2) the router is out of range
3) WiFi or Networking is disabled in Ubuntu.
4) the signal strength is low and is being blocked by stronger WiFi signals
5) another WiFi access point is using the same channel as your router.

Run

```
nm-tool
```

That may provide some information that may help. Especially if you actually have a wireless connection when you run the command. When I run nm-tool I see that there are 8 access points in range and that my router and Wifi adapter are communicating on a frequency of 2462 MHz. There are two other access points using the same frequency but their signal strength is less than the signal strength of my connection. Besides, they are also password protected. So, Network Manager has no problem taking the easy way out and making the connection it is instructed to do.

Regards.

---

### Post by chili555 on 2014-07-15
That device, 14e4:4365, is one of the trickiest devices to get going in 12.04 and on older kernel versions. How did you get it working?Just the 'Additional Drivers' tool? What is your kernel version?```
uname -r
sudo dpkg -s bcmwl-kernel-source | grep Version
```The pipe symbol | is on the right side of my US keyboard on the same key with \. Thanks.

---

### Post by roho2 on 2014-07-16
> **chili555 said:**
> How did you get it working?Just the 'Additional Drivers' tool? What is your kernel version?


Yes, just used the additional drivers tool till now. 
Here are the results;

uname -r
3.2.0-65-generic


sudo dpkg -s bcmwl-kernel-source | grep Version
Version: 6.20.155.1+bdcom-0ubuntu0.0.2

---

### Post by roho2 on 2014-07-16
> **grahammechanical said:**
> If the WiFi adapter is detecting wireless access points in range, then Ubuntu is doing what it is supposed to do. There is a driver for the WiFi adapter and it is working and Network manager is listing available networks/wireless access points.

If Network Manager sometimes automatically makes a connection. Then Network Manager is doing it job. Thinking logically there can only be a small number of reasons for this problem.

1) the router/wireless access point is switched off
2) the router is out of range
3) WiFi or Networking is disabled in Ubuntu.
4) the signal strength is low and is being blocked by stronger WiFi signals
5) another WiFi access point is using the same channel as your router.

Run

```
nm-tool
```

Thanks a lot for replying. Yes logically speaking Ubuntu and the network manager are doing their job. That's why I suspected that my router is source of the problem. But other devices in my house, tabs and smartphones running android, another laptop running windows detect the same router and can also connect. That's what got me confused.

Also I have tried connecting while sitting right next to the router, so don't think there should be any issue with range. Not sure about the frequency and strength though. I can find out only when I connect to the wi-fi next time I guess.

---

