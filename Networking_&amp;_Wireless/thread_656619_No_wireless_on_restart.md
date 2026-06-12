---
title: "No wireless on restart?"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by DLy on 2008-01-02
Ok...did a search and couldn't find exactly what I needed.  I have ndiswrapper installed with my wireless driver (bcmwl5.)  Everytime I restart my computer, it cannot find the wireless hardware and I have to uninstall and then reinstall the wireless driver for the "wireless connections" manager to pop up in my network properties.  Any ideas on how to fix this?  Thank you guys ahead of time and I apologize if this is a common question...

btw, I'm running a Compaq Presario V2410us with Broadcom 4318.

---

### Post by spd106 on 2008-01-04
Hi,

The two most common issues are:

1) Make sure you have blacklisted the bcm43xx driver.
To do this open the /etc/modprobe.d/blacklists file (with sudo) and add "blacklist bcm43xx" to the end.

2) Add ndiswrapper to the list of driver modules to be loaded at boot.
If you open the /etc/modules file, ndiswrapper should be listed. This isn't always neccessary, but I recommend doing it anyway.

---

### Post by s3raphim on 2008-01-04
I have a similar problem - wireless just flat out doesn't show up a lot of the time.  The fixes you recommended are already in place on my machine:

HP dv2416us running feisty with 2.6.20-16

any other ideas?

---

### Post by Canto on 2008-01-07
I've had the same problem for a long time, but found out yesterday that the wrong driver was installed.

Type the following in the terminal to determine if you got the right driver or not:
```
 ndiswrapper -l
```

You could read [my post]("http://ubuntuforums.org/showthread.php?t=659076&highlight=eth1") and try to do the installation of ndiswrapper once more.

EDIT: Downloading the right driver and install it correctly should do it. A complete re-installation of ndsiwrapper should not be necessary.

---

### Post by zipperback on 2008-01-07
> **DLy said:**
> Ok...did a search and couldn't find exactly what I needed.  I have ndiswrapper installed with my wireless driver (bcmwl5.)  Everytime I restart my computer, it cannot find the wireless hardware and I have to uninstall and then reinstall the wireless driver for the "wireless connections" manager to pop up in my network properties.  Any ideas on how to fix this?  Thank you guys ahead of time and I apologize if this is a common question...

btw, I'm running a Compaq Presario V2410us with Broadcom 4318.



Please reboot your computer and then tell me the output of the following commands.
I want to know BEFORE you have ndiswrapper active on your system.

```


ndiswrapper -l

ifconfig

iwconfig

```

I want to know what it says before you reload the ndiswrapper.



I'm guessing that you simply left out something after the installation of the windows driver.


After you load your driver which should look something like 
```
sudo ndiswrapper -i MyDriver.inf
```

You should issue the following:

```

sudo modprobe ndiswrapper
sudo ndiswrapper -m
sudo ndiswrapper -ma

```

That should resolve the issue with ndiswrapper not being loaded after a reboot.

- zipperback
:popcorn:

---

### Post by kvonb on 2008-01-07
-

---

