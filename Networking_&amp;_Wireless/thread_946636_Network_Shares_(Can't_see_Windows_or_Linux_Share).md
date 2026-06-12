---
title: "Network Shares (Can't see Windows or Linux Share)"
date: 2008-10-13
forum: Networking &amp; Wireless
---

### Post by Kareeser on 2008-10-13
So, I followed the directions here:
[http://ubuntuforums.org/showthread.php?t=304131&highlight=Thunar+Native+Windows+Network+Browsing](http://ubuntuforums.org/showthread.php?t=304131&highlight=Thunar+Native+Windows+Network+Browsing)

After doing all that, restarting, etc, I can see the network folders (yay!) but I can't access them. That is, if I try to access the deepest folder, the connection times out (immediately, no waiting time req'd). Any clue why?

Second problem:
Applications -> System -> Shared Folders

I set up one of my home folders as a network share (~/Shared), gave it 777, and added it to the shared folders in Xubuntu... but for some reason, when I try to access it on a Windows computer, it asks for a username and password combo? My linux username/password don't work for some reason... :(

Any ideas?

---

### Post by Iowan on 2008-10-13
Are the Windows and Samba users the same name... and did you add your Ubuntu user to the Samba users via **smbpasswd**. This infers that the windows user must be both a Ubuntu user and a Samba user.  There are ways to map Windows users to Unix users, but it's easier to make the names the same.

---

### Post by Kareeser on 2008-10-13
Thanks Iowan, I'll give that a shot and let you know.

In the meantime however, I don't understand why the usernames must match. If I were to go to another Windows installation and try to access the shared folder (on another windows computer), there wouldn't be any problems, even if the usernames were different...?

---

### Post by Iowan on 2008-10-13
I'll backpedal a little, and ask if your shares were **security=share** or **security = user** - the latter would require Samba "usership".

---

