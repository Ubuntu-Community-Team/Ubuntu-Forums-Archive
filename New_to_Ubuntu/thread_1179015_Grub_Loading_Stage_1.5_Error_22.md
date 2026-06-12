---
title: "Grub Loading Stage 1.5 Error 22"
date: 2009-06-05
forum: New to Ubuntu
---

### Post by mjayakumar2k6 on 2009-06-05
Hi ,

             I have installed UBUNTU 6.06 and installed window also. Now I added one more 80gb  harddisk and I'm getting this error


Grub Loading Stage 1.5

Grub Loading....
Error 22

Please anyone help me to solve this issue.

Thanks in advance 
Jk

---

### Post by mjayakumar2k6 on 2009-06-05
**Grub Loading Stage 1.5 Error 22**             
                                                                Hi ,

 I have installed UBUNTU 6.06 and installed window also. Now I added one more 80gb harddisk and I'm getting this error


Grub Loading Stage 1.5

Grub Loading....
Error 22

Please anyone help me to solve this issue.

Thanks in advance 
Jk

---

### Post by overdrank on 2009-06-05
Hi and welcome, please do not create multiple threads on the same issue. Threads merged. :)
Did you set the jumpers correct on the drives during the install? It would appear that you have moved the original drive that holds the grub.

---

### Post by Alias1407 on 2009-06-05
First of all try to install the latest ubuntu distro,

next try another install

---

### Post by overdrank on 2009-06-05
> **Alias1407 said:**
> First of all try to install the latest ubuntu distro,

next try another install

Would it not be easier to reinstall the grub? ;)

---

### Post by DBrocks on 2009-06-05
I got the same thing, and I re-installed grub, and it works. Here's what I did:
 
First: If you can access the grub menu, try to boot into recovery mode. I had this type of problem, and I could not get into recovery mode. If this happens to you as well, get your hands on your ubuntu install/livecd.
 
LiveCD method:
1- Boot up the cd, and select "Try Ubuntu Without Installing"
2- Get a coffee or something while the disk boots up.
3- Once you finally get into the desktop, open up a terminal, and enter these commands.
substitute {UBUNTUDISK} for the disk ubuntu is installed to.
 
```
 
sudo mkdir /mnt/recovery
sudo mount -t ext3 /dev/{UBUNTUDISK}  /mnt/recovery 
sudo chroot /mnt/recovery /bin/bash

```
You are now chrooted into your ubuntu distro's HDD. Now run this command:
 
```
 
sudo grub
find /boot/grub/stage1

```
Now REMEMBER what the last command spat out at you.
 
```
 
 root (hd?,?)

```
 
Here, input the values of the numbers that /find/boot/grub/stage1 gave you
 
```
setup(hd0)
```
sets up the MBR
 
Reboot and enjoy.
 
Shout's to catlett for this tutorial: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by mjayakumar2k6 on 2009-06-08
find /boot/grub/stage1

when tried the above command i'm getting the error and I can't do the further steps.

Error 15: File not found


Thanks,
Jk

---

### Post by LewRockwell on 2009-06-08
I'm going with hardware issues due to jumpers being set incorrectly

when the river runs blue we walk upstream to find the bathing smurfs...lol.

Never give up, never surrender!

---

