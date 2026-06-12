---
title: "quanta &amp; nautilus fail to connect to ftp"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by fsh on 2007-08-06
hello, 

i'm a beginner with ubuntu and quanta, but so far i managed to get by
normally i have no problem using ftp, so far i happened to find one server giving me headaches,
the thing is, i can connect to it via browser or gftp, but fail to connect via nautilus or quanta
i get host has no address in nautilus, quanta doesnt list any files in the directory
any help appreciated as i didn't find much with google
oh, and i'm running feisty and quanta + 3.5.6

pzdr 600

---

### Post by fsh on 2007-08-06
as always i found the solution 10min after i'd posted
anyways, problem was simple, i needed to give proper starting directory, gftp did it by itself, quanta didnt e.g. user@host sometimes need the starting directory set to /user so the full link would look like:
[ftp://user@host/user](ftp://user@host/user)

---

