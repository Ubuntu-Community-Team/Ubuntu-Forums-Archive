---
title: "Nautilus hangs on file preview"
date: 2009-11-08
forum: New to Ubuntu
---

### Post by mwalimu54 on 2009-11-08
Info: Ubuntu 9.10 64-bit, clean install running 4 GB RAM

Problem:  I have several subfolders under username/photos which contain a large number of photos (200 files @ 1.2 MB each).  Nautilus opens similar smaller folders with ease but hangs on larger folders.  

I've narrowed this down to the file/photo preview option being the problem.  When preview is turned off, nautilus runs just fine, however, that defeats the purpose.  I must be able to see the thumbnails of photos as I organize them by drop and drag.

Any ideas how to debug this one?

---

### Post by The Funkbomb on 2009-11-08
I had a very similar problem on my old laptop.  I was scraping info off of an old drive and wound up with a lot of pictures in a folder.

You simply need to split the folder into smaller folders.  You can accomplish this with a bash script.  Hopefully your files are similar.  All of mine were IMG_1234.

My bash script looked like this.

```
#! /bin/bash/
cd /path/to/original/folder/
mkdir /path/to/new/folder/1/
mkdir /path/to/new/folder/2/
mkdir /path/to/new/folder/3/
cp IMG_1*** /path/to/new/folder/1/
cp IMG_2*** /path/to/new/folder/2/
cp IMG_3*** /path/to/new/folder/3/
```

etc, etc.

Then save it as foldersplit.sh.  Go into terminal and:
```
sudo chmod u+x /path/to/foldersplit.sh
```

Run it in terminal and smile.  Your folder was just split into 3 different folders.

---

### Post by mwalimu54 on 2009-11-08
Yeah, I thought of splitting this into separate folders, but it seems unnecessary to accept this as a part of life.  In other words, this is a bug and should have a better fix.

---

### Post by lswb on 2009-11-08
If you don't mind suffering through the long wait the first time, subsequent viewings of that directory should be faster. When Nautilus first encounters an image file, it creates the thumbnail image and caches it (in ~/.thumbnails) for future use.

(There is another problem with nautilus when opening directories with a large number of files, say in the thousands, but a few hundred or so normally will not be a problem)

---

### Post by jnew93 on 2009-11-08
I too am having a similar problem. I have a folder with about 15 or so .avi video files. When I attempt to view the files with preiew enabled, nautilus hangs. Without it, the folder shows fine. It happens frequently to other folders as well, so I'm willing to bet there is a bug somewhere.

---

### Post by KeLa on 2009-11-09
I have same problem with Flash video files, only 18 files in folder and only half of them are shown by nautilus when preview is enabled. All shows fine when i disable preview.
System is clean install of 64bit Karmic. Up time is 6 Days 23:35 at this moment.

---

### Post by mwalimu54 on 2009-11-12
OK. it's working really fast for me now.  I didn't do anything.  Maybe the most recent update took care of it??

---

### Post by whitefort on 2009-11-14
> **mwalimu54 said:**
> OK. it's working really fast for me now.  I didn't do anything.  Maybe the most recent update took care of it??

I don't think the update was the fix - I'm all updated, and still having the problem in certain folders...
Definitely a bug, and a very annoying bug...

---

### Post by Acid_1 on 2009-11-30
I have the same issue. I have 2000+ photos adding to 3GB in a folder, and Nautilus is hanging, well only in that folder. I can open a tab and navigate elsewhere just fine.

Running Karmic/Gnome/32-bit/4GB Ram

---

### Post by rylleman on 2009-12-15
I also have this problem in various folders at my work-drive. 
As I'm working with images and video, not having preview is a huge handicap for me...
I think the issue is related to svg-preview for me. Is there a way to disable thumbnails for specific file-types?

Ubuntu studio 8.10, 64-bit.

---

### Post by revanb on 2009-12-15
I suggest that all of you with the preview problem file bugs. This is the best way to attract attention and a fix!

Good luck!

---

### Post by rylleman on 2009-12-16
Reported it.
[https://bugzilla.gnome.org/show_bug.cgi?id=604686](https://bugzilla.gnome.org/show_bug.cgi?id=604686)

---

