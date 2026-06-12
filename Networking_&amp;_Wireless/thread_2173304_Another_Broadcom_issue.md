---
title: "Another Broadcom issue"
date: 2013-09-09
forum: Networking &amp; Wireless
---

### Post by adam14 on 2013-09-09
Hi there,

I have been at this for over 10 hours now, trying to get wireless to work, I think I have gone thru all the forum solutions and nothing is working... 

here is my card specks

Network controller [0280]: Broadcom Corporation BCM4321 802.11a/b/g/n [14e4:4328] (rev 05)

I have the wireless tab showing in network, but no networks are showing :(

I am using the latest LTS 12.4 and I am comletely at a lost so I am hoping someone with a bit of experience can help me out... I am a total noob, just installed today. The sad thing is that it all went perfectly, apart from the wireless setup... it's almost making me quit infrustration and try another distro but I will give it one more try.

From the amount of support requests out there concerning Broadcom cards, maybe there is a bug somewhere?

Anyway TIA for any help you can give!

---

### Post by carl4926 on 2013-09-09
Support may be limited with b43 so try wl (make sure you are fully updated)

do

```
sudo apt-get install [COLOR=#000000][FONT=Droid Sans]bcmwl-kernel-source[/FONT][/COLOR]
```then reboot

---

### Post by adam14 on 2013-09-09
> **carl4926 said:**
> Support may be limited with b43 so try wl (make sure you are fully updated)

do

```
sudo apt-get install [COLOR=#000000][FONT=Droid Sans]bcmwl-kernel-source[/FONT][/COLOR]
```then reboot

Hello Carl, thank you for your response, done this before didn't work, but I will try it again the thing is that I always get a fatal error when installing the bcmwl:

```

adam@adam-iMac:~$ sudo apt-get install bcmwl-kernel-source
[sudo] password for adam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  diffstat quilt module-assistant
Use 'apt-get autoremove' to remove them.
The following NEW packages will be installed:
  bcmwl-kernel-source
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/1,344 kB of archives.
After this operation, 4,274 kB of additional disk space will be used.
Selecting previously unselected package bcmwl-kernel-source.
(Reading database ... 195895 files and directories currently installed.)
Unpacking bcmwl-kernel-source (from .../bcmwl-kernel-source_6.20.155.1+bdcom-0ubuntu0.0.1_amd64.deb) ...
Setting up bcmwl-kernel-source (6.20.155.1+bdcom-0ubuntu0.0.1) ...
Removing old bcmwl-6.20.155.1+bdcom DKMS files...


------------------------------
Deleting module version: 6.20.155.1+bdcom
completely from the DKMS tree.
------------------------------
Done.
Loading new bcmwl-6.20.155.1+bdcom DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-30-generic
Building for architecture x86_64
Building initial module for 3.8.0-30-generic
Error! Bad return status for module build on kernel: 3.8.0-30-generic (x86_64)
Consult /var/lib/dkms/bcmwl/6.20.155.1+bdcom/build/make.log for more information.
FATAL: Module wl not found.
update-initramfs: deferring update (trigger activated)
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-3.8.0-30-generic

```

Any Ideas?

Thanks

---

### Post by carl4926 on 2013-09-09
You could try b43
Let me message you

---

### Post by wildmanne39 on 2013-09-09
For the benefit of everyone please use the forum for solving issues and not pm's.
Thanks

---

### Post by varunendra on 2013-09-09
The default version of the bcmwl-kernel-source seems to have gotten some bug recently that causes it to fail to compile. My usual reference in this case has been to try an older version directly downloaded from broadcom's site > patch it with some patches I know and understand > compile > install.

However, one user recently posted a link to a newer version that installed smoothly on his system (with kernel 3.8.0-29, 64 bit). So I would suggest to try the same package before trying anything else -
[https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504](https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504)

Download the .deb package from above link, and double-click to install (while being connected to internet via cable, so that dependencies can be installed if there are any).

Please let us all know how it goes. Thanks !

---

### Post by adam14 on 2013-09-09
> **Wild Man said:**
> For the benefit of everyone please use the forum for solving issues and not pm's.
Thanks

Carl just gave me a link to a b43 dir to download and try, unfortunately it did't work anyway :(

> [COLOR=#000000]varunendra[/COLOR][COLOR=#000000][INDENT]**Re: Another Broadcom issue**
The default version of the bcmwl-kernel-source seems to have gotten some bug recently that causes it to fail to compile. My usual reference in this case has been to try an older version directly downloaded from broadcom's site > patch it with some patches I know and understand > compile > install.

However, one user recently posted a link to a newer version that installed smoothly on his system (with kernel 3.8.0-29, 64 bit). So I would suggest to try the same package before trying anything else -
[https://launchpad.net/ubuntu/+source...+build/4761504]("https://launchpad.net/ubuntu/+source/bcmwl/6.30.223.30+bdcom-0ubuntu3/+build/4761504")

Download the .deb package from above link, and double-click to install (while being connected to internet via cable, so that dependencies can be installed if there are any).

Please let us all know how it goes. Thanks ![/INDENT][/COLOR]


Nope no change, it seemed to install ok, but still not detecting any wireless networks! From time to time I am also getting this error:

> Crash Report
Sorry a problem occurred while installing software.

Package: bcmwl-kernel-source

lots of details but I guess the main one is:

bcmwl kernel module failed to build


Thanks for the help guys I really appreciate it. apart from the wireless issue, everything else is working perfectly so far.

---

### Post by adam14 on 2013-09-09
Guys a breakthrough!

In a last act of desperation I tried the "connect to hidden wireless network" option and added the name of my wireless network and password... and damn me it worked! After it connected it started picking up available wireless networks as well! So it is almost like this bumped it into action. It may have been the second boot after Varunendra's fix that could have done it, not sure... but anyway it is working now. thanks!

---

### Post by varunendra on 2013-09-09
Great ! And thanks for the feedback ! :)

I believe saving the network SSID and security key to NM helps in this case, so the key to success should be that one. But "failed to build" errors mean either there are still remnants of previous failed attempts with bcmwl-kernel-source, or even the last one I porposed also failed.

To fix that, you may try to completely purge the package(s) and retry with the one I linked to in my previous post -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get clean
sudo apt-get autoremove
```
Then reinstall the downloaded .deb package for latest bcmwl module.

Obviously, none of above is necessary if everything is working now. :P

---

### Post by carl4926 on 2013-09-09
> **varunendra said:**
> Great ! And thanks for the feedback ! :)

I believe saving the network SSID and security key to NM helps in this case, so the key to success should be that one. But "failed to build" errors mean either there are still remnants of previous failed attempts with bcmwl-kernel-source, or even the last one I porposed also failed.

To fix that, you may try to completely purge the package(s) and retry with the one I linked to in my previous post -
```
sudo apt-get purge bcmwl-kernel-source
sudo apt-get clean
sudo apt-get autoremove
```
Then reinstall the downloaded .deb package for latest bcmwl module.

Obviously, none of above is necessary if everything is working now. :P

Don't reinstall bcmwl
Because we just need to establish if you are using b43 firmware that I sent you privately
Let us see
```
lspci -nnk | grep -iA2 net
```

---

