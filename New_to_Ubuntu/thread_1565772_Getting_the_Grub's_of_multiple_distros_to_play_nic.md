---
title: "Getting the Grub's of multiple distros to play nice."
date: 2010-09-01
forum: New to Ubuntu
---

### Post by Windows Nerd on 2010-09-01
Hey guys,

I recently got a desktop computer as well as my laptop. My laptop had been running 9.04 for some time. After I had transferrer all my data I needed, I decided to make a fresh install of 10.4, and nuke the rest of the drive.

So, I installed 10.4, gave it a 25GB partition on SDA1. No  separate /home.  

Next I decided to Install backtrack to the drive. Similar setup: 25Gb partition. No seperate home. 

Swap is on SDA5.

Now, my hard drive still has a good 100 GB on it.

So, before I went any further and made a separate partition as the shared data partition (not mounted as anything), I decided to reboot.

I could only boot from my backtrack partitions once Backtrack had installed it's separate Grub. It could not boot from the Ubuntu ones.


So, here is my question: As I may plan to add more OSes to my existing two, how might I configure Grub easily so I can add Linux distros and boot from them easily as time goes on? 

And how can I make my existing configuration work? I have not done anything to the partitiona from a fresh install, so a whole repartition and reinstall will work.

Scott

---

### Post by cchaos on 2010-09-01
The only thing I can think of is to reinstall the GRUB for Ubuntu after you have setup all of your other linux distros.: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Though you might want to tweak the GRUB so you know which loader is for what distro: [http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602) <-- seems that most things are on the first post

Thats what I would do anyway

---

### Post by rolnics on 2010-09-01
How about a separate grub partition? 

I have played around with it but haven't had complete success with what I wanted it to do for it, but given more time I could. I had grub legacy chainloading into other grub menu.lst's so each distro had its own configure grub to boot.

Take a look [here at this thread.]("http://ubuntuforums.org/showthread.php?t=1465772") At the time grub2 was still new and not much on a separate grub partition, but I'm sure there's more now.

[edit] And [here's]("http://http://newyork.ubuntuforums.org/showthread.php?p=8300400") another thread.

---

### Post by oldfred on 2010-09-01
You have to decide which install's version of grub you want in control. Almost all versions of Linux let you choose where or whether to install grub to the MBR. Grub2 is very good at finding and directly booting other systems, so I find it best just to let my main Ubuntu's grub2 to be in charge.

You can in 40_custom set up boots to other Ubuntu based systems as they put links for the kernel & initrd to the most current kernel in the root:

From Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

Change to your drive & partition:
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Grub2 does not like to be installed to a partition so it does not chainboot as well as old grub did.

---

### Post by Windows Nerd on 2010-09-01
> **rolnics said:**
> How about a separate grub partition? 

I have played around with it but haven't had complete success with what I wanted it to do for it, but given more time I could. I had grub legacy chainloading into other grub menu.lst's so each distro had its own configure grub to boot.

Take a look [here at this thread.]("http://ubuntuforums.org/showthread.php?t=1465772") At the time grub2 was still new and not much on a separate grub partition, but I'm sure there's more now.

[edit] And [here's]("http://http://newyork.ubuntuforums.org/showthread.php?p=8300400") another thread.
I decided to go with this option because it seemed the most simple.

I am following this guide: [http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#grub-mkconfig) 

I made the dedicated Grub2 partition (sda3), and mounted it under /media/GRUB.

```
ubuntu@ubuntu:~$sudo grub-install --root-directory=/media/GRUB /dev/sda
Installation finished. No error reported.
```

So I got Grub installed, looks good, but I have to make my own Grub.cfg, or generate it. Being lazy, I choose to generate it. 


```
sudo grub-mkconfig -o /media/GRUB/boot/grub/grub.cfg
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?)
```

I used grub-mkconfig as opposed to update-grub because I can specify where to generate a Grub.cfg file. (hence the -o option).

Any ideas?

Scott

---

### Post by rolnics on 2010-09-01
I started this reply sometime ago, kids delayed it!!

Anyway back to the subject, I must admit I had problems when I did this, but I can't remember what exactly now as it was sometime ago. My work around was to manually copy the required info out of my working grub.cfg, which at the time was only 3 OS's. Basically then the dedicated grub directly booted the required OS, but it's not an ideal solution. As I said earlier I chainloaded with legacy, as yet I haven't got or had the time to get this working with grub.

---

### Post by oldfred on 2010-09-01
I also just copied entries. 

With old grub you can chainload and that is very easy to set up. 

Since grub2 is in its own partition but does not have the full install I do not know how to get autoupdates. The entry I have above shows how to boot a Ubuntu partition with grub2 without knowing which kernel you want to boot.

Even though you created a grub2 partition, you still have to prevent every install from overwriting the MBR. Your current MBR will point to the grub partition but each install will want to add its own bootloader to the MBR unless you specify otherwise.

---

### Post by Windows Nerd on 2010-09-01
So I got the grub.cfg file to generate:

I rebooted, took all live Cd's out

Greeted by a Grub prompt (Because there was no grub.cfg). Followed the instructions on the Grub wiki.

```
grub>set root=(hdX,Y)
grub>linux /vmlinuz root=/dev/sdXY ro
grub>initrd /initrd.img
grub>boot
```Booted into Ubuntu no problem.

Ran the command again:

```
scott@scott-laptop:~$ grub-mkconfig -o /media/GRUB/boot/grub/grub.cfg
/usr/sbin/grub-mkconfig: You must run this as root
scott@scott-laptop:~$ sudo grub-mkconfig -o /media/GRUB/boot/grub/grub.cfg
[sudo] password for scott: 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-21-generic
Found initrd image: /boot/initrd.img-2.6.32-21-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Ubuntu 8.10 (8.10) on /dev/sda2
done
```

Thanks to you all for your help!

Scott

---

