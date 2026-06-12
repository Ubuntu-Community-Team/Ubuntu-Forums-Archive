---
title: "Wireless Not Working After Ubuntu 14.04 LTS Updates"
date: 2014-07-30
forum: Networking &amp; Wireless
---

### Post by dave133 on 2014-07-30
I've been running Ubuntu for several months now and am currently running Ubuntu 14.04 LTS.  After updating my system last night, I shut down with nothing apparently wrong with the system.  This morning, however, my wireless internet connection is not working and my wireless mouse does not work.

I checked on a few other forums and was still not able to get things working.  However, after typing
```

sudo lshw -C network

```
I get:
```

*-network UNCLAIMED
         description: Network controller
         product: PRO/Wireless 3945ABG [Golan] Network Connection
         vendor: Intel Corporation
         physical id: 0
         bus info: pci@0000:0c:00.0
         version: 02
         width: 32 bits
         clock: 33MHz
         capabilities: pm msi pciexpress bus_master cap_list
         configuration: latency=0
         resources: memory:f6cff000-f6cfffff
*-network UNCLAIMED
         description: Ethernet controller
         product: NetXtreme BCM5755M Gigabit Ethernet PCI Express
         vendor: Broadcom Corporation
         physical id: 0
         bus info: pci@0000:09:00.0
         version: 02
         width: 64 bits
         clock: 33MHz
         capabilities: pm vpd msi pciexpress bus_master cap_list
         configuration: latency=0
         resources: memory:f6bff000-f6bfffff

```
I expect that a driver has been shut down or written over somewhere, but I have no idea where to start to look for it.

---

### Post by dave133 on 2014-07-30
In addition, it seems that I cannot connect to the internet by cable either.  I should add that, to install the updates I installed last night, it was necessary for me to free up some disk space on /boot by getting rid of some of the old kernels.  However, I had no problems with my computer following the uninstallation.  I only had problems after I installed the updates and rebooted.

---

### Post by dave133 on 2014-07-30
I think I know what the problem may be, but I'm not sure how to fix it.

When I freed up disk space on /boot, I uninstalled some of the linux-image-extra files that were relevant to the kernel my system is using by mistake.  I have managed to move these files from /var/lib/dpkg/info back into /boot, but I'm not sure how to make them functional again.  Any help?

---

### Post by varunendra on 2014-07-31
Please post back the outputs of -
```
uname -mr
apt-get install --reinstall --print-uris linux-image-generic linux-headers-generic
modinfo iwl3945 tg3
```

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by dave133 on 2014-07-31
uname -mr returns: 
```

3.13.0-32generic x86_64

```

The apt-get install command returns:
```

The following packages were automatically installed and are no longer required:
      libglib2.0-0:i386  libgstreamer-plugins-base0.10-0:i386
      libgstreamer0.10-0:i386  liborc-0.4-0:i386  odbcinst  odbcinst1debian2  unixodbc
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
      linux-image-extra-3.13.0-32-generic
The following NEW packages will be installed:
      linux-image-extra-3.13.0-32-generic  linux-image-generic
0 upgraded, 2 newly installed, 1 reinstalled, 0 to remove and 14 not upgraded
Need to get 36.8 MB/36.8 MB of archives.
After this operation, 152 MB of additional disk space will be used.
Do you want to continue? [Y/n]

```

When I type "Y", I get:
```

'http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-32-generic_3.13.0-32.57_amd64.deb'  linux-image-extra-3.13.0-32-generic_3.13.0-32.57_amd64.deb 36775640 MD5Sum:fe9dd9951ad3b1b8de3d650bb33d4e8f
'http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.32.38_amd64.deb' linux-image-generic_3.13.0.32.38_amd64.deb 2496 MD5Sum:a2639b278fd9a674359ce303684ae0d7

```

When I type "modinfo iwl3945tg3, I get:
```

modinfo: ERROR: Module iwl3945 not found.
modinfo: ERROR: Module tg3 not found.

```

---

### Post by varunendra on 2014-07-31
How about reading the 'Code' tags part of my post also, then edit your above post to use them?

I was anticipating the modinfo error, so no surprises. It just confirms that your kernel is broken - badly.

Now please use the links that the apt-get command gave you -
[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-32-generic_3.13.0-32.57_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-image-extra-3.13.0-32-generic_3.13.0-32.57_amd64.deb)
and
[http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.32.38_amd64.deb](http://us.archive.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.13.0.32.38_amd64.deb)

..to download these two .deb packages on a computer with internet access.

Copy these two packages back to your Ubuntu system, in a new folder (say, "kernel") on your Desktop.
Then open a terminal, and run this command to install them -
```
sudo dpkg -i Desktop/kernel/*
```
(Make sure there are only those two .deb packages in the "kernel" folder on you Desktop.)

Then reboot, try to connect again, and let us know the result.

---

### Post by dave133 on 2014-07-31
Sorry about the formatting problem.  I'm kind of new to this, but I've fixed the formatting above so that the posts are readable.

That worked perfectly!  My wireless is back on, my wireless mouse is working, and the world is at peace again.

For future reference, if I need to free up /boot space in order to perform an update, I just need to make sure that I keep the "generic," "extra," and whatever other files fall under the version of my current working kernel, right?  Anything that does not pertain to the current kernel can go?

---

### Post by varunendra on 2014-07-31
Sorry if my previous post came across as rude, didn't intend to. Just wanted to make sure you know about 'Code' tags and try it. It's never necessary, but sometimes matters a lot especially with long outputs. People may not even bother to read posts which contain a lot of unformatted terminal outputs. So preserving the formatting enhances the chance of getting proper attention and help.

Anyway, glad to know everything is back to normal again. :)
> **dave133 said:**
> For future reference, if I need to free up /boot space in order to perform an update, I just need to make sure that I keep the "generic," "extra," and whatever other files fall under the version of my current working kernel, right?  Anything that does not pertain to the current kernel can go?

Yes, keeping everything that pertains to current kernel is important. But it is also recommended to keep at least one (the last working one) older kernel (and its parts) in case something goes wrong with the current kernel and you need an older one to get a working system to fix it.

**PS:**
Please mark the thread as [SOLVED] now that it is. It helps other by indicating that this thread contains a possible solution to the problem mentioned in the Title.

---

### Post by dave133 on 2014-07-31
Great.  Thanks for everything!

---

### Post by PurpleDiane on 2014-08-05
[removed by author]

---

### Post by PurpleDiane on 2014-08-05
[removed by author]
[sorry, can't figure out how to remove attachment]

---

### Post by Hadaka on 2014-08-05
Hi Diane
You have posted to a solved thread,while your problem of not being able to connect
may be somewhat like the thread you posted to, the wifi and ethernet cards are totally
different and require different drivers than your machine. Entering commands at kernel
level can cause huge problems when not for the intended machine, as can activating drivers
that are not correct for your machine. Here are the drivers to use for your system.

Ethernet (wired)  driver = e100e
Wireless (.wifi.)  driver = RTL8192EE

Your wired connection seems to be working,
here is a link to help you get your wireless going
[http://ubuntuforums.org/showthread.php?t=2190347&page=2](http://ubuntuforums.org/showthread.php?t=2190347&page=2)        posts#11 and 13

you might want to consider reloading 14.04 as this would delete and overwrite any
and all changes you have made by entering commands from random threads.

Please start a new thread if you need help with the wireless. Title it  ~cannot connect  RTL8192EE~

---

### Post by PurpleDiane on 2014-08-05
You are right. Sorry I wasn't thinking. 

I will give that post a try - after I reinstall Ubuntu. It's very new, so that's not a problem. And if I still have problems, I will start a new thread.

---

### Post by chmod7772 on 2015-08-03
I have this exact same problem on hand right now. How did you transfer the kernels over? My wifi isn't working and USB stick isnt being recognized.

---

### Post by zxmarce2 on 2015-11-08
Hi,

This 'bug' just hit me. I was on Kernel 3.13.0.66 and the update to .67 had partial success.
Only noticed it when the laptop restarted: Instead of 1366*768 I was on 1024*768 and all networking was gone :confused:.

On the desktop machine, searched for "*ubuntu 14.04 update wrong resolution no network*", and this thread came up amongst the links.

I did something different, though, and this may save another lost soul. I restarted the laptop that failed upgrades again, but this time I kept SHIFT pressed upon restart, after the BIOS screen. This led me to the GRUB menu. I selected the former "good" kernel (.66) from the 'Advanced' entry and the laptop started with no issues: Screen and Network worked OK as before.

So, once I had network back, I followed the steps outlined by **Varunendra** to complete the failed kernel upgrade and my laptop was again working top-notch after the subsequent restart, on the new Kernel 3.13.0.67.

I was tempted to remove the **--print-uris** option so the upgrade would go all the way through, but I did not and followed the described route. I bet that it would have succeeded anyway.

Just my two cents.

zxMarce2.

---

