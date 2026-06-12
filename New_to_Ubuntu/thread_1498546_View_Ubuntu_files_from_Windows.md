---
title: "View Ubuntu files from Windows?"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Sholto on 2010-05-31
I have just installed Ubuntu (Lynx) in a dual boot with Vista. Everything works fine, in that I can see the Windows shares from Nautilus. However, I have 2 questions:
1) Is it possible to access those shares from the command line? They appear in Nautilus as e.g. D$ for my D: drive, but I can't do a 'ls D$' from the command line.
2) Can I look the other direction? I would like to be able to see the Linux filesystem from within Windows too. Is this an ask too far?

---

### Post by drdos2006 on 2010-05-31
Linux OS is very, very different to Windows OS. If you want to have both Windows and Linux to have access to files, then you need to have a legacy Windows partition devoted to legacy Windows file format, that is NTFS.
Linux can read/write to Windows legacy partition (NTFS), Windows cannot read/write to Linux (ext2, ext3, ext4), Windows is too old.
Also Windows is proprietory, Linux Open Source.

Use gparted to re-arrange your hard drive for a legacy NTFS partition and store your data files in that partition. That way both Windows and Linux can read the data files.

:)
regards

---

### Post by Sholto on 2010-06-01
Thanks DRDOS, but my Windows partition is already NTFS.  As I said, this can be accessed by both systems (well obviously Windows can access it!)
So you are saying that there is no way I can view the other way?
I have done it many years ago when I worked in places that use tools like Exceed and Citrix.
Is there any way I can access the Windows shares from a Linux command prompt?

---

### Post by Ozymandias_117 on 2010-06-01
1. Yup! If you mounted via nautilus it's most likely in /media/hard_drive_name ```
cd /media/hard_drive_name
``` (You can do ls /media to find the right name)

2. Not natively, There are some programs out there that are supposed to be able to... I can do a little searching, see if any look promising. The one that used to be the best no longer works :(

---

### Post by Sholto on 2010-06-01
Thanks Ozymandias.  I tried the ls /media, but it just displayed floppy and floppy1 (it's an old machine with floppy ports - remember them?!).  If you can see what I am doing wrong here I would be very grateful.
As for seeing my Linux folders from Windows, I accidentally found out how to do that.  In Nautilus I right-clicked on my home directory and selected Sharing Options.  I had to install the Windows sharing utility, and checked the 'Share this folder' box in the Folder Sharing window.
On the Windows machine I was able to see the Linux box and the shared directory inside the Network node in Windows explorer.  I have mapped a Windows drive letter to my Linux home folder and can grep etc into it from Windows.  Fantastico!

---

### Post by Mark Phelps on 2010-06-01
> **Sholto said:**
> ... 2) Can I look the other direction? I would like to be able to see the Linux filesystem from within Windows too. Is this an ask too far?

Unfortunately, yes.  Windows can not read Ext4-filesystems.  The driver folks are referencing only works up through Ext3.

---

### Post by Ozymandias_117 on 2010-06-01
> **Sholto said:**
> Thanks Ozymandias.  I tried the ls /media, but it just displayed floppy and floppy1 (it's an old machine with floppy ports - remember them?!).  If you can see what I am doing wrong here I would be very grateful. ...

Based on the rest of that post, are you saying you're trying to access ANOTHER windows machine over a network via terminal? I thought you were talking about another partition on your current machine.

---

