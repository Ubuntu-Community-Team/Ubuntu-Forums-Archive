---
title: "Pop up Messages"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by harveyfh on 2008-02-25
Hi! Is there any way I can send announcements to workstations in my Lab which are all in Ubuntu? Some scripts entered in my computer perhaps resulting to some sort of pop up messages in the students' workstations?

---

### Post by Rhubarb on 2008-02-25
Make sure samba is installed on any PCs you wish to be able to send messages (not required for PCs that just need to receive them).
The easiest way to do this, is to click on System --> Administration --> Shared Folders.
A box should come up asking you if you want to install samba and NFS.
Tell it to install samba (and NFS if you want - not necessary for this).
You don't need to share any folders.

Install linpopup on all PCs that need to send and recieve messages:-
```
sudo aptitude install linpopup
```

Please read the man page for linpopup
```
man linpopup
```
If you wish to read more about it.

linpopup is a nice gui program, enter in the IP address of the PC you want to send a message to, type in the message, and press send.
linpopup also works with windows PCs too.

---

### Post by harveyfh on 2008-02-25
thanks man, I'll try that... will keep you posted

---

### Post by harveyfh on 2008-02-26
Is there any way to do that without installing linpopup? i thought i saw somewhere about a script that when entered it will generate a pop up window on another ubuntu pc with its message... just didnt bookmark it :(

---

