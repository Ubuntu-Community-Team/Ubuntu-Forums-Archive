---
title: "&quot;Gave up boot waiting for root device&quot; Boot fails..."
date: 2009-04-16
forum: New to Ubuntu
---

### Post by 11010110 on 2009-04-16
Hi everyone, 

I ran a few updates and after a few hours, I decided to restart my computer. Upon rebooting, Ubuntu progress bar did not fill and after about 10 seconds it displayed a page followed by an initramfs prompt. 

The page displayed was:


```
    Booting 'Ubuntu 8.10. kernel 2.6.27-11-generic'
Filesystem type is ntfs, partition type 0x87
the current working directory(i.e., the relative path) is /ubuntu/disks
    [Linux-bzimage, setup=0x3000,size=0x222010]
    [Linux-intrid @ 0x7eed8000, 0x7e7998 bytes]
Loading, please wait...
Gave up waiting for root device. Common problems:
  - Boot args (cat /proc/cmdline)
    - Check rootdelay= (did the system not wait long enough?)
    - Check root= (did the system wait for the right device?)
  - Missing modules (cat /proc/modules; 1s /dev)
ALERT! /dev/disk/by-uuid/ACFCBDCFFCBD9304 does not exist. Dropping to a shell!


BusyBox v1.10.2 (Ubuntu 1:1.10.2-1ubuntu7) built-in shell (ash)
Enter 'help' for a list of built-in commands,

(initramfs) _

```


I have absolutely no idea what this means or what to do to get my computer working again. I am running a WUBI boot from Windows Vista so in the mean time i am running that but thats more frustrating than having nothing lol. 

Thanks a lot in advance everyone! any information is very appreciated!

---

### Post by 11010110 on 2009-04-16
I saw another thread that had the same problem as me but and said just type exit and it should boot but that did not work for me... 

Thanks again in advance

---

### Post by presence1960 on 2009-04-16
> **11010110 said:**
> bump.

Sorry I can't help you. I have never used wubi or even seen it. Therefore I am not qualified to say anything.

It is community policy to bump a thread **_ONLY_**after 24 hours of no replies. We do this on our free time, this is not paid support, but the support you will get here is by far so superior. Someone who can help you maynot be online now or hasn't come upon your thread yet.

---

### Post by theozzlives on 2009-04-16
Did it update the kernel?

---

### Post by 11010110 on 2009-04-16
I dont believe the kernel was updated. Some of the updates did not complete because my drive was 100% full. I cleared some space and restarted and now this... So unless a kernel update was put out and i didnt notice in the past week then no. It did not ask me to restart i did so a few hours after updating. 

Thanks for the replies so far everyone!

---

### Post by 11010110 on 2009-04-17
Could it possibly be because some of the updates that I was trying to install were interrupted due to the lack of space on the vitrual drive? Could one update have been mid way though and then could not finish leading to system instability?

Thanks again everyone.

---

### Post by 11010110 on 2009-04-19
I still haven't found any solutions. Sometimes if some people waited a while and typed exit at the initramfs prompt it booted fine but that didn't work here... could it be a different problem than the others?

---

### Post by 11010110 on 2009-04-20
bump

---

### Post by mikechant on 2009-04-20
> Could it possibly be because some of the updates that I was trying to install were interrupted due to the lack of space on the vitrual drive? Could one update have been mid way though and then could not finish leading to system instability?

Yes, and yes!

Normally there's various checks/cleanups you could try in the package manager but if you can't boot in the first place...you might have to back up your data in /home and anything else critical (assuming you can access it from Windows? I haven't used Wubi myself) and reinstall. However, don't rush into it. There might be something you can do about this:
> ALERT! /dev/disk/by-uuid/ACFCBDCFFCBD9304 does not exist. Dropping to a shell!

I know how to fix UUID problems for standard Ubuntu installs, but I don't know how it works with wubi, where the UUID isn't associated with a real partition.

Anyhow as I said don't rush into anything drastic, hopefully someone with some wubi experience will comment.

---

### Post by 11010110 on 2009-04-20
thanks for the reply. Yeah i dont know the wubi specific details with regards to UUID either. there are programs that allow ext3 to be read by windows so i think i will go in and recover what i can. Worst come to worst ill scrap it after the recovery once Jaunty comes out! ive been wanting to try ext4 anyways! 

Thanks again!

---

### Post by 11010110 on 2009-04-22
bump

---

### Post by 11010110 on 2009-04-24
Hopefully someone with a good amount of knowledge about Wubi sees this. 

Thanks again in advance everyone

---

### Post by AndreLeComte on 2010-01-02
I have the same issue but I didn't use WUBI. Any resolution now?

---

### Post by nibbslang on 2010-03-03
I have the same problem, won't boot up today, been fine in the past and just decided to die.

Will watch this thread with the hope that someone known how to get it to boot.

---

### Post by jthirt on 2010-03-05
If you have not yet found the solution, check [this]("http://ubuntuforums.org/showthread.php?t=1399810") post.

It solved my problem that appears to be the same.

BTW, my install has nothing to do with WUBI. It's a dual boot 'on top' of an original Windows 7 setup.

Good luck!

JT

---

