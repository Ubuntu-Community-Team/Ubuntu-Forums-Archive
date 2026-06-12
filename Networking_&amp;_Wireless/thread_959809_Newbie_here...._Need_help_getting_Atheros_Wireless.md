---
title: "Newbie here.... Need help getting Atheros Wireless Card working.."
date: 2008-10-26
forum: Networking &amp; Wireless
---

### Post by khopek on 2008-10-26
I just installed ubuntu and have no experience whatsoever. I am running an HP Compaq Presario v6000 laptop with an AMD64 AthlonX2. The wireless card is an Atheros 5007 (?).

I've tried following guides on installing with ndiswrapper and madwifi to no avail. My internet works when plugged in directly, but I am at a loss as to how to get wifi working.

---

### Post by pastalavista on 2008-10-26
Open System > Administration > Synaptic Package Manager. Then, in settings, be sure to check all the third party and nonfree software repositories. Then in a terminal (Applications > Accessories > Terminal) type ```
sudo apt-get update
```
when that's done (be sure you're online) type```
update-manager
```
Ubuntu should recognize your wireless card and download the appropriate drivers.

---

### Post by anthony_barker on 2008-10-26
I just went through this. Worked fine in old version of ubuntu but after the upgrade didn't work.

Went through [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

Card type: AR5212/AR5213

tried encrypted and unencrypted connection. With WEP turned off I could connect. Anyway after a lot of trying to troubleshoot I opened up 

sudo nano /etc/networks/interfaces file and commented out everything.

---

