---
title: "How to operate files in Ubuntu in Windows7?"
date: 2011-01-02
forum: New to Ubuntu
---

### Post by Miter_J on 2011-01-02
I have two OS( Ubuntu and Windows 7), and I&#12288;mounted the disks of Windows so that I could access the disks of Windows in Ubuntu.
But I cannot access the files of Ubuntu in Windows, that makes it very difficult when I wanted to just copy one single file from Ubuntu to Windows.
Does anyone have a solution?

---

### Post by wilee-nilee on 2011-01-02
You can't access Linux from Windows, but you can have a shared ntfs partition. Just know the limitations of the amount of partitions, and types, allowed on a single hard drive before acting. Look at your set up and make sure you can add or change the partitioning before you do.

---

### Post by Miter_J on 2011-01-02
> **wilee-nilee said:**
> You can't access Linux from Windows, but you can have a shared ntfs partition. Just know the limitations of the amount of partitions, and types, allowed on a single hard drive before acting. Look at your set up and make sure you can add or change the partitioning before you do.
Sorry, but I'm afraid that I could not follow you. I'm really new here.
Could you please tell me how to create a shared partition?
Btw, does Ubuntu use ntfs?

---

### Post by cheapie on 2011-01-02
Ubuntu has some support for NTFS. I'd recommend installing [Ext2IFS]("http://fs-driver.org/") inside Windows to accomplish this task.

---

### Post by Miter_J on 2011-01-02
This seems to be good. I'll try it. Thx

---

### Post by rvchari on 2011-01-02
sometimes a particular program for windows (say ext2... as mentioned) may not work. if at all that happens, you have lots of options to install in windows to access your ubuntu. i have done it too, but i can only copy / paste and do things like that, cant actually execute an ubuntu program from windows (as we do thru wine here)

---

### Post by Miter_J on 2011-01-02
> **rvchari said:**
> sometimes a particular program for windows (say ext2... as mentioned) may not work. if at all that happens, you have lots of options to install in windows to access your ubuntu. i have done it too, but i can only copy / paste and do things like that, cant actually execute an ubuntu program from windows (as we do thru wine here)
Yeah. The executing method for Windows and Ubuntu differ from each other.
Whatever, copying and pasting are enough for my task though.

---

### Post by Paqman on 2011-01-02
> **cheapie said:**
> Ubuntu has some support for NTFS. I'd recommend installing [Ext2IFS]("http://fs-driver.org/") inside Windows to accomplish this task.

I'm not sure if i'd trust Ext2IFS to talk to an Ext4 filesystem reliably. Use at your own risk.

A better solution would be to use a shared partition, removable storage such as a USB stick, or a file synchronisation service like Dropbox or Ubuntu One (although Ubuntu One for Windows is currently in Beta)

---

### Post by Miter_J on 2011-01-02
> **Paqman said:**
> I'm not sure if i'd trust Ext2IFS to talk to an Ext4 filesystem reliably. Use at your own risk.

A better solution would be to use a shared partition, removable storage such as a USB stick, or a file synchronisation service like Dropbox or Ubuntu One (although Ubuntu One for Windows is currently in Beta)
Could you please tell me how to make a shared patition?

---

### Post by rvchari on 2011-01-02
miter_j,
if you still have difficulty, then you have to wait. coz i have to go to my win7 and then check out whats that program. i ll copy paste the link or name that particular program.
do let me know if you cant get what you need.
i accessed my windows program file menu, it shows Ext2Fsd... i also remember having install something else, but i ll have to execute from my win 7 to let u know.

honestly speaking windows sucks, i ve kept it just coz i got it as a pre-installed OS and thought it might b handy just in case ubuntu is under maintenance !!! (which never happened till date for more than a few hours !!!)

i m comfortable and happy to connect to my office windows server via samba and doing all my office related jobs.

---

### Post by Miter_J on 2011-01-02
I don't like Windows either but too many softwares that I'm used to use can only run in Windows. I would turn to Linux and throw Windows away step by step. But now I have to use it - = Quite embarrasing.
By the way, I just downloaded the "Linux Reader" you said. But that failed. It seems to scan forever.
If your software still works well, please let me know.
Thank you.

---

### Post by Paqman on 2011-01-02
> **Miter_J said:**
> Could you please tell me how to make a shared patition?

Boot up into your Ubuntu LiveCD and use Gparted (System > Admin > Partition Editor) to shrink one or more of your current partitions to make some space. Then format that space as a new NTFS partition. Both Windows and Linux can read and write to NTFS.

---

### Post by Miter_J on 2011-01-02
> **Paqman said:**
> Boot up into your Ubuntu LiveCD and use Gparted (System > Admin > Partition Editor) to shrink one or more of your current partitions to make some space. Then format that space as a new NTFS partition. Both Windows and Linux can read and write to NTFS.
Paqman, so actually we can take any disk in Windows as a "shared partition" since the file systems used in Windows are almost all NTFS. Right?

---

### Post by Paqman on 2011-01-02
> **Miter_J said:**
> Paqman, so actually we can take any disk in Windows as a "shared partition" since the file systems used in Windows are almost all NTFS. Right?

Yes, any file on your normal Windows NTFS partition is accessible to both OSes. For ease of use you'd probably want to drop it on the root of that partition (which is likely C: ) otherwise you'll have to navigate through the whole convoluted Windows structure to get to your files in Ubuntu.

Creating a new NTFS partition for shared data is just for tidiness, really.

---

### Post by rvchari on 2011-01-02
mitter_j,
my win7 is presently using ext2fsd-0.46. its somewhat working fine. be prepared to the typical windows behaviour, even though it works well, at some point or some time u ll get a blue screen and windows will ask you to report bug or something like that. just ignore that dumb info and restart ur work, u can access it well.

u can also specify and allot a drive letter for the ext3/4 partition. hope u can do this and get what u want.

---

### Post by rvchari on 2011-01-02
miter_j,
perhaps this link should guide u
[http://www.ext2fsd.com/?page_id=16](http://www.ext2fsd.com/?page_id=16)

---

### Post by wilee-nilee on 2011-01-02
> **rvchari said:**
> miter_j,
perhaps this link should guide u
[http://www.**ext2fsd**.com/?page_id=16](http://www.**ext2fsd**.com/?page_id=16)

That is about the last advice that should be given, I'm surprised nobody seriously has called you on this.

Don't let your need to prove this works for me on my system, (which by the way there isn't a version for) out weigh common sense here.

---

### Post by Miter_J on 2011-01-02
Let me switch to Windows and see if it works~
Thank you,rvchari

---

### Post by Miter_J on 2011-01-02
> **rvchari said:**
> miter_j,
perhaps this link should guide u
[http://www.ext2fsd.com/?page_id=16](http://www.ext2fsd.com/?page_id=16)
Sorry, but this doesn't work so well.
It shows the directories in the root directory but there's nothing in those directories. That means that such directories as "home""etc""usr" are visible to me now but they are empty.
By the way, a software called "ext2explorer"(maybe that's the linux reader something... I forget that...) can show me the files in Ubuntu and I can copy files in Ubuntu and save them in Windows. But cannot move files from Windows to Ubuntu.
So I'd like you to tell me how to solve the problem with the ext2fsd. (my version is 0.48 )

---

### Post by rvchari on 2011-01-02
i doubt if you can move files from windows to ubuntu unless u have permissions. y bother for moving files to ubuntu when u can do that from ubuntu itself ?
accessing ubuntu from windows was the criteria and that problem is solved !!!

---

### Post by Miter_J on 2011-01-02
> **rvchari said:**
> i doubt if you can move files from windows to ubuntu unless u have permissions. y bother for moving files to ubuntu when u can do that from ubuntu itself ?
accessing ubuntu from windows was the criteria and that problem is solved !!!
The problem is that in your computer the software "ext2fsd" seems to be working well while in mine it just shows the directories as "empty" and I can do nothing using "ext2fsd" actually. I wonder y...

---

