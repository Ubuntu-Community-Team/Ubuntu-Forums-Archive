---
title: "Dual Boot"
date: 2011-04-19
forum: New to Ubuntu
---

### Post by yurbeen on 2011-04-19
I have just installed Ubuntu 10.10 alongside Windows 7.
Why does it appear that Windows 7 has been removed from my computer?

When I reboot there is no Windows 7 option; it automatically runs Ubuntu.
And when I enter 'sudo fdisk -l' into the terminal this is the result:

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009e0c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       59272   476097536   83  Linux
/dev/sda2           59272       60802    12285953    5  Extended
/dev/sda5           59272       60802    12285952   82  Linux swap / Solaris

```
[IMG]http://ubuntuforums.org/screenshot.png[/IMG]

---

### Post by yetiman64 on 2011-04-19
Try running the code,
```
sudo update-grub
``` then do a reboot and see if it shows up in the grub list.

If it doesn't let us know and we can look for more serious boot problems. I have seen here a few times the code above fix your situation. Unless a serious error has been made during the install proceedure Windows is likely to still be there untouched.

Edit: just noted the fdisk output, it looks like you have told the installer to use the whole disk in which case Windows is gone. Sorry, ignore the first code, it is useless.

---

### Post by yurbeen on 2011-04-19
I'm afraid I may have made my problem worse by following instructions on another thread. 
It advised for when the grub options do not appear on the computer's start up to delete a folder called /boot.
I deleted this folder and now when I reboot I get a message saying:

error: file not found.
grub rescue>

And I cannot run either operating system.
I'm currently running Ubuntu off my installation CD

---

### Post by yurbeen on 2011-04-19
> Edit: just noted the fdisk output, it looks like you have told the  installer to use the whole disk in which case Windows is gone. Sorry,  ignore the first code, it is useless. 	

I am sure I didn't do this. I definitely set the slider so that ubuntu only took up a fraction of my computer's memory.

---

### Post by Chrissd on 2011-04-19
Hi,
If you reinstall Grub2 that will get your computer loading from the hard drive again. Do you have two hard drives perchance?

---

### Post by yetiman64 on 2011-04-19
> **yurbeen said:**
> I am sure I didn't do this. I definitely set the slider so that ubuntu only took up a fraction of my computer's memory.

> **yurbeen said:**
> I'm afraid I may have made my problem worse by following instructions on another thread. 
It advised for when the grub options do not appear on the computer's start up to delete a folder called /boot.
I deleted this folder and now when I reboot I get a message saying:

error: file not found.
grub rescue>

And I cannot run either operating system.
I'm currently running Ubuntu off my installation CD

Deleting /boot will have nothing to do with the fdisk output, it serves only to mess up Ubuntu booting.
You have absolutely no windows partitions in your fdisk output. You have  overwritten Windows according to that output even if inadvertently.

I don't know exactly how you can fix the removal of /boot, wait here for  further advice on that, though I suspect it may be fixable using the  live cd and by doing a chroot into the installation where you can put in  a new /boot folder and go online and reinstall the kernel images etc. Then reinstall grub itself. I expect if it is fixable it will be quite complex, probably a bit beyond my scope of helping.

Question: Do you have a  Windows installation CD (if so, GOOD) or did  your setup rely on a recovery partition (if so, OUCH!, it is gone)?

Edit: @ Chrissd, it seems the OP has removed /boot which contains kernel images, system maps etc, not just /boot/grub. Also "sudo fdisk -l" will list multiple hard drive details.

---

### Post by yurbeen on 2011-04-19
Is there at least a chance that I can get my computer running to it's pre-ubuntu state?

And I only have one hard drive.

---

### Post by yetiman64 on 2011-04-19
> **yurbeen said:**
> Is there at least a chance that I can get my computer running to it's pre-ubuntu state?

And I only have one hard drive.

Yes, but you will need a Windows installation DVD. Any recovery partitions on that drive are no longer in existence.

---

### Post by yurbeen on 2011-04-19
Thanks for the help guys :(
Is all data lost from my computer?

---

### Post by yetiman64 on 2011-04-19
> **yurbeen said:**
> Thanks for the help guys :(
Is all data lost from my computer?

If you mean in the Windows partition, yes sorry to say, as it has been overwritten by the Ubuntu installation.

Anything in the Ubuntu install is accessible from a live cd and can be saved to external media. But I suspect you may not have much to recover from Ubuntu if it is a recent install.

---

### Post by tusharbmw on 2011-04-19
I am also facing similar problem. Used to dual boot windows 7 and Ubuntu.
Here is output of my fdisk:
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x51b6df45

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9729    78142464    7  HPFS/NTFS
/dev/sda2            9729       24322   117216256    7  HPFS/NTFS


I am not able to update grub
ubuntu@ubuntu:~$ sudo update-grub
/usr/sbin/grub-probe: error: cannot find a device for / (is /dev mounted?).


can anyone assist?
I only have udntu live CD.

Thanks and Regards,
-Tushar

---

### Post by sanderd17 on 2011-04-19
All files that are overwritten (or partly overwritten) are lost (unless you ask the FBI to recover those things). But if you really care about your data, maybe you can recover a part. Check this [http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/](http://www.howtogeek.com/howto/15761/recover-data-like-a-forensics-expert-using-an-ubuntu-live-cd/) to see how to recover a part of your data.

@Tusharbmw: your problem will probably be fixable. You still have NTFS partitions (but weird enough, I don't see an ubuntu partition). Please make another thread for that and link to the other thread from here.

---

### Post by tusharbmw on 2011-04-19
Thanks, I created : [http://ubuntuforums.org/showthread.php?t=1733322](http://ubuntuforums.org/showthread.php?t=1733322)

I used to wubi for ubuntu installation.

Regards,
-T

---

### Post by yetiman64 on 2011-04-19
> ...You still have NTFS partitions (but weird enough, I don't see an ubuntu partition)...@ sanderd17. Some people mistake a wubi install for dual booting, it is booting Ubuntu from within a file on the Windows NTFS partition, hence when fdisk is run you don't see any Linux filesystems. That mistake and wubi not being mentioned has caused me a couple of headaches while helping out here in the past.

@ tusharbmw. Just to clarify your situation. Is it a Wubi install ?

Edit: tushabmw, we posted roughly at the same time. You have answered what I asked. I'll have a quick check of your thread, but I really don't use Wubi at all myself. Good luck.

---

