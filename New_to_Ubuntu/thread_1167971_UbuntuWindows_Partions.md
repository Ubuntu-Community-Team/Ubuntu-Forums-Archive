---
title: "Ubuntu/Windows Partions"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by cerealtx on 2009-05-23
Hey im going back and doing what i should have done in the beginning and partitioning one of my harddrives, a few it dosn't matter if they are accessable by my Windows and Linux Partion But i do have some files(music/movies) that i want to be accessable on both, i used to have it partitioned as NTFS, but i can't choose that on gparted anymore if i make the partions ext3 will they be able to be accessable on both os's? or do i choose fat32?

---

### Post by benerivo on 2009-05-23
Ideally, you would want ntfs. Why can't you format it with ntfs? I thought gparted was able to do that (you might need ntfsprogs or some other package installed). You could also just format it from windows.

If none of the above are feasible, then go with ext3, and use the ext driver for windows available [here]("http://www.fs-driver.org/").

---

### Post by whoop on 2009-05-23
Install the following packages:
libntfs10
ntfsprogs

---

### Post by Bartender on 2009-05-23
I've ripped several movies using Handbrake in Vista.  Saved them to the Vista NTFS partition.  Booted back into Ubuntu, found the rips, they played just fine with Totem.
Actually, they played better in Ubuntu than they did in Vista.  In Vista, (I think I was using VLC because the Windows media players refused to even try playing the rips) some of the action scenes skipped.  The same scenes played fine in Totem.
Based on my experiences, I'm guessing that accessing the NTFS files from Ubuntu shouldn't be a problem.

---

### Post by blueridgedog on 2009-05-23
For files over 4 gig and read/write access to both OS's, NTFS is the choice.

---

