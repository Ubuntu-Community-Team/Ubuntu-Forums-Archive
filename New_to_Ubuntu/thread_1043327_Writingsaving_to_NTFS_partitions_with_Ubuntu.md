---
title: "Writing/saving to NTFS partitions with Ubuntu"
date: 2009-01-18
forum: New to Ubuntu
---

### Post by Sol401 on 2009-01-18
Hello everyone, I have looked around and couldn't find the answer I was looking for regarding this issue:

I have a dual-boot machine (Ubuntu/Vista). Therefore, I have an EXT3 and an NTFS partition. Is it "safe" to save files (just music, documents, etc) to my NTFS partition while running Ubuntu? I don't want to do anything more complicated than simply saving these files. I was just wondering if this was safe from a paritial to total data-loss point of view.

What about FAT32? Is it safe to use Ubuntu to do similar things to FAT32 partitions?  Thanks a bunch! :)

---

### Post by earthpigg on 2009-01-18
yes, NTFS reading/writing is considered 'stable'. you may get issues trying to read the NTFS partition if you turn off your computer without properly shutting down.... nothing that can't be solved with a few commands in the terminal.

FAT 32 read/write is considered 'super duper ultra stable'. at least i think that is the preferred term ;)

---

### Post by TenPlus1 on 2009-01-18
Pop into Synaptic Package Manager and do a NAME search for NTFS, then make sure the following are highlighted and installed:

ntfs-3g
ntfs-progs
ntfs-config

Then go into Applications -> System Tools -> NTFS Configuration Tool and enable everything so you can read/write to any internal and external NTFS drive...

---

### Post by Sol401 on 2009-01-18
Awesome, thank you kindly!

---

### Post by HunkirDowne on 2009-01-18
I'm having problems with NTFS myself.  I got a new 1 TB xHDD with USB/1394 and it was formatted NTFS.  I was considering reformatting but decided against it, but I may end up regretting that decision.

I am currently running into an error where I cannot write to the drive.  I'm using Gutsy and have the latest ntfs-3g available from the repo.  Checking the [ntfs-3g website]("http://ntfs-3g.org/") they mention another build for the driver.  I downloaded it and it wouldn't ./configure.  I'm not a gcc programmer so I'm basically stuck there.

Perusing the ntfs-3g.org website, I came across mention of MS-NTFS Reparse Points but do not have a windows computer that is both bootable and one that I have admin rights to.  Is there anything I can do from Linux to remove or otherwise handle these Reparse Points?

Any other ideas?  I would really like to regain my confidence in this drive.  On the other hand, if I continue to have trouble, I will start looking into reformatting it ext3 but then I doubt I'll be able to read it on the iMac (wife's computer).

---

