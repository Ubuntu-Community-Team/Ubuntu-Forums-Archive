---
title: "problems with chsh"
date: 2009-10-26
forum: New to Ubuntu
---

### Post by allegroyell on 2009-10-26
HI everybody, 

I did sth very stupid, mybe sb know what to do, then

1. I typed as root chsh
2. pressed <q> and <Enter>
3. typed exit
now when trying to login as root it tells that no such directory like q
what to do to have root account working again

thanks.

---

### Post by alphaniner on 2009-10-26
What is the output of

```
sudo cat /etc/passwd | grep root
```

---

### Post by allegroyell on 2009-10-26
krzysiek@krzysiek:~$ sudo cat /etc/passwd | grep root

We trust you have received the usual lecture from the local System
Administrator. It usually boils down to these three things:

    #1) Respect the privacy of others.
    #2) Think before you type.
    #3) With great power comes great responsibility.

[sudo] password for krzysiek: 
krzysiek is not in the sudoers file.  This incident will be reported.

---

### Post by allegroyell on 2009-10-26
krzysiek@krzysiek:~$ cat /etc/passwd |grep root
root:x:0:0:root:/home/root:q

---

### Post by alphaniner on 2009-10-26
Edit:  Maybe that's not the way to go.  There's also a file /etc/passwd- and I'm not sure what the difference is.  Best wait for some more experienced advisors.

[SIZE="1"]OK.

Open /etc/passwd for editing such as with

```
sudo nano /etc/passwd
```

and change

```
root:x:0:0:root:/root:q
```

to

```
root:x:0:0:root:/root:/bin/bash
```[/SIZE]

---

### Post by allegroyell on 2009-10-26
is any option to edit this q for /bin/bash?

---

### Post by allegroyell on 2009-10-26
yes but cant do it as current user and root is blocked, have any suggestion every welcome

---

### Post by alphaniner on 2009-10-26
I realize that now.  The only thing I can think of is to boot into a Live CD.

---

### Post by lavinog on 2009-10-26
live cd

---

### Post by alphaniner on 2009-10-26
Just realized this is a textbook example of why to use sudo instead of logging on as root. ;)

---

### Post by allegroyell on 2009-10-26
so, on cd is sth to recover from that, ok ill check it
or U told about reinstalling the system?

---

### Post by allegroyell on 2009-10-26
so U told about reistalling or some kind of recovery mode od the boot cd?

---

### Post by allegroyell on 2009-10-26
so reinstal the system u suggest, or recovery mode ? is there anything like this?

---

### Post by allegroyell on 2009-10-26
s

---

### Post by lavinog on 2009-10-26
use the live cd to edit /etc/passwd
keep in mind that the /etc/password would most likely be /media/disk/etc/passwd
(you need to mount the hd first)

---

