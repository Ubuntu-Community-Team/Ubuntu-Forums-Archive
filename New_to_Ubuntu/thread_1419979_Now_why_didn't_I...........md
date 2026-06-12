---
title: "Now why didn't I.........."
date: 2010-03-02
forum: New to Ubuntu
---

### Post by Bill Carr on 2010-03-02
Hi, folks.
I thought I would look to see how to restore or backup a system before messing with terminal or updates and such.
A two second search found the following:
 
 
[http://ubuntuforums.org/showthread.php?t=35087&highlight=restore+position](http://ubuntuforums.org/showthread.php?t=35087&highlight=restore+position)
 
My question....do I have to go thro' a hundred or more replies, or is the original post the matured in oak distillation of all the alternative offerings of the community ?
Love the challenge
Cheers
Bill Carr

---

### Post by Mark Phelps on 2010-03-02
Can't comment on the linked thread, but I've found Clonezilla to be a simple image backup/restore solution that now includes Ext4 filesystems.

With a little bit of research, using their document pages, you can store a copy of clonezilla in the boot directory of your system and then do backups/restores without having to boot from a CD.

There are other solutions like remastersys, but clonezilla does what I need.

---

### Post by Megaptera on 2010-03-02
Hi,
I don't know if it's elegant, but as a distro-hopper what I do is install, make the changes I want (restricted-extras) themes etc etc and then use Remastersys to make a back-up DVD of how I've got it set up.

This is a description, not 100% sure about the repository being current but this explains quite well:

[http://easierbuntu.blogspot.com/2008/07/backing-up-your-system-with-remastersys.html](http://easierbuntu.blogspot.com/2008/07/backing-up-your-system-with-remastersys.html)

---

### Post by Paddy Landau on 2010-03-02
I have discovered three different good ways to back up (and restore), depending on your needs.

[LIST=1]
[*]On-line (off-site) backup. My favourite by far is [SpiderOak]("https://spideroak.com/") -- effective, cross-platform, inexpensive, and with some useful extra features. Suitable for daily backups of your important data, including photographs.
[*]Back up files onto an external hard drive. For this, you would want rsync or (preferably) rdiff-backup, but they do require some work creating a script to get them working nicely. Suitable for daily or weekly backups where the volume of data is too great to back up on-line (e.g. home videos).
[*]Back up your entire partition or entire disk onto an external hard drive. This lets you restore the entire partition or disk in case of a real mess-up (e.g. your hard drive crashes), without having to go through the hassle of reinstalling. You can use [CloneZilla]("http://clonezilla.org/") (my favourite) or [PartImage]("http://www.partimage.org/"). I do this monthly.
[/LIST]
I used to use that tar method in your link, but I found it cumbersome, s-l-o-w, and fiddly.

---

### Post by ubunterooster on 2010-03-02
+1 clonzilla due to a too large number of problems w/ master sys

---

### Post by Bill Carr on 2010-03-02
Thanks, folks
I'm going to try out Clonezilla while the urge is upon me !
Cheers
BC :)

---

