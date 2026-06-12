---
title: "Broadcom BCM4312 not working / package firmware-b43-lpphy-installer issue"
date: 2014-04-24
forum: Networking &amp; Wireless
---

### Post by blitzit on 2014-04-24
Hello,

I upgraded to 14.04 yesterday from 13.10. I am using the Lubuntu flavour.

Even on my 13.10, I had an blacklisting issue with the Broadcom driver, which started working after the usual troubleshooting.

However, after the upgrade to 14.04, the troubleshooting doesn't seem to be effective anymore. From what I can understand, it is because of the package firmware-b43-lpphy-installer being unavailable from this version onwards. This Ubuntu Help page - [https://help.ubuntu.com/community/BroadcomSTA(Wireless)](https://help.ubuntu.com/community/BroadcomSTA(Wireless)) seems to suggest the package is essential in running the hardware that I have - [COLOR=#333333][FONT=Ubuntu]Broadcom Corporation BCM4312 802.11b/g [/FONT][/COLOR][COLOR=#333333][FONT=Ubuntu]LP-PHY [14e4:4315] (rev 01). When I try to install the package using apt-get, I get the error message
```
"Package 'firmware-b43-lpphy-installer' has no installation candidate
However, the following packages replace it:
firmware-b43-installer
```

I have firmware-b43-installer installed but it doesn't seem to solve the problem.

Please help.[/FONT][/COLOR]

---

### Post by Hadaka on 2014-04-24
Hi, from a wired connection please do.
```
sudo apt-get remove --purge bcmwl-kernel-source
sudo apt-get upgrade
sudo apt-get update
sudo apt-get install linux-firmware-nonfree
sudo modprobe b43
```

---

### Post by blitzit on 2014-04-24
Wonderful! Thanks Hadaka.

I had done the 4 things. the modprobe was the one that remained. Will I need to execute the modprobe on every boot now?

---

### Post by ajgreeny on 2014-04-24
You can add that module to the modules loaded at startup by editing /etc/modules as root.
```
sudo nano /etc/modules
```
and add **b43** to a new line at the bottom of the file then save it with **Ctrl+X**, **Y** for yes, **enter** to accept.

---

### Post by Hadaka on 2014-04-24
Hi, glad that worked for you!
you can also write the b43 file to load on boot with this..

```
sudo su
echo b43 >> /etc/modules
exit 0
```
thanks.

---

