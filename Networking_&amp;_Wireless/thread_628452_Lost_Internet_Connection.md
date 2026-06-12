---
title: "Lost Internet Connection"
date: 2007-12-01
forum: Networking &amp; Wireless
---

### Post by jssand2 on 2007-12-01
OK strange happenings...I have been using dual boot (XP-Ubuntu/Kubuntu) for quite some time now and never had a problem with the auto detection during install.

Last week the internet connection for Linux died while the Microcrap is still going strong without a hiccup. I did the Microsoft "update" for my RealTek 8139 about this same time but I would not think this would effect the Linux hard disk/drivers.

Was running Kubuntu at the time and reformatted and switched to Ubuntu when the problem started without success. I even downloaded and tried another popular distro and the same problem still persisted. Seems to be a Linux problem and not a system problem. 

I am not a Linux master but do enjoy it in its basic use hence why I am requesting assistance.

Does this sound remotely familiar to anyone??? 

System...

Athalon 2100xp+ on Soyo Dragon with Realtek 8139
Linksys WRT54G (hard wire only-wireless disabled)

---

### Post by jssand2 on 2007-12-01
Looks like this may be a very common problem according to another link, I will try the advise...

---

### Post by jssand2 on 2007-12-01
Worked perfect, Thank You 

All that was needed was to go into the windows control panel / system / and NIC properties to reset the Wake on LAN to "enable" as another forum stated...

[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)

---

### Post by keepitsimpleengr on 2007-12-03
This fix worked for me.

I run ubuntu  7.10 on an intel D865Gsa mainboard which has integral RealTek 8139 NIC.  The only notification I received was the message network unreachable on my private LAN.

Enabling "Wake-on-LAN" in the XP pro and reboot solved the problem.

Thanks for the help.

kise

---

