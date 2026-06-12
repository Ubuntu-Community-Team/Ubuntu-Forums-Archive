---
title: "Not checking for errors at boot."
date: 2011-05-28
forum: New to Ubuntu
---

### Post by djmac on 2011-05-28
Hi all,

After I upgraded my desktop to 11.04, I started receiving this message everytime I ssh'd in:

```
*** /dev/sdb1 will be checked for errors at next reboot ***
*** /dev/sdc1 will be checked for errors at next reboot ***
*** /dev/sdd1 will be checked for errors at next reboot ***
*
```

Unfortunately, it doesn't seem to check for errors at the boot. I have rebooted it many times since it first started (a couple of weeks back), with the hope that over time the problem would somehow rectify itself. It hasn't (and I guess usually doesn't!).

Thanks in advance.

---

### Post by wildmanne39 on 2011-05-28
> **djmac said:**
> Hi all,

After I upgraded my desktop to 11.04, I started receiving this message everytime I ssh'd in:

```
*** /dev/sdb1 will be checked for errors at next reboot ***
*** /dev/sdc1 will be checked for errors at next reboot ***
*** /dev/sdd1 will be checked for errors at next reboot ***
*
```

Unfortunately, it doesn't seem to check for errors at the boot. I have rebooted it many times since it first started (a couple of weeks back), with the hope that over time the problem would somehow rectify itself. It hasn't (and I guess usually doesn't!).

Thanks in advance.
Hi, I do not know why you are getting that message but ubuntu checks for errors every 30 boot ups.

---

### Post by djmac on 2011-05-28
Right, can you manually force it to? I guess that it is not that big an issue. Just wait until the 30th boot up?

---

### Post by wildmanne39 on 2011-05-28
> **djmac said:**
> Right, can you manually force it to? I guess that it is not that big an issue. Just wait until the 30th boot up?

Hi, you can run this command from the terminal to check your desk. I do not know how to make it check at start up. 
```
sudo badblocks /dev/sda1
```That is if your ubuntu is on /sda1 other wise you would make it /sda plus the number that your ubunt partiton is on.

---

### Post by dcsoldschool53 on 2011-05-28
Try this command```
sudo touch /forcefsck
```to check the filesystem  for errors on your next boot up.

---

### Post by djmac on 2011-05-29
Thanks,

I tried:

```
sudo touch /forcefsck
```

And rebooted, but it didn't do any checks at boot (also get the same message when ssh'ing in).

Also tried:

```
sudo badblocks -v /dev/sda1
```

(Would perhaps recommend adding verbosity just so you know what is happening - it took a long time)

But I also still got the same message - is the problem actually an issue?

---

### Post by i_r_tomash on 2011-05-30
ive came across the same behvior,on 11.04 while opening bybou 
i tried out sudo badblocks /-v dev/sda1 and fsck -y /dev/sda1 which didn't work
did you succeed in fixing it,

---

### Post by Zerauskire on 2011-06-21
I have the same problem. Anyone ever find a fix for this?

This is just one of the many problems I had updating to Natty but this seems to be the only one I have yet to get around or fix.

---

### Post by Zerauskire on 2011-06-21
Fixed my own problem. Posting in case others come across this thread they can try for themselves. Hope it helps someone.

I was getting:
> *** /dev/sdb will be checked for errors at next reboot ***

All I had to do to fix this was edit my fstab file.
> sudo vi /etc/fastab

Then for me I changed the last "0" (zero) to a 2 at the end of the line mounting my HDD.

Before:
> /dev/sdb   /mnt/hdd1   ext3   defaults   0   0

After:
> /dev/sdb   /mnt/hdd1   ext3   defaults   0   2

Then when you reboot your PC it will check that harddrive for errors. After it completes this check you can just go back and edit your fstab file and put the 2 back to a 0. 

Now from then on you shouldn't get that error.

---

### Post by jmpurser on 2011-07-27
I checked the 6th field of my fstab file for the /dev/sda1 and /dev/sda2 (the ones the message referenced) and found it was already set to "2".  I changed them to zero, rebooted, and no change.  I changed them back to "2", entered "sudo touch /forcefsck" and did a hard shutdown.  When I turned the machine back on the messages were gone.

I'd done most of this before, but hadn't edited my fstab file or done a hard reboot.  I don't KNOW what made the difference this time so I'm posting every step and hoping something in there helps.

John

---

### Post by Em0ry42 on 2012-04-06
```
sudo touch /forcefsck
sudo shutdown -h now
```

Fired it back up and did the trick for me.  Thanks!!!
:guitar:

---

### Post by LHammonds on 2012-08-27
I am also getting this message on a test server I rarely touch and really isn't doing anything:
```

*** /dev/sda1 will be checked for errors at next reboot *** 

```This is what kind of (virtual) machine I am running:

** root@srv-ubuntu:/# lsb_release -a**
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04 LTS
Release:        12.04
Codename:       precise

```

**root@srv-ubuntu:/# uname -a**
> 
Linux srv-ubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
I rebooted the server but that did nothing.  I then shutdown and powered off the server which also did nothing.

FYI - I logged in with my normal account and then typed "sudo su" to temporarily grant root access so I don't need to type "sudo" in front of each command.

To avoid any issues working on a mounted file system, I unmounted it by typing the following command:
```
umount /boot
```I ran the badblocks program and these are the results:

**root@srv-ubuntu:/# badblocks -v /dev/sda1**
```

Checking blocks 0 to 194559
Checking for bad blocks (read-only test): done                                  
Pass completed, 0 bad blocks found. (0/0/0 errors)

```I then ran fsck and these are the results:

**root@srv-ubuntu:/# fsck -y /dev/sda1**
```

fsck from util-linux 2.20.1
e2fsck 1.42 (29-Nov-2011)
boot: clean, 250/97344 files, 129479/194560 blocks

```Looking in the /etc/fstab, this is what I found (field 6, the fs_passno field, is set to 2 which is like most others which are checked by fsck after the root system):
> 
UUID=80f1b3c5-8e44-4bfa-9f86-290a681ae3e1 /boot           ext2    defaults        0       2
I then tried to force another check at boot by typing the following:

```

touch /forcefsck
shutdown -h now

```The error message still persists upon login.

I modified /etc/fstab to the following (which tells fsck the drive does not need to be checked):
> 
UUID=80f1b3c5-8e44-4bfa-9f86-290a681ae3e1 /boot           ext2    defaults        0       0
I then tried another force check, shutdown and startup.

```

touch /forcefsck
shutdown -h now

```The error message still persists upon login.

I then removed the message-of-the-day file and rebooted to see if it re-created it.

```

mv /var/run/motd /var/run/motd.old
shutdown -r now

```The error message still persists upon login.

As a last ditch effort, I noticed there are 35 updates that want to be applied:

 **root@srv-ubuntu:/# aptitude safe-upgrade**
```

The following packages will be REMOVED:
  linux-headers-3.2.0-27{u} linux-headers-3.2.0-27-generic{u}
The following packages will be upgraded:
  accountsservice apport base-files fontconfig fontconfig-config
  initscripts language-pack-en language-pack-en-base libaccountsservice0
  libcups2 libfontconfig1 libgl1-mesa-dri libgl1-mesa-glx libglapi-mesa
  libglu1-mesa libldap-2.4-2 libperl5.14 libpython2.7 libsqlite3-0 libudev0
  perl perl-base perl-modules python-apport python-problem-report
  python-software-properties python2.7 python2.7-minimal resolvconf sysv-rc
  sysvinit-utils tzdata udev update-manager-core update-notifier-common
The following packages are RECOMMENDED but will NOT be installed:
  firefox-locale-en
35 packages upgraded, 0 newly installed, 2 to remove and 0 not upgraded.
Need to get 21.9 MB of archives. After unpacking 68.3 MB will be freed.

```After the reboot, my system info now looks like this:

** root@srv-ubuntu:/# lsb_release -a**
```

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:        12.04
Codename:       precise

```**root@srv-ubuntu:/# uname -a**
> 
Linux srv-ubuntu 3.2.0-29-generic #46-Ubuntu SMP Fri Jul 27 17:03:23 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
The error message has now gone away.

---

