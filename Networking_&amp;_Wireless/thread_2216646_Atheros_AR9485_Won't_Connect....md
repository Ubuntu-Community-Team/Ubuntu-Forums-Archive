---
title: "Atheros AR9485 Won't Connect..."
date: 2014-04-13
forum: Networking &amp; Wireless
---

### Post by lordsolrac2 on 2014-04-13
Hello. I'm having issues with my Lenovo z710. I installed Linux Mint on it an at a point had working Wifi (blacklisted acer_bcmwi) and also updated kernel (to 3.11).
After fixing Grub to avoid the sync failure, I noticed that it wasn't working again. And I ended up upgrading to 3.14, and the result was the same. I also installed bcm-b43,sta,installer and still no avail.
I also did 

sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
But there isn't any change at all...

What should I do?
(currently connected through phone)

---

