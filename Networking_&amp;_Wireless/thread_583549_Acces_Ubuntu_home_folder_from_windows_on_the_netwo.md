---
title: "Acces Ubuntu home folder from windows on the network"
date: 2007-10-20
forum: Networking &amp; Wireless
---

### Post by flavio newbie on 2007-10-20
Ok i installed samba and i can access shared folders of other computers on the network, but the other people when they find my computer on mshome (and i actually would like it to be on workgroup but dont know how to) they are asked for a user and password. With the login user and password i use on start up it doesnt work, where do i change these things?

thanks in advance

---

### Post by flavio newbie on 2007-10-20
i found out

sudo smbpasswd -a "username"

---

### Post by the_blur on 2007-10-27
Hey flavio, thanks man, that solved my problem too!

now I can see my 2 ubuntu boxes from my my windows lappy and my girlfriends' winxp/ubuntu dualboot! =)

This terminal thing may be a better deal than I thought =)

now if only wubi would work with 7.1 I wold be set on my lappy as well and all my non-work pc's would be running linux and the ones that dualboot, do so because I can't run flash native in linux, otherwise I wold be all linux all the time =)

---

### Post by razorbak on 2008-01-04
> **flavio newbie said:**
> i found out

sudo smbpasswd -a "username"

I tried this but get the message:

failed to modify password entry for user

What am I doing wrong?

---

### Post by jonandrews on 2008-01-06
Have a look at my step by step guide to Ubuntu / XP networking:

[www.europe.eclipse.co.uk/Ubuntu](www.europe.eclipse.co.uk/Ubuntu)

Hope that is helpful

---

### Post by vuygun on 2008-02-29
Hello, 
You should create first, your new user as an Ubuntu user. 

$ sudo useradd -d /home/username -m username

set password for Ubuntu system

$ sudo passwd username
 type : *****
retype : *****

then try again it is a samba user also,

$ sudo smbpasswd -a "username"
 type : *****
retype : *****

dont forget enable the new user

$ sudo smbpasswd -e "username"

good luck

---

