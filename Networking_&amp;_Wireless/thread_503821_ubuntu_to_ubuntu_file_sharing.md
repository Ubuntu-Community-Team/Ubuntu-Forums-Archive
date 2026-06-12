---
title: "ubuntu to ubuntu file sharing"
date: 2007-07-18
forum: Networking &amp; Wireless
---

### Post by glendavee on 2007-07-18
I have been trying to share files between two machines both running Feisty by going to System>Administration>Shared Folders and adding the relevant files, and assigning the pc name (as listed in Network Settings) to share with (and doing the same on the other pc). Both pcs have samba and nfs installed.
Doesn't seem to work however. When I look in Places>Network I can see the other pc listed, but I can't get at the files. Am I expecting things to be too simple and straightforward?

---

### Post by overdrank on 2007-07-19
> **glendavee said:**
> I have been trying to share files between two machines both running Feisty by going to System>Administration>Shared Folders and adding the relevant files, and assigning the pc name (as listed in Network Settings) to share with (and doing the same on the other pc). Both pcs have samba and nfs installed.
Doesn't seem to work however. When I look in Places>Network I can see the other pc listed, but I can't get at the files. Am I expecting things to be too simple and straightforward?

Hi I dont know if you have solved your issue but last night I was going to answer you post on sharing. I set up my network between feisty and edgy and this morning when I rebooted the systems it was gone so I installed feisty on the spare system and set up the network with samba and works great even after reboots. If you need assistants please ask. :popcorn:

---

### Post by glendavee on 2007-07-19
Overdrank - Thanks for the thought. I've got it sorted out. Answer was to select SMB instead of NFS at the "Share through" dialog box. Just seemed strange to have to select Windows sharing when using 2 ubuntu systems!!!

---

### Post by overdrank on 2007-07-19
> **glendavee said:**
> Overdrank - Thanks for the thought. I've got it sorted out. Answer was to select SMB instead of NFS at the "Share through" dialog box. Just seemed strange to have to select Windows sharing when using 2 ubuntu systems!!!

Great deal I stumbled with that also and my problem last nite was firestarter firewall . Good luck!

---

