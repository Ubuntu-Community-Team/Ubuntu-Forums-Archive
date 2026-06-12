---
title: "List of Users in uBuntu using Terminal?"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by raziiq on 2009-05-18
Hi there.

Is there any command in Terminal that can give me a list of users available on my computer with details like Account type root or standard user etc?

---

### Post by alphacrucis2 on 2009-05-18
> **raziiq said:**
> Hi there.

Is there any command in Terminal that can give me a list of users available on my computer with details like Account type root or standard user etc?

```
cat /etc/passwd
```

Will list all accounts including system ones. You would have to filter the output to get just normal users.

---

### Post by raziiq on 2009-05-18
oh thanks for the help, i ll check it.

BTW how to filter the output? i m sorry i m very new to Linux

---

### Post by alphacrucis2 on 2009-05-18
> **raziiq said:**
> oh thanks for the help, i ll check it.

BTW how to filter the output? i m sorry i m very new to Linux


A simple way is to feed the output of cat into another program called grep which can filter based on a parameter. For example:

```
cat /etc/passwd | grep /home
```

Will take the output from the cat command (cat just lists the contents of the specified file) and feed it into grep. The /home tells grep to drop any lines that do not contain the the text /home. That means that it will list users that have a home directory under /home specified in the passwd file.

---

### Post by raziiq on 2009-05-18
thanks for the help, i ll check this command and let you know if i have any problems. thanks :)

---

### Post by imgod22222 on 2010-05-21
cat /etc/passwd | cut -f1 -d':' | sort

if you want to put it in a file in your present working directory (pwd):

cat /etc/passwd | cut -f1 -d':' | sort > filename

---

