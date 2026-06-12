---
title: "sbackup won't backup - Help."
date: 2010-04-30
forum: New to Ubuntu
---

### Post by crjackson on 2010-04-30
I installed sbackup on Lucid.  I went through the config process and selected manual backups.  I chose a new backup folder and saved my config.  I clicked on the backup now button and it gave me a pop-up telling me that the backup was started as a background process and gave me the ID number for the process.

PROBLEM?  It's not making any backups at all.

What am I doing wrong?

---

### Post by Paqman on 2010-04-30
Do you have permission to write to that location?

---

### Post by crjackson on 2010-04-30
> **Paqman said:**
> Do you have permission to write to that location?

yes, it's just a folder named sbackup in my home directory.

---

### Post by crjackson on 2010-04-30
Humm...  Still can't get it to work.  Thinking of purging and reinstalling.

---

### Post by crjackson on 2010-04-30
Okay, having now reinstalled after a purge, and determined that sbackup is not a good solution (since it doesn't work).  Is there a real program that actually works and does something similar to sbackup's intended functions?

---

### Post by crjackson on 2010-04-30
Well, I installed on another machine with a clean install of Lucid and got the same result.  It seems that sbackup is crap on my systems.

I installed a program called deja-dup and it works fairly well.  The only thing I don't like about this one is that it won't let me backup to a different hard disk.  It will restore from there perfectly, but it backup to it.  It gives me an error.  What I had to do is make a backup directory in my home folder for the backup.  Then I cut/paste the folder to another drive.

I would have been nice if sbackup had worked.  I liked it's gui.

If someone can tell me how to make it work it would be appreciated.

---

### Post by words1 on 2010-04-30
Same here -- doesn't work on a fresh clean Lucid installation.  Bummer.

---

### Post by derande on 2010-04-30
Back in Time works well if you don't need to auto-restore (just as a file/folder backup tool):

[http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html]("http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html")

---

### Post by mikodo on 2010-04-30
Sbackup is hosed for me on Lucid. 

Question: Does Back in Time work with Ext4 FS's?

---

### Post by crjackson on 2010-04-30
> **derande said:**
> Back in Time works well if you don't need to auto-restore (just as a file/folder backup tool):

[http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html]("http://www.ubuntugeek.com/back-in-time-a-simple-backup-tool-for-ubuntu.html")

I'll have a look at it.  Thanks.

---

### Post by crjackson on 2010-04-30
> **mikodo said:**
> Sbackup is hosed for me on Lucid. 

Question: Does Back in Time work with Ext4 FS's?

I'm pretty sure it does.

Glad to know I'm not the only one.

So far I've settled on daja-dup.  Nice simple GUI and works well.  I tested both backup and restore.

My only grip is I couldn't backup to another local SATA drive (only the boot drive would work locally).  I made a backup folder in my home directory, then when the backup was done, I moved it to the external drive.  Restore from an external source works just fine.

I was able to backup to an external USB drive with no problems though.

---

### Post by mikodo on 2010-04-30
Thanks for the tip on Deja Dup. I'm going to give it a try.

Mike

---

### Post by crjackson on 2010-05-01
> **mikodo said:**
> Thanks for the tip on Deja Dup. I'm going to give it a try.

Mike

It's working great for me.  Has I nice simple interface.

Here is the repository:

```
http://ppa.launchpad.net/deja-dup-team/ppa/ubuntu lucid main
```

---

### Post by crjackson on 2010-05-01
Okay, just installed Back in time.  Love it!  Why...?

I love daja-dup but it does have this bug that won't let me direct it the drive I want. I can live with it and I LOVE the GUI it has, but still.... bug....

1) It's in the default repositories.

2) It backs up EXACTLY the way I need.

3) No bugs encountered (YET)!

After my wife takes off for work, I'm going to backup my system with both tools and do a new fresh install again just so I can test the restore functions of both and time them.

I'll post back with my findings...

---

### Post by crjackson on 2010-05-01
Okay so here is my result.

My preference is daja-dup.  I filed a bug report about the backup locations as above and just got an email that the bug was fixed.  The fix hasn't hit the repository just yet however.

daja-dup works best for me because it will restore all the selected files & folders in one click. It also presents with a progress bar which is nice.

Back In Time required that you highlight each individual folder and/or file and restore them one at a time.  If you could simply select all from the backup snapshot it would be the winner for me, but since I have to select each item inside the snapshot one at a time, it's a no go for my purposes.

If I had a need to restore only one particular folder or file, then it would be a champ. I really need it to be flexible enough to either restore the whole snapshot (which I would use MOST of the time) or restore just a certain file or folder.

So if I want to be able to do both, I would have to use both programs.  Not good...

Perhaps one of the developers will see the value in this and add it to one of the applications.  Who knows?  For now I'll be using daja-dup.

Also, deja-dup compresses the files and produces a very slightly smaller backup.

---

### Post by svegress on 2010-05-02
> **crjackson said:**
> My preference is daja-dup. 

I started at the same point: the old but reliable sbackup failed when I went from Karmic to Lucid.  But I took a different path--a fork from sbackup called NSsbackup.  My testing so far show it is a worthy successor to sbackup.  It working in the familiar ways and with much the same interface--but Not So Simple.

You will find it on [Launch pad]("https://launchpad.net/nssbackup") along with an install and update PPA.  Unfortunately, there is no manual so a look at the "Answers" section of the project is necessary.

An endearing feature is that it can upgrade the old sbackup archives--again check in the "Answers".  

This kind of backup is not my perfect answer but I find many of the synchronisation applications a little intimidating.  The user interfaces tend to work really well for anyone who thinks working on the commandline is "simple".

---

### Post by crjackson on 2010-05-02
> **svegress said:**
> I started at the same point: the old but reliable sbackup failed when I went from Karmic to Lucid.  But I took a different path--a fork from sbackup called NSsbackup.  My testing so far show it is a worthy successor to sbackup.  It working in the familiar ways and with much the same interface--but Not So Simple.

You will find it on [Launch pad]("https://launchpad.net/nssbackup") along with an install and update PPA.  Unfortunately, there is no manual so a look at the "Answers" section of the project is necessary.

An endearing feature is that it can upgrade the old sbackup archives--again check in the "Answers".  

This kind of backup is not my perfect answer but I find many of the synchronization applications a little intimidating.  The user interfaces tend to work really well for anyone who thinks working on the command-line is "simple".

I'll have a look at it.  Right now I'm pretty satisfied with deja-dup. The developer is very active with bug fixing and has already addressed the only bug I've been able to find.

---

### Post by mikodo on 2010-05-03
Hi crjackson,

I installed the PPA of deja-dup to my software sources and downloaded deja-dup from the repositories, but it fails to backup to my external hard-drive. It will backup internally, during a test run. I have written about it in the same bug report in Launchpad, that you have written in. I will have to wait and see if they have an explanation for me. Happy to hear that it is working well for you.

Thank you.

---

### Post by crjackson on 2010-05-04
> **mikodo said:**
> Hi crjackson,

I installed the PPA of deja-dup to my software sources and downloaded deja-dup from the repositories, but it fails to backup to my external hard-drive. It will backup internally, during a test run. I have written about it in the same bug report in Launchpad, that you have written in. I will have to wait and see if they have an explanation for me. Happy to hear that it is working well for you.

Thank you.

I got an update for deja-dup this morning and have tested it on 2 external drives.  It's working perfectly for me now.

---

### Post by mikodo on 2010-05-04
Hi crjackson, Michael Terry wrote in the bug log, that the problem I am having, is to do with something else other than the bug, that has been corrected by the fix. He writes " 	 		Mike, your issue is a different one than this bug.  It looks like your  issue involves the disk being full/not writable or something.  Please  file a new bug". My external disks and an internal partition are not full, so I am thinking that it may have something to do with my permissions settings and am at a loss as to what to do now. Maybe I'll have to start a new bug report or as I am more inclined to do, request assistance here with a new thread.

Thanks.

---

### Post by crjackson on 2010-05-04
> **mikodo said:**
> Hi crjackson, Michael Terry wrote in the bug log, that the problem I am having, is to do with something else other than the bug, that has been corrected by the fix. He writes " 	 		Mike, your issue is a different one than this bug.  It looks like your  issue involves the disk being full/not writable or something.  Please  file a new bug". My external disks and an internal partition are not full, so I am thinking that it may have something to do with my permissions settings and am at a loss as to what to do now. Maybe I'll have to start a new bug report or as I am more inclined to do, request assistance here with a new thread.

Thanks.

I suspect that information is accurate.  I have done many backups now and it's working perfectly fine on external drives.

My only criticism is the scheduling of backups.  It has no provision for setting the time of day the backup would occur if automatic backups are activated.  There really needs to be a feature enhancement regarding this.  Otherwise the program works perfect for me.

---

### Post by mikodo on 2010-05-06
It is working fine for me now. All my wrong.I had a professional in. He  had to make a new directory for the ext. HD, correct the mount,  change  ownership and perms,  and add the new mount point in /etc/fstab. 

Thanks again for the tip about Deja-dup. I really like it.

Mike

---

### Post by crjackson on 2010-05-06
> **mikodo said:**
> It is working fine for me now. All my wrong.I had a professional in. He  had to make a new directory for the ext. HD, correct the mount,  change  ownership and perms,  and add the new mount point in /etc/fstab. 

Thanks again for the tip about Deja-dup. I really like it.

Mike

Glad to here it's working.

---

### Post by darkstaar on 2010-05-06
Oops!

I hadn't even realized that sbackup wasn't working until I checked it after spotting this thread. I was just assuming that my backups were being performed.

I guess it pays to check on such things rather than just assuming.

Anyway, happy to find out about Déjà Dup here. It's an excellent replacement.

---

### Post by mikodo on 2010-06-27
Here is a link to a fix for Sbackup with Lucid, on souceforge, offered by jcourcel. Click on the comments, and you will find in one of them, his fix, that others have used successfully.

[http://sourceforge.net/tracker/?func=detail&aid=2996590&group_id=145360&atid=761640](http://sourceforge.net/tracker/?func=detail&aid=2996590&group_id=145360&atid=761640)

Hope this helps someone.

---

