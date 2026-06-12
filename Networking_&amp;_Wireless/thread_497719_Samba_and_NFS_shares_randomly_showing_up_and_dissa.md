---
title: "Samba and NFS shares randomly showing up and dissapearing"
date: 2007-07-10
forum: Networking &amp; Wireless
---

### Post by Depressed Man on 2007-07-10
I have Samba setup however it randomly doesn't show up in my network. Sometimes I'll see my MyFiles folder. But other times I won't, and I have checked that Samba is running. Accessing the path to my share file smb://vendetta/MyFiles on my desktop works (where my desktop is the host of that folder). However on my laptop it shows up randomly. Sometimes it'll be there, sometimes it won't show up in the network. Then sometimes it won't show up but I can still access it with the path. Then sometimes it doesn't even work even if I type in the path.

Samba and NFS are both set to run on startup (though oddly I can also initiate the samba daemon later) services. I use both because my laptop may be in Linux or WIndows Vista randomly (depending on my use).

---

### Post by CheShA on 2007-07-10
Have you checked samba is definiely starting at boot? I had a problem with feisty where it pretended to start but quietly failed.

Check [this thread ]("http://ubuntuforums.org/showthread.php?t=480932&highlight=samba+deactivated")

---

