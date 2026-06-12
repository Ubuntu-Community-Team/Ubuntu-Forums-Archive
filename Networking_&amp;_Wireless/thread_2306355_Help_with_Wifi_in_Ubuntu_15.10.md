---
title: "Help with Wifi in Ubuntu 15.10?"
date: 2015-12-14
forum: Networking &amp; Wireless
---

### Post by bill96 on 2015-12-14
So, I've managed to install Ubuntu 15.10 in a dual boot with Windows 10.
I'm on an XPS 13-9343, if that is relevant. The issue I'm facing right now is that, though I can boot into Ubuntu, I am unable to connect to the wireless connection with it. What can I do to try to fix this? Is this an Ubuntu issue (a known one) or will it also plague other distros? I had same problems with 14.whatever, so its not being caused by the new version.

---

### Post by deepakdeshp on 2015-12-15
Please see 
[http://ubuntuforums.org/showthread.php?t=2306463](http://ubuntuforums.org/showthread.php?t=2306463)

---

### Post by bill96 on 2015-12-15
> **deepakdeshp said:**
> Please see 
[http://ubuntuforums.org/showthread.php?t=2306463](http://ubuntuforums.org/showthread.php?t=2306463)
Problem is, my laptop doesnt have an Ethernet port. I just bought one (it's the Moshi one-only thing available in immediate vicinity) and Ubuntu was unable to connect. The wifi symbol would do that connecting animation for a minute until it just said "nopenopenope".

---

### Post by Yawanathan_Israel on 2015-12-16
Hello,

Can you give more information on the type of Wifi chipset in the laptop? I'm sure we can help you get the correct driver. 

Thanks
Yawanathan

---

### Post by jeremy31 on 2015-12-16
Post the result in terminal for ```
lspci -nnk | grep -iA2 net; rfkill list all
```

---

### Post by slickymaster on 2015-12-16
*Moved to the ***Networking & Wireless*** sub-forum*

---

### Post by pqwoerituytrueiwoq on 2015-12-16
You can also use a wifi or LAN USB adapter to allow you to download updates/drivers, really makes it easier if you the driver requires ~8 dependencies be installed

---

