---
title: "Unable to create new folder in usb drive"
date: 2011-07-11
forum: New to Ubuntu
---

### Post by chandu870114 on 2011-07-11
HI

Am unable to create new folder in USB drive 
when I click create folder it is showing 

> [B]Error while creating directory untitled folder
There was an error creating the directory in /media/chandu.[/B]
when i click show more details
**Error creating directory: No space left on device**And also unable copy files to USB drive.

> [B]Error while copying "One Love - (Bue) - HD 720p.avi".
There was an error copying the file into /media/chandu.
[/B]when i click show more details[B]
Error splicing file: No space left on device[/B]But I have space in my USB drive.

These are my USB details. i got this by using **fdisk -l**
> Disk /dev/sdc: 2032 MB, 2032140288 bytes
63 heads, 62 sectors/track, 1016 cylinders
Units = cylinders of 3906 * 512 = 1999872 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ca8c6

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        1016     1984217    c  W95 FAT32 (LBA)Please help me ,if you have any idea about this problem.

---

### Post by alquery on 2011-07-11
This might not help (I've never experienced this issue before), but could you cd into /media/chandu and post the output of "du -sh"?

---

### Post by chandu870114 on 2011-07-11
> **alquery said:**
> This might not help (I've never experienced this issue before), but could you cd into /media/chandu and post the output of "du -sh"?

[B]chandu@chandu-PC:~$ du -sh
48G    .
[/B]


what is **du -sh???**

---

### Post by alquery on 2011-07-11
> **chandu870114 said:**
> [B]chandu@chandu-PC:~$ du -sh
48G    .
[/B]


what is **du -sh???**

"du" estimates the file space usage in a folder. But right now you are in the wrong folder. You should type in "cd /media/chandu", and then run "du -sh".

---

### Post by westie457 on 2011-07-11
Open your File Browser and click on the USB device to mount it. Look at the bottom line of the window. There you will see how much space is available. An example is attached.

---

### Post by alquery on 2011-07-11
> **westie457 said:**
> Open your File Browser and click on the USB device to mount it. Look at the bottom line of the window. There you will see how much space is available. An example is attached.

I'd like them to run "du -sh" because it might report errors that tell me if there's something wrong with the filesystem itself.

---

### Post by chandu870114 on 2011-07-11
> **alquery said:**
> I'd like them to run "du -sh" because it might report errors that tell me if there's something wrong with the filesystem itself.

after going into media/chandu , 

du -sh gave me below output
 
> 86M    .


---

### Post by chandu870114 on 2011-07-11
> **westie457 said:**
> Open your File Browser and click on the USB device to mount it. Look at the bottom line of the window. There you will see how much space is available. An example is attached.

Thanks for your response but my problem is different I'm unable to create new folder

---

### Post by chandu870114 on 2011-07-11
Thanks for your response guys

I just now copied my total data from USB drive to other location and unmounted,formated my USB drive. Now am able create new folder and successfully copied one file into USB drive.

Anybody have any idea why I got this problem??
and 
How it solved by formating USB drive??

---

### Post by alquery on 2011-07-11
> **chandu870114 said:**
> Thanks for your response guys

I just now copied my total data from USB drive to other location and unmounted,formated my USB drive. Now am able create new folder and successfully copied one file into USB drive.

Anybody have any idea why I got this problem??
and 
How it solved by formating USB drive??

Good to know it's now working :)

Maybe it was just some error with the filesystem, maybe pulling it out too early and a file didn't get synchronized correctly, and the part of the filesystem that stored the space usage of the device was reporting wrong, etc. When you ran the "du" command it surprised me by not giving any errors. Maybe then it's a bug with nautilus, the file manager. I really don't know. But what you did fixed it :P

---

### Post by chandu870114 on 2011-07-12
> **alquery said:**
> Good to know it's now working :)

Maybe it was just some error with the filesystem, maybe pulling it out too early and a file didn't get synchronized correctly, and the part of the filesystem that stored the space usage of the device was reporting wrong, etc. When you ran the "du" command it surprised me by not giving any errors. Maybe then it's a bug with nautilus, the file manager. I really don't know. But what you did fixed it :P


Ya I think it is bug with nautilus, file Manager. When I try to remove USB drive safely, It showed me 

[B]Volume is busy
My computer
nautilus[/B]

Then I restarted my system and connected USB drive agian then also while removing I faced same error.:confused:

---

### Post by variona on 2011-07-12
Did you look for hidden files? (in linux these start with .)
Maybe your trash was full (look for a folder called .trash)

HTH

---

### Post by chandu870114 on 2011-07-12
> **variona said:**
> Did you look for hidden files? (in linux these start with .)
Maybe your trash was full (look for a folder called .trash)

HTH

Sorry variona  :sad:
Now it is not possible to look becuase I formated that USB drive. After formating I didn't face any problem.

---

### Post by chandu870114 on 2011-07-12
> **variona said:**
> Did you look for hidden files? (in linux these start with .)
Maybe your trash was full (look for a folder called .trash)

HTH

Thanks veriona

I don't know about hidden files and Trash. After your reply I just looked into those files. 

Maybe Trash was full or 
It's bug with nautilus, file manager.

---

### Post by alquery on 2011-07-12
If it's working now, please take the time to mark the thread as solved (at Thread Tools menu) :)

---

