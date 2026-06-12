---
title: "Choosing a NAS device..."
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by PsycoGeek on 2007-09-17
Currently I have a Win2k server set up for file and media sharing (documents, archived install files, back-up, mp3's).  I am sick of having to update it every week or two, and sick of the file sharing getting messed up every so often (I have had to rebuild it twice already in the past 5 years).  Currently I am accessing the shares on it with samba and have no problems from three Ubuntu boxes (I'm converting the whole family to the big U for every day stuff), but I just purchased a laptop, created a user on the Win2K server to access everything from it, and can't write to the darn shares no matter what I do.  And I know it's a problem with the Win2k box.  It's happened to me before when I went into the box to add/change a user and the permissions got all messed up (probably because of the very few reboots the box goes through in a year, M$ boxes are like that... ).  I have to delete all the users, delete all the shares, reboot and re-create everything.

Anyhow, what I want :

two internal hard drives, raid 1, SATA preferable
web setup interface

If I can't have that I may have to build a FreeNAS box, but I don't really want to build one.  I don't really want a full fledged server anymore.  I just want a simple NAS box I can stick some hard drives of my choice into and set up a few user accounts and get to the files.  4gig file limit of FAT32 is not really an issue, nor is using samba to access the shares (that's how I'm accessing my Win2K server now).  Simplicity of setup is.

I have been looking at a few options and really liked the [Linksys NAS200]("http://www.linksys.com/servlet/Satellite?c=L_Product_C2&childpagename=US%2FLayout&cid=1175233152539&pagename=Linksys%2FCommon%2FVisitorWrapper&lid=5253976915B01"), but I haven't seen any real reviews of it anywhere, nor can I find any info in the user manual on such things like file system/linux accessability.

Does anyone have one of these that you are accessing with Ubuntu?  Have any suggestions for another unit that will give me what I want for a reasonable price?

-edit-  I also found this one, a [Dlink DNS323]("http://www.dlink.com/products/?pid=509")  which uses ext2 and ext3 file systems.

---

