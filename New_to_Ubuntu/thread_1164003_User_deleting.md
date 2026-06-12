---
title: "User deleting"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by Brasker on 2009-05-19
Hey, I created a user using the useradd command, and then deleted using the - System - Administration - Users and Groups delete option, and when I try to re-add the same user (it's pertinent that the user name be mobility) it says the user already exists. Can someone tell me how I should go about fixing this please?

---

### Post by unutbu on 2009-05-19
```
sudo userdel -r mobility
```
will remove /home/mobility and /var/mail/mobility directories and remove mobility from /etc/passwd, /etc/group.

---

### Post by Brasker on 2009-05-19
It says the same thing the application says, and I still cannot add a user called mobility 
```
craig@Robot:~$ sudo userdel -r mobility
[sudo] password for *****: 
userdel: user mobility does not exist

```

---

### Post by unutbu on 2009-05-19
What output do you get from:
```
sudo useradd --create-home --shell /bin/bash mobility
```

---

### Post by Brasker on 2009-05-19
My output is:
```
craig@Robot:~$ sudo useradd --create-home --shell /bin/bash mobility
useradd: group mobility exists - if you want to add this user to that group, use -g.

```

EDIT: I'm unsure of how to use the -g thing, I tried and I appear to be doing something incorrect.

---

### Post by unutbu on 2009-05-19
Try: ```
sudo groupdel mobility
```
This should remove mobility from /etc/group.
If that does not solve the problem, please post the output of 
```

grep mobility /etc/passwd
grep mobility /etc/group
```

---

### Post by Brasker on 2009-05-19
It worked, thank you very much!

---

