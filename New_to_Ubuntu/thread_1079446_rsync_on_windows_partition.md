---
title: "rsync on windows partition?"
date: 2009-02-24
forum: New to Ubuntu
---

### Post by garyed on 2009-02-24
I'm trying to backup one directory on my Hardy computer to another computer
running Gusty & Windows using rsync. Each partition is on a separate physical drive.Here are my two comands:
```
rsync -avhu /home/gary/CHOICE gary@music-desktop:~/backup
rsync -avhu /home/gary/CHOICE gary@music-desktop:/media/music_c/backup 
```
The first command copies fine but the second doesn't 
"I get all kinds of errors like this:
rsync: failed to set times on "/media/music_c/backup/CHOICE/songs": Operation not permitted (1) "

I assume it's a permission thing but I tried using sudo & that didn't work either. The windows directories are owned by root & plugdev is the group.
Any ideas?

---

### Post by binbash on 2009-02-24
I guess rsync does not preserve time.Disable preserving time, and retry.(If you dont know how to do, i strongly suggest using Grsync ;) )

---

### Post by DGortze380 on 2009-02-24
> **garyed said:**
> I'm trying to backup one directory on my Hardy computer to another computer
running Gusty & Windows using rsync. Each partition is on a separate physical drive.Here are my two comands:
```
rsync -avhu /home/gary/CHOICE gary@music-desktop:~/backup
rsync -avhu /home/gary/CHOICE gary@music-desktop:/media/music_c/backup 
```
The first command copies fine but the second doesn't 
"I get all kinds of errors like this:
rsync: failed to set times on "/media/music_c/backup/CHOICE/songs": Operation not permitted (1) "

I assume it's a permission thing but I tried using sudo & that didn't work either. The windows directories are owned by root & plugdev is the group.
Any ideas?

Is /media/music_c an NTFS parition?

If so, that's your problem, time stamps are handled differently. You can change your rsync command to ignore timestamps, or just ignore the error, I believe the command should still work.

---

### Post by garyed on 2009-02-24
> **DGortze380 said:**
> Is /media/music_c an NTFS parition?

If so, that's your problem, time stamps are handled differently. You can change your rsync command to ignore timestamps, or just ignore the error, I believe the command should still work.

Yes it is an NTFS partition but the command doesn't work on my other fat32 drive either, I just get a different error like this:

"rsync: stat "/media/music_d/backup/CHOICE" failed: No such file or directory (2)"

The directory is there & the case is correct.
I tried adding the "-I" switch to the command on the ntfs partition but I got the same error.
Also turning the time stamp off would probably defeat the idea of incremental backups every day.

---

### Post by MrWES on 2009-02-24
You might try installing grsync, the GUI for rsync. Also, if I remember correctly rsync will sync ALL files everytime when using a fat32 drive.

Bill

---

