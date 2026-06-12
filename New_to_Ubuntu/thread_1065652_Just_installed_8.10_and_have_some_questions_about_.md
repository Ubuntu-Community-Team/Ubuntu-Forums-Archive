---
title: "Just installed 8.10 and have some questions about folders and the filesystem"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by Jingle on 2009-02-10
Morning all, this is my first post on the forum, I know I've got more than one question here but I'm not sure how to separate them so here's a quick background:

**I have:**
 
1) laptop running XP
2) desktop running XP Pro and freshly installed ubuntu.  
They are working over a wireless network via a netgear router (only the cable modem is plugged into the router)
The desktop stays on 24/7 to act as a file server for accessing from the laptop

**My desktop is configured as follows: **

120Gb (master) partitioned into 40gb for XP, 40Gb for Ubuntu, 10Gb as a swap partition (not sure why I had to do this but the installer asked me to is 10Gb enough?) and the remainder left unpartitioned for a future install of the Windows 7 beta or playing with something else.

300Gb (slave) which has my documents/personal data and also all my media files

New 1Tb (external USB) drive which I want to partition about 100Gb for backing up my personal documents and the remainder (830gb)to now store all my media files.

**What I'd like to do is:**

learn what file system to format my new 1Tb drive/partitions in so that the data is readable by both XP and ubuntu. I think I created the ubuntu partition in ext3 whatever was the default in the installer.  XP can't see it I know that (which is fine)

my "My documents" in windows is pointing at the folder on my 300gb drive. I'd like to do the same in ubuntu so that my personal docs are available to me no matter which OS I'm using.  I don't mind my settings and stuff being on the 300gb drive but I'd like to hide them from XP so I don't delete by accident.

currently when I boot into ubuntu it doesn't seem to mount my 300gb drive automatically so things I've changed like my desktop background don't seem to stay the same.  every time I go to open the drive it asks for my password.   this is going to get annoying everytime I want to access my documents, will "pointing" my /home to this drive solve that? 

I've got more questions about accessing this lot over my network but I want to get it organised on the one PC first!  I'll ask those in a separate thread, but will sorting out some kind of access control over the network affect how I set up the files here first?

Sorry for rambling folks, I'll get more concise once I've worked out what the hell I'm doing with this lol!

Thanks in advance
Frazer.

---

### Post by Mark Phelps on 2009-02-10
As they say, opinions vary, but I would recommend against sharing the same profile files in Windows and Ubuntu, especially since you're planning on adding Windows 7 down the road.  

You start using the same profile files and the next thing you'll want is to know how to run all kinds of Windows apps in Ubuntu to use those files -- and the Wine fans will appear telling you how great that is.  Great, that is, if you use really OLD versions of Windows apps.  I used Wine for six months and found it to be an unmitigated disaster; so, I learned how to do all my work using Linux apps instead.

Also, if you mount your Windows OS partition read/write in Linux and have an abnormal shutdown, don't be surprised if Windows then will no longer boot.  So then, not only have you clobbered your Windows profile files, you can't boot into Windows to fix them.

If you really want to share data files (I do this all the time), I would recommend making room for an NTFS partition, and store your shared data files there.  Ubuntu reads and writes NTFS partitions just fine using NTFS-3G and Seven will be able to use that file system also.

As I said, only my opinion.

---

### Post by Therion on 2009-02-10
> **Mark Phelps said:**
> As I said, only my opinion.
I concur completely.

[quote=Mark Phelps]
You start using the same profile files and the next thing you'll want is to know how to run all kinds of Windows apps in Ubuntu to use those files -- and the Wine fans will appear telling you how great that is. Great, that is, if you use really OLD versions of Windows apps. I used Wine for six months and found it to be an unmitigated disaster; so, I learned how to do all my work using Linux apps instead.

Also, if you mount your Windows OS partition read/write in Linux and have an abnormal shutdown, don't be surprised if Windows then will no longer boot. So then, not only have you clobbered your Windows profile files, you can't boot into Windows to fix them.[/quote]
Re-read those paragraphs until they sink in.  That's some seriously excellent advice right there.

---

### Post by Jingle on 2009-02-10
Thank you both, much appreciated.  What I'll do then is keep my new drive NTFS for sharing my media files.

I've no intention of opening my windows OS partition in ubuntu, I've only done so a couple of times to get things like firefox bookmarks etc..

I'm not sure what you mean by "profile" files.  If you mean things like user settings and stuff I don't want to share that between operating systems, what I'd like to be able to access from both is the documents that I've got on my 300gb (ntfs) drive which doesn't mount itself so each time I open it it asks me for my password (which is annoying).  Also ubuntu won't let me rename any of my NTFS partitions, I take it XP "owns" them?

---

### Post by sambita on 2009-02-10
You can install pysdm (Applications->Add/Remove). Once installed go to System->Administration(the one that is not preferences, i dont know how it shows in english cause ive got ubuntu in spanish) and select "Storage device manager"
Select the partition you wish to mount automatically and in the "General configuration" tab select assitant, once there go to the "mount" tab and select "mount on startup"

that should do it. 

Heres a pysdm [**tutorial**]("http://ubuntuforums.org/showthread.php?t=872197") from the forum.

---

### Post by tarps87 on 2009-02-10
For auto mounting the GUI recommend above is useful but you may also want to look at the fstab documentation:
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

The swap partition is used for paging and hibernation, it is a separate partition in Linux and a 'file' in windows. As a general rule, to allow for reliable hibernation set it to twice the size of your ram. It is recommended to always have a swap partition although the more ram you have the less it is use, also the more memory intensive tasks you preform the more it will be used.
This should list the swap usage
```
swapon -s
```
This can also be used
```
top
```
Some more information on paging
[http://en.wikipedia.org/wiki/Paging](http://en.wikipedia.org/wiki/Paging)

For the server I suggest samba so windows can access it, you can setup the permissions latter when you set up the server.

Samba:
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Useful server documentation (I used this to setup a file and update server):
[https://help.ubuntu.com/8.10/serverguide/C/index.html](https://help.ubuntu.com/8.10/serverguide/C/index.html)

---

### Post by Jingle on 2009-02-10
Excellent, thank you for the explanation of swapping, I could have got away with a 5gb partition then lol! (1Gb physical ram)

I've sorted the mounting now.  Thanks to that fstab documentation I read it carefully and edited my fstab file manually and it's booted up with my desktop background so I assume it all works!

Now I've just got one thing left to do. Can I "point" the default documents, videos, music & pictures folders in my home directory to go to the folders that already have my personal data in on my other (now mounted) hard drive? 

As crudely illustrated in this picture...

---

### Post by tarps87 on 2009-02-10
You could remove or move the original folders in home and link to the other folders e.g.
```
ln -s /media/Documents/Music/ ~/Music/
```
optinaly you could do something like
```
ln -s /media/Documents/Music/ ~/MusicExternal/
```
ln = link
-s = symbolic
This is how I would do it, there may be a better way.

The folders you a pointing to are bookmarks, you can add them by right clicking and selecting add bookmark or under the view menu (I think it is under view, but it maybe under a different one)

---

### Post by Jingle on 2009-02-10
Thanks again.  I've edited the bookmarks and it's achieved the effect that I'm after.   I tried the ln command but this just put a link in the home/pictures directory, not quite what I was after.

I used the GUI to manually make a link and place it in the home folder and this worked great.  I didn't want to experiment with the details of the command in case I broke it!

Thanks again to all of you for the help
Frazer

---

### Post by tarps87 on 2009-02-11
That would be my fault, the command should have been
```
ln -s /media/Documents/Music/ ~/Music
```
(without the / on the end)
The main command to look out for when using the commandline would be sudo, this gives you root privelage.

---

### Post by Mark Phelps on 2009-02-11
> **Jingle said:**
>  ... Also ubuntu won't let me rename any of my NTFS partitions, I take it XP "owns" them?

I might be wrong on this (not an expert), but the last time I attempted to rename a volume in Gparted, it gave me an message indicating that it would wipe the volume in the process.  So, you need to be careful about renaming the volume.

Also, if you are using MS Office documents and want to be able to work with them both in Windows and Ubuntu, look into upgrading to Open Office 3.x. It allows you to open MS Office documents, and save them back in MS Office format.  Don't know if it can do the "new" XML formats, though; haven't tried it.

Best of Luck

---

