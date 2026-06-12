---
title: "No networking after suspend/hibernate"
date: 2005-09-06
forum: Networking &amp; Wireless
---

### Post by nacnud on 2005-09-06
Neither my wifi nor regular ethernet will work after suspending my Dell 600m.  Is there a way to restart all network services without rebooting?  ifup/ifdown and gui activation do not work for some reason after suspend.  I'm using latest ipw2200 driver.

Thanks very much

---

### Post by firecat53 on 2005-09-07
I've also noticed either non-functioning or poorly functioning wireless following a suspend. I'm using APM on an older Dell 7000 w/ dwl-g630 card/madwifi/wpa_supplicant.  It seems to almost be random. Sometimes it'll wake up working perfectly and other times it will require a reboot to get any connection at all (no combination of ifup/ifdown/ifconfig/iwconfig/wpa_supplicant will work).  Seemed to work okay tonight, except any time I send or receive something over the network, the card looks like it drops the connection briefly. Very strange!!

Scott

---

### Post by djib on 2005-09-07
Hello,
Well, instead of rebooting your computer, I assume you can just do a :
```
sudo /etc/init.t/networking restart
``` 
In init.d you can find all services running on your pc, and you can stop them, start them, ... etc

I remind you that suspend and hibernate are two experimental things and this is why you get strange results.
I use both of them but quite often I loose the usb mouse just after coming back from a sleepy state. In that case just do :
```
sudo /etc/init.d/hotplug restart
```

---

### Post by nacnud on 2005-09-07
[QUOTE=djib]Hello,
Well, instead of rebooting your computer, I assume you can just do a :
```
sudo /etc/init.t/networking restart
``` 
In init.d you can find all services running on your pc, and you can stop them, start them, ... etc [/QUOTE]

Thank you this is exactly what I was looking for.

---

### Post by djib on 2005-09-07
[QUOTE=nacnud]Thank you this is exactly what I was looking for.[/QUOTE]
You're welcome.

---

