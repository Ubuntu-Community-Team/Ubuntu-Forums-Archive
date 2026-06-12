---
title: "WPA but not WEP"
date: 2007-01-22
forum: Networking &amp; Wireless
---

### Post by opapo on 2007-01-22
Here is what I am using:
OS: Ubuntu Edgy
Wireless Chipset: Broadcom BCM4318
Driver: Ndiswrapper 1.18

I can access the WPA AP at work, but I can not connect to the WEP AP at home.  I am using a friend's AP so I can't change the AP.  I have double checked the WEP key and I know it is correct.

Here's a snippet from my /etc/network/interfaces file:
--snip--
auto eth1

iface eth1 inet dhcp
     wireless-essid <Valid essid>
     wireless-key <Valid key>

What am I doing wrong?

-Daniel

---

### Post by wieman01 on 2007-01-23
Is it possible that your friend hasn't got DHCP enabled? If that's not the problem, try to "kill" wpa-supplicant from a terminal window & try to reconnect:
> sudo killall wpa_supplicant
> sudo /etc/init.d/networking restart

---

### Post by lukew on 2007-01-23
I have had to turn on SSID Broadcasting on. It seems that with WEP it had to be on but WPA it didn't. (It would not connect otherwise) When I changed to WAP a few weeks ago I did not need to broadcast it; however my g/f laptop (xp) which could connect without it being broadcasted with WEP could not connect with it not being broadcassted under WPA.

---

### Post by opapo on 2007-01-23
I added "wireless-mode managed" to my /etc/network/interfaces file and it worked.  I should have thought of this earlier.  Thanks.

-Daniel

---

