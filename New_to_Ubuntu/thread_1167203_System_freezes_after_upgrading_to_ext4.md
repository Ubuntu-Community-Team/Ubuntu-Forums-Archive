---
title: "System freezes after upgrading to ext4"
date: 2009-05-22
forum: New to Ubuntu
---

### Post by mmasroorali on 2009-05-22
Dear All,
Recently I upgraded to Ubuntu 9.04 and at that time without going through a machine upgrade, I went for fresh a installation. The reason was I wanted use ext4 file system. Now it appears that that was not a very good decision. My machine has started to freeze. 

Previously this was rare phenomenon. Now it freezes, when I,

a) Use `Remove torrent and data' in ktorrent,
b) Try to manually delete a (rather large) file which is being seeded by ktorrent,
c) Above b) happens even when ktorrent is not running.

Which one is to blame? Ktorrent? Ext4 file system?

My machine is upgraded daily. 

Any input will be appreciated.

---

### Post by lovinglinux on 2009-05-22
I would blame ktorrent. BTW, I'm using ext4 since the release without issues (I use Deluge).

---

### Post by mmasroorali on 2009-05-23
> **mmasroorali said:**
> Dear All,
Recently I upgraded to Ubuntu 9.04 and at that time without going through a machine upgrade, I went for fresh a installation. The reason was I wanted use ext4 file system. Now it appears that that was not a very good decision. My machine has started to freeze. 

Previously this was rare phenomenon. Now it freezes, when I,

a) Use `Remove torrent and data' in ktorrent,
b) Try to manually delete a (rather large) file which is being seeded by ktorrent,
c) Above b) happens even when ktorrent is not running.

Which one is to blame? Ktorrent? Ext4 file system?

My machine is upgraded daily. 

Any input will be appreciated.

It appears that it has got something to do with deletion of big files, it does not matter whether it is from command line or from an application. 

Adding nodelalloc is fstab did not help. 

I have switched to ext3 file system and things are looking good.

---

### Post by sanderd17 on 2009-05-25
how big are your big files? cd-size big?
(just for information before I switch to ext4)

---

### Post by mkvnmtr on 2009-05-25
With no proof that the new format was causing the problems I was having I switched back to ext3 on one system and when I have time I believe I will switch on my other system as well. On my ext4 9.04 there are videos that won't open. Not all of them just a few that before the upgrade played fine. On the nother system they play. Some other strange problems also. I guenss we will just have to see if updates fix the problem.

---

### Post by mmasroorali on 2009-05-26
The files were around 2GB.

---

### Post by s0pnadisht0 on 2009-05-27
Hello,

I also have the same problem faced so far.
I don't think the problem with the ext4

I also have this kind of system freeze/hang/beeping sound from MBoard in JFS files system with ubuntu 8.10 and even in NTFS file system in XP while downloading large file using torrents.

I have suffered with this problem from over a year, but I could not get any solution. I have heard form a forum (I have forgotten the link) that it might be problem with the torrent clients that write data in the SATA drives.

Hope a solution comes form any of you.

Thanks in advance.

---

### Post by Gen2ly on 2009-05-27
I don't think I'd put this on ext4 either, haven't seen anyone else have this probelm.

---

### Post by The Cog on 2009-05-27
There have been several threads reporting freezes in Jaunty. ext4 and wireless seem to be blamed commonly. 

In my case, changing back from ext4 to jfs got rid of my freezes, and I know it wasn't wireless because I got my first freeze so soon after installing that I hadn't even connected the wireless yet.

---

### Post by kportertx on 2009-06-08
I am having the same issue, I am not using torrent files.  I was backing up some DVDs and when I went to deleted these files from my system it froze.  I tried again and had the same problem.  Next time I opened recovery mode and chose the root option.  I then browsed to my dvd backup directory and typed rm -v *, again the system froze so I came here.

I have been noticing intermittent freezes since I upgraded to 9.04.  I believe ext 4 may be to blame, but I have not tried 9.04 on ext 3 yet.  I'm still hoping a update will fix this.

BTW on the 4th attempt the files finally deleted.

---

### Post by idef1x on 2009-06-09
I am having the same on Kubuntu 9.04. First thought it was Kubuntu/KDE so changed to the GNOME desktop (ubuntu-desktop) and GDM. Still the same freezes, so finally I reinstalled Kubuntu again on ext3. So far still good.
The freezes happened almost always when deleting files. Big or small didn't matter to much.

---

