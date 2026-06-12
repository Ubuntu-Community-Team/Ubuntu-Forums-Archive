---
title: "Error booting  Ubutnu 9.10 - &quot;Mount of filesystem failed...&quot;"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by LinuxN00bTM on 2010-02-16
hello Guys im dual booting windows 7 with ubuntu 9.10
today while i choose to boot with ubuntu option the os started normally untill i got an error code
```
Mount of filesystem failed. a8d932-6c28-4c09-8b0e-23a20e8c5a9d
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@server-desktop:"#
```
and as the titile of the forums says [Absolute  Beginner Talk]("http://georgia.ubuntuforums.org/forumdisplay.php?f=326") im an absolute beginner

i have heard that fsck command nothing changes
for example it looks like something like this
ubuntu login#:fsck i press enter i get
ubuntu login#:
so basiclly nothing is changing

---

### Post by skatinjj on 2010-02-16
> **LinuxN00bTM said:**
> hello Guys im dual booting windows 7 with ubuntu 9.10
today while i choose to boot with ubuntu option the os started normally untill i got an error code
```
Mount of filesystem failed. a8d932-6c28-4c09-8b0e-23a20e8c5a9d
A maintenance shell will now be started.
CONTROL-D will terminate this shell and retry.
root@server-desktop:"#
```
and as the titile of the forums says [Absolute  Beginner Talk]("http://georgia.ubuntuforums.org/forumdisplay.php?f=326") im an absolute beginner

i have heard that fsck command nothing changes
for example it looks like something like this
ubuntu login#:fsck i press enter i get
ubuntu login#:
so basiclly nothing is changing


With the command "fsck", you need to specify the device you want to run a check on:

```
fsck -y /dev/sda
```

If you have one hard drive in your computer, that should run "fsck" and fix errors with the file system.

---

### Post by LinuxN00bTM on 2010-02-16
> **skatinjj said:**
> With the command "fsck", you need to specify the device you want to run a check on:

```
fsck -y /dev/sda
```If you have one hard drive in your computer, that should run "fsck" and fix errors with the file system.
thank you skatinjj it worked

---

### Post by atari130xe on 2010-02-17
> **LinuxN00bTM said:**
> thank you skatinjj it worked

Hello Guys, This annoying problem is happening to my friends computer, I have changed hes HD (a new one is 320GB capacity UltraATA) after installing Linux Mint 8 Helena (ubuntu 9.10) the system works great till the computer is turned off. Once its turned on again, the problem appears again. Anyone has an idea what exactly is the issue? Hardware? File system?, my friend is a newbie and he is starting to dissapoint about Linux. I have Ubuntu karmic on my box but I have no issues. Any "permanent" fix for the problem?
Does it happen with other Ubuntu versions?
Thanks!

---

### Post by skatinjj on 2010-02-19
> **atari130xe said:**
> Hello Guys, This annoying problem is happening to my friends computer, I have changed hes HD (a new one is 320GB capacity UltraATA) after installing Linux Mint 8 Helena (ubuntu 9.10) the system works great till the computer is turned off. Once its turned on again, the problem appears again. Anyone has an idea what exactly is the issue? Hardware? File system?, my friend is a newbie and he is starting to dissapoint about Linux. I have Ubuntu karmic on my box but I have no issues. Any "permanent" fix for the problem?
Does it happen with other Ubuntu versions?
Thanks!

Did you run a hard drive test on the replacement hard drive to make sure it is working properly(even new hard drives can fail out of the box)?  I would first see if the BIOS has an option to test the hard drive.

Also, what is the specs for the computer?

If you need more information on how to go about testing the hard drive, let me know the name of the manufacturer for the hard drive and I can list a few ways to test it.

---

