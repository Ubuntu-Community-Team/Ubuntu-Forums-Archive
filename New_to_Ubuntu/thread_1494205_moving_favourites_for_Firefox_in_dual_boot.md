---
title: "moving favourites for Firefox in dual boot"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by cioo on 2010-05-26
I have a dual boot installation of Ubuntu.  (The other half is win XP)

On both 'halves' I use Firefox web browser and would like to know how I copy my extensive collection of favorites from Firefox on XP over to Firefox on Ubuntu.

Thanks

---

### Post by fooman on 2010-05-26
is your windows partition/drive mounted and accessible from ubuntu?  if so,  then this will be easy.  :)

boot into windows and start firefox.  in firefox,  go to bookmarks > organize bookmarks > import and backup > export html

watch where the file is saved or manually save it somewhere where you can easily find it.  the file name will be "bookmarks.html"

boot into ubuntu and start firefox.  go to bookmarks > organize bookmarks > import and backup > import html

choose "from an html file",  click next.  under "places" on the left,  find your windows partition/drive and navigate to the saved file.  click open.

if you do not have access to the windows partition...you can still export the html file in windows,  then save it on a flash drive,  boot into ubuntu > firefox > import html and get it off the drive.

hope that helps.

---

### Post by lovinglinux on 2010-05-26
See the [Backup](http://firefox-tutorials.blogspot.com/2010/05/backups.html) section of  [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

