---
title: "[SOLVED] Crossover cable questions!"
date: 2008-09-04
forum: Networking &amp; Wireless
---

### Post by Rytron on 2008-09-04
Hi,
I have some questions regarding a crossover cable and connecting computers with similar and dismilar operating systems.

If I get a crossover cable, could I easily connect:
Ubuntu desktop to Kubuntu Laptop?
Ubuntu desktop to Vista Laptop?
XP desktop to Kubuntu Laptop?
XP desktop to Vista Laptop?

The above would be single instances and not all at once.

Would there be extra measures to take before I can start passing files from pc to laptop?

Please reply.

Thanks.

---

### Post by Iowan on 2008-09-04
The crossover cable will allow communication between two boxes - but you will still need some support software: Samba, NFS, SSHFS... 
Having never worked with Vista (lucky me?), I dunno what (if anything) other than the crossover is required for sharing between Vista and XP.

---

### Post by Rytron on 2008-09-05
Would it be straight forward to set up software to connect Ubuntu pc to Kubuntu laptop via crossover cable? Is Samba the best choice?

---

### Post by Iowan on 2008-09-05
Samba is a bit more "universal" (shares could be used with Windows machines, too) but somewhat complex to set up.  NFS is the common Unix-Unix file system, but can be problematic if the "server" is offline.  I recently installed SSHFS on a machine - seemed pretty painless... but the "server" already had SSH-server installed.  [This]("http://ubuntuforums.org/showthread.php?t=898485") thread has my experience with SSHFS, and links to the help page.

---

### Post by jerome1232 on 2008-09-05
When using a crossover cable you do have to manually assign ip addresses to the computers as there's no dhcp server present to assign them.

I'd like to second ssh for file sharing there's a great windows client called winscp that allows drag and drop copying to/from the server.

The windows implementation of openssh should allow windows to be an ssh server as well although I haven't tested it this way. (Ubuntu  has built in ssh capabilties, just hit places connect to server, select sftp provide a vaild login for the server in question and now you can browse the shares with nautilis)

---

