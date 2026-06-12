---
title: "login from windows to shared folders"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by hygum on 2007-03-21
when i try to look in the shared folders in ubuntu from windows, it asks for username and password. When i give it my ubuntu username and password it doesnt work, and i cant find anywhere in ubuntu a program with which i can administrate samba/who can login to what.

I have a shared folder in ubuntu.

Where do i administrate this?
How do i login?

---

### Post by rianquinn on 2007-03-21
I just opened a thread on this same topic. In short, there is no way. Shared Folders simply do not work in Ubuntu using samba. For two reasons,

[LIST=1]
[*]There is no gui to setup passwords
[*]Nautilis has serious problems with the Netbios name. You need to use statis IP addresses
[/LIST]

If you look at the Ubuntu Guide, it will show you how to setup user passwords via the terminal. If you find a god way to Network Windows and Linux let use know.

---

### Post by Khaled Khalil on 2007-03-21
[http://ubuntuforums.org/showpost.php?p=2240223&postcount=2](http://ubuntuforums.org/showpost.php?p=2240223&postcount=2)
"sudo smbpasswd -a"
good luck

---

### Post by rianquinn on 2007-03-22
Once again though, I don't think my Mother could do that, yet she has her own Windows Network. Seriously, Samba is not the problem, it is Ubuntu/GNOME.

---

