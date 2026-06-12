---
title: "external usb hard drive - permission problem with certain files"
date: 2009-09-14
forum: New to Ubuntu
---

### Post by souse on 2009-09-14
Hi All,

I am pleased with my ubuntu 9.04 64-bit, thanks to this forum. 

I am currently having a problem which might pull me back towards Windows if not solved. I am using external hard drive (NTFS partition) to store lot of training materials, videos, photos etc and using with Windows Vista running on a different laptop. 

When I connect the external hard drive to Ubuntu system, it detects the external hard disk and some files play and some do not. Surprisingly they are of same format with same permissions (it has owner as root). When I try to play certain files, they report **"you don't have permission to ..."**. I have gone thru multiple posts and also googled it...but none seem to assist in resolving the issue. The percentage of files that I cant play from external hard drive are about 60%. 

Note: I have required codecs, drivers etc as I am able to play another file of the same format without any problem. Also, I can play similar file with same permissions. 

I will be using the external hard drive with windows as well. 

I am a newbie and with ubuntu as I was attracted to it with its tag line "linux for human"

Counting on you..

Thanks.

---

### Post by mikewhatever on 2009-09-15
You've mentioned that the permission the files have is root ownership. I am not sure if you are aware that ownership is only part of the permissions system. Each user also has the rights to read, write and execute a file. Could it be that for some reason you don't have one of those?

---

