---
title: "Samba authentication allows unauthorized user"
date: 2018-08-29
forum: Networking &amp; Wireless
---

### Post by gcthate on 2018-08-29
I have Samba installed on a server running Ubuntu Server 16.04 and on a desktop PC running Linux Mint 19. The Samba configuration file on the server identifies one user account, "AccountX", to which read-only access is provided for a given share. No problem, works great. 

When I log into a superuser account on the desktop PC and browse to the server share, I'm prompted to authenticate access by entering a password. I enter the password for this account on the desktop PC, and voila, I have (read-only) access to the files on the server share. Problem is that this is neither the account authorized in the server's Samba configuration file nor the password for that account. How is it that the desktop PC gets access to the server share?

P.S. The superuser account name into which I'm logged on the desktop PC is the same as a superuser account name on the server. However, they have different passwords.

---

### Post by Morbius1 on 2018-08-29
Without telling us how the Ubuntu Samba server is set up your guess is as good as anyone reading your post.

Why not post the output of the following command run on the Ubuntu server:
```
testparm -s
```

---

