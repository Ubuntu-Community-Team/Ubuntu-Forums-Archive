---
title: "xcopy /d switch"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by mike_new_boy on 2008-12-16
I have a folder on a Ubuntu machine that is mapped as U from a windows box.
I want to keep a backup copy of my documents on the Ubuntu machine and have set up a batch file to do the copying. There are a large number of files so I want to copy only those that have changed. My understanding is that the xcopy /d switch will copy only those in the source that are newer than the destination.
This works as it should when copying within the windows box, but when I use it to copy from windows to ubuntu it copies files even though they have not changed. I usually use the /d /e /v /c /i /h /r /k /y  but even when I simplify it to

xcopy "C:\Documents and Settings\Mary\My Documents" "U:\Marys Documents" /D /y >c:\log.txt

The log file shows 160 files copied. Whats odd is the source contained 445 files and none had changed. Is the problem something to do with the way Ubuntu and windows store the file attributes?
Any suggestions

---

### Post by cmnorton on 2008-12-16
This is not a direct answer to your question, but is more of a supporting post. 

We have a commercial backup product, and as we were setting up what was to be backed up, I was told it was better to install a native Linux backup agent (there was one available and for Windows systems as well) than have the backup select files on a shared Samba drive. The problem was not on backing up, but if we had to perform a restore. 

As it was explained to me, it had to do with protection bits. Your post will push me to investigate this further, probably not in a timely enough fashion to be of help to you, but I'll post anything I find here.

---

### Post by handydan918 on 2008-12-16
Are you trying to copy files on the Ubuntu partition using Windows? If so, be advised that Windows does not natively support ext2/3 file systems.

---

### Post by cmnorton on 2008-12-17
> **handydan918 said:**
> Are you trying to copy files on the Ubuntu partition using Windows? If so, be advised that Windows does not natively support ext2/3 file systems.

How can anyone copy onto a SAMBA share, then? I'm confused by what the original poster is doing, and why you feel he cannot copy files.

---

### Post by mike_new_boy on 2008-12-20
> **handydan918 said:**
> Are you trying to copy files on the Ubuntu partition using Windows? If so, be advised that Windows does not natively support ext2/3 file systems.

No, I am using windows and I am copying from Windows to Ubuntu. It does copy, but all files not just those that have changed (as it does when copying from Windows to Windows).

---

### Post by unutbu on 2008-12-20
How about try copying from within Ubuntu:
```

rsync -a --delete SRC/ DEST
```

From the rsync man page:
```
 It is famous for its delta-transfer algorithm, which reduces the amount
       of data sent over the network by sending only the differences between the source
       files and the existing files in the destination.
```

The '-a' flag means 'copy in archive mode'. This preserves timestamps.

The '--delete' flag means that if a file is not in SRC/ but it is in DEST/, then the file is deleted from DEST. This is typically what you want for backups of SRC.

Be sure to include the forward-slash after the SRC path. If you don't, the backup is made in DEST/SRC/*, instead in DEST/*.

---

### Post by mike_new_boy on 2008-12-23
Thank you if I did the copy from within Ubuntu how would I get the windows machine to initiate it?
The present setup is a logoff script on the windows machine causes windows to run the Xcopy command 
xcopy "C:\Documents and Settings\Mary\My Documents" "U:\Marys Documents" /d /e /v /c /i /h /r /k /y >c:\log.txt

where U is a folder on the Ubuntu machine that is mapped as a network drive. It works but it copies ALL of the files at the source, not just those that have changed. If I change the destination to within the Windows box it copies only changed files. This makes me think it is something to do with the different ways Windows and Ubuntu record the date. If I manually copy a file from C to U and look at its properties the date created on C is 09 December 2008, 17:48:58 but on U is 09 December 2008, 17:51:50. Presumably this is because of the different file systems and I doubt if copying from within Ubuntu but I will give it a go. To cope with the spaces in the file names do I use quotes
rsync -a --delete SRC/ "/media/disk/shares/Marys Documents"
I am at a loss with the source which is on a windows machine that the Ubuntu cannt directly see, I assume I need to mount it in some way?

---

### Post by unutbu on 2008-12-23
Hm. The bit about the logoff script has me feeling uneasy. 
I don't know enough about Windows to give you a good suggestion on how to do from the Windows side. 

If you'd like to try rsync anyway, I believe the command would be

```
rsync -av --delete Windows_IP_Addr:"C:\Documents and Settings\Mary\My Documents\" "/media/disk/shares/Marys Documents"
```

---

