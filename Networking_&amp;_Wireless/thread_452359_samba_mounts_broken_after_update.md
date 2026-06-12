---
title: "samba mounts broken after update"
date: 2007-05-23
forum: Networking &amp; Wireless
---

### Post by Mujaheiden on 2007-05-23
Yesterday I mounted several samba network resources in the fstab file. This worked flawlessly.

Then this morning I got the usual update-notification, which I pursued without much thinking, and now i cant connect anymore to my samba mounts - although i can browse to them in the network.

I don't know if this is related to the update in the morning, but yesterday everything worked perfectly, also after reboot, so i really don't know whats changed besides the updating. Also i remember to see something smb-ish passing my screen, but didnt really pay attention

Any tips welcome.

---

### Post by Mujaheiden on 2007-05-23
To answer my own problem; somehow the mount point got screwed.

So I rebooted using the live cd, deleted the mount point - I couldnt access them in the normal login. Then I logged in again regularly, re-added the mount directories, and remounted my fstable, and everything was in order. No idea what happened, but I hope it was only once.

: edit : 

actually, the mount poits still dont work.

---

### Post by drybittermelon on 2007-06-01
I have the same problem.

Around three weeks ago, I set up a backup server (with rdiff-backup if anyone is interested) using Ubuntu 7.04. The machine wakes up every morning at 3am, mounts two samba shares on the network, backs them up onto its harddrive and shuts down itself at 6am. I tried running the backup script manually once, the backup takes around 1 hour. The machine only does backup and nothing else.

I check the logs of the machine during the night every now and then. I found that every so often the backup would suddenly stops working. On preliminary investigation, the samba mount points have been somehow corrupted, which causes the backup to fail. So I renamed the /mnt (where the samba shares are mounted) to /mnt1 or similar, and recreate the mount points (i.e. /mnt/a, /mnt/b), everything start working for a couple of days, before the problem repeats again.

Instead of renaming these corrupted mount points, I tried once to remove them, but its a pain; rm does not work, so I had to use root maintenance startup to fsck the drive, then delete the /mnt directory after fsck had fixed it.

Something else I have noticed, although may not be related, is that ever since this happens, when it shuts down, it switches to text mode and displays this error message :
smb_retry : no connection process

the message stays on the screen for around a minute before finally switching itself off.

Any ideas? If you have similar experience, please post it here.

P.S. I mount the drives using fstab similar to this :
//fileserver/c             smbfs               iocharset=cp950,etc.....

---

### Post by Mujaheiden on 2007-06-02
sounds similar imdeed. I recall having the same text at shutdown.

after this problem kept on recurring i resorted to mounting the samba shares as network servers, which then faces me with bug [15451]("https://bugs.launchpad.net/bugs/15451"). all i nall it my computer life not so smooth as i want it to be :(

also nautilus totally got slow when i use the fstab mounting.

---

### Post by tshannon on 2007-08-09
I just wanted to toss my hat in the ring, and say that I'm getting the exact same troubles.  I was setting up shares with my windows box to my music and movies for my Mythbox, and these issues started.

I haven't tried any other mounting points yet, but it looks like that is going to be my only choice.

Has anyone had any luck in figuring this out?

thanks,

---

### Post by tshannon on 2007-08-09
Remounting under different names works for me, but even though the corrupt entries are no longer in fstab, I still get the smb_retry error at shutdown.

Not a big deal, but it prolongs restarts by a couple minutes.

Is this an issue that is going to be recurring?  Have any of you guys seen this problem since it first happened and you remounted?

---

### Post by DugieHowsa on 2007-08-15
--------------------------------------------------------------------------------

I have found that smbfs is very buggy. You may have better luck with cifs.

I had been having trouble mounting a Windows Share. I tried to mount using smbfs. I tried to mount using cifs. In the end, some one showed me this link:

[https://bugzilla.samba.org/show_bug.cgi?id=1920](https://bugzilla.samba.org/show_bug.cgi?id=1920)

Summary: "smbfs is unmaintained and known to be severely broken." That was posted back in 2004, so needless to say probably not much has happened with smbfs in the last 3 years.

So here is the man page for mount.cifs that lists all the options:

[http://www.die.net/doc/linux/man/man8/mount.cifs.8.html](http://www.die.net/doc/linux/man/man8/mount.cifs.8.html)

Many people here have also listed many good posts, giving several good examples, on how to properly utilize cifs:

[http://ubuntuforums.org/showthread.php?t=288534](http://ubuntuforums.org/showthread.php?t=288534)

This post solved the particular problem I was having:

[http://ubuntuforums.org/showthread.php?t=483184](http://ubuntuforums.org/showthread.php?t=483184)

In summary: USE CIFS. DO NOT USE SMBFS.

---

