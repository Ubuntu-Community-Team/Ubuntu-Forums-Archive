---
title: "Ubuntu 14.04 Atheros ar9485 Wlan adapter not working"
date: 2014-05-25
forum: Networking &amp; Wireless
---

### Post by taktverkehr on 2014-05-25
Hey there, 
I have a Asus R704 Netbook with a Atheros ar9485 Wlan-Card and I recently installed Ubuntu 14.04 Gnome Version. 
I always had problems with my Wlan-Card, but on my last Ubuntu (12.04) I managed to activate the Wlan card. Now I installed Ubuntu 14.04 and nothing is working. 
I installed the ath9k driver.
My problem is: The Wlan-Card isn't working, because in Ubuntu it is hard blocked. On Windows my Wlan is perfectly working. 
There is a hot key for Wlan, but under Ubuntu it only turns on flight-mode. 
Just for information, in Ubuntu 12.04 I finally managed to turn the hardware on with the following command:
```
   sudo su
modprobe ath9k
echo "168[COLOR=#ff0000]C[/COLOR] 0032" [COLOR=#ff0000]>[/COLOR] /sys/bus/pci/drivers/ath9k/new_id
iwconfig
exit
```

Unfortunately this code isn't working on 14.04. 
It would be graet, if someone could help me.
Thanks...

---

### Post by varunendra on 2014-05-30
Welcome to the forums taktverkehr !

> **taktverkehr said:**
> My problem is: The Wlan-Card isn't working, because in Ubuntu it is **hard blocked**.

Please check this thread out, I suspect you may have the same bug : [http://ubuntuforums.org/showthread.php?t=2181558](http://ubuntuforums.org/showthread.php?t=2181558)

If the above thread doesn't solve the problem, please follow the instructions in this post to give us a detailed diagnostics report : [http://ubuntuforums.org/showpost.php?p=13024222](http://ubuntuforums.org/showpost.php?p=13024222)

---

