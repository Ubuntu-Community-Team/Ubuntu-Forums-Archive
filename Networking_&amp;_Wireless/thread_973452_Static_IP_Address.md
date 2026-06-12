---
title: "Static IP Address"
date: 2008-11-06
forum: Networking &amp; Wireless
---

### Post by josephst18 on 2008-11-06
I am trying to get Ubuntu 8.10 to run under Wubi. In Windows XP, I have a static IP address configured for my wireless network. When I boot into Ubuntu, it cannot automatically connect, but it recognizes both my ethernet and wireless card. I open network manager, and try to configure them. In Windows, my configuration is as follows: Ethernet card disabled, Wireless configured as: IP address: 10.0.0.9  |   Subnet mask: 255.255.255.000   |   Default gateway: 10.0.0.2  |   Primary DNS server: 10.0.0.2   |   Secondary DNS server: None
I enter this, and click save, but when I open the window up again, it has changed my settings, and I cannot connect. If I hook up an ethernet cable, I am able to connect, but it is a local connection (I can't access the internet). I am new to Linux/Ubuntu, and a step by step guide would be helpful.

---

### Post by Bailywolf on 2008-11-07
I'm having a similar issue- WUBI on an XP box.  I enter my static settings, and everything greenlights, but I can't resolve any URL's- for some reason, DNS isn't working.  I can enter a known IP for a site, and it connects immediatly, but I can't access anything requiring name resolution despite having both my primary and secondary DNS entries correct.

-B

---

### Post by Coreigh on 2008-11-07
This is a "shot in the dark" but several other sources have suggested that since wubi is running along side  *with* XP you will need a different IP address than the XP box. If the XP box is configured with 10.0.0.9 then try the same settings in Wubi but use 10.0.0.11 (provided 11 is not used by some other computer or device on the network.)

---

### Post by Bailywolf on 2008-11-07
> **Coreigh said:**
> This is a "shot in the dark" but several other sources have suggested that since wubi is running along side  *with* XP you will need a different IP address than the XP box. If the XP box is configured with 10.0.0.9 then try the same settings in Wubi but use 10.0.0.11 (provided 11 is not used by some other computer or device on the network.)

I just tried this, and alas, no dice- it still can't resolve a name to an IP, but can still find and connect to an IP.  

-B

---

### Post by jimv on 2008-11-07
Ditch Network Manager and try WICD instead.  From XP, download the deb file from this site and then install it in Ubuntu.

[http://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=internap&filename=wicd_1.5.4_all.deb&48670932](http://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=internap&filename=wicd_1.5.4_all.deb&48670932)

It seems to work much better for manual network settings.

---

### Post by josephst18 on 2008-11-23
> **jimv said:**
> Ditch Network Manager and try WICD instead.  From XP, download the deb file from this site and then install it in Ubuntu.

[http://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=internap&filename=wicd_1.5.4_all.deb&48670932](http://sourceforge.net/project/downloading.php?group_id=194573&use_mirror=internap&filename=wicd_1.5.4_all.deb&48670932)

It seems to work much better for manual network settings.
How do I install WICD if I don't have an intenet connection? The website says to use the terminal to download two files, but Ubuntu does not have an internet connection.

---

