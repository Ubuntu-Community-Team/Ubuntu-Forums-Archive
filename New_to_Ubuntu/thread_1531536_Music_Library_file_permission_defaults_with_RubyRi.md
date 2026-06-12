---
title: "Music Library file permission defaults with RubyRipper"
date: 2010-07-15
forum: New to Ubuntu
---

### Post by CindyP on 2010-07-15
I am trying to set up a music library in my 10.04 Ubuntu box that can be shared and maintained by  by 2 users who use Windows on their laptops. (both work machines).  I have samba shares set up to access the shared Music folder using the Windows UserIDs that are set up on Ubuntu and are members of a common group (cinbin) and all that seems to be working fine.

90% of the time files and folders are created in the Music folder using RubyRipper.   Permissions for those folders all look like the high level folder: 
[FONT="Fixedsys"]drwxrwsr-x 212 cindy cinbin 32768 2010-07-15 18:33 /home/cindy/Music/flac[/FONT]

The files created with RubyRipper are placed in in subfolders for each album - example here:
[FONT="Fixedsys"]-rw-r--r-- 1 cindy cinbin 21353711 2010-07-15 19:09 06.flac[/FONT]
  
The problem is with the file level permissions.  I would like the files to be [FONT="Fixedsys"]-rw-rw-r--[/FONT]  so we can maintain the tags from software on our windows systems.   

How do I achieve this so all new folders/files created by RubyRipper have the correct file permissions?   After reading this post [http://ubuntuforums.org/showthread.php?t=1529556](http://ubuntuforums.org/showthread.php?t=1529556) I am thinking that I maybe should set the system's global profile (/etc/profile) umask to 002.  Will this do it?  Is this wise?

Thanks

---

