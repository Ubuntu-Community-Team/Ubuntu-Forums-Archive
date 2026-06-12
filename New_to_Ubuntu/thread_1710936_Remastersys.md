---
title: "Remastersys"
date: 2011-03-20
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2011-03-20
Hi all,

I tried to make a backup of my system, including all my personal files, but I received an error message telling me that the file size was too large for an iso.

I'm not sure what could be taking up so much space since I have all my videos and music files on an external harddrive.  It could be that I have KDE installed along with Gnome.  

I guess my first question is how can I tell the program to exclude anything related to KDE?

I was able to make an iso for a Live DVD, excluding all of my personal files, by choosing the distributable option from the menu. (Choice # 2)

[IMG]http://www.jfniendorf.org/Screenshot-Remastersys.png[/IMG]

I chose to make a distributable copy including cdfs files.

Question # 2: What exactly are cdfs files and how do you use them?  The option to make an iso only also says that cd file system must have been completed already.

Question # 3:  What happens if you haven't already made the cd file system?

When everything finished I had a folder filled with files.

[IMG]http://www.jfniendorf.org/Screenshot-2.png[/IMG]

Question # 4: What do I do with the temp users' files?  I'm not sure why there are so many.  I am the only user on this laptop.

Question # 5:  How do I use the md5 file?  I think it is a checksum, but I don't know how to use it.

Question # 6:  Do I need to do anything with dummy system or temp iso folders?

I'm confused as you can tell ;)

---

### Post by Wobblybob on 2011-03-21
I've never used Remastersys so am of little us to you :confused: but from past experience backing up my home folder I found the waste bin to be a problem as it often has tons of large files in it and it sits in the /home/yourname/.local/share/Trash folder within your home. make sure you delete the waste bin before you backup.

> Question # 4: What do I do with the temp users' files? I'm not sure why there are so many. I am the only user on this laptop.

They are probably created by the backup process, try right clicking them and opening them in a text editor to check them out, or check the date/time they where created if it was at the time of the backup just delete them. I think the same goes for Q6 as the backup has failed the prog has not removed all it's working folders.

> Question # 5: How do I use the md5 file? I think it is a checksum, but I don't know how to use it. 

try [[COLOR="Navy"]https://help.ubuntu.com/community/HowToMD5SUM[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") for help on that subject.

sorry i can't be of further help, good luck

---

### Post by GrouchyGaijin on 2011-03-21
Thanks Bob,

When I look at /home/john/.local/share/Trash
I see three folders:  expunged, files and info

All three are empty.  I hit ctrl+H inside each of them to make sure there were no hidden files and still all three come up empty.

Thank you for the link about the checksum.

---

### Post by Wobblybob on 2011-03-21
no problem you could use the command line

$ df -h
in a Terminal to give you an idea of disk space used
and
$ du -sh *
for folders

good luck with the backups have you come across clonezilla [Google is you friend]

---

### Post by GrouchyGaijin on 2011-03-21
I ran those commands and this is what I got:

```


Filesystem            Size  Used Avail Use% Mounted on
/dev/sda5              27G  9.9G   16G  40% /
none                  998M  296K  998M   1% /dev
none                 1006M  540K 1005M   1% /dev/shm
none                 1006M  324K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
/dev/sdb1             932G  309G  623G  34% /media/Elements

```
Elements is an external hard drive.

and

```
1.9G	
```

This is a dual boot system with Ubuntu 10.10 and Windows XP.

Basically, I just want to backup the Ubuntu stuff so I can wipe the drive and put Ubuntu back as a single boot without having to download and install everything again.

I was able to make a Live DVD with Remastersys that looks like it has everything except my personal files.

I downloaded Clonezilla Live and will play with that to see if it might be better for what I want to do.  Ideally I'd have all my personal files (wallpaper, theme, documents, scripts etc.) in the image as well as the installed programs.

---

