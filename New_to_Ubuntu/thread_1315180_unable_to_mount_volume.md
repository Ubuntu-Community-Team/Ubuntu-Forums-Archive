---
title: "unable to mount volume"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by abhilash1989 on 2009-11-05
Hi....I was using WinXp n Ubuntu ultimate 1.8 paralelly...Now when i tried to boot windows it is admitting a problem n asking to boot into a safe mode...i tried to boot into safe mode but even then the same problem repeated..so i restarted the system n booted into ubuntu..i knew i didnt shutdown windows properly..n now im unable to access the drives in ubuntu..i dont have a copy of win to format it..so is there any solution to access my drives in ubuntu..
The following message is being displayed : 

--------------------------

$LogFile indicates unclean shutdown (0,1) Failed to mount '/dev/sda5': Operation not supported Mount is denied because NTFS is marked to be in use. Choose one action:

Choice 1: If you have windows then disconnect the external devices (etc etc)

Choice 2: If you dont have Windows then use the 'force' option for your own responsibility by using: mount -t ntfs-3g /dev/sda5 /media/disk -o force

Or add the option to the relevant row in the /etc/fstab file: /dev/sda5/media/disk ntfs -3g force 0 0

---------------------
i tried to type the choice 2 option in terminal.... but it says ONLY ROOT CAN DO THAT..

SO what should i do...
THNX for all suggesstions

---

### Post by nothingspecial on 2009-11-05
Put sudo before it.

Another thing to try.

```
sudo apt-get install ntfsprogs
```

After it`s installed

```
sudo ntfsfix /dev/sda5
```

---

### Post by abhilash1989 on 2009-11-05
This is the reply given if i put sudo 

abhi@abhi-desktop:~$ sudo mount -t ntfs-3g /dev/sda5 /media/disk -o force
$LogFile indicates unclean shutdown (0, 1)
WARNING: Forced mount, reset $LogFile.
fuse: failed to access mountpoint /media/disk: No such file or directory

Please any1 reply...Im in very much need of a solution

---

### Post by nothingspecial on 2009-11-05
I thought I just did?????

---

### Post by abhilash1989 on 2009-11-05
When i tried the other option this is the reply given

abhi@abhi-desktop:~$ sudo apt-get install ntfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package ntfsprogs is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package ntfsprogs has no installation candidate

---

### Post by nothingspecial on 2009-11-05
Have you updated since you installed?

```
sudo apt-get update && sudo apt-get install ntfsprogs
```

---

### Post by abhilash1989 on 2009-11-05
Thank u very much...i got it...
Thank u

---

### Post by nothingspecial on 2009-11-05
Yay :p

---

### Post by ndefontenay on 2009-11-05
And the disk is mounted?
Just as a genral info: If you plug a usb drive or hard shutdown windows, there's some kind of flag on the ntfs file system which is not properly reset. When you go to ubuntu you will find out that it things the disk is still being use even though it's not.

The obvious solution would be to get back to windows and perform a clean removal of your usb drive and a clean shutdown of your harddisk.

When that fails ntfsprogs can help for sure.

Nico

---

