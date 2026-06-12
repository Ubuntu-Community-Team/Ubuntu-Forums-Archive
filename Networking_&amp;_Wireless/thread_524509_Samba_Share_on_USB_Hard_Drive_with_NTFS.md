---
title: "Samba Share on USB Hard Drive with NTFS"
date: 2007-08-13
forum: Networking &amp; Wireless
---

### Post by ravid on 2007-08-13
Hello All, 

I have a quick question about a Samba share that I'm trying to create on an external NTFS formatted USB hard drive.  

1. I already have ntfs-3g installed, and the drive is working perfectly on the desktop with both read AND write capabilities

2. I've setup the smb.conf entry for the folder as follows:

[Music]
path = /media/80GIG/Music
available = yes
browsable = yes
public = yes
writable = yes
create mask = 0777
directory mask = 0777
force user = nobody
force group = nogroup
force group = nogroup

The path is correct and ive restarted the samba server, however whenever I try to load the folder on another computer it won't even list the files.  Gives a permisison error. 

Anyone have any idea's?  It would be greatly appreciated.

Thanks all.
Cheers, 
RaViD

---

