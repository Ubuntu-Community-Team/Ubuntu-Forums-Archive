---
title: "Samba creating users"
date: 2008-10-31
forum: Networking &amp; Wireless
---

### Post by SMGGM on 2008-10-31
Hello

I made Ubuntu share files, I've downloaded the files needed for SMB sharing. Everything work but how do you create Samba users. Please read on to know my problem

If I [share a folder](http://www.multidesk.be/bijlage/5688d4e5ea13194cf8019a94458d91bb.png) without Guest access, how do I access this share on my Windows computer?

I tried to create Samba users (sudo smbpasswd -a *username*) but when I use that pass and username on Windows I get an access denied error.
In Ubuntu 7.xx this worked fine but in 8.04 (or 8.10) I can only share folders with guest access.
But if I use guest access and transfer files from Windows to Linux I always have to change the permissions (with sudo nautilus) so I can change the files. And with guest access you can't edit the existing share files.

I use Ubuntu 8.10 and WinXP

Thanks in advanced ;)

---

### Post by tonyh6243 on 2008-10-31
On the machine you installed Samba on, did you open the ports for Samba in the firewall? First off, have you enabled the firewall? The ports that need to be open are 137-139, 445.

---

### Post by SMGGM on 2008-10-31
The system is just installed, it's a standard installation.
I disabled the firewall (although I don't see way). Sharing works but I'm obliged to enable guest sharing. If I don't enable that then I'm asked to give a password and username (that I don't know). Adding samba users (sudo smbpasswd -a *username*) doesn't work -> keeps getting not enough permissions.

If I use guest sharing, then I can use Guest (without password) to access my shared folders on Windows. But if I put files on my Ubuntu PC using Windows then I always have to change the rights for every file the I've placed (because the owner of the new files are Nobody).
Also I can't edit the files that are already in that folder if I just use Guest sharing.

So how do you create users that can log in when I want to access my shared folders from my Windows computer.
In Ubuntu 7.xx you just had to create Samba users (sudo smbpasswd -a *username*) but now you can't log on to the shared folders with the Samba users.

---

### Post by tonyh6243 on 2008-11-02
Can you post your smb.conf file?

---

### Post by SMGGM on 2008-11-02
As attachment

---

### Post by jonandrews on 2008-11-02
I've put a step-by-step guide to Ubuntu / XP networking which I think will show you what to do..   

[www.europe.eclipse.co.uk/Ubuntu/](www.europe.eclipse.co.uk/Ubuntu/)

---

