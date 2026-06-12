---
title: "FTP One Last Step"
date: 2007-09-17
forum: Networking &amp; Wireless
---

### Post by sunus on 2007-09-17
My very old computer is about to give up. Before it does, I mean to transfer data onto my new computer. With this in mind, I set up an ftp server on the old computer and a client on the new. Much to my surprise, I am able to log into the old computer and have succeeded in transferring data from /home.

However, I have a large number of media files which reside on a different partition on the old computer and are mounted via fstab as /media/sda5 which I cant find a way of accessing over ftp. I think I'm close but so far no coconut :)

Help required.

---

### Post by sunus on 2007-09-17
Solved my particular problem by changing the mount point to the media partition to a place within the home folder of the user I could log in as via ftp.

Would still be interested in knowing how to get at the media partition directly though. Is this one instance where having a root user would help?

---

### Post by Ashlord on 2007-09-17
Are you using any chroot jail? If not, just go to /media/sda5 directly in your ftpclient to retrieve your files. Make sure the read permissions are set though. :)

---

### Post by sunus on 2007-09-17
> **Ashlord said:**
> Are you using any chroot jail?

I was following a how-to I found on this forum. As always when I'm not really sure of what I'm doing, I tried to stay as close to the outlined process as I possibly could and typed with my fingers crossed.:) Looking at that how-to again, the instruction to set chroot local user=yes in the configuration leaps out at me thanks to your comment.

---

