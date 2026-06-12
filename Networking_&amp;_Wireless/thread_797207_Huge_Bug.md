---
title: "Huge Bug"
date: 2008-05-17
forum: Networking &amp; Wireless
---

### Post by Ponhovo on 2008-05-17
found a huge bug on ubuntu [or that's the only one i've tested] when using GPROFTPD

when you create a user for teh FTP server, you are changing the OS's users too
if you create a user with the same name of the machine user and change its passwords, it will change in the machine's too


problem: you lose the password and becomes a huge headache
advantage: if you forgot your current passwd, you can change it without knowing it
advantage's problem: bad-minded ppl would use it to screw with someone

hope you can fix this soon
i got a serious headache too, and when i found out, i went directly here to report

cheers

---

### Post by dmizer on 2008-05-17
ftp (as well as samba, ssh, and a host of others) users have actual accounts on the machine, so i believe this is expected behavior.  that's one reason why you use aliases for ftp users.  

bad-minded people can't use it unless they have root privileges.

edit:
as a side note, windows ftp servers function the same way.

---

