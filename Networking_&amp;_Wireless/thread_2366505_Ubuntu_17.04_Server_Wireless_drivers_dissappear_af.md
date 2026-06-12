---
title: "Ubuntu 17.04 Server: Wireless drivers dissappear after a restart."
date: 2017-07-18
forum: Networking &amp; Wireless
---

### Post by oneindelijk on 2017-07-18
Dear People, 

I want to use my freshly installed server to make a bridge between a wifi hotspot and my own network.
The driver I need to use is the iwl4965

Under normal circumstances (read: never) I would have to install the linux-kernel-image and linux-kernel-image-extra
However they are not in the repos (version: 4.4.0-21-generic)

So I installed the .deb packages after which ```
modprobe iwl4965
```succesfully loads the driver.

After a reboot I have to do it all over again...
(Reinstall the .deb files and load the driver)

---

### Post by Hadaka on 2017-07-18
Hi, to load the driver on boot or  startup, open a terminal..ctrl/alt/t
then Copy and paste..
```
echo 'iwl4965' | sudo tee -a /etc/modules
```
*What it does...
   cat /etc/modules
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

---

### Post by oneindelijk on 2017-07-20
> **Hadaka said:**
> Hi, to load the driver on boot or  startup, 

Sorry, I forgot to mention that
the drivers are GONE after a reboot,
meaning the whole directory `wireless `under [COLOR=#303336][FONT=inherit] [/FONT][/COLOR][FONT=inherit][COLOR=#858c93]/lib/modules/--my-kernel-version--/kernel/net
is gone after a reboot.
```
dpkg -i <linux-image & linux-image-extra>
```
brings it back[/COLOR][/FONT]

---

### Post by wildmanne39 on 2017-07-20
> **oneindelijk said:**
> Did you even read my post ?
The drivers are GONE after a reboot
No need to be snippy and he gave you the command that should add the module so it will load on boot, then the command to look into the file to make sure it is there.

---

### Post by jeremy31 on 2017-07-20
Is Ubuntu installed on a hard drive or are you running it from USB or DVD?

---

### Post by oneindelijk on 2017-07-21
> **wildmanne39 said:**
> No need to be snippy and he gave you the command that should add the module so it will load on boot, then the command to look into the file to make sure it is there.

I know, I'm sorry, I apologize

---

### Post by oneindelijk on 2017-07-21
> **jeremy31 said:**
> Is Ubuntu installed on a hard drive or are you running it from USB or DVD?

Ubuntu is indeed installed on the hard drive

---

### Post by jeremy31 on 2017-07-21
So after a reboot the modprobe iwl4965 returns module not found.  If you install updates using ```
 sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```
Do you have a different kernel after reboot?

---

### Post by oneindelijk on 2017-07-21
> **jeremy31 said:**
> So after a reboot the modprobe iwl4965 returns module not found.  If you install updates using ```
 sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```
Do you have a different kernel after reboot?

I'm not getting a different kernel after a reboot (which would suprise me, the ISO I had downloaded to install the server was the latest release, less than two months ago.
I keep on getting this weird message of apt telling me it needs to download 0 B/151 kB (EDIT: I just found out this comes from libjs-jquery, which will download when the apt cache is cleared, but it won't install)
(might be related to my broken nfs-kernel-server: [https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1590799](https://bugs.launchpad.net/ubuntu/+source/nfs-utils/+bug/1590799) ; although a fix was released in march, I'm still experiencing this error)

Maybe all these errors are the result of a broken apt system ?
(I've already emptied the cache, which has solved some other issues)

---

### Post by oneindelijk on 2017-07-21
> **jeremy31 said:**
> So after a reboot the modprobe iwl4965 returns module not found.  If you install updates using ```
 sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```
Do you have a different kernel after reboot?

These [FONT=monospace][COLOR=#333333]packages are reported to be installed:[/COLOR][/FONT]
linux-image-extra-4.10.0-28-generic

They don't match my release:
```
uname -r
4.4.0-21-generic

```

---

### Post by oneindelijk on 2017-07-22
I was wondering about these releases. 
A installation of a Ubuntu Desktop 16.10 is still on the same disk as the Ubuntu Server 17.04.
Ther kernel version of the Ubuntu Desktop 16.10 is 4.10.something, 
while the server version of 17.04 seems to be only at 4.4.0
Is this just due to the server versions being a tad more conservative or is this an issue I should look into ?

---

