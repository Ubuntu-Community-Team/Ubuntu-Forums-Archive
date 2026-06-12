---
title: "Add a user to Ubuntu server"
date: 2011-01-16
forum: New to Ubuntu
---

### Post by mikeybinec on 2011-01-16
I tried useradd and the message get is:
 
useradd: cannot lock /etc/passwd; try again later
 
What am I doing wrong?
 
Thanks

---

### Post by v1ad on 2011-01-16
sudo useradd <username>
sudo passwd <username>

man useradd -will tell u all about useradd and how to use it. if you r not root u will need to use sudo.

---

### Post by mikeybinec on 2011-01-17
> **v1ad said:**
> sudo useradd <username>
sudo passwd <username>

man useradd -will tell u all about useradd and how to use it. if you r not root u will need to use sudo.

I'll try it..I am the root. I just installed the server edition on saturday. I want to get a backup root or something in case the original  gets hosed.  I need a book.

---

### Post by Crusty Old Fart on 2011-01-17
> **mikeybinec said:**
> I'll try it..I am the root. I just installed the server edition on saturday. I want to get a backup root or something in case the original  gets hosed.  I need a book.
The book: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

---

### Post by mikeybinec on 2011-01-17
thanks for book suggestion..Now why do you think I can't add a user even though I am the root?

---

### Post by bodhi.zazen on 2011-01-17
> **mikeybinec said:**
> I'll try it..I am the root. I just installed the server edition on saturday. I want to get a backup root or something in case the original  gets hosed.  I need a book.

[https://help.ubuntu.com/10.04/serverguide/C/index.html](https://help.ubuntu.com/10.04/serverguide/C/index.html)

[https://help.ubuntu.com/community/Servers](https://help.ubuntu.com/community/Servers)

---

### Post by Crusty Old Fart on 2011-01-17
> **mikeybinec said:**
> thanks for book suggestion..Now why do you think I can't add a user even though I am the root?Now that right there is a damned good question.

I think I ran into something like this a long time ago. It seems to suggest that maybe the password for the root account was never set. Try this:
```

sudo passwd

```Just taking a shot in the dark here. It may be a stupid suggestion, but so far, nobody seems to be coming up with anything.

Hope it works.

---

### Post by CharlesA on 2011-01-17
The root account isn't enabled by default on Ubuntu. You use *sudo* to run commands that need root permissions.

---

### Post by mikeybinec on 2011-01-17
Ok, now we're getting somewhere... So going with V1ad's suggestion
 
sudo useradd *new_username *passwd *blahblahblah*
 
I can create joeblow, but joeblow still has'nt got a login password for some reason..(well the systme won't let him in)
 
What is correct command syntax to add a user?
 
And still wanting to know what this means: 
 
useradd: cannot lock /etc/passwd; try again later
 
thanks!!

---

### Post by CharlesA on 2011-01-17
You need to be root to add users.

That is why you use sudo.

You need to set their password like so:

```
sudo passwd username
```

---

### Post by mikeybinec on 2011-01-17
so sudo su - will make me the root.  got it and thanks

---

### Post by bodhi.zazen on 2011-01-17
> **mikeybinec said:**
> so sudo su - will make me the root.  got it and thanks

I will, but the preferrred method is:

```
sudo -i
```

---

### Post by v1ad on 2011-01-18
marked solved once everything works. under thread tools.

---

