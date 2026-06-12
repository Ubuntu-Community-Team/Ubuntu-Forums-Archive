---
title: "add user"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by degarb on 2011-01-16
WE need a GRAPHICAL way to add a samba user!!!!!!

I have memory issues on these sort of things and just want to add users without keeping on googling, failing on instructions, googling more outdated stuff.

I just failed with half hour googling and trying stuff.  2 week ago I added a user after 14 hours of reading defunct pages, but back at square one today.  It refuses to adduser.   Stopping samba doesn't work.  Shares are not browsable by others, despite telling share to let anyone browse.

---

### Post by wednesday allfather on 2011-01-16
There is a GUI I used before in the repos.  

```
sudo apt-get install system-config-samba
```

Hope that helps.

---

### Post by degarb on 2011-01-16
> **wednesday allfather said:**
> There is a GUI I used before in the repos.  

```
sudo apt-get install system-config-samba
```

Hope that helps.

Thanks I will try that when I get back on the machine.

I did see a samba config gui, but no apparent way to add users and passwords.  Just adding folder and users that already exist.

---

### Post by degarb on 2011-01-16
Do you need to stop samba when adding via:


sudo smbpasswd -a <username>
New SMB password: ######
Retype new SMB password: ######

It replied, unable to add user to me.  3 times.

---

