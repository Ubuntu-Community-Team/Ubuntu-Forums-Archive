---
title: "Blacklist kernel module"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by AMuze on 2009-09-16
Hello,

I am trying to prevent the default ethernet kernel module from being loaded at boot time. I have added it to the /modprobe.d/blacklist.conf file, but it continues to load every boot. I have built the correct module for my eth0 interface and added it to my /etc/modules file. This seems to allow the new module to load at boot. I just can't seem to get the default one to not load. So I can't use the new one without rmmod the old one first.

My question is what am I doing wrong with the blacklist? I've read about some alias expansion, do I need to do something in another file to stop the default module from being loaded?

I'm running 9.04 on a msi U123 wind. so far it's running pretty nice.

many thanks,
--amuze

---

### Post by tgalati4 on 2009-09-16
Don't fight it.  Let it load.  Then unload it.

Put the following in /etc/rc.local  (before exit 0 line)

ifdown eth0
modprobe -r badethernetmodulethatyouaretryingtoremove
modprobe goodmodule
dhclient -l

---------------

You might need to modify it a bit.  

What is the bad module and why is it not working?

---

### Post by AMuze on 2009-09-16
Hi tgalati4,

Thanks for the speedy reply. First, the module it not necessarily bad, it's just I wanted to build and use the correct module for my hardware. This is a way for me to start understanding the environment better. I could use the default one, but in the long run I'd rather understand how things are really working and how to change them.

I'm not against doing the load/unload technique, but would like even better to not have to waste processing resources on it if there is supposed to be a means of not letting it load. Why does the blacklist not work for this module, yet it seems every search I do on this topic people say to use it?



--amuze

---

### Post by AMuze on 2009-09-16
any additional suggestions?

--amuze

---

### Post by tgalati4 on 2009-09-17
There are several ways that modules can be triggered for loading.  USB hotplug for example.  Every 2 seconds (and this is changeable) the USB ports are scanned.  If a device is detected, the hotplug system scans the product/vendor ID and loads the appropriate driver.  You can change definitions or add definitions for new devices and change modules and behavior through the hotplug system.

I'm not sure how the ethernet ports are detected.  I presume that hald (hardware daemon) picks out the type of card and loads the appropriate driver.

man hald

You would have to get into the hald internals to understand how they work and how to change them.

I've used blacklist to disable ipv6 on Ubuntu versions before Jaunty.  It's now part of the kernel framework for Jaunty and is not easily disabled.  Why your blacklist does not work for your ethernet card is a mystery.  Perhaps it is a bug or it's loaded right away before the blacklist takes effect.  I don't really know.

Ubuntu is probably not the best distro for the build-it-yourself user.  Try slackware, arch linux, or gentoo for that roll-up-your-sleeves-and-get-axle-grease-dirty experience.

Ubuntu has so many auto-detection tools that make it easy to setup but more difficult to customize at a low level.

---

### Post by AMuze on 2009-09-17
Hi TG,  thanks for the reply. I think I did read somewhere that blacklist can't be used for default kernel modules, so maybe you are correct in that it loads before blacklist takes effect. I'll have a look at what hal does, and while I'm at it I'll read more on the blacklist as well.  I've run gentoo in the past, and it's too much axil greeze for me. I'm not looking for that much of a project (too much emerge for me), just looking to understand the system better.  many thanks for the replies, and if anyone else has suggestions please let me know. I have some wireless speed questions, but want to work on one thing at a time. I've got it running WPA in N mode, could be worse... the MSI U123 is pretty cool.  --AMuze

---

### Post by AMuze on 2009-09-22
Hi All,

any other suggestions, I've not had any luck so far. According to the blacklist info it should work. Figured I would try once more in here before I post in the more advanced forum

thanks,
--amuze

---

### Post by AMuze on 2009-09-24
solved:
[http://ubuntuforums.org/showthread.php?t=1273479](http://ubuntuforums.org/showthread.php?t=1273479)

---

