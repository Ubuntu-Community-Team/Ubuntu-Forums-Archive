---
title: "How to backup over multiple CD's easily?"
date: 2010-07-25
forum: New to Ubuntu
---

### Post by Mick8882003 on 2010-07-25
I have about 10 gig in my home directory. I am wondering if there is an easy way to back this up to DVDs Ideally I would run a command and then just swap the CD's out as they are full.

edit: oh yes I am using Ubuntu 10.4

Cheers Mick Carey

---

### Post by tyleruk on 2010-07-25
```
rar a -v4500M backup.rar ~/ 
```

This will make several 4.5GB .rar files of your home directory, just burn these to your cd's.

---

### Post by Mick8882003 on 2010-07-25
I just tried this and ended up with a file (backup.rar) only 32meg
The contents of home (and subdirectorys) add up to about ten gig.

---

### Post by Mick8882003 on 2010-07-25
I assume that I need to tell it to include the subdirectories, I have looked through both the man pages and --? and cannot see anything helpful.

Cheers Mick

---

### Post by AlphaLexman on 2010-07-25
Try to 'list' the contents of the .rar file to see what is missing:
```
rar l
```
(subdirectories)?

---

### Post by Mick8882003 on 2010-07-25
I just get the help menu.

Do I have the right version?
I just used apt-get install rar to get it.

And by subdirectories I mean the directories further down the tree.

Mick

---

### Post by Mick8882003 on 2010-07-26
Bump

---

### Post by Bachstelze on 2010-07-26
```
tar cvf home.tar /home/user
7zr a -v700m home.tar.7z home.tar
```

Use tar for archiving and 7z for compresion (or RAR, but 7z is usually better).  Do not use RAR or 7z for archiving, you will lose a lot of information about your files.  If you don't care about compression but only want to split, you can disable compression altogether to make the process faster:

```
7zr a -v700m -mx=0 home.tar.7z home.tar
```

---

### Post by jtarin on 2010-07-26
The standard way to do backups in Unix is to use ["tar"]("https://help.ubuntu.com/community/BackupYourSystem/TAR").....it's very versatile and easy to learn. Read _completely and thoroughly_ then make a practice directory with sub-directories and files.

---

### Post by Paddy Landau on 2010-07-26
If you want to use tar to split over DVDs, there is a way.

**First**

Create your archive. You can do that in the command-line (CLI) using tar, or you can use Nautilus (right-click the directory you want to archive and select Compress). Be careful to not save the archive inside the directory that you're compressing...

**Second**

Use tar to split the archive into DVD-sized chunks. You will need to do this via the CLI. The specific options that you need to look at in the manual are -M and -L. For -L, the number to use for a DVD is 4589350, and for a double-sided DVD is 8912000 (I'm not entirely sure about the latter figure, but it's about right).

You will need to find out about how to name the files. It's not in the manual (why?), so use Google.

**Third**

Once you've created your chunks, save them individually to DVD. You can then delete the original archive and all its derived chunks from your hard drive.

**Fourth**

Test! Try to restore a file. Hint: You'll need to pull all the chunks from the DVDs back onto disk, and rebuild the original archive. Once you've done that, you can use Nautilus to open the archive (if you prefer the GUI).

**Comment**

Personally, I found the process so tiresome that I wrote a script to semi-automate the process. (If you want the script, just ask.)

Even then, I still found the process so tiresome that I gave up and purchased an external USB, to which I back up using rdiff-backup (which means that not only do I have a full backup, but also it's quick to do a daily backup, and I have past versions of files that I can go back to).

---

### Post by jtarin on 2010-07-26
> **Paddy Landau said:**
> 
Even then, I still found the process so tiresome that I gave up and purchased an external USB, to which I back up using rdiff-backup (which means that not only do I have a full backup, but also it's quick to do a daily backup, and I have past versions of files that I can go back to).
Amen! 1TB USB

---

