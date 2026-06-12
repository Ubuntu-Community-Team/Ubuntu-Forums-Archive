---
title: "Which Format Is Best For Backup Partition?"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by sblunix on 2009-08-15
Hey all, I just recently started preparing to backup my files and got a little 20GB HD just for backups, but I wanted to know how to format it, right now it's all unallocated space, but what should it be, NTFS, FAT32, Ext3? Ext2? I'm not sure which is best and what makes each one different, so I'm asking the community.

---

### Post by hockeyfighter09 on 2009-08-15
If I were you I would use Ext3.  It is mature, stable and fast. Plus it is the default format that Ubuntu uses on install. :popcorn:

---

### Post by sblunix on 2009-08-15
> **hockeyfighter09 said:**
> If I were you I would use Ext3.  It is mature, stable and fast. Plus it is the default format that Ubuntu uses on install. :popcorn:
I was thinking that too, but I wasn't sure if Ext4 was more advanced or if there was some reason why it was there?

---

### Post by Twittery on 2009-08-15
I'd say ext4 (thats just my opinion though) . I don't find anything unstable about it and its much faster that ext3 . But then again its just my opinion . And I haven't encountered any problems with it and quite some linux OS use it as default . (Even Ubuntu is much faster in ext4 .) Cheers :)

---

### Post by Twittery on 2009-08-15
And also for a backup partition ext4 should work very well without doubt

---

### Post by cmannnn on 2009-08-15
Etx4 has higher transfer speed and fat32 makes it windows compatible

---

### Post by hockeyfighter09 on 2009-08-15
> **sblunix said:**
> I was thinking that too, but I wasn't sure if Ext4 was more advanced or if there was some reason why it was there?

Ext4 is a good option too, it is fast, new and shiny. But IMO it is too new to trust your backup data too.  I read a couple months ago it had a problem with losing data.  I am sure that is not the case now.  But still, when it comes to backing up my important data I would use something that is proven rock solid stable.

---

### Post by sblunix on 2009-08-15
> **Twittery said:**
> I'd say ext4 (thats just my opinion though) . I don't find anything unstable about it and its much faster that ext3 . But then again its just my opinion . And I haven't encountered any problems with it and quite some linux OS use it as default . (Even Ubuntu is much faster in ext4 .) Cheers :)
Really, why doesn't Ubuntu install on Ext4 then?

---

### Post by sblunix on 2009-08-15
Well, speed isn't really an issue for this, and Stability really is, so I think I'll stick to Ext3 for a while... It's only backups :\

---

### Post by Twittery on 2009-08-15
> **sblunix said:**
> Really, why doesn't Ubuntu install on Ext4 then?

Thats because when Jaunty ( the stable release of Ubuntu) was released ext4 had many issues . But they were later solved and I am quite sure its safe now . But ext3 is also or for sure is good

---

### Post by Barrucadu on 2009-08-15
> **sblunix said:**
> Really, why doesn't Ubuntu install on Ext4 then?

The next release will by default, IIRC.

---

### Post by binbash on 2009-08-15
I would go for ext3 rather than ext4

---

### Post by Bartender on 2009-08-15
Will this backup device be used ONLY on your Linux PC or PC's?  Reason I ask is if there's any possibility that you will at some point want to access the data via a Windows machine, you'll wish you'd formatted the drive as NTFS or FAT.

I go back and forth between Windows and Linux with a 1TB HDD and one of those dock thingies.  I hated to format the drive as NTFS, but Linux isn't having any problems accessing the NTFS data (music, video, documents, .jpg's).  If I'd gone the other way and formatted as ext the drive would be useless on the Windows PC's.

---

### Post by colau on 2009-08-15
Ext3 format preferable.

---

### Post by Liolikas on 2009-08-15
If you plan to use that backup with windows then fat32, if not then ext3/4. Fall of 2009 is good time to begin using ext4 instead of 3, of course there is no need to rush with this upgrade.

---

### Post by oldfred on 2009-08-15
I was backing up to a FAT partition and it always stopped at 4GB. I thought that was the size of my backup until I understood that FAT has a maximum of 4GB per file. I am now wondering if I have any backups.

---

### Post by swerdna on 2009-08-16
FAT32 = -3
NTFS = -1
ext4 = 0
ext3 = +2

---

### Post by colau on 2009-08-16
ext3=+2
ext4=+1
fat32=0
ntfs=-1

---

