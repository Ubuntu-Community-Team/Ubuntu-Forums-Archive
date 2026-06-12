---
title: "How to restart network service without rebooting"
date: 2006-11-20
forum: Networking &amp; Wireless
---

### Post by osx on 2006-11-20
In Fedora I could restart the network service without rebooting by using the command "service network restart". This doesn't work with Ubuntu. Is there a similar way in Ubuntu without rebooting the computer?

---

### Post by mssever on 2006-11-20
> **osx said:**
> In Fedora I could restart the network service without rebooting by using the command "service network restart". This doesn't work with Ubuntu. Is there a similar way in Ubuntu without rebooting the computer?

Use ```
sudo /etc/init.d/networking restart
```

---

### Post by osx on 2006-11-20
Thanks! That did the trick.

---

### Post by deadite66 on 2006-11-23
anyway to do it without sudo?

---

### Post by mssever on 2006-11-23
Not really, unless you enable the root password and log in as root. You could also fiddle with various permissions, but you're likely to break something by doing that unless you know what you're doing.

---

### Post by osx on 2006-11-25
I noticed this did not invoke my changes to resolv.conf. Is there a way to make those changes active without rebooting, too?

---

### Post by spd106 on 2006-11-25
The resolv.conf is usually automatically overwritten on netowork restart by the dhcp process. Try this thread [http://www.ubuntuforums.org/showthread.php?t=160689](http://www.ubuntuforums.org/showthread.php?t=160689)

---

### Post by mssever on 2006-11-25
> **osx said:**
> I noticed this did not invoke my changes to resolv.conf. Is there a way to make those changes active without rebooting, too?

Changes to resolv.conf take effect immediately. You dont need to restart anything.

---

### Post by h4rdwire on 2006-11-28
sudo -i and u'll log into ur root in that terminal and all commands wont have to use the sudo.

---

### Post by christian130 on 2008-03-03
**i think it's wrong for some machines**
it has to be:

*_user@machine$/etc/init.d/ sudo ./networking restart_*


just like the way the pal wrote will not work for some machine
good for people who r looking for quick help

---

