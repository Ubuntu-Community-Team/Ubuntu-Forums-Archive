---
title: "Viewing windows 7 files on ubuntu 10.04"
date: 2010-06-20
forum: New to Ubuntu
---

### Post by madoldfart on 2010-06-20
Can someone provide me with an easy step by step tutorial on how to view my windows 7 64bit document and media files whilst in ubuntu 10.04 64bit. I have one 2TB hard drive with approximately 1TB of files that i want to read and write.

---

### Post by mikewhatever on 2010-06-20
Click the Windows partition in the left panel of the file browser, and view away.

---

### Post by madoldfart on 2010-06-20
Thanks Mike for the quick response

Maybe i should explain what i am trying to do

Within ubuntu i click on the folder "pictures" select a photo which is looking in "my pictures" folder in the windows partition. 

Then i make some changes to the picture, save it whilst using ubuntu. 

Later on if i want to access the saved picture, i can view ,modify or delete it from within windows or ubuntu.

I guess basically what i am trying to do is set up 3 partitions, 1)one for ubuntu OS and applications, 
2)one for windows OS, windows applications and games
3)one for storage of all my documents and media files.

Backup up all the storage data using my western digital external hardrive using its included backup software WD Smart ware
[http://www.wdc.com/en/products/wdsmartware/](http://www.wdc.com/en/products/wdsmartware/)

---

### Post by friv_livs on 2010-06-20
Last I checked, WD smartware is windows only. I prefer tarballing.

The documents partition should be fat32 to be visible to both windows and ubuntu.

Not sure on how to tell windows to use the fat32 as documents and have the ubu recognize it as documents storage.

The order of partitions should be: windows, fat32, ubu.

---

### Post by drdos2006 on 2010-06-20
In order to use Windows 7 you need to have one partition formatted as Windows NTFS. Windows 7 cannot read/write to Linux ext2, ext3 or ext4 formated partitions. Linux can read/write to NTFS partition.
regards

---

### Post by mikewhatever on 2010-06-20
madoldfart, what's the problem with you being able to do all that? Is there any problem viewing files on the W7 partition from Ubuntu?

---

### Post by WinterRain on 2010-06-21
> **friv_livs said:**
> 
The documents partition should be fat32 to be visible to both windows and ubuntu.



Ubuntu can also read NTFS, which is a better file system btw.

---

### Post by madoldfart on 2010-06-21
> **mikewhatever said:**
> madoldfart, what's the problem with you being able to do all that? Is there any problem viewing files on the W7 partition from Ubuntu?

I have no problem viewing them i just want to be able to read(easy) and write(not sure how) from both systems and backup only from windows using WD smartware. 

I have done a bit of googling since posting this thread and found this tutorial below. I am going to give this a try unless you guys know of a simpler way. 
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

---

### Post by mikewhatever on 2010-06-21
I really don't know what way or tutorial you are looking for. Out of the box, Ubuntu can read and write to files on the Windows partition. It doesn't get any easier then that.
Anyway, good luck with that link.

---

### Post by corncob on 2010-06-21
I too am not sure what you're looking for but the partition you want to read needs to be mounted.  You can do this with gparted in the System/Administration menu.  Or with the Storage Device Manager (pysdm in Synaptic.  Also, I've been told that NTFS-config (in Synaptic) is needed to read NTFS partitions although its not installed in my computer and I am reading them.

---

### Post by ieee488 on 2010-06-21
> **madoldfart said:**
> I have no problem viewing them i just want to be able to read(easy) and write(not sure how) from both systems and backup only from windows using WD smartware. 

I have done a bit of googling since posting this thread and found this tutorial below. I am going to give this a try unless you guys know of a simpler way. 
[http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony](http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony)

That link isn't anything special. It basically gives you instruction with pictures for dual booting Windows 7 (NTFS) and Ubuntu.

I dual boot between XP (also NTFS) and Ubuntu with no problems. I generally use Ubuntu, but I have a D:\ that is NTFS which I use to store data files. I access those files fine from Ubuntu.

---

### Post by Mark Phelps on 2010-06-21
> **madoldfart said:**
> I have no problem viewing them i just want to be able to read(easy) and write(not sure how) from both systems and backup only from windows using WD smartware. 

You can't do both from both systems ...

Ubuntu will be able to read & write from/to NTFS partitions.

Win7 will NOT be able to read from or write to your Ubuntu partitions.

WD Smartware is most probably an MS Windows app, meaning that it's also most likely NOT going to be able to read your Ubuntu partitions, meaning, it's also NOT going to be able to do backups of them.

But since you started out saying  you only wanted to do backups of your storage partitions (NTFS), you will be OK in that case.

---

### Post by bigsmitty64 on 2010-06-21
> **madoldfart said:**
> 

I guess basically what i am trying to do is set up 3 partitions, 1)one for ubuntu OS and applications, 
2)one for windows OS, windows applications and games
3)one for storage of all my documents and media files.


As long as #3 is ntfs there shouldn't be a problem right? 

My setup was (I no longer use windows),
1st hdd ubuntu   ext4
2nd hdd ntfs
3rd hdd storage ntfs

saved all media pics docs to 3rd drive, and accessed from both OS's

---

### Post by madoldfart on 2010-06-21
> **Mark Phelps said:**
> You can't do both from both systems ...

Ubuntu will be able to read & write from/to NTFS partitions.

Win7 will NOT be able to read from or write to your Ubuntu partitions.

WD Smartware is most probably an MS Windows app, meaning that it's also most likely NOT going to be able to read your Ubuntu partitions, meaning, it's also NOT going to be able to do backups of them.

But since you started out saying  you only wanted to do backups of your storage partitions (NTFS), you will be OK in that case.

Thanks for all your help guys, i am slowly starting to understand.
I checked last night and i can read and write from ubuntu to windows. Although understanding that you have to open up the Host folder to get to them. I just need to change the folder structure so that when my wife(who has very limited knowledge of computers) clicks on say pictures folder in ubuntu and she can access the photos in windows or the storage partition without having to know that she has to go to the host folder/documents & settings/user/my pictures.

Had some issues with Rythombox and wma files but im sure with a little bit of googling i can find the right codecs


With respect to writing from windows to ubuntu has anybody tried this
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

Again thanks for all your help

---

### Post by Mark Phelps on 2010-06-21
> **madoldfart said:**
> With respect to writing from windows to ubuntu has anybody tried this
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

Again thanks for all your help
That was before the default filesystem for Ubuntu changed to Ext4 -- which, last time I checked, the Ext Windows drivers still can not read or write.

---

### Post by madoldfart on 2010-06-21
> **Mark Phelps said:**
> That was before the default filesystem for Ubuntu changed to Ext4 -- which, last time I checked, the Ext Windows drivers still can not read or write.
thankyou

What about Samba? Is this a better option for my needs. From what i have quickly read about samba, samba is used for windows and mac pc to view files on a linux pc. Can i use samba to view files from a mac or linux PC where all the files are stored on the windows pc

is samba used for multiple computer sharing files or can it be used for dual boot systems - or both

PS. Should i have created a new thread for samba

---

### Post by mikewhatever on 2010-06-21
Samba is for multiple computers and network storage devices. It's not suitable for sharing files on a single dual boot system.

---

### Post by madoldfart on 2010-06-21
thanks Mike
you saved me a lot of time downloading and trialling samba

Can you help me with my other question as i may have a need to do this

Can i use samba to view files from a mac or linux PC where all the files are stored on the windows pc

as i understand it samba is used for windows and mac pc's to view files on a linux pc, which is vise versa to what i want

---

### Post by SunnyRabbiera on 2010-06-21
Install NTFS config and it should help in your dual boot,

---

### Post by sandyd on 2010-06-21
> **madoldfart said:**
> Thanks for all your help guys, i am slowly starting to understand.
I checked last night and i can read and write from ubuntu to windows. Although understanding that you have to open up the Host folder to get to them. I just need to change the folder structure so that when my wife(who has very limited knowledge of computers) clicks on say pictures folder in ubuntu and she can access the photos in windows or the storage partition without having to know that she has to go to the host folder/documents & settings/user/my pictures.
[B]I actually have a setup with this.

just drop all the files into a NTFS partition, and run the following commands in the terminal
```

sudo apt-get install ntfs-config
palimpsest
```
A window will come up with the partitions on your computer.

click on your hard drive (left hand side of the window).

The right side will show info about partitions on that drive.

under the "volumes" heading, identify the drive you are going to use to store data. click on it.
record the stuff in the "device" entry (still under the volumes entry). It should be something like "/dev/sda1"

```
sudo ntfs-config
```
A window will now open, listing your NTFS partitions and their "supposed" mountpoints.

using the stuff you recorded, identify the data partition, and place a check mark next to the device in the "add" column. click on "click here to add mountpoint" and type in windows.


_If you are accessing your pics in the windows partition_
now, in the upcomming steps, you will need to replace <linux-username> with your linux username and <windows-username> with your windows username.
remember, this is case-sensative!

```

rmdir ~/Pictures
rmdir ~/Music
rmdir ~/Documents
ln -s /media/windows/Users/<windows-username>/Pictures /home/<linux-username>/Pictures
[/B][B]ln -s /media/windows/Users/<windows-username>/Documents  /home/<linux-username>/Documents
[/B]**ln -s /media/windows/Users/<windows-username>/Music  /home/<linux-username>/Music**
[B]
```

that permanantly links the pictures, music, and documents folder to linux.

[U]Data partition method
[/U]Still, everything is case sensative...
replace stuff in the square brackets with your info. If your confused on how to do this, the [path] that im asking for is the folders from the drive.

For example, if my pics were located at D:\ME\Pictures (I just picked D because that is what it shows on my comp), I would replace the [path] with "ME\Pictures"

[/B][B]```

rmdir ~/Pictures
rmdir ~/Music
rmdir ~/Documents
ln -s /media/windows/[path/to/pictures]  /home/<linux-username>/Pictures
[/B][B]ln -s /media/windows/[path/to/documents]  /home/<linux-username>/Documents
[/B]**ln -s /media/windows/]path/to/music]  /home/<linux-username>/Music**
**
```**
Had some issues with Rythombox and wma files but im sure with a little bit of googling i can find the right codecs


With respect to writing from windows to ubuntu has anybody tried this
[http://www.howtoforge.com/access-linux-partitions-from-windows](http://www.howtoforge.com/access-linux-partitions-from-windows)

Again thanks for all your help
yeah, that was long

---

### Post by sandyd on 2010-06-21
> **madoldfart said:**
> thanks Mike
you saved me a lot of time downloading and trialling samba

Can you help me with my other question as i may have a need to do this

Can i use samba to view files from a mac or linux PC where all the files are stored on the windows pc

as i understand it samba is used for windows and mac pc's to view files on a linux pc, which is vise versa to what i want
yup, it can do both.

p.s.
Ive found that the app [[system-config-samba]]("apt:/system-config-samba") quite useful for setting up file samba. (just click on the link to install it!)

---

### Post by madoldfart on 2010-06-21
> **carlee said:**
> yeah, that was long

Wow thankyou Carlee it was long but good, and most of all i appreciated it.

Was your post about 2 methods
1)If you are accessing your pics in the windows partition 
and
2)Data partition method

What is the difference?
And does the data partition method still require me to drop all my files into a NTFS partition

please excuse me, but i am a complete old noob(is there such a thing) to computors but a great learner.

---

### Post by sandyd on 2010-06-21
> **madoldfart said:**
> Wow thankyou Carlee it was long but good, and most of all i appreciated it.

Was your post about 2 methods
1)If you are accessing your pics in the windows partition 
and
2)Data partition method

What is the difference?
And does the data partition method still require me to drop all my files into a NTFS partition

please excuse me, but i am a complete old noob(is there such a thing) to computors but a great learner.
here, I was not really sure about what you wanted. initially, i thought that you wanted a seperate NTFS partition for all your files (data partition), but later on, I found that you wanted to simply save the stuff on your windows installation and read it from ubuntu.

---

