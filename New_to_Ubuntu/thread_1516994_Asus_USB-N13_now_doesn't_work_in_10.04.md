---
title: "Asus USB-N13 now doesn't work in 10.04"
date: 2010-06-24
forum: New to Ubuntu
---

### Post by jacklinux on 2010-06-24
Hi, i recently installed ubuntu 9.10 and my wireless was working fine.
i upgraded to 10.04 and it no longer works. could someone please assist with this?

---

### Post by jacklinux on 2010-06-24
bump! i really need help.

---

### Post by Triranta on 2010-06-24
I am having the same trouble like you. I recently changed my connection from ethernet to wi-fi. Asus USB N13 works great on windows but failed on Ubuntu 10.04.
Hope to find a solution at the soonest...

---

### Post by harry003 on 2010-06-24
I got instant relief loading Windows XP drivers and running ndiswrapper. 

Look at the last entires in: 


new starbucks wireless thread


Apparently 10.04 is lagging behind on wireless drivers.

---

### Post by stefanmuc2k on 2010-06-28
> **harry003 said:**
> I got instant relief loading Windows XP drivers and running ndiswrapper. 


Tried it, but that did not work for me. I used a fresh Lucid install, ran the updates and rebooted. I attempted to follow the tutorial: 
  [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
So installed ndiswrapper packages and ndisgtk. 
Tutorial suggests to get a Windows driver from the list using the chipset ID (lsub actually returns the device ID not the chipset ID, in my understanding):
  [http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB)
However the list is not organized by chipset ID, and there is no driver for an ASUS card which is remotely similar to this one. So tried to use the one provided on the CD, later downloaded the latest version from the ASUS website which made no difference. 

Copied the driver from the CD into my user directory and loaded it with System->Administration->Windows Wireless Drivers. The tool shows no error and claims that it sees hardware present.

Running ifconfig shows no wireless device. Network Manager shows no wireless. 

Running:
```
sudo   ndiswrapper -l
```

Shows:
```

WARNING: All config files need .conf: /etc/modprobe.d/ndiswrapper, it will be ignored in a future release.
rt2870 : driver installed
	device (0B05:1784) present

```

Then ran:
```
 sudo depmod -a
 sudo modprobe ndiswrapper

 tail /var/log/messages
```

The output from tail:
```

Jun 29 00:40:39 pvr kernel: [ 4726.972013] usb 1-4: reset high speed USB device using ehci_hcd and address 3
Jun 29 00:40:39 pvr loadndisdriver: loadndisdriver: load_driver(358): couldn't load driver rt2870
Jun 29 00:40:39 pvr kernel: [ 4727.128603] usbcore: registered new interface driver ndiswrapper
```

Again ifconfig, iwconfig etc (predictably) show no WLAN device.

So no luck with that approach, if I missed something I'd be grateful if someone pointed it out to me.

---

