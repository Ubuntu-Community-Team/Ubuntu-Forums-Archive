---
title: "chroot to repair GRUB - How does it work?"
date: 2011-02-21
forum: New to Ubuntu
---

### Post by yc2 on 2011-02-21
Hello,

One can use chroot to repair GRUB(2). I am just not clear about how it works. I know that chroot will make the following commands "act on the hard disk" and not on the live CD.

Below is a simple example. I can understand that one mounts the harddisk under /mnt of the LiveCD and then chroots to it.

However I do not understand the following three mount commands (dev, proc, sys). I can maybe understand that one mounts the /sys of the LiveCD under the /sys of the harddisk so that one can chroot to the harddisk and get fresh sys-commands from the LiveCD?? Is that the reason??

However, why does one mount the /dev of the LiveCD under the /dev of the harddisk? If you want to make actions on the /dev (after chrooting) these actions will have effect on the LiveCD???

Sorry if I got it all wrong. Grateful for help. Thanks.

```
sudo mount /dev/sda1 /mnt

sudo mount --bind /dev /mnt/dev
sudo mount --bind /proc /mnt/proc
sudo mount --bind /sys /mnt/sys 

sudo chroot /mnt

update-grub

sudo grub-install /dev/sda
```

---

### Post by deconstrained on 2011-02-21
The proc, dev, sys (and devpts) filesystems are needed by grub (and update-initramfs); they contain symbolic links to devices and whatnot. If the aforementioned programs can't find them, they'll print error messages; for example, if there is no /dev/sda in the chrooted environment, what good will running grub-install /dev/sda do?

Also, /dev and all the device files/symlinks it contains is sort of an interface between the kernel and the hardware devices. Actions made on devices in the chrooted environment are not going to affect the live disk, but they WILL affect the devices!

What mount -o bind does is just make an alternate path to the same thing (whether it be a filesystem location in memory or a filesystem location on a block device).

---

### Post by wilee-nilee on 2011-02-21
On the forum look in the authors sig for more.
[http://ubuntuforums.org/showthread.php?t=1581099](http://ubuntuforums.org/showthread.php?t=1581099)

---

### Post by yc2 on 2011-02-21
Thanks guys.

Lets say I just destroyed GRUB2 by f.ex. a DOS fixmbr-command. In that case my Ubuntu system on the hard disk would be completely intact. Then maybe this would be enough (from a LiveCD)?
```
sudo mount /dev/sda1 /mnt
sudo chroot /mnt
sudo grub-install /dev/sda
```

---

### Post by oldfred on 2011-02-21
there is at least two ways to reinstall grub2.

Reinstall grub2 - Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

#Comments are anything after the #, enter commands in terminal session
#Install MBR from LiveCD, Ubuntu install on sda5 and want grub2 in drive sda's MBR:
#Find linux partition, change sda5 if not correct:
sudo fdisk -l
#confirm that linux is sda5
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
#If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt/ /dev/sda
# After rebooting into working system
sudo update-grub

---

### Post by yc2 on 2011-02-21
Thanks.

I am grateful you help out. I do not have a current problem, but knowing how to repair GRUB2 is important, I think. Already much clearer now, thanks.

In the example given, would this
```
...
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda
...
```
be the same as
```
...
sudo mount /dev/sda5 /mnt
sudo chroot /mnt
sudo grub-install /dev/sda
...
```
?

(I wasn't aware of that grub-install option before.)

---

### Post by oldfred on 2011-02-22
Normally in a chroot you mount many folders/partitions to have the full system available. Not sure if a chroot into just a partition would work.

Some more examples of chroots:
drs305 chroot to reinstall grub2
[http://ubuntuforums.org/showpost.php?p=9107370&postcount=12](http://ubuntuforums.org/showpost.php?p=9107370&postcount=12)
kansasnoob------------------------------
[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)
[http://ubuntuforums.org/showthread.php?t=1470597](http://ubuntuforums.org/showthread.php?t=1470597)

---

### Post by yc2 on 2011-02-22
Thanks, you are helpful and knowledgeable. I already got a lot of help.

I am just translating an instruction how to repair GRUB2 by chroot (into Swedish). When I came to this part I wanted to add a little explanation.
```
sudo -i
mount /dev/sda7 /mnt
mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr
chroot /mnt

```

I wanted to add an explanation of _why_ you should mount more directories than sdaX:
```

mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr

```

Maybe this is a simple and reasonably accurate explanation: ??
> In addition to mounting your Ubuntu partition you should also mount /dev, /proc, /sys, /usr from the LiveCD *in order to ensure that the system you are working from is fresh and without errors*.

---

### Post by oldfred on 2011-02-23
I do not know all the details, but Linux stores parts of system files in all those places. So depending on what you are updating, you may need to update a file in any of those locations. Safest to just mount all the standard locations, so anything that needs to be updated is updated.
Even with grub, if you have a separate /boot partition you have to also mount that whether using the short or full chroot method.

Example of two line version that becomes 3 lines:
If separate /boot
$ sudo mount /dev/sda2 /mnt
$ sudo mount /dev/sda1 /mnt/boot
$ grub-install --root-directory=/mnt /dev/sda

---

### Post by yc2 on 2011-02-24
These two I think I understand. You mount hard disk partitions under /mnt so they will be affected by the following commands after you chroot into /mnt
```
mount /dev/sda7 /mnt
mount /dev/sda1 /mnt/boot
```


But the four below I interpret differently. I interpret them as you mount "guaranteed healthy" filesystems (from the LiveCD and not your harddisk which may or may not be defect)

[U]I interpret them as making these four LiveCD filesystems available also after the chroot command is executed.
[/U]
If the /dev, /proc, /sys, /usr from the _Live CD_ are used to supply the environment/commands for repairing GRUB you are sure they are not corrupt/incompatible.

I think /proc and /sys are related to kernel function. /usr are system commands. You mount these from the Live CD in order to bring the healthy/relevant (Live CD) environment with you when you make the chroot jump onto the hard disk??
 
```
mount --bind /dev  /mnt/dev
mount --bind /proc /mnt/proc
mount --bind /sys  /mnt/sys
mount --bind /usr/ /mnt/usr

```

But I'm not sure, it is just an interpretation, that's why I'm asking :)

---

