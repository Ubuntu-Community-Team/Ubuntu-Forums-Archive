---
title: "Mapping Home folders in a W2K3 Domain, with ubuntu client"
date: 2008-02-18
forum: Networking &amp; Wireless
---

### Post by fernandes_s on 2008-02-18
Hi Guys, at school we have a W2k3 domaine, with debian fileservers,and xp clients, but I wanted to install an ubuntu client, that can see the shares automatically, similar to the scripts which we put on netlogon, and I also want to mount the home folder automatically, the problem, is that every user is in another group, and the server doesnt have: like \\server\share\user, it is more like, \\server\share\group\folder\user,  and what i want to do is to determine the home folder for each user, so that if a AD user logins to the ubuntu client, he/she has his habitual shares mapped on the desktop. I have already samba goin on, and have added the ubuntu client to the domain ( i have followed lot's of tutos).
wbinfo-u and getent passwd works, i can see the domain users. I think ill be able to mount the common shares in the fstab, according to which group the user is in, but I don't know how to retrieve the user folder, my boss showed me a very complicated script using ldap querys, but i can't figure how to make use of it, and put it in script, and he wouldn't show me the script a second time, lol. I am already thanking you for all your Help.

Suraj Fernandes

---

### Post by fernandes_s on 2008-02-19
Up

---

### Post by fernandes_s on 2008-02-25
up please, nobody never experienced this, because, if i can do this, then i would be able to install couple more ubuntu clients in a Windows domain

---

### Post by fernandes_s on 2008-03-31
bump bump

---

