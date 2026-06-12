---
title: "ASUS USB N-10 Wifi adapter terrible speeds"
date: 2017-03-20
forum: Networking &amp; Wireless
---

### Post by adventure man on 2017-03-20
I have this USB adapter on my desktop (Ubuntu 16.04) and the speeds have always been fast then slow.  It usually starts off fine with 30 Mbs download but after a few minutes goes down to 0.5 Mbs download and stays there.  I have searched around the forums for a fix but nothing seems to work.  

Here is the adapter: [https://www.asus.com/us/Networking/USBN10/](https://www.asus.com/us/Networking/USBN10/)

Here are two threads I found that flesh out the issue a bit more but just didn't resolve things for my desktop:
[https://ubuntuforums.org/showthread.php?t=2290449](https://ubuntuforums.org/showthread.php?t=2290449)
[https://ubuntuforums.org/showthread.php?t=2241067](https://ubuntuforums.org/showthread.php?t=2241067)

This adapter works fine in Windows 7.

Any help is greatly appreciated.

---

### Post by howefield on 2017-03-20
Thread moved to "*Networking & Wireless*" as requested.

---

### Post by jeremy31 on 2017-03-20
See the wireless script link in my signature and post results

---

### Post by adventure man on 2017-03-20
Thanks howefield :)

Followed the Wireless Script jeremy here are the results:
[http://paste.ubuntu.com/24215736/](http://paste.ubuntu.com/24215736/)

---

### Post by jeremy31 on 2017-03-20
Can you change the access point to channel 9 and change encryption to WPA2-AES instead of the mixed mode it uses now?

---

### Post by adventure man on 2017-03-20
Ok Jeremy, set those settings up as you asked.  After about 40 minutes internet went from 35 mbps to 0.5 mbps.  Then after about a five minute wait it bounced back to 35mbps then another 5 min. later back down to 0.27 mbps.  I have a laptop running ubuntu 16.04 and the internet speeds were consistently 35 mbps the entire time.

---

### Post by jeremy31 on 2017-03-20
See if going into Network Manager settings for  your connection and setting IPv6 to ignore helps, also run the following in terminal
```
sudo sed -i 's/wifi.powersave = 3/wifi.powersave = 2/' /etc/NetworkManager/conf.d/default-wifi-powersave-on.conf
```
As Network Manager tries to enable power management on the wireless and that may cause some issues

---

### Post by praseodym on 2017-03-20
Have you tried:

```
echo "options r8712u low_power=1 power_mgnt=0 ht_enable=0" | sudo tee /etc/modprobe.d/r8712u.conf
sudo modprobe -rfv r8712u
sudo modprobe -v r8712u
```
Re-plug the stick

---

### Post by adventure man on 2017-03-24
Hey thanks guys, I did everything you said and I have stabilized speeds matching my windows set-up.  Thank you again :popcorn:

---

