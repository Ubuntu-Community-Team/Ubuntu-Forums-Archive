---
title: "Gusty Upgrade, Now KNetworkManager doesnt see Wireless Card"
date: 2007-10-07
forum: Networking &amp; Wireless
---

### Post by superbenny on 2007-10-07
I recently (yesterday) upgraded from 7.04 to 7.10. My card worked fine with everything right out of the box on 7.04, but when i upgraded, KNetworkManager stopped seeing it. Right now, im connected via wifi-radar, but I hate using that for regular use. I tried reinstalling network-manager and knetworkmanager and still, nothing. lshw shows my card, and iwconfig sees my network. as does wifi-radar (obviously) and so does just about everything else.:confused::confused:
intel chipset
Lenovo (IBM) ThinkPadR60

thanks!

---

### Post by ernstblaauw on 2007-10-08
I don;t know if I have the same issue, but my KNetworkManager (KNM) doesn't seem to like my RT2500.
I just upgraded to 7.10. In 7.04, I used the serialmonkey drivers and RutilT to graphically manage the network card. After I upgraded to 7.10, my internet stopped working. I got it working again by just using the built-in capabilities of Kubuntu, (K > System > Network), and removing all the by hand added lines in /etc/network/interfaces.
Now, I also want to have an application like RutilT (KNetworkManager is), but it doesn't see my (only) network connection. Maybe the cause is, that in 7.04 I disabled the KNM and now I did not enable all parts. However, I think it's just KNM's fault and I don;t know what I can do to make KNM see my WiFi.

---

### Post by ysidoro on 2007-10-16
I have the same problem:  Knetworkmanager do not shows any network device neither eth0 nor eth1 (wireless).   However if I go to "Manual Configuration" there are my to devices enabled.

Under "Privative drivers" there is the wireless card enabled too.

I can not locate the problem.  

The 7.04 knetworkmanager works ok, up to 7.10 dist-upgrade through kubuntu tools.

---

### Post by GENEius on 2007-10-20
I'm having this same issue! If anyone gets this working, please let me know!

---

### Post by shadowhywind on 2007-10-21
I also had this issue, following the advice of one of the posts i found in a different topic, i deleted my /etc/network/interfaces, after making a backup first, rebooted, and knetworkmanger worked. Great so the issue laid somewhere in /etc/network/interfaces. After looking around a bit, it looks like they have changed the format of /etc/network/interfaces slightly. instead of auto wlan0(or eth0/eth0) followed by iface wlan0 inet dhcp, it is now replaced with just auto wlan0(or your other devices). 

Also if you have a static ip at the end of your static settings, add metric 0, save /etc/network/interfaces give it a few moments, and knetworkmanager should work. You may have to reboot to make it take effect but that is all you should have to do.

Hope this helps

---

### Post by GENEius on 2007-10-21
> **shadowhywind said:**
> I also had this issue, following the advice of one of the posts i found in a different topic, i deleted my /etc/network/interfaces, after making a backup first, rebooted, and knetworkmanger worked. Great so the issue laid somewhere in /etc/network/interfaces. After looking around a bit, it looks like they have changed the format of /etc/network/interfaces slightly. instead of auto wlan0(or eth0/eth0) followed by iface wlan0 inet dhcp, it is now replaced with just auto wlan0(or your other devices). 

Also if you have a static ip at the end of your static settings, add metric 0, save /etc/network/interfaces give it a few moments, and knetworkmanager should work. You may have to reboot to make it take effect but that is all you should have to do.

Hope this helps

Doing that worked for me so far!

---

### Post by ysidoro on 2007-10-23
Yes!  Yes!  Yes!!    remove */etc/network/interfaces* and reboot.... it is working now!

Thank you [COLOR="DarkRed"]shadowhywind[/COLOR]  =D>

---

### Post by bottleman on 2007-10-31
I had the same problem with an extra twist -- a fresh install of Kubuntu 7.10 left the wireless card functioning, but not visible in KNetworkManager.  In addition, I couldn't via any Kubuntu GUI get a WPA connection to work.  (WEP did work.)  Shadowhywind's idea fixed both those problems.   Thanks!

---

### Post by oh.mynameiscupid on 2007-11-25
Worked here as well :)

---

