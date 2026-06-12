---
title: "Mounting Windows Server 2003 volumes"
date: 2007-08-24
forum: Networking &amp; Wireless
---

### Post by radink on 2007-08-24
Hey all,

I want to be able to mount our windows server 2003 volumes in Ubuntu, but I can't seem to find the answer im looking for. Searching doesn't seem to reveal the right answer. Any ideas where to get started with this?

Thanks!

---

### Post by loserboy on 2007-08-24
doesn't server 2003 use NTFS?

if so i think you can just install ntfs-3g


edit: oh im sorry you said mount, for some reason I thought u wanted write access

---

### Post by radink on 2007-08-24
It does, but I'm not sure what to do from that point. I've already mounted my windows volume that's on this pc, but not sure about the server.

---

### Post by loserboy on 2007-08-24
oh are you trying to mount them remotely?

---

### Post by radink on 2007-08-24
I haven't done anything yet, since I have no clue of what to do. I guess im looking for the noob answer :)

---

### Post by loserboy on 2007-08-24
what im sayin is do you have server 03 and ubuntu on one computer and you're just trying to access the server partitions or is ubuntu on one computer and server on another and you want to access them remotely

---

### Post by radink on 2007-08-25
Loserboy,

Gotcha, the 2003 server is a separate machine across the network.

---

### Post by loserboy on 2007-08-27
i believe the easiest way to do that is to use Samba   just search for "howto: samba" or something.... if you're still watching this thread

edit: this link should be helpful [http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+setup+samab](http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+setup+samab)


      this is an alternative using the program called NFS [http://ubuntuforums.org/showthread.php?t=310168&highlight=samba](http://ubuntuforums.org/showthread.php?t=310168&highlight=samba)   NFS is actually designed for use betwen 2 linux boxes, but this person made it work with windows and seems to be happy

---

