---
title: "Sharing Linux files"
date: 2007-02-14
forum: Networking &amp; Wireless
---

### Post by f1renz on 2007-02-14
I've tried without luck to properly connect my laptop to my desktop PC

**_Laptop Specs:_**
OS WInXP
Intel Dual Core, 512MB RAM

Desktop PC Specs:
OS Ubuntu6.10
Amd Athlon2300Mhz, 256MB RAM

Here's the problem:

Under Places>Network Servers  (on my PC) samba has two options available 
1>JOE (which is my laptop's shared documents) and 
2>HomeComputer (referring to the PC).

I can read, copy from, move and delete files in JOE and the shared files on my PC can be seen when working on the PC

However on my laptop I can't access the files from HomeComputer. A MESSAGE saying "\\HomeComputer is not accessible.  YOU MIGHT NOT HAVE PERMISSION TO USE THIS NETWORK RESOURCE.................Network path not found" comes up.

So in other words my Xp laptop can't access my Linux PC. But my Linux PC can access my laptop.

Any ideas???

---

### Post by gradedcheese on 2007-02-14
You need to do a little samba configuration, namely adding an smbuser for the PC.  Here's a simply guide I wrote: [http://andrey.thedotcommune.com/samba.html](http://andrey.thedotcommune.com/samba.html)

---

### Post by f1renz on 2007-02-14
I did most of what was listed in the help file beforehand except configuring the /etc/samba/smb.conf file.

Did that to make the user account 'writable' and 'browsable'.

However still getting error messages on my Xp laptop when trying to connect. Could it be a problem with the Xp side of things?

---

### Post by gradedcheese on 2007-02-14
Does XP give you a username/password dialog box?  If so, make sure the username field has just the user name, and not the user name plus some other info (XP likes to put user@hostname or something as I recall).  Also make sure that, as my writeup said, you added the user that you are truing to log in as from XP to smbusers and make sure that you restarted samba (since that's when changes take effect).  Otherwise, I don't think the XP-side settings should affect it.

---

