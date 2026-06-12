---
title: "Kubuntu Samba shared folder does not appear on network"
date: 2006-12-08
forum: Networking &amp; Wireless
---

### Post by r.cannell on 2006-12-08
I am setting up a home network with, initially, one Ubuntu and one Kubuntu machine (both dual boot XP). In each case I have a folder on the desktop called SharedFiles that will be shared on the network. The Ubuntu machine works fine. The Kubuntu machine appears on the network but when I try to access the shared folder I get a message saying that the folder does not exist. 
I have tried setting it up using the kcontrol gui and by manually modifying the smb.conf file. I have even copied smb.conf from the Ubuntu machine and just changing the relevant path to the shared folder:

path = /home/andrew/Desktop/SharedFiles

There is no " Netbios ="   in either file (there is a "server string = " though. Is this important? - I presume not as the file works OK on the Ubuntu machine.

Can anyone help, please?

---

### Post by r.cannell on 2006-12-10
Solved it! I hadn't added a user to Samba on this machine!

---

