---
title: "Need desperate help"
date: 2011-04-24
forum: New to Ubuntu
---

### Post by Jbakies on 2011-04-24
I deleted the partition that ubuntu was Installed on since I did not u ubuntu since the my wifi adapter would only run for ten minutes then say disconnected. Any way ihave a ubuntu 10.10 CD and flash drive but no matter what I boot to I the grub rescue> prompt comes up:confused::confused:

---

### Post by Rubi1200 on 2011-04-24
Hi and welcome to the forums :)

Is Windows also installed?

Do you have an installation/recovery CD for Windows?

Is BIOS set to boot from the flash drive?

Please do the following so we can get a better idea of what is going on:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here in a new post. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by Jbakies on 2011-04-24
Yes windows is installed, I don't have a windows recovery disk, yes bios is set to boot from the USB, but i get a blank screen with a blinking underscore as if asking for input but when I type my comp beeps and nothing happens

Thank you for the quick reply, I am typing on my iPad so I will be typing slow

---

### Post by Rubi1200 on 2011-04-24
If you deleted the Ubuntu partition, there may be vestiges of the its bootloader left in the MBR of the drive.

In any event, to get Windows booting again you need to restore its bootloader.

I am not sure why the USB is not booting.

You might consider setting a boot parameter and see if that works:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by Horseboy on 2011-04-24
[I]On your issue that Windows isn't booting, boot into the Installation CD for windows (I'm assuming Vista/7), when it loads put in your language. After that, click on "Repair your Computer" and open a command prompt window. Type in "fixmbr" without the quotes and it will fix the master boot record. After that, you should be able to use Windows again.

[/I][SIZE=4]**NEVERMIND**[/SIZE]
PM me and I'll see if I can help you with your installation disk.

---

### Post by Jbakies on 2011-04-24
I do not understand what todo with the information you gave me

---

### Post by Horseboy on 2011-04-24
Just send me a Private Message: click on my name at the top of the post and "Send Horseboy a Message".

---

### Post by Jbakies on 2011-04-24
What is the command to reset the boot partition to what it was before Linux I think I saw. It somewhere in another thread on another board. I have decided to just keep windows and completely remove linux because my wireless does not work ell on Linux

Also if I can not restore the win 7bootloader can I put grub onto the windows partition instead of the Linux

---

### Post by Hedgehog1 on 2011-04-24
Fix MBR

First, get your PC to boot directly into Windows again:

Y0u can download the ISO Windows Recovery Disks for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-24
To remove & Reuse Ubuntu partitions (you have already done some of this):

[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]


***The Hedge***

:KS

---

### Post by Horseboy on 2011-04-25
To the above responses, this solution has already been mentioned by me, and the OP has also said he doesn't have the disk.

---

### Post by FormatSeize on 2011-04-25
I had a problem like this last week. 
When you get to the grub rescue prompt, type in 
```
ls
```.
 
What do you see?

---

### Post by Hedgehog1 on 2011-04-25
> **Horseboy said:**
> To the above responses, this solution has already been mentioned by me, and the OP has also said he doesn't have the disk.

The beginning of the post explains where to download the ISOs to build the  recovery disks:

*You can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")*


**If you prefer, I can stay out of your threads, however.**


***The Hedge***

---

### Post by Horseboy on 2011-04-25
> **Hedgehog1 said:**
> The beginning of the post explains where to download the ISOs to build the  recovery disks:

*You can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")*


**If you prefer, I can stay out of your threads, however.**


***The Hedge***

I'm sorry, was simply saying that he said he didn't have the disk. And I based my reply on the pictures, didn't read the top of your post.

And you don't have to talk like that (If you prefer, I can stay out of your threads). We all help, chip in etc. I just misunderstood your reply since I didn't actually read it, I based it on pictures.

---

### Post by Hedgehog1 on 2011-04-25
Horseboy,

I do apologize for my tone - sorry - OK if we just keep helping folks and I will be less grumpy?


***The Hedge***

:KS

---

