---
title: "using crossover cable to connect windows to ubuntu"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by bump_ on 2008-05-15
Hello,

I am trying to connect my laptop with Ubuntu to a desktop with Win XP. I connected the two via a crossover cable. I have set the desktop's connections to 

ip:192.168.0.1 subnet:255.255.255.0

and the laptop to

ip:192.168.0.2 subnet:255.255.255.0

Both computers are able to ping each other and when i go to view workgroups in win xp, i can see my samba share. but here is where my problems begin.

When I try to access that samba share from win xp, i am told i do not have the permission, even though my account is an admin account. When I go to the samba part through nautilus (the location smb:\\\) and type 192.168.0.1 in the address bar, i get an error saying 192.168.0.1 is not a folder.

Any idea what i am doing wrong?

---

### Post by zenwalker on 2008-05-15
Have u shared few DIRs in Windows to get accessed for SAMBA. And probably in the Linux User Groups, i think u need to enable SAMBA support. Just a wild guess.

---

### Post by bump_ on 2008-05-15
Ok, i fiddled a bit and managed to get ubuntu to get into the Win xp. It turned out, I needed to delete one of the 3 ///'s so it read smb://192.168.0.1 before the shared folders popped up in nautilus.

But the the problem with privledges in Win xp still stand :(

Zenwalker: could you explain enabling samba in the user groups?

---

### Post by Iowan on 2008-05-15
Speaking of accounts... Did you set up your user via **smbpasswd -a**? Besides having an Ubuntu account, the user also needs a Samba account.

---

