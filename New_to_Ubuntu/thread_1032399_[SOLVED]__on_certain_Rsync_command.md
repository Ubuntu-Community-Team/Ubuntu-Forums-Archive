---
title: "[SOLVED] ? on certain Rsync command"
date: 2009-01-06
forum: New to Ubuntu
---

### Post by Kellemora on 2009-01-06
Hi Gang

Does anyone know which command or combination of commands that will cause Rsync to copy ONLY files that updated, not rewrite all 500,000 files at each mirror time?

I've read the man rsync until I'm blue in the face and the pages are frayed.  Everything that suggests it will do this, doesn't.

If I use "--ignore-existing" changed files do not get copied to the mirror.  I tried "--update" with some small files as a test.  And it did not update the mirror.  And if I tell it to "--perms" I end up with all the files locked to the users.

I myself use "--delete" on smaller files that were amended.  But I don't DARE use this command in the backup from File Server to it's Mirror as someone could wipe out our whole database with ease.

I'm used to Mirroring programs in XP that read the source, read the destination, then copy ONLY those files that are NEW or CHANGED since the last mirroring was run.

Rsync is supposed to be more powerful, faster, and offer more options.  It may, except I can't figure out how to get it to do the simplest chores, read source, read destination, then copy ONLY those files that are NEW or CHANGED since the last time Rsync was run.

I know it will do it!  But HOW??????

Thanks for your help!

TTUL
Gary

---

### Post by bryanl on 2009-01-06
> Everything that suggests it will do this, doesn't. ... if I tell it to "--perms" I end up with all the files locked to the users.
I don't think your problem is rsync but rather with the source file attributes.

Here is the command from a snapshot backup script that does what you ask.
```
rsync -a --delete --modify-window=10 $source/ $TARGET/$BACKUP_DATE/$source/ 
```
the modify-window is needed for my CIFS shares to handle time stamp roundoffs. The $ items are script variables to designate the source and destination directories. The --delete removes files from the destination that aren't in the source. The -a is an archive setting that saves having to enter a whole pile of options.

---

### Post by Kellemora on 2009-01-06
HI Bryan

Thanks for responding!

I'm not sure what the --archive does, mainly because I don't know what recursive means in this case.

Although I would like to be able to use --delete, I think it's opening the door to have our entire mirror wiped out if an employee decides to wipe the file server just before it mirrors itself.  Unless using --archive prevents this, which I don't think it does.

I like the idea of --modify-window=10 after reading it.  But once again they mention recursive.  I'm sure the dictionary definition is nothing like Rsync's definition, hi hi.....

On my personal work, I've been using
rsync -av -delete source destination

Previously I used rsync -av -delete --ignore-existing source destination, until I found out it did not update changed files.

My goal here is to get rsync NOT to recopy all of the files every time it runs, only those files that have changed.

Is THAT what Recursive or Archive means?????

TTUL
Gary

---

### Post by bryanl on 2009-01-06
The archive switch also copies permissions, owners, groups, and does other things so that the copy is an exact duplicate of the original. Recursive means to include all subdirectories and their contents below the source directory.

> Although I would like to be able to use --delete, I think it's opening the door to have our entire mirror wiped out if an employee decides to wipe the file server just before it mirrors itself
You are thinking ahead! I just read a caution about some mirroring device that warned about just this problem.

The fix is to use a snapshot backup such as the script I use by Brice Burgess (multi_backup.sh -- backup to a local drive using rsync. Uses hard-link rotation to keep multiple backups). It should be findable on the web. It creates dated backup copies with hard links that are 'filled in' by rsync to update changes. You set how many and can use a cron job to make a new timestamped snapshot at intervals you think appropriate. 

> On my personal work, I've been using
rsync -av -delete source destination
that should make a nice copy and the data transferred report will give you an idea of just how much has changed.

> My goal here is to get rsync NOT to recopy all of the files every time it runs, only those files that have changed.

If you are getting all files copied each time, it means either the size or the modified timestamp indicate it is different between source and dest. 

If you are getting files copied that you don't think have changed, check the file size and last modified time stamp. The modified-window is available to solve the problem of copies between 2 systems with slightly different ways of keeping time. But if your dest doesn't handle the timestamp or size properly that might also cause some problems.

If you have certain parts of the file hierarchy below source you don't want in the copy, you have to use the exclude switch.

---

### Post by Kellemora on 2009-01-06
Hi Bryan

I've been experimenting with a group of smaller files so it didn't take so long to test.

For one, I was giving you the wrong line.  I had forgotten I had removed the -a due to so many errors with some files that cannot have anything about them changed.  "Operation Not Permitted" is the error.

Here is what I've been using tonight, and I sorta learned something tonight too (thanks to your help)

```
rsync -r -v --progress --delete source destination
```

Naturally I will NOT use --delete in the automatic backup of the File Server for reasons already mentioned.

But here is what I learned new!

After running rsync to load a blank folder, I changed 8 files out of the 30 I'm playing with and deleted 1 of them.

rsync to a blank folder naturally copies ALL of the files, it's supposed to.
But I noticed after it deleted the 1 file, it still copied ALL of the files the second time also.  I made changes to 8 of them again, different than the last, and this time it only copied those 8 files (after reading source and destination).
So I added 4 files, deleted an existing file, and edited 4.
This time I ran rsync, it deleted the deleted file, then copied all of the files.
Ran rsync with no changes to the files of any kind, it still copied the 4 new ones a second time, and the 4 edited ones a second time, but none of the rest.
Then running it again, without touching anything, it didn't copy any since they were already there.

Maybe rsync just double checks itself on new changes and additions?????

But it appears after the third run with no changes, it no longer copies any files that have not changed.
That was hard to tell with like 387,000 files that were moved!

I'll mark this solved now, since it seems I'm back on track again.

Thank you VERY VERY Much!

TTUL
Gary

---

### Post by Kellemora on 2009-01-06
Hi Bryan

I had marked this solved and after doing some more tests came back and marked it unsolved.........

Here is what I found and why I marked it unsolved.

On the test of my small file, it worked as I said.

I ran the same test on some folders so I was just under 100,000 files, after the third time through it worked as expected.

But when I upped the file count to 150,000 files, it continued to copy ALL of the files, including old archives that have not changed in over 5 years.
I ran rsync 4 times with the same results EVERY FILE COPIES EVERY TIME!  No wonder it takes 6 hours to run a 15 minute mirror!

I'm going to turn in a bug report on this!

Good thing I kept a couple of XP machines around!
I'll just use a WORKING mirror program on the DOZE I've used for years with no problems like this ever!
I have to keep a Doze machine around anyhow in order to use Ubuntu!  This just adds yet another reason to the growing list!

TTUL
Gary

---

### Post by bryanl on 2009-01-07
"operation not permitted" implies that you do not have the proper file access permissions. Try it with sudo or check the permissions for the user doing the rsync. It may be that you don't have permission to write to the destination.

If you are doing backups to files where you are not the owner it is always better to use sudo to run the backup as root.

for the cases where all files are being copied, compare the source and dest modified timestamps. If it appears they are the same and rsync still wants to do the update, try the modified-window parameter and see if different values make a difference.

---

### Post by Kellemora on 2009-01-07
Hi Bryan

One of the fellows from the IT department where the frau works was nice enough to stop by again tonight.  Not that we managed to get any further along than I already was.

He took a look at the small 9,000 files in 30 folders since it would be the quickest to experiment with.  Source drive is 200 gig formated EXT3, destination drive 10 gig also formatted EXT3.
Both of these are INTERNAL hard drives IDE.

He used several combinations of commands and rsync would consistently keep rewriting files, but not all the time and not the same files.  If we use -a the errors are coming from control files that are part of that database.

But the whole thing that even has him befuddled is that it will write the entire file the first time, write about 1/2 of it the second time, write nothing the third time, then rewrite the entire file over again the fourth time.

Rsync should NOT be doing this when no files have changed.
It COULD if I was writing from one computer to another, but not on the same computer on internal hard drives.

We also tried a couple of other experiments.
Direct copy using cut n paste ran nearly twice as fast as rsync and produced no errors.  Then running rysnc deleted the files already there and rewrote them completely, then rewrote them completely again.

As far as my larger files from the file server, that turns out to be another matter entirely.
Rsync for UNIX must be quite a bit different than Rsync for Linux, because he had several commands that don't work in Linux that they use all the time.

He gave me a line to try this evening on the large file that seems to be working with the smaller file.
Oh, we also reloaded a newer version of Rsync than what was in the repositories.  I think mine was 2.6.9 and we downloaded and installed 3.0.3 I think he said 3.0.4 is out but not debugged yet.

In any case, I'll let you know how things go tonight.
He wants me to keep image files moved separately using a -W (capital W) in the line.  Image corruption seems to be a problem still on LARGE Hi-Res image files.

I have to sort my notes here before I forget which is for which, hi hi.......

TTUL
Gary

---

### Post by Kellemora on 2009-01-08
Hi Brian

I hate to say this, but I'm giving up!

Every time I think I have it and it's not recopying files, then almost immediately using the exact same settings on another set of files, it's back to recopying files again.
This happens like 4 to 8 times before it finally stops doing that, until you make one small change in a single file, then it recopies all of them again all over again another 4 to 8 times.

If I use -t to check times, I get 1 error for EVERY Single Folder, because you can't set times on folders I guess.

What I want is to MIRROR the files from my Data File Server and rsync royally screws up ALL the times and dates of the files.  And so does the Copy n Paste command in Ubuntu.

After working at this the ENTIRE DAY and NIGHT and last night too!
I decided to try something!
I went to a Windows machine and had it Fetch the files from the Ubuntu File Server and mirror them to the backup drive on the same Ubuntu machine.  It did so perfectly, not a single problem.  I ran the program a second time and zero files were copied since zero files changed.

I figure if the IT guy who runs the IT department of a major company cannot figure out why rsync does not work on Ubuntu, but it works fine on CentOS and on UNIX, the only thing it could be is something is not right with the Kernel Ubuntu has modified.
Many rsync commands he uses daily are NOT RECOGNIZED in Ubuntu!
3/4 of them are recognized in CentOS and all of them in UNIX.

In fact, he STRONGLY SUGGESTED I drop Ubuntu and return to CentOS (which is a clone of Red Hat) that way almost any IT person will be able to help sort out the problems I've encountered.

It just so happens that I do have CentOS on a couple of machines as dual boot.  I ran the same backup this afternoon using the same rsync parameters and it worked perfectly and did NOT copy ANY files the second run through.  When I changed one single file by only changing the size of line spacing.  It copied ONLY that file and no others.  Of course it had to read all the files first.  But it also did not change the modification times of the files either.

In any case, I'm going to mark this solved, even though it isn't so folks quit whipping a dead horse!

Thanks for the help you have given me!

TTUL
Gary

---

### Post by b0b138 on 2009-01-08
I've been playing with rsync lately and here's the command I've been using without problem

```
rsync -vurt --progress --delete source destination
```

---

### Post by Kellemora on 2009-01-09
Hi Bob

Thanks for chiming in here!

I noticed you had the -u command in your string!

I've made very good use of that in the past myself, especially with certain shared files and Font files too, that we maintain a massive database of.

I think we've narrowed down our problem considerably, by changing from version 2.6.9 to version 3.0.3 but it too still has bugs when run on Ubuntu that don't appear on other distros.

Here's why!
Now think about this for a second and you'll see WHY rsync is messing up on us.

Put YOUR definition behind the following commands, and you'll see why the ERRORS we are getting are illogical.

chgrp means
set time means
chown means

Preserve Group means
Preserve Time means
Preserve Permission means

In the first group of three above, the command is for an ACTION to make a CHANGE from what existed previously.  EG: chgrp means to change group.
OK, in the second group of three, the command is to Leave things as they are, do NOT make any changes.  EG: Preserve Group means if the document is owned by BOZO now, leave it don't change it, it's Bozo's, keep it that way.

I'm sure you came up with the same definitions as I did!

If you did, can you explain the following errors?

Failed to SET TIME on blah de blah
Failed to chgrp on blah de blah, etc.

rsync should NOT be trying to CHANGE THE GROUP, it was set to LEAVE THE GROUP ALONE........Same way with TIME, it was told to PRESERVE TIME, NOT CHANGE IT.

After using rsync, 100% of our time critical DATED files have been altered to the date in which they were rsync-ed.
On some documents we can open the documents and find the creation date.  But the modification dates no longer jive.
According to our database.  Our 1995 through 2007 Tax Receipts were created yesterday.  The date we transmitted our closing documents for 6 houses purchased in 1998 and sold in 2000 was Yesterday!  How can we CLOSE on the purchase of 6 houses on January 8, 2009, take possession of those houses, renovate those houses, place them on the market, and sell them in the year 2000, if we didn't close on them until January 8, 2009?

But our biggest problem is that the ENTIRE Database is backing up instead of just changed files.  What should take less than 10 minutes is taking over 6 hours.  I call that EXCESSIVE WEAR AND TEAR of the Hard Drives, besides the times and dates on everything being changed.

This does NOT happen on UNIX or CentOS running the same program!

Preserve should mean Preserve, and Change should mean Change, not just the opposite!

I think the problem is, my computers are haunted!
Or at least there is a lot of poltergeist activity in them lately, hi hi.............

We have STRANGE network problems too!
For several days, everything is hunky dory.
Then one day, shared files won't show up.
Without doing anything, just waiting, within a day or two, everything starts working fine again.

Thanks for your input, it was appreciated I assure you!

TTUL
Gary

---

### Post by b0b138 on 2009-01-09
Are you trying to sync between linux and windows?

---

### Post by Kellemora on 2009-01-10
Hi bOb

No, I'm trying to rsync from sdb to sdc on the same computer, THEN sdc gets rsynced to an external hard drive.  All EXT3 drives.

I HAVE learned a little trick messing with this over the past week though!

If I use -t in my command it will only copy over changed files, but give me an error message for every folder in those files.
Then I can run rsync again without the -t and it will check that there were no changes and say completed with no errors.  So at least I know everything copied over as it should.

Nonetheless, If change even one file, lets say one file in the ACTIVE folder, then rsync even with -t in the script will recopy EVERYTHING including the ARCHIVED FILES already on the drive it's writing to.  Once the file is rewritten I can run it again with -t in the script and no files will copy, but I get all the error messages.  Take out -t and it shows no files to copy, or copy complete in a matter of minutes on the large file folder.

Changing ONE document in the ACTIVE folder, should NOT cause ALL of the old folders and especially NOT the ARCHIVE to be recopied to the second hard drive.

Now, since my last message to you, I have made a few changes to the File Server.  No program generated data is stored in the Database now.  So, when I run RSYNC with -av, etc. I no longer get the error messages, not even on the folders.  AND it appears that it is only copying files that changed now too, because it ran in only 14 minutes and showed 9 files copied over.  But it's not consistent at doing this.  I could tell from the log file from last night that it ran from 2AM to 7:38AM which means once again it recopied the entire hard drive, not just the changed files.  In other words, it took close to 6 hours again!  But when I checked it today manually, it ran again in like 12 minutes, 2 new files copied over, which are the two files I did change this morning.  

I'm thinking about moving THIS computer up to the tier and pulling down the Dell and using it for my workstation.  Seems some of the programs I'm having trouble with are working better on the Dell than on this machine for some reason.

However, I will say, since all the new updates and upgrades, including the new Kernel that came down the pike over the past couple of days, several of the problems I was having cleared up.
Of course with a new Kernel I had to reboot all the machines too!  One gave me fits and I had to go into recovery mode to fix that.  But every since, most of the things that was causing me grief have fixed themselves.  Just hope it lasts.  I've been working with the Bug team on one of those, and a couple of the changes that came down the pike I think were a result of that.

In any case, I seem to have figured out a work around that seems to work OK most of the time now.  So I'm going to see if a little tweaking here or there might make it better yet.

I've already set rsync to run the smaller folders individually, first with the -t in the script and then right after that without the -t so the log file shows complete with no errors, hi hi.......

It's like back when I first started and did NOT know what a symlink was yet.  Using pre-printed instructions I was able to put /home on a different partition.  But I wasn't sure how to put files on OTHER hard drives.
I royally messed things up by using the word /home/user/folder on different drives.
And I'm still NOT Sure I'm doing it correctly as it is.

On my sda drive, I have /home in it's own partition.
Then within /home, besides /home/user I have made several folders inside of /home but ahead of /home/user without using the word /home. For Example: I have /Business, /Family, /Reference, /Property on sda.  But NOTHING is in any of those folders.  Then on sdb I have /Business, /Family, /Reference, /Property.  And made a symlink to their equivalent in the /home directory.  This is working just fine for me!  Knock on simulated woodgrain, hi hi..........

But, before I learned about symlinks, I had used /home/business, /home/family, /home/reference and /home/property on sdb.  Setting business, family, home and property as USERNAMES.
It actually worked, except you had to LOG OUT of business to get to log-in on family.  That was good in a way as I had a different password for business than I did each of the others.

But, I was told what I did was impossible, it can't work, yet it was working just fine for almost a month, then BANG, I couldn't log-in to any of them anymore, said they didn't exist.
And I didn't change anything.  However, I did get some update I downloaded, the red down arrow icon type.  I did not lose any data though, because using gparted I think it was, I brought them back into use.  But quickly changed things using the symlink method I had learned about.
But NOW, since I built a new file server, I just have ONE FOLDER on the entire hard drive named appropriately FILE SERVER and within that folder is a folder named Business, a folder named Family, etc. and of course, umpteen zillion folders inside of those.  In other words, for once, things around here are gaining some semblance of order.

Hey sorry, I tend to ramble!

I think we can drop the rsync problems since I have a work around that's working well enough.  And I also found out that if it decides to do a full download, it's OK to hit pause, wait for it to catch up, then Stop the program, when this happens during the work day.

Happy New Year!

TTUL
Gary

---

### Post by b0b138 on 2009-01-11
The reason I was wondering about linux and windows was it kinda sounds like you've got some funky permissions problems,

> On my sda drive, I have /home in it's own partition.
Then within /home, besides /home/user I have made several folders inside of /home but ahead of /home/user without using the word /home. For Example: I have /Business, /Family, /Reference, /Property on sda. But NOTHING is in any of those folders. Then on sdb I have /Business, /Family, /Reference, /Property. And made a symlink to their equivalent in the /home directory. This is working just fine for me! Knock on simulated woodgrain, hi hi..........

While I am definitely not a linux expert, the above doesn't make sense (to me anyways :)) If you have home on it's own partition, then you should have something like / mounted to sda1 and /home mounted to sda2. /Business would be on sda1.  The only way for it to be on homes partition (sda2) is to have the folder as /home/Business.

Also, any folders you made off of / would had to have been made with sudo because you don't have permission to create files/folders there. ie. sudo mkdir /Business.  Then you would also need to chown and chmod the folder for it used normally.  This would also need to be done for a second disk (sdb). Either taking ownership of the whole drive or creating a folder and taking ownership of that. Anything on that drive would be located at /path/to/mount_point. For example my 3rd disk I'm using for backups is at /media/backup. I specified the name backup but it could be anything.

---

### Post by Kellemora on 2009-01-11
Hi bOb

Since I've changed to a file server, and not using the symlink method I was using before I was trying to figure the Terminal command to list the list the contents of the drive.

I used ls /dev/disk/by-label which showed the disks on the system.

But I don't remember HOW to move to a different disk to list root directory on that disk from terminal to post it here for you to see.

Now in Nautilus it just shows the hard drives and if I select the File Server hard drive, all I see are two folders, One says System Volume Information the other says FileServer which is a folder.  If I open that Folder then I see my Broad Subject Folders as expected.

If I try cd /fileserver all I get is no such file or directory.
Which makes sense since I'm on the wrong hard drive while typing that.  I've also tried ls /dev/disk/by-label/and the name showing as the drive label name.  No Luck.

In any case, I just wanted to show you that all it shows is:
/FileServer
/System Volume Info
and I think
/Lost & Found
is there too or it is on one of them.

It works just fine and all the machines can see it just fine, so that's all that really matters to me.

TTUL
Gary

---

### Post by b0b138 on 2009-01-11
Could you post the outputs of these commands

```
cat /etc/fstab
```

```
mount
```

---

### Post by Kellemora on 2009-01-12
HI Bob

Be glad to!

```
gary@HPpav753nUbuntu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
   UUID=5ecf8cf3-6da6-4a8c-98fb-03f0795065ce /               ext3    relatime,errors=remount-ro 0       1
# /dev/sdb1
   UUID=d3fbb684-3d1d-4ce3-9bc0-bff0e7400bb3  /media/sdb1  ext3  relatime,errors=remount-ro  0  2
/dev/sda5       none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/scd1       /media/cdrom1   udf,iso9660 user,noauto,exec,utf8 0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
gary@HPpav753nUbuntu:~$ 
```

```
gary@HPpav753nUbuntu:~$ mount
/dev/sda1 on / type ext3 (rw,relatime,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.24-23-generic/volatile type tmpfs (rw)
/dev/sdb1 on /media/sdb1 type ext3 (rw,relatime,errors=remount-ro)
securityfs on /sys/kernel/security type securityfs (rw)
nfsd on /proc/fs/nfsd type nfsd (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/gary/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=gary)
/dev/sdc1 on /media/500gigExtIomegaHD type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
/dev/sdd1 on /media/FILESERVER500gigExtIomega HD type fuseblk (rw,nosuid,nodev,noatime,allow_other,blksize=4096)
gary@HPpav753nUbuntu:~$ 
```

Still don't show the tree though!

TTUL
Gary

---

### Post by b0b138 on 2009-01-13
No, but it does show that the system is installed on sda. /home is NOT on a separate partition or disk, it is also on sda. sdb I'm assuming is a second internal drive mounted at /media/sdb1. Then at the time you ran the mount command, there seems to be 2 external disks. sdc1 mounted to /media/500gigExtIomegaHD and sdd1 mounted to /media/FILESERVER500gigExtIomega HD

more commands.....

ls -l /   (shows directory listing at the root level of sda)

ls -l /media/sdb1   (shows directory listing at the root level of second disk sdb)

and can you post the whole rsync command(s) you use

---

### Post by Kellemora on 2009-01-14
Hi Bob

ls -l /media/sdb1 AND ls -l /media/FILESERVER, etc. BOTH give me, No Such File or Directory.....

ls -l on the root directory gives.
```
gary@HPpav753nUbuntu:~$ ls -l
total 248
drwxrwxr-x 3 gary gary  4096 2008-10-30 15:17 Businesses
drwxrwxrwx 4 gary gary  4096 2009-01-06 20:12 Desktop
drwxrwxr-x 2 gary gary  4096 2008-12-01 15:19 Documents
lrwxrwxrwx 1 gary gary    26 2008-09-25 16:16 Examples -> /usr/share/example-content
-rw-r--r-- 1 gary gary 31887 2008-11-24 13:12 hs_err_pid16815.log
-rw-r--r-- 1 gary gary 32333 2008-12-21 10:34 hs_err_pid25006.log
-rw-r--r-- 1 gary gary 32746 2008-11-07 20:32 hs_err_pid26858.log
-rw-r--r-- 1 gary gary 26080 2008-12-02 10:12 hs_err_pid6825.log
-rw-r--r-- 1 gary gary 33252 2008-12-01 17:32 hs_err_pid7439.log
-rw-r--r-- 1 gary gary 32396 2008-11-11 19:00 hs_err_pid8938.log
drwx------ 2 gary gary  4096 2008-11-12 20:32 memo_file
drwxrwxrwx 2 gary gary  4096 2008-11-03 07:57 Music
drwx------ 3 gary gary  4096 2008-11-12 20:34 MyPDA
drwxr-xr-x 3 gary gary  4096 2008-11-13 19:22 Photos
drwxrwxrwx 2 gary gary  4096 2008-11-03 07:57 Pictures
drwxrwxr-x 3 gary gary  4096 2008-10-07 19:40 Public
drwxrwxr-x 2 gary gary  4096 2008-09-25 20:30 Templates
drwxrwxr-x 4 gary gary  4096 2008-10-26 23:17 Thunderbird eMailFolder
-rw-r--r-- 1 gary gary   192 2008-10-30 15:09 translog.20081030150913.log
-rw------- 1 gary gary   352 2008-11-25 12:57 unison.log
drwxrwxrwx 2 gary gary  4096 2008-11-03 07:57 Videos
gary@HPpav753nUbuntu:~$ 
```

I've never learned how to get the second hard drive OR the externals to list what's in them, other than using the GUI Nautilus.

```
gary@HPpav753nUbuntu:~$ ls -l /media/sdb1
ls: cannot access /media/sdb1: No such file or directory
gary@HPpav753nUbuntu:~$ 
```

And here is an attempt at seeing the External Mirror of the File Server
```
gary@HPpav753nUbuntu:~$ ls -l /media/FILESERVER500gigExtIomega
ls: cannot access /media/FILESERVER500gigExtIomega: No such file or directory
gary@HPpav753nUbuntu:~$ 
```

Does the same thing with ls -l /media/sdd1 also!

My rsync is pretty simple
```
rsync -r -v -t --progress --modify-window=1
```

I stopped using the -av and replaced it with -v -t else I get dozens of pages of errors.  The -t is working fine on the File Server now, since I deleted it and started from scratch using the -t, but other mirrors are still pitching errors on program generated data that needs mirrored with the data.  Like the index to the data generated by the program itself.

But as I said a couple of posts ago, the backup (mirror) for the data file server is working fine now, about 70% of the time.

For some unknown reason it decided to copy ALL the files again, not just the ones that have changed.  But only happening once in awhile and the fact I can pause and then stop it when it does it during work times, although a pain, at least it doesn't stop my work from getting done anymore.

I like to run the mirror at 10AM, Noon, 3PM, 6PM and at 3AM.
When it decides it wants to do the WHOLE FILE SYSTEM at 10AM or 3PM is when it irks me to no end, or did until I found out I can stop it without it causing any damage.
The problem of it deleting the entire mirror before writing was a problem with the old version I'm no longer using.

Also, I should mention that when I started over, I reformatted the mirror to NTFS to see if that would make a difference.  It didn't!  Works the same (time wise and bug wise) as it did when it was EXT3.  I still prefer EXT3's file system.  So will probably go back to that if I reformat again.

TTUL
Gary

---

### Post by Kellemora on 2009-01-14
Hi Bob

A follow up!

Somebody showed me the error of my ways, hi hi........

```
gary@HPpav753nUbuntu:~$ ls -l /media/"FILESERVER500gigInt HD"
total 0
drwxrwxrwx 1 root root 0 2008-12-28 16:29 FILE-SERVER
drwxrwxrwx 1 root root 0 2008-06-10 18:36 System Volume Information
gary@HPpav753nUbuntu:~$ 
```

NOW, is there a WAY to LIST what is under the folder FILE-SERVER?????

TTUL
Gary

---

### Post by Kellemora on 2009-01-14
Hi bOb

Also, here is the error list from a very short backup I made just a minute ago of my lunchtime e-mails.

```
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Embedded": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Embedded/2005": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Embedded/2006": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Embedded/2007": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/EudPriv/Ads": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/InOld.fol": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/LinkHistory": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Nickname": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/OutOld.fol": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Plugins": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Plugins/Esp": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Search": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Sigs": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/attach": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/attach/2005": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/attach/2006": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/attach/2007": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/icons": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/spool": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Embedded": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Embedded/2005": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Embedded/2006": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Embedded/2007": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/EudPriv/Ads": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/InOld.fol": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/LinkHistory": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Nickname": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/OutOld.fol": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Plugins": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Plugins/Esp": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Search": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/Sigs": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/attach": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/attach/2005": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/attach/2006": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/attach/2007": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/icons": Operation not permitted (1)
rsync: failed to set times on "/media/sdb1/BackupEudoraData/spool": Operation not permitted (1)
rsync error: some files could not be transferred (code 23) at main.c(977) [sender=2.6.9]

```

I was using ```
rsync -r -v -t --progress --delete --modify-window=1
```

If I run rsync without the -t first, it WILL recopy the entire file including all the archives.
But, if I run rsync with the -t first, it only copies the changed files, THEN I can run rsync without the -t and it will just show Completed after running with no errors.

So, as a matter of habit, I have to run rsync TWICE, once with the -t and once without the -t and remember to put the -t back in the script else it will copy the ENTIRE FILE.

rsync just should NOT work that way!

TTUL
Gary

---

### Post by b0b138 on 2009-01-14
hmm... alright.  Let me see the whole rsync command you're using, I want to see what you're entering for the source and destination. For example mine looks like ```
rsync -vurt --progress --delete --exclude=.* /home/rob /media/backup
``` You might not want to use --delete though. This will remove previously synced files that have since been deleted from the source.

and this again, you left off the / which then showed your home folder ```
ls -l /
```

and ```
ls -l /media
```

Do you have 2 external drives, or just one? Either way, unplug them and post the output of the above command. And the command again with them plugged in.

and ```
df -h
```

and ```
blkid
```

To see the contents of FILE-SERVER ```
 ls -l "/media/FILESERVER500gigInt HD/FILE-SERVER"
```

Linux doesn't like spaces in names, that's why it needs to be in quotations. It can also be ls /path/to/folder\ with\ spaces/ (I like quotes better, less cluttered)

---

### Post by Kellemora on 2009-01-15
Hi bOb

We REALLY have a major problem this morning!
NO ONE (not even me) can access the File Server now.
Thank Goodness I have an External Mirror to work from!

Don't know if this caused it or not, but last night I ran a different set of rsync commands.

```
rsync -r -t -p -o -g -v -W --progress --modify-windows=1
```
It RAN with ZERO errors.  And everything looks right.

Since we are working from the Mirror, which I don't want overwritten, I've disconnected the FileServer's HD for now.

I CHANGED the name of the HD because of that SPACE in it!
Boy, NOTHING is EASY in Ubuntu is it!
In Windows you just right click, select RENAME, make the change and your done.

This morning after I found none of the employees could do any work AGAIN (this is getting expensive), I ran to our closest place here in east podunk to grab another HD.  
AS I speak, I'm in the process of converting ALL of our Data back to the NTFS file system, SO I can just plug the drive into a Windows Box and do things quickly and easily!
After I complete the copying over to the new hard drive, I'll still have to run rsync on what WAS my mirror to get todays work saved.

It's really BAD (Almost worst than Bill Gates), when a computer takes control of your life and you cannot do anything at all because nothing works right.....

Even using chown -R user:user /media/etc. did not take.

I saw you used the command --exclude=.* 
To me that means exclude any file with a standard filename and suffix.  I used --ignore-existing once or twice, comes in handy for moving fonts files around.  Also used --existing thinking it meant to exclude files that were existing unchanged, but if they were changed, then they wouldn't be existing in that state.  What happened is it did NOT update any of the files that were changed to the mirror, and I didn't discover this until after I had built the file server and went to print out the finished orders and there WERE NONE TO PRINT........  Thankfully, each of those files were still on the machines they belonged on.

I'm going to have to drop working on this topic for now!
Looks like I have more serious things to consider right now!

Don't know whats worse, not being able to use your computer with Bill Gates permission and him knowing everything you do.
OR having the computer take control and not allowing you to do anything at all, unless you are the root user!

Having to make ALL of your employees ROOT USERS in order to accomplish menial tasks, is MORE DANGEROUS than running Mickey$oft Spyware!!!!!
Then I get errors about can't log-in more than once to the same files or by more than one user.  SAY WHAT, worked fine yesterday!

OK, gotta run, I'm the only one who can move files around and reset permissions that change on their own, etc.

After today, not much will be set up as it has been!
I found several delicate files in /var/lib/samba that had absolutely NO BUSINESS being there, for any reason!
Only stumbled across them due to error messages in nautilus alerting me to them.

I can't run an office when things work one day, the next day they don't, then the next day even I'm locked out of my OWN files.  Ridiculous!

I didn't spend all these manhours moving thousands of files around, and losing their VITAL HISTORICAL DATA in the process, only to find Folder Sharing does not work in Ubuntu to Ubuntu because ROOT takes CONTROL of the Folder and refuses to give it back again.

I made a post about what had happened, but then found the same problem listed in yet another unresolved Bug Report.

I started with CentOS and it looks like if I want to stay with Linux and have something that works, I had better seriously consider using an OS that works properly.  CentOS is an exact copy of Red Hat Enterprise Linux, only with no support behind it.
I chose Ubuntu just because of the wonderful folks here and their support, but many of the problems I've experienced from day one are still NOT RESOLVED and most are even shunned as, well you don't need that mouse to work or that keyboard to work or nobody uses floppies anymore so forget about it and use a CD instead.  Everything that does manage to get fixed is not a fix at all but a multi-step work around.

You can check back on my posts from 4 months ago and find the issues I need most, even after reposting several times or bumping the post up.  If there's a reply, it's it can't be done!

Center Mouse Button is set to a default function I've never used in my life, and nobody I know has used it for that purpose.  But the consensus is all Linux users use it to PASTE with.  And NOBODY wants to use it as the BACK button on a web browser.
In Windows, you can reassign any mouse button to any function even up to 28 button meeces which don't even exist yet.
Ubuntu, two buttons can be switched or reversed and that's about it.  
The keyboard and Mouse are the two MAJOR human interfaces with a computer, and the monitor too of course.  But Ubuntu has little to no support for these two items, they barely squeak by with the basics and then even those are iffy at times.

I hate to say this, but I'm thinking UBUNTU moved to #1 not because of Quality but because of these forums.  Like a FAD, everybody had to have a Pet Rock!

As I said way back during the beginning of this thread, rsync works in CentOS as expected, no problems.
In Ubuntu, it has been virtually disastrous!
Files I've had INTACT with their file dates and times since 1995 and earlier, and up to present, have all been changed via rsync or nautilus to the date they were moved.  I'm glad I never moved my main accounting data else all time sensitive audit trails would have been altered too........ 

I can NO LONGER go back to an image and see it's creation date to know if the image was last years issue or next years issue!
I can't look at family photos and know how old the folks in the pictures are anymore based on the date the photo was taken.
But the very worst thing is, I cannot go back to my client correspondence to see which orders came when.  In order to do my quarterly report, I now have to go back through all the paperwork associated with every quarterly report to see which orders applied and which didn't.  ALL of them have the same dates on them now.  Another UBUNTU EXCLUSIVE DISASTER!!!!

TTUL
Gary

---

