---
title: "[SOLVED] How to access files on my secondary internal hard drive"
date: 2008-12-30
forum: New to Ubuntu
---

### Post by robond8 on 2008-12-30
I just got Ubuntu 8.10 up and running. I have two internal hard drives. One of them is called "file system" in "My Computer" the other one just says 40 GB Media. I have a lot of document and media files on that hard drive that I would like to access. How do I do that? Is there a program that can access the drive in Ubuntu? Isn't that called "mounting" the drive?

Thanks! Please help!

---

### Post by robond8 on 2008-12-30
Oops I forgot to say that I used Windows XP to load all the files on my second drive, but I am unable to get back into Windows after installing Ubuntu 8.10...I am fine with that but I really need to access those documents and media!

---

### Post by adult swim on 2008-12-30
what happens when you click on the 40gb media?

---

### Post by Messyhair42 on 2008-12-30
i ran into something like this after installing ubuntu on another desktop comptuer. i didn't have a problem booting windows but the other HD was under filesystem>home>(username)

---

### Post by Dumbestcrayon on 2008-12-31
Is it NTFS or what?

---

### Post by robond8 on 2008-12-31
Answer to Dumbestcrayon's question: I don't know what type of drive it is except that it worked in Windows XP. I thought it was called a FAT32 or something? Excuse my ignorance!


Answer to Adult Swim's question: When I click on the drive it says "unable to mount volume" the in the Details it basically says I have "2 choices". The first is to remove the hard drive safely in windows. (note that it is an INTERNAL hard drive and I no longer have Windows, so that wouldn't work). Choice two says to type some stuff in the command line. I am not sure how to do all of that but I can give it a try. What should I do? Thanks!

---

### Post by hoppyandy on 2008-12-31
look like you are having same problems as me with my external hard drive, i have tried safely removing from windows and it didnt make any difference. i managed to get mine connected but only by manually typing into terminal each time i start computer, i havent resolved my problem yet still trying but suspect may be same problem. if you want to see your hard drive label if same as mine you can see if connected but not mounted in system - administration - partition editor. by using the drop down arrow in the RH top corner you can change between each of your hard drives.

May give you some info you can use to manually mount your drive.
Hope this helps

---

### Post by robond8 on 2008-12-31
Thank you Hoppyhandy for the advice. I was able to find out that the hard drive is NTFS. The "path" for the drive is /dev/sdb1. I do not know how to "manually mount the drive" I am hoping there is a program or way to mount the drive so I can have it for storing documents and media.

This problem is not yet solved! Thanks for the help so far though!

---

### Post by sadaruwan12 on 2008-12-31
Hi,

Well normally Ubuntu automatically mounts NTFS and FAT32 drives when you double click on that partition. Ubuntu will ask for your for your Super User password and that partition get auto mounted. But in your case I can't understand why it doesn't ask for that option. OK go to nautilus and right click on that 40GB drive and see whether you can see mount volume menu item if it's there use that to mount your drive. If it's not there then let me know I'll give you a solution.

---

### Post by hoppyandy on 2008-12-31
mine was labelled the same except mine was fat32. have a look at my post refering to seagate external hard drive.
basically you need to mount it some instructions were sent to me via link have a look at those before doing anything
yours wont be exactly the same as drive name for mine is SEA_DISK you need to label yours to name of your hard drive. also mine is fat32 so had to enter vfat. you need to change these, someone else will give you better advise i am to new to advise, sorry
basically i typed this into terminal

sudo mkdir /media/SEA_DISK
enter - then
sudo mount -t vfat /dev/sdb1 /media/SEA_DISK

as i said before you will need to change some of that to suit your hard drive.

If i get an better answer to my problem i will pass it on to you.

---

### Post by hoppyandy on 2008-12-31
This is a link sent to me on mounting hard drives etc heavy reading but you may understand better than me ?
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by robond8 on 2008-12-31
thank you hoppyhandy for your advice, I will look into that stuff.

answer to sadaruwan12: okay, yes, I do have the "mount the drive" option but when i click it, it says "unable to mount volume" and when you click details it says all the things i already said in an earlier post (refer to that if you want to know). So any other way to mount the drive?

---

### Post by vanadium on 2008-12-31
The only proper solution to your problem is to do "Choice 1" of the error message you received.

You get the error message because the ntfs drive was not properly closed or is otherwise not in a healthy state. Ubunt will not auto mount such a drive in order to not further damage the drive. You can still force-mount such a drive, though (which is Choice 2) if you do not have access to a Windows machine anymore.

Hook up the drive to a Windows machine. Have the drive checked using the Windows drive checking tools. Then properly disconnect the drive using the "Safely remove hardware" incon in the Windows tray. To be sure, repeat this a few times. After that, the drive should auto-mount under Ubuntu.

If you do not have Windows yourself, it is strongly recommended not to use ntfs anymore. Format it to ext3 instead. An ntfs formatted drive (being a proprietary file system) can only be properly checked by a Windows system. Thus, you should use ntfs only if you also have ready access to MS Windows.

---

### Post by robond8 on 2008-12-31
thank you for the advice vanadium but wont formatting the drive to ext3 erase the data on the drive? I was hoping to be able to keep the documents and media I have on it. Also the drive is internal and taking it out and putting in another case with an XP PC is easy but time consuming, so i am going to rule that out. 

I know you mentioned "force mounting" the drive. what does that mean? if i do that will I then be able to copy the files I want onto my primary hard drive? If I did that would I then be able to re-format the ntfs secondary drive to ext3 and then have it available for further storage use? 

Sorry for the ignorance and asking so many questions! It's how you learn though! Thanks again!

---

### Post by vanadium on 2008-12-31
Indeed, matters are different is the drive is internal. That is one more reason why ntfs is not recommended.

The best way for you to go if you cannot connect the drive to a Win system would be to force mount the drive read-only, then copy the data off to an external drive or other removable media, then reformat the drive to ext3 and put the data back.

Anyway, if you care for the data, you should have a backup. A hard disk can fail for various reasons, and one day, it will.

You could force mount the drive in your etc/fstab and continue to use it like that. You risk one day that the file system is more corrupt and all your data are gone.

There is also the ntfsfix utility. It can fix and repair "basic problems" with ntfs. It might render your drive healthy, but also, it might not if the problems with the file systems are beyond that what ntfsfix can repair.

---

### Post by hotstovejer on 2008-12-31
Robond,

A couple of questions for you.

Is that 40 gig drive the drive you had Windows installed on?

The last time you were in Windows, did you do a proper shutdown of it?

When your computer boots up, and it shows the grub loading screen (very early on in the booting process, before the Ubuntu loading screen) do you have the option of hitting Esc and seeing if Windows is listed in the list there? Windows is more than likely still there, but if you don't see it in grub, you will think it's gone. While grub is counting down, just hit esc.

All of these things tie together. Don't worry, just breathe. 

:)

Thanks!

Jeremy

---

### Post by robond8 on 2008-12-31
thanks vanadium! Can you give me some basic instructions on how to force mount the ntfs drive to "read-only" so I can get the files? 

I will then copy the files to another drive, reformat the drive to ext3 which I believe I can do without help. Thanks!

---

### Post by robond8 on 2008-12-31
okay Jeremy here are the answers to your questions:

Yes the drive was running windows.

I am not sure if I properly shut it down because I used wubi to install Ubuntu 8.10. Though part of installing wubi is re-booting (which I did).

On the Grub loading screen I DO see windows xp as an option BUT when I click on it it says I have to insert an xp disc to validate my session or something like that. So I am thinking my whole account on windows xp is busted which is okay because I have all the files I wanted to keep on the drive that...........wait a minute...........I just figured things out!

I installed Ubuntu on my secondary drive in windows that had all the files I wanted on it. I did this be accident! Darn! So the secondary drive in Ubuntu was my MASTER drive in windows. So all my files that were on my SLAVE drive in windows are gone because I partitioned the whole thing to Ubuntu! So basically I am stuck with the master drive that ran windows as my slave drive in ubuntu. I will reformat it and I'll just have to take the loss of the files as a lesson well learned.

Thanks everyone who helped me out on this! I will post as SOLVED as soon as I figure out how to do so! Thanks again!

---

### Post by wolfen69 on 2008-12-31
right click the drive and select mount. when it tells you it can't mount, look at the details option. it will tell you how to force mount. just put *sudo* at the beginning of the command.

---

### Post by vanadium on 2009-01-01
The commands for force mouting would be like this. You make a mount point, then mount the drive

```

mkdir temporary
sudo mount /dev/sdb1 temporary -t ntfs -o force

```

The drive should now be acessible by navigating into the directory temporary, allowing you to copy the data to a safe location. "force mount" is an emergency measure. When done retrieving the data, unmount the drive ("sudo umount /dev/sdb1") and format it to ext3. You can do that using gparted.

gparted is not by default installed. If needed, install it using Symaptic package manager or with the command

```

sudo apt-get install gparted

```

Launch gparted with root permissions

```

sudo gparted

```

Select your drive dev/sdb using the dropdown in the right corner. Right-click the partition and choose "Format to", then "ext3".

Sorry if I am too long winded for you, but this is the Absolute Beginners section ;)

---

### Post by robond8 on 2009-01-01
answer to vanadium: Thanks for command instructions! Though somebody else already showed me how to force mount the drive. It's nice to know how to do but I was really hoping to be able to access the drive normally. When I originally posted this thread as solved I had just figured out how to access the drive, but I am unable to add/remove any files on it! So that's why I started another thread sort of on the same issue as this thread. So if you would go see all my threads and click on the thread:

"[ubuntu]   I am not able to create folders or do any editing to files on my second hard drive" 

There you can see how things have been going on the issue and give me any further help (if you can!).

Thanks a bunch!

---

### Post by robond8 on 2009-01-01
Okay, I got the hard drive working with the help of forum member ballooza.

See my other thread on the matter if you are interested in what worked to fix it. Thanks!

---

