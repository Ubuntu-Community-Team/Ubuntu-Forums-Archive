---
title: "using rsync to create an exact mirror"
date: 2010-08-11
forum: New to Ubuntu
---

### Post by pataphysician on 2010-08-11
Could someone please give me an example of what rsync command needs to be issued to maintain an exact mirror of the source?

I thought I used to just use *rsync -a --delete source/ dest* but it doesn't seem to be removing subdirectories (e.g., if I rename a folder, the new one gets copied, but the old one is kept at the back-up source as well). I've RTFM'd a few times and Googled all afternoon on this. I've tried all the --delete variations (--delete-after, etc.) as well as using trailing slashes and asterisks in various combinations. I also tried the graphical frontend but it too left subdirectories.

I'd like the end result to be an exact duplicate of my home directory on an external USB drive, including subdirectories, symlinks, dot files, ownership and permissions.

---

### Post by anglican on 2010-08-12
> **pataphysician said:**
> Could someone please give me an example of what rsync command needs to be issued to maintain an exact mirror of the source?

I thought I used to just use *rsync -a --delete source/ dest* but it doesn't seem to be removing subdirectories (e.g., if I rename a folder, the new one gets copied, but the old one is kept at the back-up source as well). I've RTFM'd a few times and Googled all afternoon on this. I've tried all the --delete variations (--delete-after, etc.) as well as using trailing slashes and asterisks in various combinations. I also tried the graphical frontend but it too left subdirectories.

I'd like the end result to be an exact duplicate of my home directory on an external USB drive, including subdirectories, symlinks, dot files, ownership and permissions.rsync behaves exactly as you'd expect if you rsync between ext3 filesystems (--delete behaves as you want) but there may be problems if you are using ntfs (or other non-Linux filesystem). Try adding the option "**--modify-window=1"** if "dest" is ntfs.

H

---

### Post by plucky on 2010-08-12
I think **luckybackup** has that option to sync your /home directory.

Good Luck

---

### Post by baddnady23 on 2010-08-12
Please post your exeact command that you typed into the terminal to copy

---

### Post by pataphysician on 2010-08-12
Hi, thanks for the replies.

> **baddnady23 said:**
> Please post your exeact command that you typed into the terminal to copy

I tried about 30 different things, but it mostly got to the point where I was just throwing slashes and asterisks and random switches.

I started with *rsync -av --delete /home/mike /media/backup*

Also *rsync -av --delete /home/mike/ /media/backup/mike*

Then *rsync -av --delete /home/mike/* /media/backup/mike*

Then I retried all of those with the various --delete options (--delete-after, --delete-during, and so on). Then I tried them all with --recursive because I read a thread that said you need to specify it sometimes even though -a implies it.

When none of those worked I re-read the manual and added the --force option to each of the commands above, so that my final three attempts looked like

*rsync -av --delete --recursive --force /home/mike /media/backup/*

*rsync -av --delete --recursive --force /home/mike/ /media/backup/mike*

*rsync -av --delete --recursive --force /home/mike/* /media/backup/mike*

The last one (with the asterisk) seems to work on sub-directories, but it skips a lot of files for some reason. I can't tell which or why, but if I do a dry run with and without it, there's a huge difference in what gets copied. It certainly ignores dot files from the source.

Like I said, I swear I've done this before with the first, simple command. Both drives were probably ext3 then. The source drive here is jfs and the destination is ext4.

---

### Post by baddnady23 on 2010-08-12
Refer to my post at #10 here:  [http://ubuntuforums.org/showthread.php?t=238672]("http://ubuntuforums.org/showthread.php?t=238672")

Specifically, it states:
> be aware that rsync pays particular attention to the / at the end of a path. If it is there, it will copy only the contents of that directory into the desired location. If it is not there, it will copy the the actual directory and its contents. For example:
```
rsync -av [COLOR="Red"]/home/andrew/[/COLOR] andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_laptop

```
copies the contents of my /home to the desired location. Whereas
```
rsync -av [COLOR="Red"]/home/andrew[/COLOR] andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_laptop
```
copies the actual /andrew folder and its contents to the desired location.


Although I am copying to a directory on another computer, the principle is exactly the same.

The actual command that I use everyday to backup my personal /home directory is:
```
rsync -av --delete --exclude='/.gvfs/' --log-file=/home/andrew/Logs/rsync/ubuntu\ 10.04/$(date +%Y%m%d)_rsync.log /home/andrew/ andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_desktop
```

Take out all the extra crap and it simply is this:
```
rsync -av --delete /home/andrew/ andrew@192.168.1.70:/media/data/backups/ubuntu_home_backup/home_desktop
```

Stick to something similar and you should have no problems.  Please post back with any further questions!

---

### Post by pataphysician on 2010-08-12
Strange, that's what I tried but it just doesn't work over here.

```
cd /media/backup/mike/Desktop/
mkdir delete_me
cd delete_me
touch bye.txt
rsync -avn --delete /home/mike/ /media/backup/mike | grep delete_me
[no output]
rsync -avn --delete /home/mike/ /media/backup/mike | grep bye
[no output]
```

Nor does it work when I add --force. This is all done as user "mike," and everything has the same/correct permissions.

However, if I cd up to /media/backup/mike:

```
mkdir go_away
cd go_away
touch dunno.txt
rsync -avn --delete /home/mike/ /media/backup/mike | grep go_

deleting go_away/dunno.txt
deleting go_away/
```

It's like it just refuses to delete subdirectories.

---

### Post by QLee on 2010-08-12
Well, it's looking to me like it might be something about the JFS --> Ext4 that could be similar to what anglican was referring to in post 2 about the time difference between Ext3 -->NTFS and problems with deletes when resyncing from one to the other.

Like the others, I can verify that I mirror correctly a dir from Ext-->Ext


Edit:  -n ??? , you're still doing a dry run?

---

### Post by pataphysician on 2010-08-12
> **QLee said:**
> Well, it's looking to me like it might be something about the JFS --> Ext4 that could be similar to what anglican was referring to in post 2 about the time difference between Ext3 -->NTFS and problems with deletes when resyncing from one to the other.

Like the others, I can verify that I mirror correctly a dir from Ext-->Ext


Edit:  -n ??? , you're still doing a dry run?

Well, I ran two actual back-ups. The second run is when I noticed it wasn't keeping subdirectories in sync. After that I started using -n for testing various switches.

Since I just got the drive and it's only got back-up data on it, maybe I'll just format to JFS and see what happens.

---

### Post by anglican on 2010-08-12
> **pataphysician said:**
> Well, I ran two actual back-ups. The second run is when I noticed it wasn't keeping subdirectories in sync. After that I started using -n for testing various switches.

Since I just got the drive and it's only got back-up data on it, maybe I'll just format to JFS and see what happens.Have you tried the"--modify-window=1" switch (you can even try numbers larger than 1 - though that shouldn't be necessary)? Whilst I wouldn't expect this to be a problem with jfs (which is normally a very reliable file system) there may be some issue with times that is causing this. If you get the same problem backing up jfs->jfs then I guess it's time to submit an rsync bugreport :(

H

---

### Post by pataphysician on 2010-08-13
> **anglican said:**
> Have you tried the"--modify-window=1" switch (you can even try numbers larger than 1 - though that shouldn't be necessary)? Whilst I wouldn't expect this to be a problem with jfs (which is normally a very reliable file system) there may be some issue with times that is causing this. If you get the same problem backing up jfs->jfs then I guess it's time to submit an rsync bugreport :(

H

Yeah, it's still not working. I appreciate the replies though! I don't think it's a time thing because I'm just creating directories and files on the destination which never existed on the source, and then when I run an rsync test the subdirectories I created don't get deleted.

```

[mike@robots mike]$ pwd
/media/8c4d270d-6139-4fed-8a32-2df8d28acdf3/mike
[mike@robots mike]$ mkdir deleteme1
[mike@robots mike]$ cd deleteme1/
[mike@robots deleteme1]$ touch deleteme1.txt
[mike@robots deleteme1]$ cd ../
[mike@robots mike]$ cd ./Desktop/
[mike@robots Desktop]$ mkdir deleteme2
[mike@robots Desktop]$ cd deleteme2/
[mike@robots deleteme2]$ touch deleteme2.txt
[mike@robots deleteme2]$ rsync -avn --delete /home/mike/ /media/8c4d270d-6139-4fed-8a32-2df8d28acdf3/mike | grep deletem
deleting deleteme1/deleteme1.txt
deleting deleteme1/
[mike@robots deleteme2]$ 

```

So, it doesn't get rid of deleteme2. It'll only do the subdirectories in the "root" of the backup.

```


[mike@robots deleteme2]$ cd ../
[mike@robots Desktop]$ rsync -avn --delete /home/mike/Desktop/ /media/8c4d270d-6139-4fed-8a32-2df8d28acdf3/mike/Desktop | grep deletem
deleting deleteme2/deleteme2.txt
deleting deleteme2/

```

---

### Post by QLee on 2010-08-13
This seems like a good day for a WAG about this issue.

Does it make any difference if you use 

rsync -av --delete /home/mike /media/8c4d270d-6139-4fed-8a32-2df8d28acdf3

instead of

rsync -av --delete /home/mike/ /media/8c4d270d-6139-4fed-8a32-2df8d28acdf3/mike

It's just something I would try before making the bug report, not much hope.


Edit: You did try delete-after didn't you?

---

### Post by QLee on 2010-08-13
[QUOTE=pataphysician]Yeah, it's still not working. I appreciate the replies though! I don't think it's a time thing because I'm just creating directories and files on the destination which never existed on the source, and then when I run an rsync test the subdirectories I created don't get deleted.[/QUOTE]

Forgive me for not reading this carefully enough the first time. When I use rsync to "mirror" a dir it is for the purposes of backup, I want an exact copy. It seems from your testing you're trying to create a way to "mirror" two directories, either of which could change (in my situation the "backup" never has files injected by myself or the system, so the occasion never arises where they would need to be deleted because they weren't on the source). Maybe you should look at the package unison, to synchronise both ways.

---

### Post by pataphysician on 2010-08-14
Well, like most of the stuff I ask about here, it turns out I was just being an idiot. I posted to the rsync mailing list and someone asked me to check the more verbose output (-vvv). Turns out there's a sub-directory in my home that's owned by root and which I don't have read access to. Once rsync hit that, I guess it would just give up on deleting anything else? I'm excluding that directory now and everything looks fine. Thanks again for everyone's replies.

---

### Post by QLee on 2010-08-14
> **pataphysician said:**
> Well, like most of the stuff I ask about here, it turns out I was just being an idiot. I posted to the rsync mailing list and someone asked me to check the more verbose output (-vvv). Turns out there's a sub-directory in my home that's owned by root and which I don't have read access to. Once rsync hit that, I guess it would just give up on deleting anything else? I'm excluding that directory now and everything looks fine. Thanks again for everyone's replies.

Well that points you to another problem you'll have to solve, how did that dir get there where it doesn't belong and how can you prevent it in future.

If you'd rsynced as root rather than as user it would have worked as you expected, wouldn't it, and the permissions would have still been preserved.

---

### Post by LewRockwell on 2010-08-14
For those who arrived at this particular thread while searching for mirrors or clones or back-ups:

We use Clonezilla and reference it for the non Command-line Commandos amongst us.

[http://distrowatch.com/table.php?distribution=clonezilla](http://distrowatch.com/table.php?distribution=clonezilla)

.

---

### Post by baddnady23 on 2010-08-16
Glad to hear you figured it out pretty much on your own!  It's amazing sometimes how little things like that will throw off such a seemingly simple process.  Best of luck in your future endeavors!

---

