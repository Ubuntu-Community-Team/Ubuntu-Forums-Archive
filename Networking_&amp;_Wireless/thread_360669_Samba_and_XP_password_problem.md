---
title: "Samba and XP password problem"
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by Jontydog on 2007-02-13
I have a network of 4 pcs in the house.  1 is Ubuntu dapper drake the other 3 are Winbloze XP.  I have set a shared folder on the linux pc and the linux pc shows up on the network fine.  I can browse the other 3 computers fine all is well that way.  When in XP I try and add a network place I am being asked for a password even though I haven't set one.  I have tried the password and username I use to log into linux but that is rejected and the root details which are also rejected.  Anyone shed any light on what I am doing wrong?

---

### Post by vdp09 on 2007-02-13
I had the same problem.

By default Samba uses some password. You can change it by using "sudo smbpasswd" 

Hope it helps!

---

### Post by dannyboy79 on 2007-02-13
um, from my experience with samba, there is no default password. you have to add a user to the samba password database. this is done with these commands

sudo smbpasswd -a username (note: username is the username you want to use to log into your ubuntu box over the network. this user has to already be a user on your ubuntu box)

it will ask you for a password twice.

then enable that account

sudo smbpasswd -e username

you can read all about it here: [http://manticore.2y.net/doc/SWAT/help/smbpasswd.8.html](http://manticore.2y.net/doc/SWAT/help/smbpasswd.8.html)

good luck

---

### Post by Jontydog on 2007-02-16
thanks for the info you 2 managed to get it working with a lot of help from those posts and a lot of messing about running from room to room logging in and out :D

---

### Post by dannyboy79 on 2007-02-16
i can' t tell, are you asking me a question or did you mean to put that "YOU" got it working???? if you're asking me i ran from room to room to figure out how to get samba running than no, I didn't cause I just used ssh to ssh into my box and turn samba on and off and I also used my xbox, so I was able to do it all from my laptop.

---

