---
title: "My ethernet connection isn't working."
date: 2016-05-15
forum: Networking &amp; Wireless
---

### Post by Nickforall on 2016-05-15
My ethernet connection on Ubuntu isn't working anymore for some reason. I have read a lot of the fixes here, but none of them seem to work.

I found one solution that works, but I have to run it every time I reboot or come out of hibernation mode.
```

nick@nick-Aspire-TC-120:~$ cat Desktop/driver_networkfix.sh 
sudo ethtool -s eth0 speed 100 duplex full autoneg off
sudo ethtool eth0

```

EDIT: I am running 14.04

---

### Post by houstonbofh on 2016-05-15
If you need to turn autonegotiation off, that means it is turned off in your switch.  So, yes you have to set it manually every time the interface it brought up.

---

