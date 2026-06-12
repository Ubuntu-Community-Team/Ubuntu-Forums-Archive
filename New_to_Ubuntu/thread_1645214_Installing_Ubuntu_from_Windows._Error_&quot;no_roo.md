---
title: "Installing Ubuntu from Windows. Error &quot;no root file system is defined...&quot;"
date: 2010-12-14
forum: New to Ubuntu
---

### Post by irpsit on 2010-12-14
Hi all,

I am trying to install Ubuntu.
I have Windows XP and I want to have a dual boot system.

Since I dont have a CD drive and my BIOS fails to start from USB, I am using Unetbootin to install Ubuntu.

I follow the steps commonly recommended.

1) first with Part Magic I resized the Windows partition and created unalocated space after.
Besides this, there is also a second partition after, and a third one (for windows recovery)

2) Second, I boot the LiveCD of Ubuntu. In this environment, there is a linux installer, which I used.

3) However, every time it comes to the option for the partition to install, it gives me the same error, always, whatever partition or free space I try to use. ***[I]No root file system is defined*.[/I]* [I]Please* correct this from the partitioning menu[/I]**

What should I do?

I dont want to use Wubi, because I want to be independent from Windows. And Unetbootin offers this option, without the use of a CD or USB drive.

---

### Post by fatharraxman on 2010-12-14
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by irpsit on 2010-12-14
I know how to resize, delete and create partitions.
I have my disk volumes as following:

/dev/sda1 52GB where is Windows, mounted at /cdrom 
free space 90GB
/dev/sda2 10GB, where I would like to install Ubuntu, not mounted

Should I do something concerned this, like mounting sda2 partition, before running the installer?
Why is the installer giving me this error "no root file system defined"?

---

### Post by tajiknomi on 2010-12-14
[SIZE=2]What option are you using during installation...?

Erase whole Disk..?
Use largest space?

OR

Specify Partition manually..?
Have you select the **Mount-point** within "[/SIZE][SIZE=2]Specify Partition manually"[/SIZE][SIZE=2] ...?[/SIZE] [SIZE=2]Check out the Screen-shot....[/SIZE]

---

### Post by prat22 on 2010-12-14
You have not created a root filesystem. create a partition by selecting a "/" partition, and install over it. You may also create a swap partition, usually twice your RAM size. Hope it works!!

---

### Post by irpsit on 2010-12-14
My installer does not appear like that!

Where do you find that installer?

Is there a download link?
Or shortcut in Ubuntu desktop?

The desktop I am using is a frugal hard disk install (which is a kind of LiveCD but on your hard disk)

> **tajiknomi said:**
> [SIZE=2]What option are you using during installation...?

Erase whole Disk..?
Use largest space?

OR

Specify Partition manually..?
Have you select the **Mount-point** within "[/SIZE][SIZE=2]Specify Partition manually"[/SIZE][SIZE=2] ...?[/SIZE] [SIZE=2]Check out the Screen-shot....[/SIZE]

---

### Post by tajiknomi on 2010-12-14
[SIZE=2]Go for it > [/SIZE][http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)

---

### Post by irpsit on 2010-12-14
My installer gives me this screenshot, when I click install now it gives me the error.

I will now open part magic and see if I can create a partition on /
I assume that this is mounted as root /, no?

EDIT: Part Magic tells me it cannot start due to an unexpected error.
So, I guess I will have to run Part Magic outside of the frugal install ubuntu environment.

---

### Post by tajiknomi on 2010-12-14
> **irpsit said:**
> My installer gives me this screenshot, when I click install now it gives me the error.

I will now open part magic and see if I can create a partition on /
I assume that this is mounted as root /, no?

EDIT: Part Magic tells me it cannot start due to an unexpected error.
So, I guess I will have to run Part Magic outside of the frugal install ubuntu environment.

[SIZE=2]You don't have to Go for part-magic etc...Just Go to manual-partition section, their select your Drive(where you want to install Ubuntu)[/SIZE] [SIZE=2],in Mount-point Write*** /***[/SIZE] ....[SIZE=2]As shown in Screen-shot[/SIZE] [SIZE=2]Above[/SIZE].....[SIZE=2]Also select your Desire Formate e.g ext-3 or ext-4...And tick the Formate option...
[/SIZE][SIZE=2]
If you want to have Separate ***HOME-Partition***, you should select your desire drive for that and in Mount point, type [B][I]/home

[/I][/B]Edit:- yes,*** "/" is Root***
[/SIZE]

---

### Post by irpsit on 2010-12-14
I have no CD drive, so I cannot install Ubuntu from a burnt CD.

The installer within the hard disk "frugal install" always gives me this same error.
This installer was meant to be run within the frugal install, and I already have free unpartitioned space (90GB), so I cant understand why the installer is not working!


> **tajiknomi said:**
> [SIZE=2]Go for it > [/SIZE][http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml)

---

### Post by irpsit on 2010-12-14
OK, this allows to select one partition.
And it asks me to create a swap partition.

So, I was thinking accordingly to the advice below, a swap partition, one partition mounted / and one partition mounted /home.

Would this be the recommended partitioning, correct?

I was thinking assigning 2GB for the swap, 20G for the partition / and 60GB for the home partition.

I am intending using more space for photos, music, than software. Do you think this makes sense?

Thank you all for your excellent help!


> - With the "free space" line selected, click on  the "Add" button. In the new window, type 2000 in the "New partition  size in megabytes" field and select the "swap area" option from the "Use  as:" drop down list. Click the OK button and, in a few seconds, you'll  notice a "swap" line with the specified size;
 
 - With the "free  space" line selected, click on the "Add" button. In the new window,  select the "Primary" option, type a value between 10,000 and 50,000 in  the "New partition size in megabytes" field and select / as the "Mount  point." Click the OK button and, in a few seconds, you'll notice an  "ext4 /" line with the specified size;
 
 - With the "free space"  line selected, click on the "Add" button. In the new window, select the  "Primary" option, type a value between 30,000 and 50,000 (or whatever  space you have left on the drive) in the "New partition size in  megabytes" field and select /home as the "Mount point." Click the OK  button and, in a few seconds, you'll notice an "ext4 /home" line with  the specified size

> **tajiknomi said:**
> [SIZE=2]You don't have to Go for part-magic etc...Just Go to manual-partition section, their select your Drive(where you want to install Ubuntu)[/SIZE] [SIZE=2],in Mount-point Write*** /***[/SIZE] ....[SIZE=2]As shown in Screen-shot[/SIZE] [SIZE=2]Above[/SIZE].....[SIZE=2]Also select your Desire Formate e.g ext-3 or ext-4...And tick the Formate option...
[/SIZE][SIZE=2]
If you want to have Separate ***HOME-Partition***, you should select your desire drive for that and in Mount point, type [B][I]/home

[/I][/B]Edit:- yes,*** "/" is Root***
[/SIZE]

---

### Post by tajiknomi on 2010-12-14
> **irpsit said:**
> OK, this allows to select one partition.
And it asks me to create a swap partition.

So, I was thinking accordingly to the advice below, a swap partition, one partition mounted / and one partition mounted /home.

Would this be the recommended partitioning, correct?

I was thinking assigning 2GB for the swap, 20G for the partition / and 60GB for the home partition.

I am intending using more space for photos, music, than software. Do you think this makes sense?

Thank you all for your excellent help!

[SIZE=2]1) For Root 20G is Good Choice, but !! If you want more softs installed on Ubuntu, then you can Increase root partition ***Accordingly***, 

2) For Home, i think 60G is Quite Enough,depending on your ***Amount*** of Videos,Audios,Gallery Etc.....

3) Swap would be Good Enough , if it is, ***2X*** of Ram, means if you has 1G of Ram, your Swap should be ***2G***...

Edit :- it isn't ***necessary*** that you had ***Separate /home*** Partition, But if you want, it is Good..If you Didn't select /home Mount-point on a Drive, it will be placed in*** root*** [B][I]/.

[/I][/B] Good Luck :p
[/SIZE]

---

### Post by prat22 on 2010-12-14
> **irpsit said:**
> I have no CD drive, so I cannot install Ubuntu from a burnt CD.

The installer within the hard disk "frugal install" always gives me this same error.
This installer was meant to be run within the frugal install, and I already have free unpartitioned space (90GB), so I cant understand why the installer is not working!


[B]Dear ISPIRIT, it seems you are getting tensed... ;)
See, you have a GUI installation, right? Select to manually partition your drive, and then click on your 90gb file system (where you want to install ubuntu), and click on edit/new. then a dialog box appears. Enter the size of the disk, and select / from the list, select ext3/ext4/fat, and you are done. If it returns some messages after this, simply ignore them and install.

If this does not do the install, I recommend you to use a live cd, or make the image on pen drive/HDD again. 

Let us know!:lolflag:
[/B]

---

### Post by irpsit on 2010-12-14
Thanks a lot people!!

I will do the install in a while, and then post the results here

:)

---

### Post by irpsit on 2010-12-14
Ok, in my system I have 4 partitions. 
First is for Windows
After this I have 2GB free space
Second partition will be for Ubuntu (about 80GB, mounted /), and ext3 format

The 3rd is hidden and is related to windows recovery (about 4GB), the last one I dont know what it is, it might also be related to the windows recovery system. The file system is unknown, it has 49MB, all fully used.

I want to create another (fifth) partition in those 2GB free space for use as a Swap Ubuntu partition, but of course I cant (limit is 4 partitions)

I am unsure of deleting the last fourth partition because I want to keep my Windows recovery system (its on the hard disk, because my laptop has no CD drive).

Other than that I am ready for installing Ubuntu!

---

### Post by prat22 on 2010-12-14
> **irpsit said:**
> Ok, in my system I have 4 partitions. 
First is for Windows
After this I have 2GB free space
Second partition will be for Ubuntu (about 80GB, mounted /), and ext3 format

The 3rd is hidden and is related to windows recovery (about 4GB), the last one I dont know what it is, it might also be related to the windows recovery system. The file system is unknown, it has 49MB, all fully used.

I want to create another (fifth) partition in those 2GB free space for use as a Swap Ubuntu partition, but of course I cant (limit is 4 partitions)

I am unsure of deleting the last fourth partition because I want to keep my Windows recovery system (its on the hard disk, because my laptop has no CD drive).

Other than that I am ready for installing Ubuntu!

[B]The best way is to start over again.

Firstly, Ensure that your windows is working fine.

Now, delete all other partitions with Ubuntu or windows cd.

Now, create a recovery space for windows. Now you have two partitions (win+recovery) and the rest is free space.

Insert your Ubuntu disc (or whatever you have) and make a root partition for Ubuntu, and one Swap.

Now you have total four partitions!!

Will this do?

Also if you can take a bit chance, you may delete the 49mb space, and do the installation. After installing, you can check out if the 4gb was the recovery space, if yes, ok. But if it was not, you can always make it! But be careful not to do anything to the Windows partition, or else you will end up in a complete mess!!
[/B]

---

### Post by irpsit on 2010-12-15
Now I have another problem.
I have four partitions in the following order:
sda1 is Windows 50GB
sda4 is swap 2GB
sda2 is ext3 90GB 
sda3 is Windows recovery disk 6GB

With Unetbootin, it install a "LiveCD" in the hard disk (in sda1), as a "frugal install", and from this ubuntu desktop there is an install program. I have to do this way, because I have no CD drive nor its possible to boot from USB.

When I get to the partition menu, I choose again sda2 as a partition for installing ubuntu (ext3 and mount as /). However when I click install now, it gives me a dialog message saying 

> the installer needs to commit changes to partition tables, but cannot do so because partitions on the following mount points could not be unmounted:

/cdrom

Please close any applications using these mount points

Would you like the installer to try to unmount these partitions again?


What should I do?

If I press continue instead of go back, the installation proceeds but stalls, saying "checking file system" or something like that. 

In /cdrom sda1 is mounted, I tried to unmount in the console, but says its not possible, I think its because the installer is running within this same partition.

Note: when I run Unetbootin from Windows it is only possible to install this frugal install in C: (that is, sda1)

---

### Post by irpsit on 2010-12-15
I also have tried sudo umount -l -r -f /cdrom
It works past the previous error, but when it starts copying files, the installer crashes down with a fatal error. 
Because probably it is trying to copy files from the directory that is now not mounted.

I have seen that this problem affects many users.
So, how can you install Ubuntu without Wubi, a CD drive or a USB stick?

Any help would be greatly appreciated.

---

### Post by irpsit on 2010-12-15
[LEFT]Uh, I discovered such an interesting trick.

I ran the frugal install from Unetbootin.

First thing, I went to the console and did sudo umount  -l -r -f  before clicking on the installer!

Then, I start the installer, choose language, then choose partitions to install (advanced configuration). **This solved the error "no root file system defined"**

I choose a free partition as ext3 and mounted as /
And a second one choosen as swap.
The two remaining partitions were Windows (sda1) and windows recovery disk.
**This solved the error "the installer needs to commit changes to partition tables, but cannot do so because partitions on the following could not be unmounted /cdrom"**

Then, very important, just before I pressed "install now", I opened again the console and typed sudo mount /dev/sda1 /cdrom (so, **this solved the fatal error that was crashing the installation**)
And it is copying the files now! :D


Previous steps:
1) Originally I installed Unetbootin because my laptop has no CD-drive nor cannot boot from USB.

2) With Unetbootin I first installed Parted Magic and arranged my partitions as following
sda1 Windows 50 GB
sda4 Linux-Swap format 2GB
sda3 Ext3 format 90 GB
sda2 Windows recovery disk 6GB

3) Booted again with Windows and pressed Unetbootin, it asked me to uninstall and I did it (Parted Magic), then clicked again on it to install Ubuntu 10.10. This installed a "LiveCD" as a frugal install in your hard disk in sda1 which is the Windows partition (C:).

4) Rebooted, and started with Unetbootin in the frugal ubuntu install desktop, and did the steps mentioned above, starting with sudo umount -l -r -f /cdrom, before clicking on the installer.

Remember to back-up your data, and do disk scans before and after rearranging the partitions.

[/LEFT]

---

### Post by prat22 on 2010-12-15
**Remember to mark your thread as "Solved" when done!! congrats anyway!!**

---

### Post by Devon Fletcher on 2011-01-06
> **irpsit said:**
> Hi all,

I am trying to install Ubuntu.
I have Windows XP and I want to have a dual boot system.

Since I dont have a CD drive and my BIOS fails to start from USB, I am using Unetbootin to install Ubuntu.

I follow the steps commonly recommended.

1) first with Part Magic I resized the Windows partition and created unalocated space after.
Besides this, there is also a second partition after, and a third one (for windows recovery)

2) Second, I boot the LiveCD of Ubuntu. In this environment, there is a linux installer, which I used.

3) However, every time it comes to the option for the partition to install, it gives me the same error, always, whatever partition or free space I try to use. ***[I]No root file system is defined*.[/I]* [I]Please* correct this from the partitioning menu[/I]**

What should I do?

I dont want to use Wubi, because I want to be independent from Windows. And Unetbootin offers this option, without the use of a CD or USB drive.
**[FONT=&quot]Re: No root file system is defined -What is the workaround[/FONT]**[FONT=&quot] [/FONT]
  [CENTER][CENTER][FONT=&quot]    [/FONT][/CENTER][/CENTER]
  [FONT=&quot]1. boot Ubuntu from CD (or USB stick)
2. run Gparted (System>Administration>Partition Editor), to set up the Ubuntu Partition. I formatted the partition as ext4, this may not be essential.
3. run Disk Utility, select the partition (click on the appropriate rectangle in 'Volumes').
4. click 'Edit Filesystem Label' and type "/" (without quotes) in the 'Choose a new filesystem label' dialogue box. click 'Apply'.
5 double-click the 
‘Install Ubuntu' icon, away she goes! Well, it worked for me!...
[/FONT]

---

