---
title: "shared folders: how do i log in"
date: 2005-04-11
forum: Networking &amp; Wireless
---

### Post by doni on 2005-04-11
hi there....

my computer is "sonic", my user is "aaron"....

if i share a folder with SMB and want to access it from a windows machine, how do i have to log in? i tried it with "aaron" and "sonic\aaron"...even "sonic\root" and "root", but nothing worked....

how do i do it?

thanks!
doni

---

### Post by localzuk on 2005-04-11
[QUOTE=doni]hi there....

my computer is "sonic", my user is "aaron"....

if i share a folder with SMB and want to access it from a windows machine, how do i have to log in? i tried it with "aaron" and "sonic\aaron"...even "sonic\root" and "root", but nothing worked....

how do i do it?

thanks!
doni[/QUOTE]
 The problem lies with encrypted passwords.

Your computer needs to have a password set for that user in samba. Run 

smbpasswd aaron

as root. It will ask you for a password - this can then be used to log in.

---

