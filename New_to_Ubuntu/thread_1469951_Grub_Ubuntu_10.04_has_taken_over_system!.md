---
title: "Grub/ Ubuntu 10.04 has taken over system!"
date: 2010-05-02
forum: New to Ubuntu
---

### Post by iGuitar on 2010-05-02
I recently installed Lucid Lynx and it has given me tons of problems. I used to dual boot between Windows Vista and Ubuntu 9.10. It worked great! I could use both operating systems without a hitch. 

However, since I have installed Lucid it has rendered Vista and it's recovery hard drive useless. I even tried to boot from a vista recovery disk from the bios. I pressed enter on the cd rom drive from the boot menu and it just took me to the useless grub menu. 

It seems Grub has messed up something when i upgraded to Lucid.

---

### Post by vipin.balakrishnan on 2010-05-02
Can you please give us the error you are getting in GRUB.

---

### Post by iGuitar on 2010-05-02
Well when I select either Windows Vista or its recovery hard drive I get a black screen with a blinking cursor.

---

### Post by zeepal on 2010-05-02
Did you upgrade from 9.10 to 10.04 or a fresh install? **(nvm I need to read!)**

You may want to try running the following as it will update the grub cfg file:

```
sudo update-grub
```

---

### Post by iGuitar on 2010-05-02
Updated Grub. I still have the same problem.

---

### Post by vipin.balakrishnan on 2010-05-02
Hi iGuitar

  Did you tried to reinstall GRUB,


[LIST]
[*]First, grab a copy of the latest [Ubuntu  LiveCD]("http://www.ubuntu.com/getubuntu/download") and boot it. 
[*]Open  a terminal and type 
[/LIST]
$ sudo fdisk -l 

[LIST]
[*]Mount the file system of your linuxto /mnt 
[/LIST]
$ sudo mount /dev/sda1 /mnt  

[LIST]
[*]If you have /boot  on a separate partition, that need's to be mounted as well.  For  reference, /dev/sda2 will be used. 
[/LIST]
$ sudo mount /dev/sda2 /mnt/boot *Make sure you don't mix these  up, pay attention to the output of FDISK* 

[LIST]
[*]Now  mount the rest of your devices and some other things needed in the  chroot 
[/LIST]
$ sudo mount --bind /dev /mnt/dev
 $ sudo mount --bind /proc /mnt/proc
 $ sudo mount --bind /sys /mnt/sys  

[LIST]
[*]Now chroot into  your system 
[/LIST]
$ sudo chroot /mnt 
You should be chroot'd into your system as root, you can  now run commands as root, without the need for sudo. 

[LIST]
[*]Now you need to edit the **/etc/default/grub**  file to fit your system 
[/LIST]
$ nano /etc/default/grub 

[LIST]
[*]When that is done  you need to run **update-grub** to create the configuration  file. 
[/LIST]
$ update-grub 

[LIST]
[*]To install GRUB 2 to  the MBR, next you need to run **grub-install /dev/sda** 
[/LIST]
$ grub-install /dev/sda  

[LIST]
[*]If you encounter any errors, try **grub-install  --recheck /dev/sda** 
[/LIST]
$ grub-install --recheck /dev/sda 

[LIST]
[*]Press Ctrl+D to exit out  of the chroot. 
[*]Once  you exit back to your regular console, undo all the mounting, first the  /dev and others 
[/LIST]
$ sudo umount /mnt/dev
 $ sudo umount /mnt/sys
 $ sudo umount /mnt/proc  
Now you can  unmount the root system. (But if you have a separate boot partition  which you mounted earlier, you have to unmount this first, or you will  get a "device busy" error message.)

---

### Post by zeepal on 2010-05-02
Hello iGuitar,

If Vipin.Balakrishnan's steps doesn't resolve the issue it seems to be the booting issue with Windows not Ubuntu or GRUB.

**--- ONLY IF Vipin.Balakrishnan's STEPS DIDN'T WORK ---**

Try putting your Vista DVD into your computer and go into repair mode and try the following commands:

```
bootrec /fixmbr
bootrec /FixBoot
```
**Ref:** [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

This will replace GRUB with the normal Windows boot loader then you should be able to get into Windows when you reboot but not Ubuntu!

If this does work you can follow Vipin.Balakrishnan's steps again to restore GRUB to boot between Ubuntu and Windows.

If it happens to break again (Unlikely if Windows's "bootrec" commands fix Windows) you will know how to fix Windows's boot loader again and we can see what other ideas we have but I don't think this will be the case.

---

### Post by iGuitar on 2010-05-02
Okay thanks guys. Downloading the live cd now. I'll try those steps and get back to you.

---

### Post by iGuitar on 2010-05-02
> **vipin.balakrishnan said:**
> Hi iGuitar

  Did you tried to reinstall GRUB,


[LIST]
[*]First, grab a copy of the latest [Ubuntu  LiveCD]("http://www.ubuntu.com/getubuntu/download") and boot it. 
[*]Open  a terminal and type 
[/LIST]
$ sudo fdisk -l 

[LIST]
[*]Mount the file system of your linuxto /mnt 
[/LIST]
$ sudo mount /dev/sda1 /mnt  

[LIST]
[*]If you have /boot  on a separate partition, that need's to be mounted as well.  For  reference, /dev/sda2 will be used. 
[/LIST]
$ sudo mount /dev/sda2 /mnt/boot *Make sure you don't mix these  up, pay attention to the output of FDISK* 

[LIST]
[*]Now  mount the rest of your devices and some other things needed in the  chroot 
[/LIST]
$ sudo mount --bind /dev /mnt/dev
 $ sudo mount --bind /proc /mnt/proc
 $ sudo mount --bind /sys /mnt/sys  

[LIST]
[*]Now chroot into  your system 
[/LIST]
$ sudo chroot /mnt 
You should be chroot'd into your system as root, you can  now run commands as root, without the need for sudo. 

[LIST]
[*]Now you need to edit the **/etc/default/grub**  file to fit your system 
[/LIST]
$ nano /etc/default/grub 

[LIST]
[*]When that is done  you need to run **update-grub** to create the configuration  file. 
[/LIST]
$ update-grub 

[LIST]
[*]To install GRUB 2 to  the MBR, next you need to run **grub-install /dev/sda** 
[/LIST]
$ grub-install /dev/sda  

[LIST]
[*]If you encounter any errors, try **grub-install  --recheck /dev/sda** 
[/LIST]
$ grub-install --recheck /dev/sda 

[LIST]
[*]Press Ctrl+D to exit out  of the chroot. 
[*]Once  you exit back to your regular console, undo all the mounting, first the  /dev and others 
[/LIST]
$ sudo umount /mnt/dev
 $ sudo umount /mnt/sys
 $ sudo umount /mnt/proc  
Now you can  unmount the root system. (But if you have a separate boot partition  which you mounted earlier, you have to unmount this first, or you will  get a "device busy" error message.) 

Well I got down to 
```
sudo mount --bind /dev /mnt/dev
```

And the terminal said
```
mount: mount point /mnt/dev does not exist
```

---

### Post by zeepal on 2010-05-02
You will have to create the folders.

eg:
```
mkdir /mnt/dev
```

---

### Post by Sealbhach on 2010-05-02
This sounds like the same problem as Lazy-buntu has got:

[http://ubuntuforums.org/showthread.php?t=1466038](http://ubuntuforums.org/showthread.php?t=1466038)

So far, that problem has not been solved.

.

---

### Post by iGuitar on 2010-05-02
> **zeepal said:**
> Hello iGuitar,

If Vipin.Balakrishnan's steps doesn't resolve the issue it seems to be the booting issue with Windows not Ubuntu or GRUB.

**--- ONLY IF Vipin.Balakrishnan's STEPS DIDN'T WORK ---**

Try putting your Vista DVD into your computer and go into repair mode and try the following commands:

```
bootrec /fixmbr
bootrec /FixBoot
```
**Ref:** [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

This will replace GRUB with the normal Windows boot loader then you should be able to get into Windows when you reboot but not Ubuntu!

If this does work you can follow Vipin.Balakrishnan's steps again to restore GRUB to boot between Ubuntu and Windows.

If it happens to break again (Unlikely if Windows's "bootrec" commands fix Windows) you will know how to fix Windows's boot loader again and we can see what other ideas we have but I don't think this will be the case.

Well the issue is now somewhat fixed. I did this and can boot to windows. All I have to do now is restore grub. Sounds like a job for tomorrow. Thanks guys! I'll tell you how grub restores tomorrow.

---

### Post by vipin.balakrishnan on 2010-05-03
Hi iGuitar,

boot with the live cd, open terminal in the live CD

1) First you need to mount the root file system(/) to the folder /mnt.
(ie this is the file system of the Linux OS you installed. Not the live CD)

You can find it out by using the command
```

$ fdisk -l.

```
usually this file system will contain all the directories like /dev, /etc

use this below command to mount root file system.

```

$ sudo mount /dev/sda1 /mnt  (assuming root file system is in sda1)

```

2) While installing your Linux OS. If you have created a new partition for boot. Like /boot. You need to mount this inside the /mnt folder. If you are not created then you don't need to do this operation.
```

$ sudo mount /dev/sda2 /mnt/boot  (assuming your boot partition is sda2)

```



3) Now you have mounted your Linux OS boot and Filesystem. Now you need to do the  rest of your devices and some other things needed in the chroot. For that please follow below steps.

```

$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /proc /mnt/proc
$ sudo mount --bind /sys /mnt/sys

```

Note : Once you are done the step-1 correctly all the folder will be there inside the /mnt folder. You don't need to create. Depends on your partitions you just need to mount the required.

4) After these all the 3 steps are done successfully. You need to run the chroot command.

```

$ sudo chroot /mnt (this is the folder where you mounted the root filesystem in the first step.)

```

5. It is not mandatory to edit the /etc/default/grub  file. If you need to change any config. You can do that.

6. Run in the terminal you mounted in step 4.

```

$ update-grub

```

7./dev/sda should the parition which belows the root parition or If you have a seperate boot partition that should be.

```

$ grub-install /dev/sda

```

8. Exit the chroot by Ctrl+D

    * Once you exit back to your regular console, undo all the mounting, first the /dev and others

$ sudo umount /mnt/dev
$ sudo umount /mnt/sys
$ sudo umount /mnt/proc
Now you can unmount the root system. (But if you have a separate boot partition which you mounted earlier, you have to unmount this first, or you will get a "device busy" error message.)

Restart your system.

I hope this will gave your answer

---

