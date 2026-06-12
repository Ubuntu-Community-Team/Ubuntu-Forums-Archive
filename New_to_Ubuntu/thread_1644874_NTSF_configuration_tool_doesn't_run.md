---
title: "NTSF configuration tool doesn't run"
date: 2010-12-13
forum: New to Ubuntu
---

### Post by eggwardo on 2010-12-13
Hi 
I'm trying to run NTFS configuration tool to mount my NTFS partition permanently.  
I install it, run it, it asks for my password, i put it in (correctly), and then nothing happens.

Is there another program i can use to do this?  I've seen reference to NTFS-3g but can't find it in the repository.

Or does anyone know why config tool wouldn't be opening??

thanks in advance

---

### Post by cariboo on 2010-12-14
Have a look [here]("https://help.ubuntu.com/community/MountingWindowsPartitions") for help mounting your NTFS partition at boot.

---

### Post by amjjawad on 2010-12-14
Or: [http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by Mark Phelps on 2010-12-14
If the NTFS partition you intend to mount is an OS partition containing Vista or Win7, I would advise strongly AGAINST mounting it -- unless you mount it read-only.

Mounting a Vista or Win7 OS partition read-write is asking for trouble.  One unclean shutdown or journal error and the whole partition is then unbootable.  And since you then can't boot into Vista or Win7 to run chkdsk to fix it, you're hosed.

---

### Post by coffeecat on 2010-12-14
> **Mark Phelps said:**
> If the NTFS partition you intend to mount is an OS partition containing Vista or Win7, I would advise strongly AGAINST mounting it -- unless you mount it read-only.

Mounting a Vista or Win7 OS partition read-write is asking for trouble.  One unclean shutdown or journal error and the whole partition is then unbootable.  And since you then can't boot into Vista or Win7 to run chkdsk to fix it, you're hosed.

Agreed 100%.

@eggwardo, are you running Maverick/10.10? I believe there is an issue with ntfs-config in Maverick that prevents it running, but there's a simple fix. Something to do with python if I remember correctly. Much as I dislike helping getting ntfs-config to run (it can do very silly things and you are better in the long run learning how to edit /etc/fstab) so that we can see what the problem is, open a terminal and:

```
gksudo ntfs-config
```Post any error messages you get.

---

### Post by Acimer on 2011-03-05
sorry for hijacking but I have the same issue as OP.

> 
@eggwardo, are you running Maverick/10.10? I believe there is an issue with ntfs-config in Maverick that prevents it running, but there's a simple fix. Something to do with python if I remember correctly. Much as I dislike helping getting ntfs-config to run (it can do very silly things and you are better in the long run learning how to edit /etc/fstab) so that we can see what the problem is, open a terminal and:

```
gksudo ntfs-config
```Post any error messages you get.

 i am running maverick and have the same issue: NTFS Config does not load after password

the output is

```
gksudo ntfs-config
Traceback (most recent call last):  File "/usr/bin/ntfs-config", line 102, in <module>
    main(args, opts)
  File "/usr/bin/ntfs-config", line 75, in main
    app = NtfsConfig()
  File "/usr/lib/pymodules/python2.6/NtfsConfig/NtfsConfig.py", line 56, in __init__
    os.mkdir(HAL_CONFIG_DIR)
OSError: [Errno 2] No such file or directory: '/etc/hal/fdi/policy'

```

I'm trying to make my win7 partition automount on startup. What am i doing wrong? Thanks for help

---

### Post by coffeecat on 2011-03-05
> **Acimer said:**
> I'm trying to make my win7 partition automount on startup.

My advice - don't. And I'm not the only one. I agree 100% with Mark Phelps' reasons:

> **Mark Phelps said:**
> If the NTFS partition you intend to mount is an OS partition containing Vista or Win7, I would advise strongly AGAINST mounting it -- unless you mount it read-only.

Mounting a Vista or Win7 OS partition read-write is asking for trouble.  One unclean shutdown or journal error and the whole partition is then unbootable.  And since you then can't boot into Vista or Win7 to run chkdsk to fix it, you're hosed.

The risk is so great and ntfs-config is such a buggy, poorly-implemented utility that does the most extraordinarily stupid things on occasion that I am doing you a favour by not telling you how to get it going.

If you really must read your Windows C: partition, mount it on an as-needed basis from the Places menu and then dismount it as soon as you can. Even this can lead to trouble. This is not an Ubuntu problem - this is entirely down to Windows.

If, however, you want a shared NTFS data partition to be accessible in both Windows and Ubuntu then that's another matter. If that's what you want and you need help with editing /etc/fstab then I suggest you start another thread but don't think of using ntfs-config, even if someone recommends it. I've seen it do the craziest things. It's a mess.

---

### Post by Acimer on 2011-03-05
> **coffeecat said:**
> My advice - don't. And I'm not the only one. I agree 100% with Mark Phelps' reasons:



The risk is so great and ntfs-config is such a buggy, poorly-implemented utility that does the most extraordinarily stupid things on occasion that I am doing you a favour by not telling you how to get it going.

If you really must read your Windows C: partition, mount it on an as-needed basis from the Places menu and then dismount it as soon as you can. Even this can lead to trouble. This is not an Ubuntu problem - this is entirely down to Windows.

If, however, you want a shared NTFS data partition to be accessible in both Windows and Ubuntu then that's another matter. If that's what you want and you need help with editing /etc/fstab then I suggest you start another thread but don't think of using ntfs-config, even if someone recommends it. I've seen it do the craziest things. It's a mess.

ok, thanks for the advice! I will not use it. 
I wanted to do it because i want to share my Windows 7 music and video folders in Amarok/Vlc on ubuntu. I'll ask in a new thread i guess

---

### Post by coffeecat on 2011-03-05
> **Acimer said:**
> ok, thanks for the advice! I will not use it. 
I wanted to do it because i want to share my Windows 7 music and video folders in Amarok/Vlc on ubuntu. I'll ask in a new thread i guess

Good luck with that! I should have added that I've had a separate NTFS data partition on several Windows/Linux multi-booting machines, with the data partition mounted on bootup, and never had a problem. It's Windows that can take unkindly to access of its C: partition. But I've always hand-edited /etc/fstab - better than letting ntfs-config loose on my partitions. :wink:

---

### Post by amjjawad on 2011-03-08
I totally agree with Coffeecat. I do NOT use such tools to mount NTFS Partitions and if I have to, then I'll use some other easier approach.

For me, I mount "Windows Partition - C:" ONLY when I need that and I unmount it once I finish. Actually I was following the "right/advisable" approach by default. Now, I know it's strongly recommended.

The best approach as already suggested by Coffeecat is **a new "Shared" NTFS Partition ** which can be auto-mounted at boot time (if desired) or can be mounted when needed. It's better not to mess around with System Partitions specially when it comes to Windows. That is just another reason why most of us prefer Linux over Windows ;)

---

### Post by Ben Page on 2011-03-08
Just make a directory in this path: /etc/hal/fdi

```
cd /
```

```
sudo mkdir /etc/hal/fdi
```

This will make NTFS-Config tool work in Ubuntu 10.10. There is no danger in using NTFS-Config tool, I automount 3 NTFS partitions in Ubuntu for a while now all configured with NTFS-Config tool. /etc/fstab is clean and rocksolid.

---

### Post by coffeecat on 2011-03-08
> **Ben Page said:**
> There is no danger in using NTFS-Config tool, I automount 3 NTFS partitions in Ubuntu for a while now all configured with NTFS-Config tool. /etc/fstab is clean and rocksolid.

You were lucky. Unfortunately ntfs-config does some very dangerous things at times. I've been involved in a handful of threads where it's made a real mess for the OP. On two occasions at least it set up fstab so that two different partitions were mounted to the same mountpoint. :-s

By the way, I like your avatar. I'm an admirer of Ocicats. :)

---

### Post by Morbius1 on 2011-03-08
I really don't know why people are so dependent on ntfs-config to mount ntfs partitions.

The very first thing ntfs-config asks you when you launch it for the first time is if you want to enable write support. NTFS through ntfs-3g already has write support by default and has so for some time now. So you have to ask yourself 2 questions:

(1) Why doesn't ntfs-config know that.
(2) What on earth will ntfs-config do should you answer yes.

I would propose a safer approach:

(1) Run the following command just to make sure you're pointing to the right partition:
```
sudo blkid -c /dev/null
```You will get an output that looks something like this for the ntfs partition:
> /dev/sda1: LABEL="WinXP" UUID="DA9056C19056A3B3" TYPE="ntfs" (2) Create a permanent home for the partition to live in:
```
sudo mkdir /media/WinC
```(3) Add a line to /etc/fstab:
```
/dev/sda1 /media/WinC ntfs defaults,umask=222 0 0
```(4) Back in the terminal run the following command to check for errors and mount the new partition:
```
sudo mount -a
```Note: The fstab line above will mount the partition as read only. If you're feeling lucky remove the "umask=222" parameter and allow write.

Note2: There are other GUI utilities that will mount partitions but as luck would have it they are even more unreliable that ntfs-config.

---

### Post by Ben Page on 2011-03-08
> **coffeecat said:**
> You were lucky. Unfortunately ntfs-config does some very dangerous things at times. I've been involved in a handful of threads where it's made a real mess for the OP. On two occasions at least it set up fstab so that two different partitions were mounted to the same mountpoint. :-s

By the way, I like your avatar. I'm an admirer of Ocicats. :)

Thnx, it's my little Oci ;), and a phunn at the new 11.10 official name, "Oneiric Ocelot".

I guess it can be dangerous if you have no experience, I had more trouble by manually editing my fstab file, luckily I know how to fix it. I have set up more PCs with this tool since 9.04 and had no complaints by now.

Using both methods is the safest way, let NTFS tool do the work and then check the fstab file manually and correct if any errors are found.

---

### Post by Morbius1 on 2011-03-08
> **Ben Page said:**
> I guess it can be dangerous if you have no experience .... 
That's the paradox. If a person has no experience they will use a utility to do this and won't know how to fix it.

I would argue that providing the user with a set of templates is a better approach. If you were to add non-system partitions to fstab during the install process instead of after it's installed the Ubuntu installer will generate these lines as an example:

NTFS:
> UUID=DA9056C19056A3B3 /windows/WinXP  ntfs    defaults,nls=utf8,umask=007,gid=46 0       0FAT32:
> UUID=C4DB-C1B0  /windows/J      vfat    utf8,umask=007,gid=46 0       1EXT3/4:
> UUID=f7927995-b098-42be-ada0-987857f5177a /DATA           ext3    defaults        0       2Use them as templates and show the user how to use blkid and mkdir to specify the correct UUID and mount point. Tell them about how to adjust it for accessing the Windows OS partition and  then when ntfs-config or some other utility no longer works they know how to do it themselves.

---

