---
title: "Samba issues"
date: 2007-06-07
forum: Networking &amp; Wireless
---

### Post by seraphim_72 on 2007-06-07
For some reason after my upgrade to Feisty my Samba has gone all wonky. Now after much messing around - I have discovered it to be a Konqueror issue, not a Samba one. Until the upgrade all was well, and I loved being able to use samba in Konq, but it all ended with the upgrade. It stalled every time. It even saw my windows network, and then died on the search of it.  Now I looked [ here]("http://ubuntuforums.org/showthread.php?t=426739&highlight=feisty+cifs+fstab+permission+denied") and thought I uninstalled and reinstalled Samba, none of that helped, none of the other problems were near mine. So I remembered good old [smb4k]("http://smb4k.berlios.de/") and I installed it, and it worked like a charm [(caveat)]("http://www.debuntu.org/2006/05/31/58-how-to-smbfs-smbmnt-must-be-installed-suid-root"). 

So I fired up Konqueror - same thing. So I want to ask this - Has anyone else seen this? My other machine at work (500+ machines - I am the lone linux person) has worked after the upgrade, but it is darn slow and will time out in Konq first, then on the second or third search find the machines on the network (it always finds the network just fine oddly). 

I thought before I drag my woes to the KDE team I would ask here to see if anyone else has had samba/KDE issues after an upgrade. I am going to put a fresh install at work on Monday and will report on my findings then.

Sera

---

### Post by dmizer on 2007-06-07
try this:
```
sudo aptitude update
sudo aptitude install smbfs
```
followed by:
```
sudo smbpasswd -L -a your_username
sudo smbpasswd -L -e your_username
```
where "your_username" is your actual ubuntu account name.

edit:
by the way, the links you posted (except smb4k) were all geared toward configuring kubuntu for hosting shares out to windows computers, not for allowing kubuntu to view shares on windows computers.  for a command line approach to viewing windows shares from kubuntu, follow the second link in my sig.

---

