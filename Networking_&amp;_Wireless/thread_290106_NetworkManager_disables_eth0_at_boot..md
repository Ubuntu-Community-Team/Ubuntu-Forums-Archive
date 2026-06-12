---
title: "NetworkManager disables eth0 at boot."
date: 2006-10-31
forum: Networking &amp; Wireless
---

### Post by kylevan on 2006-10-31
ok... I don't know what setting I screwed up, but after a recent reboot, eth0 wasn't working.  I ran ifdown and ifup and things were peachy.  rebooted again and the same thing happened.  looked in /var/log/daemon.log and found a few interesting lines.

```
Oct 31 15:20:45 musicman NetworkManager: <information>^Istarting... 
Oct 31 15:20:45 musicman NetworkManager: <information>^Ieth0: Driver 'ne2k-pci' does not support carrier detection. ^IYou must switch to it manually. 
Oct 31 15:20:45 musicman NetworkManager: <information>^Inm_device_init(): waiting for device's worker thread to start 
Oct 31 15:20:45 musicman NetworkManager: <information>^Inm_device_init(): device's worker thread started, continuing. 
Oct 31 15:20:45 musicman NetworkManager: <information>^INow managing wired Ethernet (802.3) device 'eth0'. 
Oct 31 15:20:45 musicman NetworkManager: <information>^IDeactivating device eth0. 
```

this is some ancient SMC 10Base-T network card that's in a jukebox project of mine.  why it's being disabled, I have no idea... if anyone can shed some light, I would be muchly appreciative.

---

### Post by kylevan on 2006-11-01
Apparently I solved this...

did the obvious thing... uninstalled the NetworkManager package.

what I think was the main problem is the line in the logfile where it says that my NIC doesn't support carrier detection.  would make it pretty difficult for NM to figure out whether it can connect or not. :rolleyes: 

moral of the story, if you have a wired ethernet connection that you never change, don't use NM, it's a bunch of hassle. (although it works beautifully on my wireless laptop)

---

