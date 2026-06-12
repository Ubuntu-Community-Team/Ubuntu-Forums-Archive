---
title: "Wireless network frequently freezing"
date: 2016-12-07
forum: Networking &amp; Wireless
---

### Post by v-mark-5 on 2016-12-07
Hello,

I am running Ubuntu 16.04 on a Dell XPS laptop.

I have been using Ubuntu for a couple of months with no issues, but a few days ago I started getting problems with the WiFi. (there were no significant driver or hardware changes I can think of).

I will be connected to a network and then all of a sudden the network will stop working, and I am unable to ping any IP addresses except for my local adapters IP.

The ping doesn't time-out or say network unavailable, it actually does not respond with anything.

Here are the hardware details of my laptop:
[https://gist.github.com/LondonAppDev/9cb52ed8b2a6e26c00946708d8c33a33](https://gist.github.com/LondonAppDev/9cb52ed8b2a6e26c00946708d8c33a33)

Any help would be much appreciated.

---

### Post by darren780 on 2016-12-07
Have you tried restarting your router?  Also test the network with other devices such as cell phones.

---

### Post by wildmanne39 on 2016-12-07
Hi, please click on the wireless script in my signature and follow the directions for running the script and posting the results here. 
Thanks

---

### Post by v-mark-5 on 2016-12-08
Thank you, here is the diagnostic output:

[https://gist.github.com/LondonAppDev/9cb52ed8b2a6e26c00946708d8c33a33](https://gist.github.com/LondonAppDev/9cb52ed8b2a6e26c00946708d8c33a33)

---

### Post by v-mark-5 on 2016-12-08
> **darren780 said:**
> Have you tried restarting your router?  Also test the network with other devices such as cell phones.

Thanks for your reply. In this case I don't have access to the router to reset it as it's at an office.

I tested at home and the wireless seems to work flawlessly...

So this would suggest that the issue is with the network right? However, over 15 people connect to the same network on the same access point and they don't seem to be having the same issue.

I'm wondering if it could be a problem with Ubuntu + this specific access point?

---

### Post by Keith_Helms on 2016-12-08
I sometimes have the same problem on my laptop which also has the Intel 7260 wifi adapter.  It seems to be network specific in my case.  On my home router, it rarely ever happens.  When I'm using my Android tablet as a hotspot, it happens frequently, often every few minutes, which is VERY annoying.

The workaround for me is to just click on the wireless network again in network manager.  That resets/reestablishes the connection and gets it going again.

Before installing Xubuntu 16.04, I used Xubuntu 14.04 on this laptop and never experienced the problem, so it's a bug somewhere in the 16.04 networking.

---

### Post by v-mark-5 on 2016-12-11
Interesting. Yeah it seems to work perfectly for me on my home network also. Seems the issue is a combination of a driver bug and the access point. I wonder if the bug is with the intel drivers or with Ubuntu itself?

---

### Post by jeremy31 on 2016-12-11
It could be the wifi powersave defaulting to on in Ubuntu 16.04, see if this fixes
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

---

### Post by v-mark-5 on 2016-12-11
Thanks Jeremy I will try that. Is there a command I can run to check if powerslave is currently on or not? So I can check before and after I reboot to make sure the command worked?

---

### Post by jeremy31 on 2016-12-11
```
iwconfig
```
Will show if Power Management is enabled or not.

It also looks like your wifi connection at work is using TKIP encryption and that usually causes problems

---

### Post by Keith_Helms on 2016-12-13
I turned off powersave a long time back.  It did resolve another problem where after letting the system sit unused for a while the wireless icon would change to a wired icon and the list of wireless networks would disappear.  It did not fix the random freezes on certain networks.  I've also tried various other suggestions that are frequently mentioned, such as setting the regulatory domain/country code and setting options iwlwifi 11n_disable=8 in /etc/modprobe.d/iwlwifi.conf. 

This does seem to be a bug in the intel driver.  I can plug in an external USB wifi adapter and connect to the same network that gives me problems using the internal adapter and that works with no problems.

---

### Post by v-mark-5 on 2016-12-13
> **jeremy31 said:**
> It could be the wifi powersave defaulting to on in Ubuntu 16.04, see if this fixes
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
Reboot

Hi Jeremy,

I tried what you suggested however when I rebooted my WiFi icon just disappeared completely. I then set powersave back to 3 and rebooted and it came back...

Cheers,
Mark

---

### Post by jeremy31 on 2016-12-13
> **Keith_Helms said:**
> I turned off powersave a long time back.  It did resolve another problem where after letting the system sit unused for a while the wireless icon would change to a wired icon and the list of wireless networks would disappear.  It did not fix the random freezes on certain networks.  I've also tried various other suggestions that are frequently mentioned, such as setting the regulatory domain/country code and setting options iwlwifi 11n_disable=8 in /etc/modprobe.d/iwlwifi.conf. 

This does seem to be a bug in the intel driver.  I can plug in an external USB wifi adapter and connect to the same network that gives me problems using the internal adapter and that works with no problems.

Have you tried setting 11n_disable=1 as it may work better with some networks

---

### Post by Keith_Helms on 2016-12-13
> **jeremy31 said:**
> Have you tried setting 11n_disable=1 as it may work better with some networks

I don't really want to turn off "N" completely.  I mostly have the wifi stops responding problem when I'm travelling and using my Android tablet as a hotspot.  I don't have problems when on my home network.  The bug is just one of those annoyances that I figure will eventually get fixed and go away.

---

