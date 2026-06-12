---
title: "Windows has wiped GRUB, tried following instructions, doesn't work, please help!"
date: 2009-11-01
forum: New to Ubuntu
---

### Post by sebovzeoueb on 2009-11-01
Hello,
I have a triple boot on my MacBook Pro with OS X, Ubuntu Karmic and Windows XP. I have reinstalled Windows and now my GRUB seems to have been erased. Seems like a fairly standard problem, and I have tried to carefully follow instructions on how to restore it from Live CD (I only have the Jaunty disk, do I need to burn another Karmic one for this to work?). Firstly the find /boot/grub/stage1 command doesn't find anything, and I can't find the file in the file browser either, I also don't seem to have a menu.lst file in the grub directory. So I have tried the mounting the partition and using chroot technique as per 2 different websites. These are the results:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/hd
ubuntu@ubuntu:~$ chroot /mnt/hd
chroot: cannot change root directory to /mnt/hd: Operation not permitted
ubuntu@ubuntu:~$ sudo chroot /mnt/hd
root@ubuntu:/# grub-install /dev/hd
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

``````
ubuntu@ubuntu:~$ sudo umount /mnt/hd
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda3 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# sudo grub
sudo: unable to resolve host ubuntu
sudo: grub: command not found
root@ubuntu:/# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
grub: command not found

```The file browser shows the hard drive to be mounted in mnt
Please bear in mind that I don't really know what I am doing, as I am new to Linux, hence Absolute Beginner Talk. Would someone be able to tell me step by step how to reinstall GRUB based on the fact that I have tried the two methods from here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), and neither have been successful for me?

Thank you.

---

### Post by sliketymo on 2009-11-01
> **sebovzeoueb said:**
> Hello,
I have a triple boot on my MacBook Pro with OS X, Ubuntu Karmic and Windows XP. I have reinstalled Windows and now my GRUB seems to have been erased. Seems like a fairly standard problem, and I have tried to carefully follow instructions on how to restore it from Live CD (I only have the Jaunty disk, do I need to burn another Karmic one for this to work?). Firstly the find /boot/grub/stage1 command doesn't find anything, and I can't find the file in the file browser either, I also don't seem to have a menu.lst file in the grub directory. So I have tried the mounting the partition and using chroot technique as per 2 different websites. These are the results:

```

ubuntu@ubuntu:~$ sudo mount /dev/sda3 /mnt/hd
ubuntu@ubuntu:~$ chroot /mnt/hd
chroot: cannot change root directory to /mnt/hd: Operation not permitted
ubuntu@ubuntu:~$ sudo chroot /mnt/hd
root@ubuntu:/# grub-install /dev/hd
grub-probe: error: cannot find a device for /boot/grub.

No path or device is specified.
Try ``grub-probe --help'' for more information.
Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.

``````
ubuntu@ubuntu:~$ sudo umount /mnt/hd
ubuntu@ubuntu:~$ sudo mkdir /mnt/root
ubuntu@ubuntu:~$ sudo mount -t ext4 /dev/sda3 /mnt/root
ubuntu@ubuntu:~$ sudo mount -t proc none /mnt/root/proc
ubuntu@ubuntu:~$ sudo mount -o bind /dev /mnt/root/dev
ubuntu@ubuntu:~$ sudo chroot /mnt/root /bin/bash
root@ubuntu:/# sudo grub
sudo: unable to resolve host ubuntu
sudo: grub: command not found
root@ubuntu:/# grub
The program 'grub' is currently not installed.  You can install it by typing:
apt-get install grub
grub: command not found

```The file browser shows the hard drive to be mounted in mnt
Please bear in mind that I don't really know what I am doing, as I am new to Linux, hence Absolute Beginner Talk. Would someone be able to tell me step by step how to reinstall GRUB based on the fact that I have tried the two methods from here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351), and neither have been successful for me?

Thank you.

Check this thread :
[http://ubuntuforums.org/showthread.php?t=1308662](http://ubuntuforums.org/showthread.php?t=1308662)

---

### Post by Earl_Maroon on 2009-11-01
This should work, hopefully:

Boot up the live CD and try
```
sudo grub
```
```
root (hd0,0)
``` (assuming "/" is on the first partition of the first disk. 0,1 is the second partition of the first disk; 1,0 is the first partition of the second disk etc...)
```
setup (hd0)
``` (assuming "/" is on the first disk.)
```
quit
```
```
sudo reboot now
```

When your computer restarts you should come to the Grub screen and be able to choose.

---

### Post by kansasnoob on 2009-11-01
Look here:

[http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/](http://www.openpeta.com/index.php/how-to-recover-ubuntu-grub-after-windows-installation/)

> do I need to burn another Karmic one for this to work?

No, I usually use a Jaunty disc because it boots to live desktop faster.

---

### Post by kansasnoob on 2009-11-01
> **Earl_Maroon said:**
> This should work, hopefully:

Boot up the live CD and try
```
sudo grub
```
```
root (hd0,0)
``` (assuming "/" is on the first partition of the first disk. 0,1 is the second partition of the first disk; 1,0 is the first partition of the second disk etc...)
```
setup (hd0)
``` (assuming "/" is on the first disk.)
```
quit
```
```
sudo reboot now
```

When your computer restarts you should come to the Grub screen and be able to choose.

That no longer works with grub 2.

To determine what version of grub is installed you need to run the command "grub-install -v". (0.97 is old grub, 1.97+ is grub 2)

---

### Post by sebovzeoueb on 2009-11-01
Thanks for your replies. Earl_Maroon, I have tried this method a few times already, with no luck. 

Well, I thought I was onto something with that link kansasnoob gave me, however my computer still just goes straight to Windows XP when I load the Windows option at startup. No sign of grub unfortunately. 

But none of the fixes I have found so far seem to take into account installing grub on a partition, they all say to install it on the whole hard drive, well, as in hda0, whereas originally I had mine installed on my Linux partition (sda3). I don't really get what is going on at all. 

I might just have to reinstall Ubuntu, but it is annoying to have to reinstall Ubuntu just because I reinstalled Windows.

I did the version check at some point, and I think it came up with 0.97, but when GRUB was working I had 1.97...

It would be nice to have a solution, because it would be good for me to know how to fix Grub anytime I reinstall Windows.

Thanks for replies so far.

---

### Post by kansasnoob on 2009-11-01
Post the output from terminal of:

```
sudo fdisk -l
```

---

