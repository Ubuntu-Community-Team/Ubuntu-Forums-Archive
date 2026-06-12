---
title: "How to do a basic file search????"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by mistypotato on 2009-08-14
In Windows, if I want to search for a file in a folder, for example all files with an HTML extension, I can simply put ***.html** in the files and folders search box.  Windows dutifully and nicely returns all files with that extension.

This does not appear to work with ubuntu?

Is there a way to search for files of a particular extension in Ubuntu?

thx

---

### Post by alindgr1 on 2009-08-14
It works for me fine.  I use the typical "Search For Files" at the bottom of the Places menu.  I just type in *.whatever, tell it where to look, at it finds them all.  No problems at all.

---

### Post by MrWES on 2009-08-14
> **mistypotato said:**
> In Windows, if I want to search for a file in a folder, for example all files with an HTML extension, I can simply put ***.html** in the files and folders search box.  Windows dutifully and nicely returns all files with that extension.

This does not appear to work with ubuntu?

Is there a way to search for files of a particular extension in Ubuntu?

thx

Open Nautilus (the file manager/browser), Places | Home, then navigate to the folder you want to search and then type in your criteria. Or Places, Search, or use Beagle search tool.
[https://help.ubuntu.com/community/Beagle]("https://help.ubuntu.com/community/Beagle")

Bill

---

### Post by RuneGeek on 2009-08-14
Don't forget that filenames are case-sensitive in Linux.  If you are searching for *.html and you have files named *.HTML, they won't show up in your search list.

---

### Post by superprash2003 on 2009-08-14
another good option would be Google desktop ,works really well for me in ubuntu

---

### Post by BobJam on 2009-08-14
A related question . . . how do you get it to search the entire computer?  Seems like it will only search one particular media/file system at a time.

Hate to make a comparison to Windows, but in Windows you could search all drives at once (I guess that would be partitions in Ubuntu).

---

### Post by credobyte on 2009-08-14
```
find / -name *.config

```

More info:
```
man find
```

---

### Post by philinux on 2009-08-14
> **BobJam said:**
> A related question . . . how do you get it to search the entire computer?  Seems like it will only search one particular media/file system at a time.

Hate to make a comparison to Windows, but in Windows you could search all drives at once (I guess that would be partitions in Ubuntu).

Places search for files> look in folder > File system or disk if mounted etc.

---

### Post by HotShotDJ on 2009-08-14
> **BobJam said:**
> A related question . . . how do you get it to search the entire computer?  Seems like it will only search one particular media/file system at a time.I don't often (ever?) need to search my entire computer -- I usually know approximately where what I'm looking for is located (/, /home, /var, /media/disk, etc)... but then again, I've been using Linux for 8 years, so I'm familiar with where things ought to be.

So, I tested.  Go to Places -> Search for files.. (you can add this to your panel as an applet if you want).  Put in your search term.  To search your entire computer, simply select "File System" from the "Look in folder" drop-down menu. It sucessfully searched and found files contained in my root partition (/; sda1) and my home partition (/home; sda3). It did not search the USB flash drive that I had plugged in (/media/disk; sdb1).  I suspect (but have not tested) that it only searches drives/file systems listed in /etc/fstab.

I also noted that, unlike command line search tools, the search is NOT case sensitive.  When I did a search for "*.dll" (because I know there are *.dll files on all the mounted partitions), it returned files that matched both *.DLL and *.dll.

I hope this information is helpful to you.

---

### Post by XCan on 2009-08-14
```
 locate *.html 
``` is a very fast way to search your entire filesystem. Of course, that's because it uses cached information, but still if the file is not super recent it will be faster.

---

### Post by philinux on 2009-08-14
> **XCan said:**
> ```
 locate *.html 
``` is a very fast way to search your entire filesystem. Of course, that's because it uses cached information, but still if the file is not super recent it will be faster.

Needs

sudo updatedb

running first.

---

### Post by oldos2er on 2009-08-14
A nice GUI search tool is catfish, in the repositories.

---

### Post by XCan on 2009-08-14
> **philinux said:**
> Needs

sudo updatedb

running first.

Indeed it does, however, it appears that it does run automatically periodically, as I can locate recent files with no trouble. According to man, it usually runs daily, but I couldn't find an entry in root's crontab. As I said, it searches a cache and won't be able to find very recent files.

---

