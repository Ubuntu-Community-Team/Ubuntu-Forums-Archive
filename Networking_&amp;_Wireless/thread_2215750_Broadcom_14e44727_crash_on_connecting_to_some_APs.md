---
title: "Broadcom 14e4:4727 crash on connecting to some APs"
date: 2014-04-08
forum: Networking &amp; Wireless
---

### Post by gregg128 on 2014-04-08
I can't connect to some APs with my Broadcom 4313. See dmesg output here:[ATTACH]251824[/ATTACH]

#cat /etc/issue
Ubuntu 13.10

#lshw -class network|grep driver
driver=wl0 driverversion=6.30.223.141 (r415941)

#uname
3.11.0-19-generic #33-Ubuntu SMP Tue Mar 11 18:48:34 UTC 2014 x86_64

#dpkg -l |grep nonfree
ii  linux-firmware-nonfree                            1.14ubuntu1

What is going on with my card ? Any help ? 
Thank you!

---

### Post by varunendra on 2014-04-10
Please try -
```
sudo apt-get purge bcmwl-kernel-source
```
Then reboot and see if the wireless works. If not, please follow the "Wireless Script" link in my signature, download and run the script as per instructions there, and post back the report it generates.

While posting the outputs, please use '**Code**' tags. It preserves the output's formatting and makes the post cleaner, compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Using Code Tags" link in my signature.

---

### Post by Rob Sayer on 2014-04-21
I've had a similar problem with my netbook running lubuntu 13.10 with the same Broadcom adapter (4313, PCI ID 4727) in 13.10.  I needed a backport.

This worked for me ...

[http://ubuntuforums.org/showthread.php?t=2191126&page=2&p=12889620#post12889620](http://ubuntuforums.org/showthread.php?t=2191126&page=2&p=12889620#post12889620)

... although having to recompile/build the driver module every time the kernel is updated is a wee bit of a pain.  I didn't have to recompile backported modules in previous ubuntu versions, though I must say it's working better than ever.

Since it's a 3.12.something backport and ubuntu 14.04 has a newer kernel, the latter should work better than 13.10.  In theory anyway.  I downloaded the lubuntu 14.04 iso and burned it to USB stick but haven't installed it yet.  Still checking out potential problems.

I saw one problem with the broadcom 4313 on askubuntu and someone recommended yanking bcmwl-kernel-source and activating brcmsmac, which is the open source driver.  The OP said that worked so it looks promising to me at this point.

bcmwl-kernel-source is what gets installed in settings -> additional drivers.  Unfortunately one thing I don't like about ubuntu (though there's absolutely nothing else I'd recommend to a linux newbie) is that additional drivers is not necessarily the best option.  It looks like the obvious way to go for novices but sometimes it doesn't work.  This is one of those times.

---

