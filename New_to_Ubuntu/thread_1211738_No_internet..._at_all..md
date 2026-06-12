---
title: "No internet... at all."
date: 2009-07-13
forum: New to Ubuntu
---

### Post by Prom3therion on 2009-07-13
I just installed easy peasy on my asus eee 1005ha and i cant get my internet to work at all. Both wireless and wired are a no go. Ask for more info if needed.

---

### Post by nothingspecial on 2009-07-13
To give more info open a terminal however you do that in easypeasy (it will probably be in a menu somewhere, looking at the screenshots in accessories)

Type ```
sudo lshw -C network
```

and copy and paste the output here.

---

### Post by superprash2003 on 2009-07-13
also post output of 
1)ifconfig
2)iwconfig

---

### Post by walt.smith1960 on 2009-07-21
The Eee1005HA uses Atheros chips for both WiFi & wired ethernet. These appear to not be supported in 9.04. I have a TrendNet USB adapter TEW-424UB ** H/W:3.1** which is recognized natively. I also have an older version that was not recognized.  I then found a tutorial that said in essence:

From a terminal window


[LIST=1]
[*]sudo apt-get update
[*]sudo ap-get upgrade
[*]reboot. Again from a terminal window
[*]sudo apt-get install linux-backports-modules-jaunty
[*]reboot.
[/LIST]
The WiFi adapter is now recognized. The last time I checked the LAN (wired ethernet) adapter is still not working.  I believe a newer kernel might fix these issues. Perhaps with 9.10?  I'm a FNG(freakin' new guy) and not an IT type but I have fun:cool:

---

