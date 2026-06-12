---
title: "Copying from external hard drive help"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by cubedeathk on 2009-08-07
Hello All, I'm having some trouble and would like to know if anybody knows what I'm doing wrong here.

I'm trying to move a folder of music in an external hard drive to my computer via terminal but have been running into some issues.  By accident I created two other mounting places in my media file because I didn't think the drive was mounted and now I can't seem to delete any of these empty folders. 

My main problem was though was that I could never get into the external hard drive (it is mounted)  to see what files were in it, but I don't even know if that is neccesary.  I thought I should be able to type cd /Media/Smith Backup and that would put me into that directory where I could type ls to see the files in it, of which iTunes Music is what I am trying to move.  I cant seem to find anything  on the internet.  Just ask if you need me to clarify anything because my linux isn't that good yet.

Any help is appreciated thanks,  :o

---

### Post by synapsys on 2009-08-07
If your mount point is Smith (space) Backup, then this is most likely your problem. When using spaces in the command line you need to let it know there is a space. You can do this by using a slash. The exact way escapes me at the moment but it is one of these:
Smith\ Backup
Smith/ Backup
Smith \Backup
Smith /Backup

It would be a whole lot easier if you changed the name of the folder to contain no spaces e.g. "SmithBackup" You can test if you have access by using your file manager (nautilus) to navigate to the media folder and see if you can open your mount point from there.

---

### Post by cgb on 2009-08-07
Not entirely sure I understand completely what is, or is not, happening.  If you type "ls" under cd /media does it show your external hard drive listed?

---

### Post by synapsys on 2009-08-07
The media folder will show your mounted media. If you are in the media directory and you type ls it will show you a list of folders in the media directory. If your hard disk is mounted, it will most likely be in this directory. Try this at the command prompt:

```
nautilus /media
```

This should bring up a file manager window showing the media folder. You can simply double click to open the folders here, and if your hard disk is mounted, it should come up and show you the files it contains.

---

### Post by theozzlives on 2009-08-07
it's:```
cd /media/Smith\ Backup
```

---

### Post by synapsys on 2009-08-07
> **theozzlives said:**
> it's:```
cd /media/Smith\ Backup
```

There ya go. Thanks ozz. I'm on a windows machine at work :D

---

### Post by cubedeathk on 2009-08-08
Righteous guys thanks:D  I hate how little things like that one space got me all thrown off though.

---

