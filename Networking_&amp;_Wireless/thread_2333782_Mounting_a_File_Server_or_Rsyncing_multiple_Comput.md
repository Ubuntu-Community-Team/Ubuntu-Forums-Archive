---
title: "Mounting a File Server or Rsyncing multiple Computers and Data Backup"
date: 2016-08-13
forum: Networking &amp; Wireless
---

### Post by Alcidious on 2016-08-13
Hello all fellow enthusiasts! I have a slightly convoluted question, involving aspects of different questions, for one specific purpose. I appreciate your indulging me and thank you.

I currently have three linux setups: (Main) a PC Tower running 64-bit Kubuntu 16.04 LTS, (secondary) a laptop running 64-bit Ubuntu 16.04 LTS, and a Raspberry Pi "server" running Raspbian. I have spent the past couple months setting up a wired LAN, so that I could have a centrally located home file-server. Besides the ability to share pictures, videos, etc., I am mainly interested in a shared "Documents" folder. If I write a new version of a document, or create and updated spreadsheet, or whatever, I'd like to access it and write to the file from any of my devices. 

First, I collected all the data I wanted on the server to a 2TB HDD in my PC. Then I used rsync to copy and sync the folders. 

Second, I used rsync to copy what data was on my laptop to a second folder ... just b/c I wanted to be careful about not losing data. 

Is it better to have all my Documents & Music on the file server, and just keep separate backups on something like an external HD? I have yet another PC Tower 2TB HDD and could keep backups there, but I'm not sure if I can compress the files (both docs and music) and preserve their integrity. I also considered creating some type of images as a means of backup to this other HDD. Is it better to have hard copies of all my files, on large drives, in my PC? Then rsync to the server, and then rsync again to my other computer (laptop)? If so, could I set up cron jobs and just automate that approach? 

Third, as an alternative to the above, should I just mount the file server on whichever computer I am using? I installed SAMBA, but have also looked at NFS. The problem I see is that it is not quite like "mounting" a physical drive to computer. What should I use if I go with this approach?

Thanks so much!

---

### Post by SeijiSensei on 2016-08-13
I have a server where I store all my documents and similar files.  It runs both NFS and Samba so that it's visible to both Linux and Windows machines. On the Linux clients, I mount the exported NFS shares via /etc/fstab as root into locations under /media.  My client machines have /etc/passwd files that match the pairings of usernames and UIDs on the server so permissions work identically across the network.

I could use a central authentication server running NIS or LDAP, but for the small number of clients I have, it's easier just to copy a few lines from the server's /etc/passwd into the equivalent files on the clients.

---

