---
title: "Networking permission"
date: 2008-10-21
forum: Networking &amp; Wireless
---

### Post by Silenus on 2008-10-21
I'm using samba from 8.04 to windows xp, on the xp box it shows my shared folders, but it says does not have privlages to access or permission.

I can't figure out how to get around this as I've done everything in every guide I have found.

---

### Post by Iowan on 2008-10-21
Your Windows user has an account on Ubuntu AND Samba?

---

### Post by Silenus on 2008-10-21
I am not 100% on how to set that up, the guides just said to make a guest but when I try.

sudo smbpasswd -a guest
enter pass: ....
enter pass: ....
Failed to modify password entry for user guest

---

### Post by Iowan on 2008-10-21
Is there an Ubuntu account for your Windows user (assuming Windows username is not "guest")? It's usually easier to create them with the same name, but there are ways to map from one to the other.  You'd need to use **adduser** to create an account on Ubuntu, then use **smbpasswd -a** to create the user for Samba.  More info via ** man adduser** and **man smbpasswd**. Have you seen the How-To's by [Stormbringer]("http://ubuntuforums.org/showthread.php?t=202605") and  [dmizer]("http://ubuntuforums.org/showthread.php?t=288534")?

---

### Post by dmizer on 2008-10-21
Closed. Duplicate here: [http://ubuntuforums.org/showthread.php?t=955026](http://ubuntuforums.org/showthread.php?t=955026)

Please do not post duplicate threads. That way, people don't have to duplicate troubleshooting.

---

