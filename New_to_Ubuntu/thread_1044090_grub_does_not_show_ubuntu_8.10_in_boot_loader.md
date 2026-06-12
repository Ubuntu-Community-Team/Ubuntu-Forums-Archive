---
title: "grub does not show ubuntu 8.10 in boot loader"
date: 2009-01-19
forum: New to Ubuntu
---

### Post by tavati on 2009-01-19
i have two IDA disks. 40gb(master) and 300gb(slave & new drive). 
i have win xp on master. i installed 8.10 by creating primary partition on slave to mount on '/' and rest all logical partitions on slave and mounted on '/boot', 'home' etc. grub also loaded fine. but after installation, when i restarted the machine, grub only showed the following

[I]ubuntu 8.10, memtest86+

Other operating systems

Windows XP Professiional[/I]

but where is my ubuntu ? 
when is select the first line and press 'enter' memtest starts but no ubuntu.

---

### Post by unikuser on 2009-01-19
One possibility is that grub would have been installed on slave disk and left master intact.
* Try changing boot order(f8 ..) and boot from slave. 
* Try manually boot from grub menu(press c) and then change grub the way you want. 

[https://help.ubuntu.com/community/GrubHowto#Manually boot into a Linux OS](https://help.ubuntu.com/community/GrubHowto#Manually boot into a Linux OS)

---

### Post by bumanie on 2009-01-19
Boot up a live ubuntu cd and post the output of > sudo fdisk -luThis will list your dives and partitions and will be helpful for those wishing to help :).

---

### Post by caljohnsmith on 2009-01-19
Did you by chance install Ubuntu from a CD that came in a recent Linux magazine? I can't remember the exact name of the magazine, but the bottom line is that the CD that comes with it is unfortunately corrupt; if you install Ubuntu with that CD, the result is exactly what happened to you, namely the Ubuntu kernels fail to install so you only get the "memtest86+" option on start up. 

But if that's not your case, how about booting your Live CD (the Ubuntu install CD), download the [Boot Info Script]("https://sourceforge.net/projects/bootinfoscript/") to your Ubuntu desktop, open a terminal (Applications > Accessories > Terminal) and do:
```
sudo bash ~/Desktop/boot_info_script*.sh
```
That will create a "RESULTS.txt" file in the same directory from where the script is run, namely your desktop; please copy/paste the contents of that file to your next post, highlight the copied text, and click the pound sign # graphic in the Ubuntu forum message box so that the text will get "code" tags put around it. The results of that script will help clarify your setup and hopefully what your booting problem might be.

---

### Post by tavati on 2009-01-19
i think u r right. i have the magazine cd and it must be corrupt.
one more thing, i installed ubuntu studio 8.10 and it is installing only text mode and if i try anything else it is hanging up. thanks !! i will install gutsy or is it gusty ?

---

