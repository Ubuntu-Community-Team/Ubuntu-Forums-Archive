---
title: "WMP54Gs Broadcom 4318 - Looking for a little help"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by siciliancasanova on 2007-03-16
So when I first installed Edgy Eft, installing wireless was simple.  I even made a guide for how I got my 4318 to work.  After a reinstall of Edgy Eft, the same procedure no longer works.  So I decide to go up to Fiesty Fawn if I'm going to be reconfiguring things anyway.

I have followed most of the better guides out there for the 4318, to the dot.  I have uninstalled Ndiswrapper and reinstalled the latest version.  Gone in and blacklisted the 43xx drivers.  I've installed the most up to date driver.  ```
anthony@anthony-desktop:~$ ndiswrapper -l
Installed ndis drivers:
wmp54gsa        driver present, hardware present 
anthony@anthony-desktop:~$ 

```

It's installed correctly.  The broadcom shows up as Eth1.  It does initially until you go in and blacklist the 43xx, then when you run ```
iwconfig
``` Eth1 is no longer there.  

I've been at it for a week now, initially thought I was fine when I did it myself and I hate to harrass others to help me out but some help or guidance through this would be appreciated.  Thanks, :)

---

### Post by Kobalt on 2007-03-16
Have you blacklisted and unloaded your bcm43xx drivers before compiling ndiswrapper and installing the new drivers ?

---

### Post by siciliancasanova on 2007-03-16
I don't believe so, but let's say I did, what do I need to do from here if that is the case?

---

### Post by Floppyjoe on 2007-03-16
> **siciliancasanova said:**
> So when I first installed Edgy Eft, installing wireless was simple.  I even made a guide for how I got my 4318 to work.  After a reinstall of Edgy Eft, the same procedure no longer works.  So I decide to go up to Fiesty Fawn if I'm going to be reconfiguring things anyway.

I have followed most of the better guides out there for the 4318, to the dot.  I have uninstalled Ndiswrapper and reinstalled the latest version.  Gone in and blacklisted the 43xx drivers.  I've installed the most up to date driver.  ```
anthony@anthony-desktop:~$ ndiswrapper -l
Installed ndis drivers:
wmp54gsa        driver present, hardware present 
anthony@anthony-desktop:~$ 

```


Where did you get that driver from? I have a broadcom 4318 in my laptop but it uses the driver listed in the howto in my signature.

---

### Post by siciliancasanova on 2007-03-17
I installed the BCM driver.  It is still not working.

---

### Post by Kobalt on 2007-03-17
> **siciliancasanova said:**
> I don't believe so, but let's say I did, what do I need to do from here if that is the case?
You do need to blacklist but most importantly unload the bcm43xx module before starting the install process, otherwise I don't think it might work well... 
```
sudo modprobe -r bcm43xx
```

---

