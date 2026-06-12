---
title: "Home media server"
date: 2010-01-18
forum: New to Ubuntu
---

### Post by blevault on 2010-01-18
Ok, I have my Ubuntu server up and running and I have a 250GB drive formatted to NTFS that shows up under a folder /media/WinMedia.
 
Now what is the best way to set up the NTFS partition.  I have tried to add folders and I dont seem able to do so.  I set up the folder in SAMBA to allow RW, but, I cannot copy anything to it from my PC.  I get an error that access is denied.  
 
Is Samba the right software for what I want to do.
 
Create several folders to do regular backups to from dedicated PC's (one per folder).  Setup a music and pictures folder.  I still feel like I want to add the new pics to my PC, then backup to the server so the family can access.   My PC has 2 750GB drives in a Raid 1 config that I like for protection of files.
 
Anyways I am looking for some good thoughts and directions on which way to go with this project.
 
Thanks

---

### Post by Miljet on 2010-01-18
I am definitely not a server expert. Actually, I am still experimenting with my own local server.
> Is Samba the right software for what I want to do.
I think that would depend on what the other computers are running. If some are running on Windows, Samba is probably your best option. On the other hand, all my computers are running Ubuntu so I set up my server disk as Ext3 and use ssh to access the server. That way I can avoid any permission conflicts.

---

### Post by srt4play on 2010-01-18
> **blevault said:**
> Is Samba the right software for what I want to do

Yes, samba is what you want to use for filesharing.

Why are you using NTFS on the server? The windows client does not interact with the server's filesystem, it interacts with samba. You should use ext3/4 on the server and configure your shares via the right-click menu on your directories.

---

### Post by blackened on 2010-01-18
Samba is great in that you can access the files from pretty much any operating system. There was a great and simple samba howto floating around on the forums that used netbios. Let me see if I can dig it up. **Edit:** here it is [http://ubuntuforums.org/showthread.php?t=202605]("http://ubuntuforums.org/showthread.php?t=202605").

If you're only going to access the files from another Linux machine, then I prefer sshfs in that you can transparently mount the remote directory into the local filesystem. There is a program called Dokan that can mount sshfs in Windows, but it's still in its infancy and a bit on the flaky side.

---

