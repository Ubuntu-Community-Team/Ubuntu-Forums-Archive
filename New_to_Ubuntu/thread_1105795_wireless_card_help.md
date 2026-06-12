---
title: "wireless card help"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by eddski on 2009-03-25
I have a Cisco aironet card w/Atheros AR5001X+ chipset and I am having trouble finding/loading the driver for it. Please help..

---

### Post by anewguy on 2009-03-25
Have you tried this:

[http://ar-domena.com.pl/ar5001x/]("http://ar-domena.com.pl/ar5001x/")

Dave :)

---

### Post by eddski on 2009-03-25
thanks, but I dont have an acct. there and I'm getting some kind of mysql connection error

---

### Post by 3rdalbum on 2009-03-25
The Intrepid release notes tell you how to enable the driver for this card, but this is the outline of how to do it:

1. Enable the Backports repository in the Software Sources program, and reload the package list when it asks you to.
2. Install the "generic-intrepid-backports-modules" package from Synaptic Package Manager (just search for "intrepid" by name and you'll find it).
3. Open the /etc/modules file as root (gksudo gedit /etc/modules) and add the line:

```
ath5k
```

Save your changes.
4. Open the file "/etc/modprobe.d/blacklist" as root (gksudo gedit /etc/modprobe.d/blacklist) and add the following line:

```
ath_pci
```

Save your changes. Reboot.

This procedure installs a new driver, tells Linux to load it on every startup, and tells it not to load the old driver (because the old driver would otherwise try to attach itself to the device).

---

### Post by eddski on 2009-03-25
thanks 3rdalbum, I'll try it and see what happens. I already have the ath_pci in the modprobe.d file.

---

### Post by eddski on 2009-03-26
I'm very new, but how do I enable the backports package?

---

### Post by nothingspecial on 2009-03-26
With a wired internet connection type

```
sudo apt-get install linux-backports-modules-intrepid 
```

---

### Post by 3rdalbum on 2009-03-26
> **eddski said:**
> thanks 3rdalbum, I'll try it and see what happens. I already have the ath_pci in the modprobe.d file.

You need "ath_pci" in the blacklist file (/etc/modprobe.d/blacklist), not in the modprobe.d folder.

---

### Post by eddski on 2009-03-26
thanks, I finally have the driver loaded and the blacklist corrected, but when I power on with the card in I have to turn it on with "ifconfig wlan1 up" command. Is there a way to permanently turn it on? Also will this interfere with the internal Intel wireless card?

---

### Post by 3rdalbum on 2009-03-28
That sounds like an oddity of that specific device; I haven't heard of this happening before. So, I'm not sure if it can be "permanently turned on". You could add that command to the "/etc/rc.local" file before the line at the end that says exit. That would cause the command to run as root whenever you start up, just before X starts.

It shouldn't interfere at all with your internal Intel card.

---

### Post by mainshell on 2009-03-28
Thank you 3rdalbum - the backports solution has sorted my Atheros wireless. It now starts ok upon reboot.

---

