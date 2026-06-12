---
title: "[SOLVED] ndiswrapper install problem"
date: 2008-10-28
forum: Networking &amp; Wireless
---

### Post by RootExposure on 2008-10-28
Hello everyone,

very new to linux.  I'm sure this question has been answered but I have spent a few days searching over the forums and can't seem to track down the answer.  Recently installed Ubuntu Studio 8.04.  Trying to install newer version of ndiswrapper to get my linksys wireless card working (following this [guide]("http://ubuntuforums.org/showthread.php?t=225206")).  When I run the sudo make install command.  I get this error

Makefile:34: *** Cannot find kernel version in /lib/modules/2.6.24-19-rt/build, is it configured?. Stop

Any help you can provide will be appreciated.  Let me know if you need more info on the issue

Thanks Everyone

---

### Post by Ayuthia on 2008-10-28
You might try installing ndiswrapper from the install CD using the Terminal:
```
sudo apt-cdrom add
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```Or if you know how to add the cd from Synaptic, you can do it from there also (I think to manage the repositories it is Settings->Repositories)

As for your current issue (if you still want to compile), you might want to check and see what is out there for /lib/modules and see if there is one for your current kernel:
```
ls /lib/modules
ls /usr/src
uname -r
```
Make sure that there is a directory in /lib/modules that matches the results of uname -r (that is your current kernel version).  You will also want to make sure that you have the linux-headers that matches the kernel version also.

---

### Post by RootExposure on 2008-10-29
Thanks for the response.
First off I decided to not use ndiswrapper.  I found a Broadcom driver that works with this linksys card ([thread]("http://ubuntuforums.org/showthread.php?t=847226&highlight=wusb54gsc+chipset")) and figured that would be better than using the wrapper.  Unfortunately while trying to do that I am having the same error.

uname -r   2.6.24-19-rt
I checked the /lib/modules/ directory.  There are two directories within that: 2.6.24-19-rt and 2.6.24-19-generic.  There is Build folder (a linked folder to /usr/src/linux-headers-2.6.24-19-generic) in the 2.6.24-19-generic directory but not in the rt folder.

In /usr/src/ there is a linux-headers-2.6.24-19-generic directory and a linux-headers-2.6.24-19 directory.

---

### Post by RootExposure on 2008-10-29
So I decided (since I haven't really done much since installing) just to do a fresh install, this time with my wired NIC plugged in (got to love 50ft cables). Completely removed and deleted linux partitions from XP (I have a dual boot system, obviously had to fun fixboot and fixmbr).

After install ran update mananger.  It installed 160 updates (including an updated kernel: 2.6.24-21-rt) and I restarted.  Loaded the 2.6.24-21-rt kernel at boot.  I opened up Synaptics and it looks like linux-headers are installed for a bunch of the kernels (including 2.6.24-21-rt and 2.6.24-19-rt).  Also checked for build-essentials, which was also installed by default.

Tried to run the install of the broadcom driver and ran into the same problem as before (obviously the error had 2.6.24-21-rt instead of 2.6.24-19-rt) when running the make command.

Should the linked Build folder in /lib/modules/2.6.24-21-rt/ folder be created during the linux-headers install?  Should I try removing the linux-headers and reinstalling through synaptics.

---

### Post by Ayuthia on 2008-10-29
> **RootExposure said:**
> Thanks for the response.
First off I decided to not use ndiswrapper.  I found a Broadcom driver that works with this linksys card ([thread]("http://ubuntuforums.org/showthread.php?t=847226&highlight=wusb54gsc+chipset")) and figured that would be better than using the wrapper.  Unfortunately while trying to do that I am having the same error.

uname -r   2.6.24-19-rt
I checked the /lib/modules/ directory.  There are two directories within that: 2.6.24-19-rt and 2.6.24-19-generic.  There is Build folder (a linked folder to /usr/src/2.6.24-19-generic) in the 2.6.24-19-generic directory but not in the rt folder.

In /usr/src/ there is a 2.6.24-19-generic directory and a 2.6.24-19 directory.
It looks like you are missing the linux-headers-2.6.24-19-rt.  You will need to install that first.

---

### Post by RootExposure on 2008-10-29
Thanks again, must have been posting at the same time.  I guess I should have put all the information in one post

---

### Post by Ayuthia on 2008-10-29
> **RootExposure said:**
> So I decided (since I haven't really done much since installing) just to do a fresh install, this time with my wired NIC plugged in (got to love 50ft cables). Completely removed and deleted linux partitions from XP (I have a dual boot system, obviously had to fun fixboot and fixmbr).

After install ran update mananger.  It installed 160 updates (including an updated kernel: 2.6.24-21-rt) and I restarted.  Loaded the 2.6.24-21-rt kernel at boot.  I opened up Synaptics and it looks like linux-headers are installed for a bunch of the kernels (including 2.6.24-21-rt and 2.6.24-19-rt).  Also checked for build-essentials, which was also installed by default.

Tried to run the install of the broadcom driver and ran into the same problem as before (obviously the error had 2.6.24-21-rt instead of 2.6.24-19-rt) when running the make command.

Should the linked Build folder in /lib/modules/2.6.24-21-rt/ folder be created during the linux-headers install?  Should I try removing the linux-headers and reinstalling through synaptics.

I would thinnk that the link would be made automatically when linux-headers was installed.  If it isn't, you should be able to create one:
```
sudo ln -s /usr/src/linux-headers-2.6.24-21-rt /lib/modules/2.6.24-21-rt/build
```

---

### Post by RootExposure on 2008-10-29
Thanks, I was playing around with that before I reinstalled everything, but I never really fully tested it.  I will try it on the new kernel when I get home and let you know how it worked out.

---

### Post by RootExposure on 2008-10-29
Ok so apparently I don't pay attention.  I figured I would double check before running the command.... turns out the linux-headers weren't installed for the rt kernel after all.  I looked twice after the reload and once before the reload and I could have sworn they were installed.  Apparently that was the problem all along.

Thanks for hanging in there with a newbie.

---

