---
title: "&quot;grab rescue&quot; error, cant load ubuntu"
date: 2010-05-13
forum: New to Ubuntu
---

### Post by greg_ntu on 2010-05-13
I've just install Ubuntu 10.04 on to an old Dell Pentium III, which has a primary and slave hard disk, the slave is partitioned into 2 drives, and the primary has Windows XP installed.

I went through the installation process and selected all the standard options, i selected the option to install Ubuntu and keep Windows XP, and the installation was completed successfully. At the end i was prompted to re-start, but when i did so the following error came up:

error: no such device: e82b0b69-8810-4f16-9580-8ee96bd46aa6
grub rescue>

I rebooted with the Ubuntu CD in and started up Linux off the CD. I've discovered that the installation put Ubuntu in

/media/e82b0b69-8810-4f16-9580-8ee96bd46aa6/

so i could only assume that grub either cant find the system files or grub isn't installed correctly. I went into the terminal and installed grub, then re-booted but still had the same problem. I can't access Windows or Ubuntu.

How can i fix this? Is the installation incorrect or is it Grub?

Thanks.

---

### Post by -humanaut- on 2010-05-13
Where is grub installed? the MBR or / and what drive?

---

### Post by greg_ntu on 2010-05-14
Ubuntu is installed on the slave hard drive and grub seems to be at

 /media/e82b0b69-8810-4f16-9580-8ee96bd46aa6/boot/grub

---

### Post by softis on 2010-07-24
> **greg_ntu said:**
> I've just install Ubuntu 10.04 on to an old Dell Pentium III, which has a primary and slave hard disk, the slave is partitioned into 2 drives, and the primary has Windows XP installed.

I went through the installation process and selected all the standard options, i selected the option to install Ubuntu and keep Windows XP, and the installation was completed successfully. At the end i was prompted to re-start, but when i did so the following error came up:

error: no such device: e82b0b69-8810-4f16-9580-8ee96bd46aa6
grub rescue>

I rebooted with the Ubuntu CD in and started up Linux off the CD. I've discovered that the installation put Ubuntu in

/media/e82b0b69-8810-4f16-9580-8ee96bd46aa6/

so i could only assume that grub either cant find the system files or grub isn't installed correctly. I went into the terminal and installed grub, then re-booted but still had the same problem. I can't access Windows or Ubuntu.

How can i fix this? Is the installation incorrect or is it Grub?

Thanks.

Hi i did run updates.. now after rebot i get same as above error: no such device: *************************
grub rescue>  how can i s slove this one? regards

---

### Post by ks07 on 2010-07-24
Seems you haven't had a response in a while :p.

Anyway, could you boot from the live CD and run the Boot Info Script by following the instructions at [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) and then copy and paste the contents of the results.txt file here. Remember to wrap the pasted text in code tags. Use [*code][*/code] without the '*'s. Thanks.

---

### Post by softis on 2010-07-24
> **ks07 said:**
> Seems you haven't had a response in a while :p.

Anyway, could you boot from the live CD and run the Boot Info Script by following the instructions at [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280) and then copy and paste the contents of the results.txt file here. Remember to wrap the pasted text in code tags. Use [*code][*/code] without the '*'s. Thanks.


i don't use cd.. i use wubi.exe 32/64

---

### Post by linux18 on 2010-07-24
" sudo grub-install /dev/sdb && sudo update-grub "

---

### Post by ks07 on 2010-07-24
> **softis said:**
> i don't use cd.. i use wubi.exe 32/64
Ah, that's a problem. I've never used Wubi, so I can't really help you. :( Hope you find someone who can help you, sorry!

EDIT: [I did find this]("http://calamari.wordpress.com/2009/12/01/fixing-a-broken-wubi-grub-after-ubuntu-updates/") after a quick search, it may help you.

---

### Post by softis on 2010-07-24
> **linux18 said:**
> " sudo grub-install /dev/sdb && sudo update-grub "


i cant do that, cos i can not logon on ubuntu or windows:(

---

### Post by bcbc on 2010-07-24
> **softis said:**
> i cant do that, cos i can not logon on ubuntu or windows:(

it wouldn't work anyway - with wubi you need the windows bootloader in the MBR, not grub.

Do you still see the windows boot manager with the choice of Windows or Ubuntu or does it drop you straight into a grub> prompt? 
Or is it that when you select Windows, it no longer boots? This information is important because if you go straight to the grub prompt you need to install the windows bootloader back to your drive MBR.

Let's try booting ubuntu from the grub prompt in the meantime.
Enter ```
search.file /ubuntu/disks/root.disk
``` in the grub prompt. Note the reponse:
(hd0,1) = /dev/sda1
(hd0,2) = /dev/sda2
etc.
(hd1,1) = /dev/sdb1

Then boot manually entering the following commands (substituting (hd0,1) and /dev/sda1 for what you found above):
```
insmod ntfs
set root=**(hd0,1)**
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=**/dev/sda1** loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```

Then run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back.

---

### Post by softis on 2010-07-24
> **bcbc said:**
> it wouldn't work anyway - with wubi you need the windows bootloader in the MBR, not grub.

Do you still see the windows boot manager with the choice of Windows or Ubuntu or does it drop you straight into a grub> prompt? 
Or is it that when you select Windows, it no longer boots? This information is important because if you go straight to the grub prompt you need to install the windows bootloader back to your drive MBR.

Let's try booting ubuntu from the grub prompt in the meantime.
Enter ```
search.file /ubuntu/disks/root.disk
``` in the grub prompt. Note the reponse:
(hd0,1) = /dev/sda1
(hd0,2) = /dev/sda2
etc.
(hd1,1) = /dev/sdb1

Then boot manually entering the following commands (substituting (hd0,1) and /dev/sda1 for what you found above):
```
insmod ntfs
set root=**(hd0,1)**
loopback loop0 /ubuntu/disks/root.disk
set root=(loop0)
linux /vmlinuz root=**/dev/sda1** loop=/ubuntu/disks/root.disk ro quiet splash
initrd /initrd.img
boot
```Then run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/") and post the results back.


Do you still see the windows boot manager with the choice of Windows or  Ubuntu or does it drop you straight into a grub> prompt   that one.. can't do anything, i'm stuck here :(  i only see the black screen at the begining when you start the comp. here is a screen, sorry for the bad pic.. bad cam LOL  [http://img14.imageshack.us/img14/6831/bild376x.jpg](http://img14.imageshack.us/img14/6831/bild376x.jpg)  

[[IMG]http://img14.imageshack.us/img14/6831/bild376x.th.jpg[/IMG]]("http://img14.imageshack.us/i/bild376x.jpg/")

Uploaded with [ImageShack.us]("http://imageshack.us")   thats the only
 i see after start up comp

---

### Post by bcbc on 2010-07-24
> **softis said:**
> Do you still see the windows boot manager with the choice of Windows or  Ubuntu or does it drop you straight into a grub> prompt   that one.. can't do anything, i'm stuck here :(  i only see the black screen at the begining when you start the comp. here is a screen, sorry for the bad pic.. bad cam LOL  [http://img14.imageshack.us/img14/6831/bild376x.jpg](http://img14.imageshack.us/img14/6831/bild376x.jpg)  

[[IMG]http://img14.imageshack.us/img14/6831/bild376x.th.jpg[/IMG]](http://img14.imageshack.us/i/bild376x.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)   thats the onky i see after start up comp

What does it return when you type ```
search.file /ubuntu/disks/root.disk
```

After you get ubuntu booted you'll need to reinstall the windows bootloader. But let's first focus on booting ubuntu and getting the bootinfoscript results.

---

### Post by softis on 2010-07-24
> **bcbc said:**
> What does it return when you type ```
search.file /ubuntu/disks/root.disk
```After you get ubuntu booted you'll need to reinstall the windows bootloader. But let's first focus on booting ubuntu and getting the bootinfoscript results.

i can't type /  when i try it will be &  :s  when i use shift and number 6

---

### Post by bcbc on 2010-07-24
> **softis said:**
> i can't type /  when i try it will be &  :s  when i use shift and number 6

If you can't boot ubuntu, you can use your windows repair disk to fix windows.

---

### Post by bcbc on 2010-07-25
> **softis said:**
> i can't type /  when i try it will be &  :s  when i use shift and number 6
grub uses the US keyboard layout. the / key is to the left of the right shift (and it doesn't need the shift)

---

### Post by softis on 2010-07-26
> **bcbc said:**
> grub uses the US keyboard layout. the / key is to the left of the right shift (and it doesn't need the shift)


thx m8.. i did use windows disk.. so now is all fixed :)

---

