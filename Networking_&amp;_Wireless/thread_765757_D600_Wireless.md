---
title: "D600 Wireless"
date: 2008-04-24
forum: Networking &amp; Wireless
---

### Post by pcmedic on 2008-04-24
I am BRAND NEW to linux. I installed 8 today. Everything is working except my wireless. Any help would be greatful.

---

### Post by superprash2003 on 2008-04-24
hey.. please go to the terminal(Applications->Accessories->Terminal) and type ifconfig and post results here

---

### Post by cob on 2008-04-24
I have a D600 and have a Broadcom BCM4309, the simplest method to get this working is to 'sudo apt-get install b43-fwcutter' and allow it to download the correct driver.  Reboot and it should work, although there seems to be some bug which causes the chip to only work reliably at a very short distance.  The reported fix is to 'sudo iwconfig wlan0 rate 5.5M'.

---

