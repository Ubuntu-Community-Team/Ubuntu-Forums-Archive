---
title: "Ubuntu 11 randomly corrupts files in NTFS partition"
date: 2011-05-11
forum: New to Ubuntu
---

### Post by vadimmakarov on 2011-05-11
I've a dual boot with the latest version of Ubuntu (version 11, fully updated) in its own partition, and Windows 7 in an NTFS partition. All my data and personal files are kept in the NTFS partition, such that I can access them from both OSes. Computer: ASUS V1S laptop.

Problem: Ubuntu occasionally and randomly barfs in the NTFS filesystem, corrupting the directories and files that are written from under Ubuntu. Something it does incorrectly with the filesystem records. chkdsk from under Windows fixes these filesystem errors, but the files get lost (sometimes recovered by chkdsk without a correct filename but with correct content, sometimes lost permanently). The problem is a show-stopper.

How do I debug this?

Colleagues mentioned version 11 is not very stable, and I should install 10.04 long-term support one.

I've just lost an entire project I've been working on last few days; very annoying. I'm not doing any work from under Ubuntu again until this problem is rooted. (Not meant to start a flame war, but I need the Windows boot to run certain application, and I need access to all my data from it. On the other hand, Linux is nice but I can live without it.)

---

### Post by Matt__ on 2011-05-11
For the most stable release its always advisable to stay with LTS.
the only reason to upgrade is if something isnt working with your current version or youre "must have the newest version" junkie :)

//edit: I cant find anything on your data corruption problem (an earlier bug corrupted ntfs boot sectors in grub but is fixed). I only have 11.04 on a test system with xp/10.10/mint and have no problems with it. (except the awful unity...which should have stayed as netbook edition only imo).

You could also try [Scrounge-nfts](http://manpages.ubuntu.com/manpages/natty/man8/scrounge-ntfs.8.html) to recover damaged files on an ntfs partition, though its a little tricky to use until they implement disk partition info searching.

---

