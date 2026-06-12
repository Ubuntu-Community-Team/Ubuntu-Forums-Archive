---
title: "Newbie: WPA-PSK TKIP not working, unencrypted working"
date: 2008-04-28
forum: Networking &amp; Wireless
---

### Post by lagu2653 on 2008-04-28
I installed the Hardy Heron 8.04 on saturday. I've got WLAN without encryption working. How do you get WPA-PSK TKIP working? In Administration > Network I can only choose WPA Personal and WPA2 Personal. Where is the TKIP option? Please state the entire path from a desktop menu so there is no confusion about where to start.

/Lars

---

### Post by epee on 2008-04-28
Eh, I think you need to do a LOT more searching in the wireless forum posts here - there is a heap of info on these topics. Mind you, you'll have to sift through the various bits of advice to discard the useless, ignore the irrelevant and home in on the tidbit that will solve **your** problem(s).

For example, check [this]("http://ubuntuforums.org/showthread.php?t=318539") out.

Anyway, in due course, the following *may* be of some use.

In the [FONT="Courier New"]file /etc/network/interfaces[/FONT] I have:

```
auto wlan0
iface wlan0 inet dhcp
        pre-up ifconfig wlan0 down
        pre-up dhclient -r wlan0
        pre-up ifconfig wlan0 up
        pre-up iwconfig wlan0 essid "xxxxxxxxxx"
        pre-up iwconfig wlan0 mode managed
        pre-up iwpriv wlan0 set SSID="xxxxxxxxxx"
        pre-up iwpriv wlan0 set AuthMode=WPAPSK
        pre-up iwpriv wlan0 set EncrypType=TKIP
        pre-up iwpriv wlan0 set WPAPSK="yyyyyyyyyyyyyyyyyyyyy"
        pre-up dhclient wlan0
```

The above was culled from various different posts here.

After going from Gutsy to Heron I had trouble getting the wireless to work - my Belkin USB wireless adapter requires the [RT73]("http://ubuntuforums.org/showthread.php?t=400236") driver, but initially it didn't work with that either. It seemed as if it did actually connect to the wireless network, but either didn't authenticate properly and certainly didn't receive an IP address from the DHCP server in the router.

Most of the config above was already there - the main changes were the addition of the '[FONT="Courier New"]dhclient[/FONT]' lines, so perhaps the actual problem with Heron is related to DHCP.

Anyway - Heron is now up and working, but next time I'll think twice before 'upgrading'. (Going from Feisty to Gusty ALSO gave me problems with wireless!)

FYI, I run 64-bit Ubuntu on AMD64.

---

### Post by lagu2653 on 2008-05-02
I installed rutilt but the title of the window is RT2500USB. I think my driver is supposed to be rt2570 I have the DWL-G122 version B1. when I #lsmod | grep rt2570 I get results. For rt2500 and rt73 I get nothing. I downloaded the latest hourly tar-ball, not the beta release, and installed it. I tried to configure it with rutilt. The MAC of my Heron machine pops up in my windows machine access point window. So it's associated. But I still can't ping the access point in encrypted mode.

---

