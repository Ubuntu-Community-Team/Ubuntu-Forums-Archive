---
title: "Dual booting's problems (Vista installed 1st then Ubuntu)"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by amjjawad on 2009-10-31
Hello everyone,

This is my 1st day with Ubuntu after 10 years with Windows. I had some problems but looks like I fixed some and still have some to be fixed.

Here are my problems:

1) I used my Vista's DVD to fix my MBR [ bootrec/fixboot and bootrec/fixmbr] so Vista is loading before Ubuntu only if I choose "Vista" from the booting list. Problem/question is, How can I get rid of that list and make Vista loading without choosing it? is the only way to do that is to format or uninstall Ubuntu? my guess is YES but just need to check with someone who has more experience than me :)

2) How to uninstall Ubuntu? can I do that by deleting Ubuntu's partitions from Windows>Disk Management? or there's another trick for that?
The reason why I want to get rid of Ubuntu is bcoz during the installation, I did a mistake and I lost a partition with 200GB and I can't read it neither by Windows nor Ubuntu. Also bcoz I want to read more about Linux before I use it.

3) My Windows's filing system is NTFS while my Ubuntu's filing system is ext4. They can't read each other so is there any way I can access my Ubuntu's partitions from Windows and/or access my Windows's partitions from Ubuntu? I'm planning to install new copy in case someone will answer my 2nd Q :)

4) I've been told earlier in this forum that it's better to let Ubuntu do the partitioning job. Before I installed Ubuntu, I made 4 partitions (root,swap,home,date) using Disk Management under Windows but looks like it's not the right way to do that. IN CASE I must let Ubuntu do the job OR I have to do that DURING Ubuntu's installation, HOW CAN THIS BE DONE?


Thank you :)

---

### Post by Schendje on 2009-10-31
Hi, and welcome to Ubuntu! :D

I'll try to answer some of your questions...

> **amjjawad said:**
> 1) I used my Vista's DVD to fix my MBR [ bootrec/fixboot and bootrec/fixmbr] so Vista is loading before Ubuntu only if I choose "Vista" from the booting list. Problem/question is, How can I get rid of that list and make Vista loading without choosing it? is the only way to do that is to format or uninstall Ubuntu? my guess is YES but just need to check with someone who has more experience than me :)
I'm not sure I understand... Doesn't fixmbr remove GRUB?

If it does, you don't have the option to boot Ubuntu anymore, do you?

If it doesn't, you can install Startup Manager in Ubuntu (it's in the Software Center) to change the default booting operating system.

Don't worry, you won't have to remove Ubuntu to let it boot automatically into Windows. :)

> **amjjawad said:**
> 
2) How to uninstall Ubuntu? can I do that by deleting Ubuntu's partitions from Windows>Disk Management? or there's another trick for that?
The reason why I want to get rid of Ubuntu is bcoz during the installation, I did a mistake and I lost a partition with 200GB and I can't read it neither by Windows nor Ubuntu. Also bcoz I want to read more about Linux before I use it.

Well, yeah, one of the ways is to delete the partitions. It'll be gone for sure, but you'll probably have to fix your bootloader (by using the fixmbr method you mentioned earlier).

Could you provide some more information about your lost partition? That sounds like a serious problem.

> **amjjawad said:**
> 
3) My Windows's filing system is NTFS while my Ubuntu's filing system is ext4. They can't read each other so is there any way I can access my Ubuntu's partitions from Windows and/or access my Windows's partitions from Ubuntu? I'm planning to install new copy in case someone will answer my 2nd Q :)
From Ubuntu you can automatically access Windows partitions, but not the other way around. The only way to do so would be to use an ext3 filesystem, but even if you did Windows would need extra drivers since they're not included by default.

> **amjjawad said:**
> ]
4) I've been told earlier in this forum that it's better to let Ubuntu do the partitioning job. Before I installed Ubuntu, I made 4 partitions (root,swap,home,date) using Disk Management under Windows but looks like it's not the right way to do that. IN CASE I must let Ubuntu do the job OR I have to do that DURING Ubuntu's installation, HOW CAN THIS BE DONE?

During installation, the Partition Editor pops up. You can either let Ubuntu create its own partitions, or choose "manual" if you want to do it yourself. It'll open the partition editor if you do.

Hope these tips help.

---

### Post by amjjawad on 2009-11-01
Hi and thank you for everything :)

1) Yes, looks like bootrec/fixboot and bootrec/fixmbr can remove GRUB (Ubuntu loader) and get Windows loader back but still there's a booting list and you need to choose between Windows and Ubuntu. You know what happened after I used the above two commands to fix MBR? I was unable to boot into Ubuntu so I had to delete the partitions where Ubuntu was installed and after that I didn't get that booting list anymore ;)


2) I didn't get any reply on my Q so I couldn't wait :P I deleted the partitions where Ubuntu was installed, create new partitions, formatted them to NTFS and I got 2 empty partitions now waiting for me to fill them :)

I lost that partition coz I chose the wrong option (mount) during Ubuntu installation. Looks like the only way to get it back is to delete the partitions using "Disk Management" which comes with Windows.


3- I was unable to read my Windows NTFS partitions from Ubuntu. I know I can't read Ubuntu's partitions from Windows coz they're ext3 or ext4 (which I chose during installation) but problem was accessing the NTFS partitions from Ubuntu and that was impossible!
For future reference, what file system I must use when I install Ubuntu? can I use FART32 or that's not possible? FAT32 will make it possible to access these partitions from Windows but I'm not sure if Ubuntu will accept that during the installation? 

4- If I will let Ubuntu do that, that means the 1st option (use the entire disk) or the 3rd(use the largest continuous space)? 
and if I want to go for "manual" what should I do? I started new thread about this issue [[http://ubuntuforums.org/showthread.php?p=8212044#post8212044]](http://ubuntuforums.org/showthread.php?p=8212044#post8212044]) and I really need some answers/solutions for this problem!


Thank you so much :)

---

### Post by seshomaru samma on 2009-11-01
In the partition part you should choose Manual 
look at the attached picture

format Ubuntu as ext3
you have an NTFS data partition right? Ubuntu should be able to see it

---

### Post by amjjawad on 2009-11-01
I swear I know that :D
I just want to know HOW to do it after I choose that option ;)

---

### Post by seshomaru samma on 2009-11-01
sorry :-)
[here]("http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition")'s a good howto for manual partition

---

### Post by gn2 on 2009-11-01
[EasyBCD]("http://neosmart.net/dl.php?id=1") might be useful.

---

### Post by Rambar on 2009-11-01
You may want to check this thread:

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)


I am having simmilar issues, somehow I have 3 linux installations under my linux partition (???) and I dont really know what happened there.

---

### Post by amjjawad on 2009-11-01
> **seshomaru samma said:**
> sorry :-)
[here]("http://www.howtoplaza.com/how-to-install-ubuntu-904-on-a-manually-created-partition")'s a good howto for manual partition

Still now what I "exactly" want but THANK YOU SO MUCH :)
I'll go a head with the installation and see what will happen, hahah

---

### Post by amjjawad on 2009-11-01
> **Rambar said:**
> You may want to check this thread:

[http://ubuntuforums.org/showthread.php?t=508927](http://ubuntuforums.org/showthread.php?t=508927)


I am having simmilar issues, somehow I have 3 linux installations under my linux partition (???) and I dont really know what happened there.

Actually I fixed that in much easier way!
You need Vista's DVD, use "bootrec/fixboot" and "bootrec/fixmbr" to restore your MBR, then after you restart your PC (don't forget to remove the DVD from your driver), right click on my computer>manage>disk management>delete the partitions where Ubuntu was installed, after that you need to fix the partitions so you can use them under Windows.

If I'm not wrong, I wrote that somewhere :P

---

### Post by Rambar on 2009-11-01
I fear I'm going to have to do that sooner or later and make a fresh install aferwards. Although my Vista DVD must be somewhere around my parent's home which is.... thousands of Kms away :).

---

### Post by amjjawad on 2009-11-01
> **Rambar said:**
> I fear I'm going to have to do that sooner or later and make a fresh install aferwards. Although my Vista DVD must be somewhere around my parent's home which is.... thousands of Kms away :).

It's better to do that coz you have 3 installation as you said which is a lot of mess if you ask me :)

Golden rule: ALWAYS make sure to have TWO copies of your "important CDs/DVDs" in case one of them is lost, damaged, somewhere else, etc, you don't have to worry about anything ;)

---

### Post by amjjawad on 2009-11-01
Ok, I installed Ubuntu and without losing any partition this time ;)

I just need to know how to use Wubi. I checked this site [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi) but it doesn't explain it clearly.

---

### Post by Schendje on 2009-11-01
> **amjjawad said:**
> Ok, I installed Ubuntu and without losing any partition this time ;)

I just need to know how to use Wubi. I checked this site [http://www.psychocats.net/ubuntu/wubi](http://www.psychocats.net/ubuntu/wubi) but it doesn't explain it clearly.
Great! 

But, Wubi is just a different way of installing Ubuntu. If you've already installed it using the Live CD and it's on a different partition, you don't even have to touch Wubi. :)

//Edit: clarification:

**1. "Real" install**
  - By **booting from** the Live CD
  - Ubuntu is installed in a **new partition**
  - Ubuntu is a **separate** installation (so you can remove Windows)

**2. Wubi install**
  - By running the Live CD **while Windows is on**
  - Ubuntu is installed **inside Windows**, in one huge file
  - Ubuntu **isn't a separate** installation
  - Advantage is no messing with partitions

---

### Post by amjjawad on 2009-11-01
Well, I started with Wubi but chose different partition so basically the outcome ain't "Wubi" installation :)

I went through option 1 and Ubuntu is up and running (even though I'm still using Vista now :P)

I just have one more silly Q to close this subject :)

If I'll use Wubi, install Ubuntu inside drive (C) where Vista is installed, both Windows and Ubuntu in one drive and one partition (same), and no messing with partitions, that's understood but my Q is:

Is it 100%like installing any program under windows? install and uninstall Ubuntu anytime I want?
Will that harm and/or remove/delete any Windows installation/file or it's safe to do that? sorry but I've never tried it before :(

If I'm going to use Wubi and install Ubuntu, so is this installation like a virtual Ubuntu installation or it will be exactly the same if I'll go for option1 you mentioned?


Thank you so much :)

P.S.
I need to know that in case I want to install Ubuntu again and/or teach one of my friends how to do it ;)

---

### Post by Schendje on 2009-11-01
Yes, one of the advantages of Wubi is that you can easily remove Ubuntu just like any other program. Of course, it's a really, really big program and all your settings in Ubuntu will be lost if you remove it. But I think that's obvious. ;)

Think of Wubi as a virtual partition inside your Windows partition. It won't mess around with Windows at all. It'll have all of the features of a regular Ubuntu install, though.

---

### Post by amjjawad on 2009-11-01
Aha, that's great to know, thanks a lot :)

I think it's very good option for those who don't want really to go deep and bother themselves with partitions and stuff + it's very helpful for those with ONE partition only (don't want or don't know how to create partitions).

My Vista partition is 40GB so maybe this won't be enough for Ubuntu. I was just curious about Wubi and I'm sure I don't need to use it ;) but I'll teach my friends, those who don't know how to create partitions!

Thank you so much :D

---

### Post by Schendje on 2009-11-01
> **amjjawad said:**
> Aha, that's great to know, thanks a lot :)

I think it's very good option for those who don't want really to go deep and bother themselves with partitions and stuff + it's very helpful for those with ONE partition only (don't want or don't know how to create partitions).

My Vista partition is 40GB so maybe this won't be enough for Ubuntu. I was just curious about Wubi and I'm sure I don't need to use it ;) but I'll teach my friends, those who don't know how to create partitions!

Thank you so much :D
You're welcome!

What you said is indeed what it's meant for. Both Vista and Ubuntu on a 40GB partition is possible, but it'll be tight. ;)

---

