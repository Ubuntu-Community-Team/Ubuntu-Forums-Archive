---
title: "Root???"
date: 2010-07-12
forum: New to Ubuntu
---

### Post by sagmate on 2010-07-12
I am trying to enter root on the command-line under my other user and I've tried sudo root, sudo bash, and su and neither is working and its giving me a message saying I'm not in the sudoers file. I tried changing the properties for my groups but nothing seems to be working...does anyone have any suggestions???

---

### Post by Crunchy the Headcrab on 2010-07-12
Edit: if you're not in the sudoers file, sign back into your other acct and and yourself to it.  
vi sudoers 
or
nano /etc/sudoers

---

### Post by RiceMonster on 2010-07-12
The root account is locked on Ubuntu by default. To get root privilages, you must run commands with sudo, however I wouldn't say running "sudo bash" is a good idea.

As for the error about not being in the sudoers file, you must add yourself to the admin group to run sudo commands.

---

### Post by ibuclaw on 2010-07-12
Two things to note.

1) You need to be part of the admin group
2) If you change / assign / remove groups, you need to logout/login before it will take effect.



If you think you've got a groups problem, post the output of:
```
groups
```

---

### Post by RiceMonster on 2010-07-12
> **Crunchy the Headcrab said:**
> vi sudoers 
or
nano /etc/sudoers

Bad idea. You should edit /etc/sudoers with visudo so it will warn you if you make a change that can break something.
You can even do it with nano if you'd like:
```
EDITOR=nano visudo
```

---

### Post by Crunchy the Headcrab on 2010-07-12
> **RiceMonster said:**
> Bad idea. You should edit /etc/sudoers with visudo so it will warn you if you make a change that can break something.
You can even do it with nano if you'd like:
```
EDITOR=nano visudo
```
Nice! You're right of course.

Also, I knew about visudo but not that you could use nano to do it :)

---

### Post by sagmate on 2010-07-12
Okay so I tried adding myself to the admin group and a message pops up saying:

The configuration cannot be saved
An unknown error occurred

---

### Post by blur xc on 2010-07-12
you probaly need to boot into recovey mode to get root access to edit those files.

Think about it- if you are not a sudoer  on your system, how are you going to edit files that you need root privelages for?

BM

---

### Post by philinux on 2010-07-12
> **sagmate said:**
> I am trying to enter root on the command-line under my other user and I've tried sudo root, sudo bash, and su and neither is working and its giving me a message saying I'm not in the sudoers file. I tried changing the properties for my groups but nothing seems to be working...does anyone have any suggestions???

[http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

---

