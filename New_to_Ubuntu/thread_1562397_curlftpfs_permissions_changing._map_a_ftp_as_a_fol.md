---
title: "curlftpfs permissions changing. map a ftp as a folder in ubuntu"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by coredatarecovery.com on 2010-08-27
I'm a noob to ubuntu, but not debian.

I wanted to soft link a directory to my webserver and quickly be able to change permissions using chmod or sudo chmod on the directories as well as upload/download and backup my work on several webservers.

I've setup curlftps but I can't change any permissions on the remote ftp filesystem.

3 questions:

1) am I using the right method to mount as a soft link a remote fs using ftp

2) Am I doing something wrong, or have I missed a setting in my config procedure:
        cd /
sudo mkdir weblnks
sudo chown chuck weblnks
cd weblnks
mkdir website.com

curlftpfs 'ftp://username:password@website.com' /weblnks/website.com

I can browse the site but not change permissions
I can upload files in nautilus.
but it shows the owner as root so I can't change permissions with it either.

3) is there an easier way to do what I am attempting to do?

If it matters, I'm running the x64 version of 10.0.04 ubuntu on a dell inspiron dual core 1420 with 4 gigs of ram and a 640 gb hard disk. It's fully updated as of today.

I've already tried places, connect to server and that allows browsing but not permissions changing either.

---

