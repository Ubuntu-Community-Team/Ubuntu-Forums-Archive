---
title: "Internet connection sharing"
date: 2008-07-21
forum: Networking &amp; Wireless
---

### Post by mpn_1990 on 2008-07-21
I have a seemingly unresolvable and very frustrating problem that has me at wits end.

I want to share my wirelessly connected Ubuntu PC via ethernet to my Windows 2000 PC. The wireless machine gets its internet using wlan0 off a Linksys WRT54G router that also has two wired machines on it. The Windows 2000 machine will not reach the router and I would like to get an internet connection off the nearby Ubuntu machine.

The ubuntu machine has an unused ethernet port (eth0) and I would like to share my connection using this port, to the Windows 2000 machine.

Do not point me toward [this]("http://http://ubuntuforums.org/showthread.php?t=91370&page=19") guide, it is extremely unhelpful. ipmasq and dnsmasq halted my internet traffic after I restarted and are sorry excuses for network utilities. Do not ask me to spend $50 on a network dongle for the other computer, either.

GNOME's stupid unintuitive networking utility seems to be f**ing everything all up and whenever I connect the two computers together, it automatically connects the internet to eth0 instead of wlan0 where the internet is actually COMING FROM and then I don't have internet on either machines.

What am I supposed to do? I'm thinking of just switching back to windows where all you have to do is...get ready...CHECK ONE LITTLE BOX!!

---

### Post by dmizer on 2008-07-21
it took me two weeks to get ICS working on my XP the first time i tried to set it up and i considered myself to be an extremely knowledgeable windows user.  it was far from being as easy as, "check one little box".

try this guide: [https://help.ubuntu.com/community/Internet/ConnectionSharing?](https://help.ubuntu.com/community/Internet/ConnectionSharing?)

make sure you have either a hub, or a crossover cable connecting the windows computer to the ubuntu computer.

---

### Post by mpn_1990 on 2008-07-21
Oh yeah, and I've tried firestarter, too. 

When the cable is unplugged, it says eth0 is not responding.
When the cable is plugged in, it says wlan0 is not responding.

Junk.

---

### Post by mpn_1990 on 2008-07-21
> **dmizer said:**
> it took me two weeks to get ICS working on my XP the first time i tried to set it up and i considered myself to be an extremely knowledgeable windows user.

try this guide: [https://help.ubuntu.com/community/Internet/ConnectionSharing?](https://help.ubuntu.com/community/Internet/ConnectionSharing?)

Thanks, I'll try it.

---

### Post by dmizer on 2008-07-21
> **mpn_1990 said:**
> Oh yeah, and I've tried firestarter, too. 

When the cable is unplugged, it says eth0 is not responding.
When the cable is plugged in, it says wlan0 is not responding.

Junk.

if you still have firestarter installed, you'll probably run into problems.  make sure it's uninstalled.

---

### Post by Washer on 2008-07-22
> **mpn_1990 said:**
> Oh yeah, and I've tried firestarter, too. 

When the cable is unplugged, it says eth0 is not responding.
When the cable is plugged in, it says wlan0 is not responding.

Junk. Connect wlan0 then plug in eth0 & set it up manually "sudo ifconfig eth0 192.168.W.XYZ up"

firestarter is all you need.

---

