---
title: "&quot;Access is Denied&quot; when trying to copy TO Ubuntu share from winxp x64"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by Etoexo on 2009-03-23
Hi, 
    I've done a good amount of searching to find resolve with my issue and have found threads that deal with similar problems, but not quite what I'm having. In any case, my apologizes in advance if I'm posting on a topic that's already been dealt with. So here goes...

Setup - small home network comprised of a winxp x64 machine and an Ubuntu 8.1 box. 

The issue - I was able to mount my media folder from my winxp machine to Ubuntu, using samba. I then (guided by a forum) setup my Ubuntu home folder to be shared on the network using the "shares-admin" command in the terminal. Then, I made sure that the "read only" checkbox was unchecked. Afterwards I was able to mount the Ubuntu share on my winxp machine using "Map network drive". So far, everything was working well; I was able to mount, explore, even copy from the Ubuntu share onto my winxp. However, when I attempt to copy TO the Ubuntu share I get the following error: "Cannot copy FILENAME: Access is denied. Make sure the disk is not full or write-protected and that the file is not currently in use." Disk is definitely not full, neither is the file in use, and I was under the impression that by unchecking the "read only" box I turned off the write protection. 

I suppose its not too big a deal since I can always just put whatever I want to copy in the media folder I already have mounted, but for the sake of learning how to use Ubuntu, it would be nice to get this to work properly. Thanks in advance for any suggestions! 

Kind regards,
Dmitry

---

### Post by lavinog on 2009-03-24
The problem sounds like the actual folder permissions.
right click on the folder and select properties and click on the permissions tab.
if you are connecting to the share as a guest, you have to set the folder access for 'others' to create and delete files. If your share requires a login you should check the folder access for that name to allow creating and deleting files.

---

