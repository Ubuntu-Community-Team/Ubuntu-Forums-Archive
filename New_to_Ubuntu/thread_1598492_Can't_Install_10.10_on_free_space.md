---
title: "Can't Install 10.10 on free space"
date: 2010-10-16
forum: New to Ubuntu
---

### Post by EpikRageQuit on 2010-10-16
I was following directions posted in this link...[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

and i am now installing via disk... I shrank the windows partition leaving 220 GB of free space... And I can't install 10.10 to the free space it gives me this warning when I try... "No root file system is defined. Please correct this from the partitioning menu." Now I am starting to think I needed to create some sort of directory or name with the space I freed and I didn't Any advice is helpful... I started this problem yesterday at another help post ======>   [http://ubuntuforums.org/showthread.php?t=1597816](http://ubuntuforums.org/showthread.php?t=1597816)

Any Help is greatly appreciated!

---

### Post by Hippytaff on 2010-10-16
did you use a live cd...and did you choose the manual partition option?

or is it a wubi install?

---

### Post by EpikRageQuit on 2010-10-16
> **Hippytaff said:**
> did you use a live cd...and did you choose the manual partition option?

or is it a wubi install?

Okay so I had installed through wubi, couldn't expand partition so I uninstalled it. Now all day i have downloaded and burnt an iso of 10.10 amd64, and I shrank the size of the c drive in windows, booted from the cd and now I am trying to install ubuntu on the free space I created by shrinking the c drive but the setup is saying it is unusable. AND yes I choose manual because I want to keep windows 7. I did this to have a true dual boot.

---

### Post by Hippytaff on 2010-10-16
so you get to the point at installation where you get the option to wipe your entire harddirve and os's or partition?...where does it say its unusable? :-)

---

### Post by EpikRageQuit on 2010-10-16
> **Hippytaff said:**
> did you use a live cd...and did you choose the manual partition option?

or is it a wubi install?

> **Hippytaff said:**
> so you get to the point at installation where you get the option to wipe your entire harddirve and os's or partition?...where does it say its unusable? :-)
I click manual then it displays this screen giving me the option to install on, either /dev/sda1, /dev/sda2, /dev/sda3, unusable, /dev/sda4. they are displayed in a chart and I click the unusable and it reads an error when I click install saying "No root file system is defined. Please correct this from the partitioning menu"

---

### Post by sandyd on 2010-10-16
> **EpikRageQuit said:**
> I click manual then it displays this screen giving me the option to install on, either /dev/sda1, /dev/sda2, /dev/sda3, unusable, /dev/sda4. they are displayed in a chart and I click the unusable and it reads an error when I click install saying "No root file system is defined. Please correct this from the partitioning menu"

you have to set the partiton to mount to "/". If you click "properties" or "edit" on the partition, you should be able to set the mount point to "/"edit: just choose use largest block of free space. its easier, because then it creates your swap as well.

---

### Post by EpikRageQuit on 2010-10-16
> **sandyd said:**
> you have to set the partiton to mount to "/". If you click "properties" or "edit" on the partition, you should be able to set the mount point to "/"edit: just choose use largest block of free space. its easier, because then it creates your swap as well.

Uhmm... Is there a way to screenshot what I see so I can show you where I am because I'm not sure we are on the same page..?

EDIT ** Attached

---

### Post by qamelian on 2010-10-16
It looks to me like you have 4 primary partitions plus the unused space. That would be the problem. You can only have 4 primary partitions per physical disk. To install to this drive, you would need to rethink your partitioning scheme for this disk or else add another physical HDD.

---

### Post by EpikRageQuit on 2010-10-16
> **qamelian said:**
> It looks to me like you have 4 primary partitions plus the unused space. That would be the problem. You can only have 4 primary partitions per physical disk. To install to this drive, you would need to rethink your partitioning scheme for this disk or else add another physical HDD.

OH... So if there was only 3 I could of added a partition and called it whatever and installed ubuntu on it right?

---

### Post by Hippytaff on 2010-10-16
you needc to have one partition set up as just / then you should have your root partition

---

### Post by EpikRageQuit on 2010-10-16
> **Hippytaff said:**
> you needc to have one partition set up as just / then you should have your root partition

Okay so I can go into Windows, remove/merge a partition come back to the boot cd and create a pertition called "/" and I should be able to install normally right?    

Don't know how safe/smart it is to remove or merge windows partitions though. If I just got rid of the recover one I should be okay, just if it ever messes up I will be screwed right?

---

### Post by Hippytaff on 2010-10-16
> **EpikRageQuit said:**
> Okay so I can go into Windows, remove/merge a partition come back to the boot cd and create a pertition called "/" and I should be able to install normally right?    

Don't know how safe/smart it is to remove or merge windows partitions though. If I just got rid of the recover one I should be okay, just if it ever messes up I will be screwed right?

Whenever you partition you should back everything up...and it's probably worth defragging windows before you partition...but yes it can go **** up, but having said that it could be worse...make sure anything thats important to you is on cd or dvd and go for it

---

### Post by EpikRageQuit on 2010-10-16
> **Hippytaff said:**
> Whenever you partition you should back everything up...and it's probably worth defragging windows before you partition...but yes it can go **** up, but having said that it could be worse...make sure anything thats important to you is on cd or dvd and go for it

Alright gonna transfer files to another computer then try, defrag, remove recovery, then install ubuntu, once thats done, gonna try Windows 7 and see if it still works...

---

### Post by arubislander on 2010-10-16
You already have lots of free space, there is no need to defrag anything. Especially not any partition that you're going to be deleting anyway.

---

### Post by Quackers on 2010-10-16
There is likely to be a program on your pc to make a set of recovery discs. I would make those first, maybe even 2 sets.

---

### Post by Hippytaff on 2010-10-16
> **arubislander said:**
> You already have lots of free space, there is no need to defrag anything. Especially not any partition that you're going to be deleting anyway.

Don't think the op is intending on deleting anything !? :-s

---

### Post by arubislander on 2010-10-16
> **Hippytaff said:**
> Don't think the op is intending on deleting anything !? :-s
If the OP wants to install Ubuntu on the hard drive containing the 4 primary partitions the OP will have no choice but to delete one.

---

### Post by Hippytaff on 2010-10-16
> **arubislander said:**
> If the OP wants to install Ubuntu on the hard drive containing the 4 primary partitions the OP will have no choice but to delete one.

good point

---

### Post by EpikRageQuit on 2010-10-16
> **Hippytaff said:**
> Whenever you partition you should back everything up...and it's probably worth defragging windows before you partition...but yes it can go **** up, but having said that it could be worse...make sure anything thats important to you is on cd or dvd and go for it


Okay, that WAS an adventure! So I deleted a partition after moving the files on it to a different one. Now when I create the partition to install ubuntu on what options should I select .... ATTACHMENT shows what I think I should have... please let me know so I don't do it wrong, thanks.

---

### Post by sandyd on 2010-10-16
> **EpikRageQuit said:**
> Okay, that WAS an adventure! So I deleted a partition after moving the files on it to a different one. Now when I create the partition to install ubuntu on what options should I select .... ATTACHMENT shows what I think I should have... please let me know so I don't do it wrong, thanks.
how much RAM do you have?
If you have enough, you don't need a swap file.
however, if you want to hibernate, you have to have one.
typically, if you want to hibernate, the swap space must be as large as your RAM
so, if you have 2GB ram, do 221694 (subtract it properly, don't use what I just did)(1024mb = 1gb) for the current partition your about to create and 2000 for the swap partition.

However, if you don't need to hibernate, but still want to have swap space (swap space is sorta like the windows paging file), I would reccomend using 1GB swap.

Therefore, the size of the partiton you would create in that case would be 222694mb
and create a swap using the 1GB free space thats left.

and you can ignore everything I said, and click "ok" if you don't need a swap file

---

### Post by EpikRageQuit on 2010-10-16
Going to mark this solved and start a new thread because I solved the way how to put ubuntu on the space. Now i will start the another thread about creating a partition.. THANKS for everyone's  help GREATLY appreciated!

---

### Post by Peterfc on 2010-10-22
Hi i have a similar problem. I have just tried to install 10.10 on a 250Gb drive with one partition for windows and free space as 2.3GB. i can't figure out how to change the windows partition so i can install Ubuntu.

I got to this post by doing a search for Partitions.

I have included a screen shot. 

I have my drive at 

Sda1 201.7GB
Free space 2277MB

---

### Post by Hippytaff on 2010-10-22
> **Peterfc said:**
> Hi i have a similar problem. I have just tried to install 10.10 on a 250Gb drive with one partition for windows and free space as 2.3GB. i can't figure out how to change the windows partition so i can install Ubuntu.
 
I got to this post by doing a search for Partitions.
 
I have included a screen shot. 
 
I have my drive at 
 
Sda1 201.7GB
Free space 2277MB
 
Back up everything important. You can use gparted on the live cd to repartion stuff during the install, but it might be worth starting a new thread :-)

---

### Post by Peterfc on 2010-10-22
Re: Can't Install 10.10 on free space
Hi i have a similar problem. I have just tried to install 10.10 on a 250Gb drive with one partition for windows and free space as 2.3GB. i can't figure out how to change the windows partition so i can install Ubuntu.

I got to this post by doing a search for Partitions but was advised to create a new Post.

I have included a screen shot.

I have my drive at

Sda1 201.7GB
Free space 2277MB

---

