---
title: "Setting up PC network to transfer files"
date: 2016-02-15
forum: Networking &amp; Wireless
---

### Post by Macamba on 2016-02-15
Let me start with apologising for asking this. I could not find the answer. **My question is how do I set up a network?**

My home network consists of a WiFi router to which my Windows XP/Ubuntu 14.04.3 LTS is connected by wire. I bought a new PC with Windows 10 and I have an installation DVD with Ubuntu 15.10. When I have the new system configured I want to move files from the old to the new system. 

Documents I read: 
[LIST]
[*][Router - Community Wiki]("https://help.ubuntu.com/community/Router"). Not used as it describes how to set up _an Ubuntu installation_ acting as a router
[*][Networking - Community Wiki]("https://wiki.ubuntu.com/Networking"). Not used as it goes quit deep into configuring a mobile (?)
[*]:confused:
[/LIST]

Can anyone point me in the right direction so I can create a (temporary) network using one router and two PC's?

---

### Post by kurt18947 on 2016-02-15
Are you talking primarily data files? I'd probably use the 21 st century version of sneaker net - portable hard drive or flash drive. I have some files I want available to all machines but don't really want to enable file sharing due to probably outdated security concerns. I have a second router with USB port. I plug a flash drive into that port and store files I want all machines to have access to there. I could attach an external hard drive there if I wanted to but don't need the speed and capacity of a hard drive. I refer to it as a poor man's NAS.

If I wanted to move or synchronize files over a network I'd enable file sharing (I think that's necessary) then use something like Unison or Lucky Backup to move files over the network.

---

### Post by Macamba on 2016-02-15
> **kurt18947 said:**
> Are you talking primarily data files?

Yes. Something like that. At the moment I have a router, an old and new PC, an external HD and a NAS. But I would prefer to move/copy files from the old to the new PC using the router (eg. the network).

Using an external HD/NAS means copying a file twice!

Edit:
For future/my reference: [HOWTO: Easy, simple GUI setup of smb file server]("http://ubuntuforums.org/showthread.php?t=1685718"). This might help, but household chores call.

---

### Post by Macamba on 2016-02-15
It seams [HOWTO: Easy, simple GUI setup of smb file server]("http://ubuntuforums.org/showthread.php?t=1685718") is the answer. By identifying folders for 'Local Network Share', and subsequent installation of Samba, I might be travelling into the right direction. But I can't check it out, as the power cord of that computer is in use for said 'household chores'.

---

### Post by Dennis N on 2016-02-15
To move numerous files from Computer A to Computer B over the LAN, you can employ an SSH connection using OpenSSH. No Samba needed.

---

### Post by Macamba on 2016-02-17
> **Dennis N said:**
> To move numerous files from Computer A to Computer B over the LAN, you can employ an SSH connection using OpenSSH. No Samba needed.

Interesting. Some questions:
[LIST]
[*]Can a computer be both a server and a client
[*]Is there graphical support, like opening Nautilus and click-copy files? Or is the usage of a terminal the way to go?
[/LIST]

---

