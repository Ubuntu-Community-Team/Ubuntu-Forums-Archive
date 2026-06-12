---
title: "How to share directories with samba and NFS?"
date: 2007-03-12
forum: Networking &amp; Wireless
---

### Post by sieg on 2007-03-12
How to share directories?
I've used the ubuntu GUI for sharing for both samba and NFS. However, this is confusing since I have one share named siegfried_smb and the other named siegfried_nfs where both are sharing /home/siegfried.

However, the GUI does not seem to want to let me do this. I click edit properties for the first one and change the name to siegfried_smb and then I go edit the properties of the second one and find its name has changed to siegfried_smb so I change that to siegfried_nfs and find that this changes the first one from siegfried_smb to siegfried_nfs too!

I have both smb and samba servers started.

I have SFU installed on windows 2003 server and I'm expecting to be able to see the NFS shares and samba shares too.

I'm actually seeing the share (from windows) as \\10.169.0.127\siegfried (but never both at the same time) but I cannot see the contents. When I try to view the contents of the shares, it prompts for username password. When I correctly enter the username and password, it tells me they are incorrect!

Thanks,
Siegfried

---

### Post by gradedcheese on 2007-03-12
First of all:

> 
shares, it prompts for username password. When I correctly enter the username and password, it tells me they are incorrect!


This means that you need to add yourself (and any other users you need) via smpasswd, I wrote instructions about it [in this little guide]("http://andrey.thedotcommune.com/samba.html") -- that should take care of that problem.

As for the main question: Samba takes a path (ie: the real share name) and shares it under a 'name' that you pick.  For example, /var/share could be shared as 'photos' or whatever you want.  NFS, however, just shares the real path.  Therefore, you just need to choose the 'name' for samba.

---

