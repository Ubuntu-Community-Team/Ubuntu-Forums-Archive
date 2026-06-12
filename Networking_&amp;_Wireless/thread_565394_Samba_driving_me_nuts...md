---
title: "Samba driving me nuts.."
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by LeGollemux on 2007-10-02
I am having the same problem on several Ubuntu machines. 
I create a user, but I cant log into the machine from any of my XP or Vista boxes. I have tried various tools, and many many different options but I seem to be missing something specific that will allow a user, once created and given the relevant permissions and group memberships to log in...

somebody point me in the right direction...

---

### Post by RoyalPro on 2007-10-02
Have you set up samba pass words?
you@computer:~$ sudo smbpasswd –a "account name here"
	New SMB password: ********
	Retype new SMB password:********

---

### Post by SteveHillier on 2007-10-03
I have done this but I get a message ' Failed to modify password entry for user ...'.
Any known reasons (this is on fiesty)

---

### Post by dmizer on 2007-10-03
if you havn't seen it already, check the first link in my sig.  this is the reference i use when setting up a samba server.  if that doesn't work to make your shares available, then you will have to look into other possible causes (like firewalls)

---

