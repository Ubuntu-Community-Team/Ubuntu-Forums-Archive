---
title: "Wifi No Longer Functions (Presumed broken by latest update)"
date: 2024-01-19
forum: Networking &amp; Wireless
---

### Post by dark-wanderer on 2024-01-19
About a week ago now, I started having issues with my wifi.
It was displaying as if it was connected, but the internet wasn't actually functioning at all.
The only way to reliably resolve this, I've found, is to turn the wifi off and on again.
Even a quick flick gets it going again once it reconnects.
Unfortunately, this happens very regularly. Sometimes every few minutes, but now it looks like several times per minute.

Looking around the internet, it seems that around a week ago there was some sort of kernel update?
Unfortunately, I'm not savvy enough to really know what I'm doing. I have managed to switch the kernel version around several times.
Unfortunately, said kernels either have the same issue, or they crash the system before I can even log in, or they don't recognise the wifi as even existing.

I really don't know what I am doing, and I would love some help.
Even if that help is how to prevent Ubuntu updating the kernel on a fresh install.
I can, if it comes down to it, copy all my files to an external hard drive and back again, but that takes an annoyingly long time to do.

It's Ubuntu 22.04.03 LTS, if that's relevant.

---

### Post by foxsquirrel on 2024-01-19
> **dark-wanderer said:**
> About a week ago now, I started having issues with my wifi.



Even if that help is how to prevent Ubuntu updating the kernel on a fresh install.


It's Ubuntu 22.04.03 LTS, if that's relevant.

We have had several very bad incidents with the 6.5 kernel update. Only work around has been to back peddle to 20.04 LTS. You can click on software updater
 then settings and turn automatically check for updates to never. You are not alone on this, have not any trouble for years so we allowed the systems to update, that has just ended...

I did successfully revert a laptop, it was just very basic and did not have all the important stuff on it that required kernal module rebuilds and such. If you system is very basic you can revert if the 6.2 files are still present.

```
sudo apt remove linux-image-$(uname -r) linux-headers-$(uname -r)
```

ONLY USE THIS IF you still have a folder for 6.2 in lib/modules 
If those files are not present your system will be broken.

```
fred@webvm:~$ cd /lib/modules
fred@webvm:/lib/modules$ ls
6.1.0-10-amd64  6.1.0-17-amd64

```

That is from a Debian box however it will similar to what you should see.

---

