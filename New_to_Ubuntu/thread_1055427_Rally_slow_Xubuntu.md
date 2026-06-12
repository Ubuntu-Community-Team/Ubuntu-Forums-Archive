---
title: "Rally slow Xubuntu"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Hadso on 2009-01-30
Hi. I have notebook with 500 of ram, 40gb hd, it's an AMD 1.2, I had installed Xubuntu 8.10. 
I should that it would be very fast, to work and booting. 
But now it's slower than WinXP that I have also in this machine. It's take more for booting and do simple things lihe surfing the net, open documents, etc. 
I read in the Systemo Monitor that it's using the 65% of my ram. This is wire, but is the only.

What can I do? 
Thank you very much!

---

### Post by gymophett on 2009-01-30
Its probably because you dual booted it. That will slow your computer. :/

---

### Post by Hadso on 2009-01-31
In another forum they said that I should tried installig flux. How can I do that?

Thanks!

---

### Post by cardinals_fan on 2009-02-01
> **gymophett said:**
> Its probably because you dual booted it. That will slow your computer. :/
Completely and totally wrong.
> **Hadso said:**
> In another forum they said that I should tried installig flux. How can I do that?

Thanks!
[https://help.ubuntu.com/community/Fluxbox](https://help.ubuntu.com/community/Fluxbox)

Xfce should run okay on those specs, but Fluxbox is lighter and awesome anyway.

---

### Post by Crafty Kisses on 2009-02-01
If you like Flux you should try Fluxbuntu, I know they are not releasing any more versions at the moment and they will start again soon, but if you like Flux, try it. [http://fluxbuntu.org/](http://fluxbuntu.org/)

---

### Post by OutOfReach on 2009-02-01
> **gymophett said:**
> Its probably because you dual booted it. That will slow your computer. :/

No, this is not true. Dual-booting does not decrease performance at all.

@OP Your specs seem fine. What exactly is slow? Certain apps or just the general system? (Boot, etc, etc)

You can install Fluxbuntu if you want a flux enviroment. I would also recommend installing Crunchbang Linux (it has Openbox, a lightweight and fast window manager)

---

### Post by Praxicoide on 2009-02-02
Did you include a swap partition? I had that problem once, (I moved it and fstab didn't recognize it anymore. The machine crawled). If you didn't add a swap partition, insert the LiveCD again, or a Gparted CD and add one, since you have 500MB of ram, it should be 1GB if you want to be able to hibernate; if you don't 500MB should be OK.

Also, look in System monitor what exactly is eating up RAM (The System Monitor itself will be one of the culprits, I've changed it to XFCE4-Taskmanager which is much lighter). There are other gnome dependencies that you can replace for better performance, but I don't know how stable the xfce stuff is. I've switched pretty much everything to xfce without any problems so far, but do so at your own risk (you can always turn stuff back, of course). You can safely try "slim" instead of gdm for logging in, slim is much faster. Xfce also has its own notify manager, that I'm using without problems so far.

There is some autostart stuff that is safe to turn-off. Look under "Applications"----------> "Configuration", there's an entry there for "autostarted applications." Click it and check if you need the stuff mentioned (you can probably turn off things like Bluetooth support).

There are other things you can do, such as messing with the boot options, changing swappiness (I wouldn't recommend this), disabling IpV6 for faster web-surfing, and of course, compiling your kernel (I did so with good results on one machine, but failed miserably on another). First though, make sure you have swap, that could be your problem.

XFCE remembers the stuff loaded when logging out to load it the next time. So another good idea would be to close the applications you will not need. Check again in with the System Manager for stuff that could be in the background. Something less resource-hungry than the manager is to open up a terminal and type "top"

---

