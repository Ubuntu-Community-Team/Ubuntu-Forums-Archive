---
title: "Ubuntu 10.04 refuses to boot."
date: 2011-01-11
forum: New to Ubuntu
---

### Post by LinuxFox on 2011-01-11
My mother's computer has Ubuntu 10.04 installed via Wubi, and she wanted me to install the updates.  I installed them and now Ubuntu won't boot.

First I thought it was Windows, so I ran the "chkdsk -/r" and checked it, but even after that it won't work.  At the screen where I could choose Windows and Ubuntu, when I choose Ubuntu, it just restarts it self back to the Motherboard boot screen (don't know what it's called) and then back to the selection menu.  It won't even boot GRUB.  Windows boots fine.  I even searched Google and can't find anything.

Can someone please help me here, my mother wants to use her computer and she likes Ubuntu more than Windows.  Please no "serious Ubuntu users don't use Wubi" type remarks.  I have her computer using Wubi for a reason.

---

### Post by Quackers on 2011-01-11
It may be worthwhile taking a look here
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by LinuxFox on 2011-01-11
> **Quackers said:**
> It may be worthwhile taking a look here
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)I looked under Problem 2 and it sounds like the problem I'm having.  I want to fix it, but I can't figure out how to loop mount the root.disk while on the Live CD.

Thanks, but I need some assistance trying to fix this as I never done something like this before.

---

### Post by drs305 on 2011-01-11
> **LinuxFox said:**
> I looked under Problem 2 and it sounds like the problem I'm having.  I want to fix it, but I can't figure out how to loop mount the root.disk while on the Live CD.

Thanks, but I need some assistance trying to fix this as I never done something like this before.

It's this part of the problem-solving section:
```

sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
[COLOR="DarkRed"]**sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt**[/COLOR]
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```

It's actually the dark red command that mounts root.disk, but you need to accomplish the previous steps to set it up. If your Windows partition isn't sd**a1** you would need to change this value.

Added: If you don't know how to open a Terminal: Applications, Accessories, Terminal.

---

### Post by LinuxFox on 2011-01-11
> **drs305 said:**
> It's this part of the problem-solving section:
```

sudo mkdir /media/win 
sudo mount /dev/sda1 /media/win
[COLOR="DarkRed"]**sudo mount -o loop /media/win/ubuntu/disks/root.disk /mnt**[/COLOR]
sudo cp /mnt/boot/grub/grub.cfg /mnt/boot/grub/grub.cfg.copy
sudo chmod +w /mnt/boot/grub/grub.cfg
gksu gedit /mnt/boot/grub/grub.cfg
```

It's actually the dark red command that mounts root.disk, but you need to accomplish the previous steps to set it up.I've been doing that, but I can't find the mounted drive. :(  When I went to use the chmod command it just said "chmod: cannot access 'mnt/boot/grub/grub.cfg': No such file or directory."

I can't get it to do anything.  I don't even know if it's mounted.

---

### Post by Bucky Ball on 2011-01-11
Wubi is really for trying Ubuntu. You may have your reasons but updates are not really a goer with Wubi.

---

### Post by drs305 on 2011-01-11
> **LinuxFox said:**
> I've been doing that, but I can't find the mounted drive. :(  When I went to use the chmod command it just said "chmod: cannot access '[COLOR="Red"]mnt[/COLOR]/boot/grub/grub.cfg': No such file or directory."

I can't get it to do anything.  I don't even know if it's mounted.

It may be just a copy/paste error but 
mnt/boot/grub/grub.cfg
is missing the / at the start
/mnt/boot/grub/grub.cfg

If that wasn't the problem, run the following:
```

ls /media/win  # Do you see Windows folders?  If not:
sudo umount /media/win
sudo fdisk -l  # lowercase L. Inspect the return. Windows could be sda2, etc
sudo mount /dev/sda**X** /media/win  # Using the new device: sda2, sdb1, etc
ls /media/win  # Do you see the Windows folders now?
```

---

### Post by LinuxFox on 2011-01-11
Thanks, now I've gotten somewhere and the grub.cfg is up.  But I'm not too sure what to do now.  The topic says "In other words, from the start of the file up to, but not including, the following menuentry" ```
 ### BEGIN /etc/grub.d/10_lupin ###
```

Does this mean I delete everything before that line, or the first line like it?

---

### Post by drs305 on 2011-01-11
> **LinuxFox said:**
> Thanks, now I've gotten somewhere and the grub.cfg is up.  But I'm not too sure what to do now.  The topic says "In other words, from the start of the file up to, but not including, the following menuentry" ```
 ### BEGIN /etc/grub.d/10_lupin ###
```

Does this mean I delete everything before that line, or the first line like it?

Everything above that line. The line you quoted should be the first line in the file.

---

### Post by LinuxFox on 2011-01-11
I did that, saved it, and the Ubuntu Boot sound was sweet music to my ears. 8)  It booted up and now my mother can use Ubuntu again.

Thanks a million for helping me out with this. :D

---

### Post by drs305 on 2011-01-11
Glad you fixed your problem. 
 
Please mark the thread SOLVED via the 'Thread Tools' link at the top right of the first post. It helps users looking for posts with answers and also lets helpers concentrate on unresolved problems.

Happy Ubuntu-ing (Wubi-ing) !

---

### Post by Quackers on 2011-01-11
Wubuntuing :-)

---

