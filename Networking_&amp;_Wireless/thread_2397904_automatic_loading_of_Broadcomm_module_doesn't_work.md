---
title: "automatic loading of Broadcomm module doesn't work"
date: 2018-08-04
forum: Networking &amp; Wireless
---

### Post by DreiBaer on 2018-08-04
Hi,

in this post Hadaka mentioned how to make a module autoloaded by inserting it into the file /etc/modules
([link to post]("https://ubuntuforums.org/showthread.php?t=2080520&p=12336604#post12336604"))
```
sudo echo 'brcmsmac' >> /etc/modules
``` 
This command doesn't work, but I did it manually:
```
sudo nano /etc/modules
```
I added the line brcmsmac to the file and hoped it works.

But unfortunately it doesn't work for me. The module isn't loaded after restart. But everytime I execute the command ```
sudo modprobe brcmsmac
``` the module is loaded and my WLAN works fine. ... until the next restart.

Does anyone know how to solve?


Best Reagards
DreiBaer

---

### Post by jeremy31 on 2018-08-04
See the wireless script link in my signature and post results

---

### Post by praseodym on 2018-08-05
Check the blacklists:
```

grep brcm /etc/modprobe.d/*
```

---

### Post by DreiBaer on 2018-08-05
```
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcm80211
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmfmac
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmsmac

```

---

### Post by praseodym on 2018-08-05
There it is blacklisted. Take it out from that file
```

gksudo gedit /etc/modprobe.d/blacklist-bcm43.conf
```
save, close the editor and reboot

---

