---
title: "[SOLVED] How to see users"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by jspolen on 2008-12-12
Simple problem I guess but how can I as root see what users are created, in a terminal without looking in the /etc/passwd file?

---

### Post by kpkeerthi on 2008-12-12
```
ls -ld /home
```
???

---

### Post by jspolen on 2008-12-12
Well the users I created does not have their own folder

---

### Post by Mucho on 2008-12-12
you can see users on file /etc/group

$view /etc/group 

your users will be below groups

---

### Post by Sarmacid on 2008-12-12
It's almost the same as looking at the passwd file, but you can look at the /etc/shadow file.

---

### Post by jspolen on 2008-12-12
Yeah I know, that's where the passwords are located. But I was wondering if there is a command of some sort to list the users. like showusers or something.

---

### Post by spikoley on 2008-12-12
I don't think this is exactly what you are looking for, but these commands show logged in users.  It sounds like you are just looking for users on the system.

```
w
```
```
who
```
```
finger
```

---

### Post by bluefrog on 2008-12-12
make your own command.

vi showusers.sh
  #!/bin/bash
for i in $(awk 'BEGIN{FS=":"} {if ($3 >= 1000) print $1}' /etc/passwd ); do echo $i; done

chmod u+x showusers.sh
./showusers.sh

you could link it as well into /sbin

sudo ln -s ~/showusers.sh /sbin/showusers

then showusers command is available

---

### Post by jspolen on 2008-12-12
Oh nice idea. Will do that imediatly thanks!

---

