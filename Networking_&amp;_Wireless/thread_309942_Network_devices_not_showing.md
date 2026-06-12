---
title: "Network devices not showing"
date: 2006-11-30
forum: Networking &amp; Wireless
---

### Post by kgee on 2006-11-30
I've been trying to get my wireless on my laptop going, but the more i try the more lost I get.

I'm running Edgy server on my acer aspire 5610 laptop, and previously when I ran the dapper desktop it configured my network (ethernet and wireless) automatically. the wireless was eth0 and the ethernet was eth1. Both were present in /dev as i expected.

Right now, my ethernet works fine, the only difference is that it seems to be running off eth0. But thats when i start getting confused. when I do an iwconfig the results show lo, eth0, and sit0, all with no wireless extensions. I might be wrong in assuming that iwconfig has actually found these listed devices, but when i look in /dev there is no eth0 listed. 

ndiswrapper -l shows no drivers installed, unfortunately i dont know anything about ndiswrapper, i just know from other posts that it typically shows some drivers installed before things work :P

lspci does show a:
05:00.0 Network controller: Intel Corporation PRO/Wireless 394ABG Network Connection (rev 02)

so long story short, i know it can find my wireless card, but i dont think its being used in /dev and im out of ideas. anyone feel like giving some advice? I'm also curious to know why i cant find my ethernet device, since im clearly plugged in and using it right now :P

---

### Post by Henry Rayker on 2006-11-30
I'm not sure about your problem, but I was curious: Why did you downgrade from Dapper to Hoary?

---

### Post by kgee on 2006-11-30
ugh, sorry, meant edgy. i'll fix it. my mistake

---

### Post by Henry Rayker on 2006-11-30
One of Edgy's weaknesses, in my opinion (and judged by other people's experiences) is that it has worse wireless support than Dapper did.

Did Dapper automatically configure your wireless, or did you have to load any drivers or do anything?

---

### Post by kgee on 2006-11-30
dapper did configure wireless on its own. Just install the OS, turn the network card switch on, go to the network manager, pick from the list of essid's, and its done.

unfortunately, im running fluxbox instead of gnome (this is why i installed the server version instead of the regular desktop) so the network manager tool im used to is no longer installed. I tried to find and reinstall it, and thought i _did_ find it when i installed NetworkManager, but whenever i run it absolutely nothing happens. I dont even think it would be much help, since /dev is not picking up any of my network devices anyway (which I really dont understand because i know im using at least one network device)

---

### Post by Henry Rayker on 2006-11-30
The server install isn't necessary if you want to use a different desktop environment. I believe there is a fluxbuntu project, actually...and I know fluxbox is available in the repos...

not that this fixes the problem at hand =\

---

### Post by Thumper322 on 2006-11-30
> **kgee said:**
> ndiswrapper -l shows no drivers installed, unfortunately i dont know anything about ndiswrapper, i just know from other posts that it typically shows some drivers installed before things work :P

**ndiswrapper** is a tool to use Windows drivers under Linux; to use it, you need ndiswrapper-common and ndiswrapper-tools. (I think there's also a GUI available, called ndiswrapper-gtk or something similar.) But I don't think you need to use it: I checked [this database]("http://linux-wless.passys.nl/"), and found your card; **drivers for your model are available [here]("http://ipw3945.sourceforge.net/")**.

> **kgee said:**
> unfortunately, im running fluxbox instead of gnome (this is why i installed the server version instead of the regular desktop) so the network manager tool im used to is no longer installed. I tried to find and reinstall it, and thought i _did_ find it when i installed NetworkManager, but whenever i run it absolutely nothing happens. I dont even think it would be much help, since /dev is not picking up any of my network devices anyway (which I really dont understand because i know im using at least one network device)

I don't know how FluxBox works, but as far as I know there are only Network Manager applets available for KDE and Gnome. Try:
```
apt-cache search network-manager
```I'm not on my Ubuntu box right now, so I can't tell you the results off-hand. You might find [Connection Manager]("http://ubuntuforums.org/showthread.php?t=299462") useful; it can be configured without the optional tray icon, and appears to support most everything that Network Manager does.

What kind of network is this? Unsecured, WEP, WPA, other?

Good luck... hope this helps.

---

### Post by kgee on 2006-11-30
The driver links above need me to install ieee80211-1.2.15, which in turn needs me to reconfigure my kernel. Thats a little over my head at the moment :P

the network i'm trying to connect to is unencrypted.

and I'll go install network-manager now :)

I'll probably be back sometime tomorrow with a verdict, in the mean time if you think of anything else please speak up :D

---

### Post by Thumper322 on 2006-11-30
> **kgee said:**
> The driver links above need me to install ieee80211-1.2.15, which in turn needs me to reconfigure my kernel. Thats a little over my head at the moment :P

the network i'm trying to connect to is unencrypted.

and I'll go install network-manager now :)

I'll probably be back sometime tomorrow with a verdict, in the mean time if you think of anything else please speak up :D

Doesn't [look]("http://ipw3945.sourceforge.net/INSTALL") *too* hard... Just cut and paste. Give it a try; if you end up having to recompile your kernel, then ask for help. (I've never recompiled a kernel myself, so I wouldn't know what's involved...

> If you encounter problems with the above, you may need to install the 
ieee80211 sources into your kernel and then build it as part of your 
kernel image.  See the INSTALL and README.ieee80211 files provided in 
the ieee80211 subsystem package for more information.

You can also download the Windows drivers from the manufacturer's website, and use them with **ndiswrapper**--much easier.

Good luck...

---

