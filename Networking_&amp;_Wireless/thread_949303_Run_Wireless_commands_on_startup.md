---
title: "Run Wireless commands on startup"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by rypicken on 2008-10-16
I am using a Belkin wireless adapter and have it working fine once I run depmod and modprobe on it. I was wondering if there was a way I could have the system automatically run these commands so I don't have to go into terminal and run them every boot.

---

### Post by Bucky Ball on 2008-10-16
You could write a script to go in your right click menu following this:

[http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/](http://ubuntu-tutorials.com/2006/12/29/right-click-to-launch-custom-scripts-with-nautilus-ubuntu-6061-610/)

Not quite sure what you would write in there though as I am only just starting to get into bash-ing meself. :)

I have been trying to get a script in there to restart or start network connection as I can't seem to find any one click solution to get the wireless up, so if I forget to switch the router on and boot, I go switch the router on then have to open a terminal and type:

sudo /etc/init.d/networking restart

... to get it going again. I'll let you know if I figure it out.

---

### Post by Ayuthia on 2008-10-16
> **rypicken said:**
> I am using a Belkin wireless adapter and have it working fine once I run depmod and modprobe on it. I was wondering if there was a way I could have the system automatically run these commands so I don't have to go into terminal and run them every boot.
Are you sure that you have to run depmod on it?  That builds the dependencies for modules in /lib/modules.  It might just be a matter of adding the modules to /etc/modules:
```
echo <module name without brackets> | sudo tee -a /etc/modules
```

---

### Post by itsjareds on 2008-10-16
Write a BASH script using the same commands as you would use in the terminal. Save the file to your desktop as _restart-internet_ (or anything you want), then go to System > Preferences > Session and add the command:

```
/home/[USER]/Desktop/restart-internet
```

Name it whatever you want and remember to replace [USER] and restart-internet with your personalized names.

---

### Post by Bucky Ball on 2008-10-16
> **itsjareds said:**
> Write a BASH script using the same commands as you would use in the terminal. Save the file to your desktop as _restart-internet_ (or anything you want), then go to System > Preferences > Session and add the command:

```
/home/[USER]/Desktop/restart-internet
```Name it whatever you want and remember to replace [USER] and restart-internet with your personalized names.

This looks good, but wouldn't that then mean the command would run on boot (net already automatic at boot) rather than if the router gets switched off during a session and I need to reconnect?

---

