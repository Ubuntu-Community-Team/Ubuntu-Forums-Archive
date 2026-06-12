---
title: "Help! Can anyone tell me how to setup a file server for my local network?"
date: 2010-08-15
forum: New to Ubuntu
---

### Post by dongk on 2010-08-15
Hello,

I'm trying to setup a NAS for my network, the only problem is that I can't figure out how to do it.  On my network I have about 3 computers however only I only use 2 of them so I thought that maybe I could use the third computer in such a way that I could access it 24/7 from the internet as a server for all of my files (school papers, music etc etc...). The only problem is that I don't know where to get started. Both of the computers I'm currently using are Windows and the one that I,hopefully, can turn into a server is running on Ubuntu. So, any advice or tutorials that someone can point me towards?

Thanks in advance

---

### Post by drdos2006 on 2010-08-15
> 
[http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs](http://ubuntuforums.org/showthread.php?t=249889&highlight=howto+nfs)
HOWTO: NFS Server/Client 

Addendum:	On the Server machine
Needed to add Group of users on the machine designated as the server. Added the group via Webmin because that was what I was using. If that does not work then use terminal on the Server machine:
sudo addgroup MyGroupName
Added /media/sharedfiles on server with :	sudo mkdir /media/sharedfiles
Needed to change group permissions for /media//sharedfiles
sudo chgrp MyGroupName  /media/sharedfiles
//**
On the Client machine: Created a directory of /media/sharedfiles with : sudo mkdir /media/sharedfiles, mounted /media/sharedfiles from terminal as /media/sharedfiles with : 
sudo mount  <serverIPaddress>:/media/sharedfiles  /media/sharedfiles 
Can also be added to /etc/fstab for automatic mounting.
Copied files as test and it worked.
regards

---

### Post by bodhi.zazen on 2010-08-15
You could use several methods to do this. If you are connecting over the internet I suggest you consider a http server (nginx would work).

If you want two way transfer of files , I highly advise ssh. Be sure to secure the ssh server (use keys, disable passwords).

From Windows you would use putty or winscp.

---

