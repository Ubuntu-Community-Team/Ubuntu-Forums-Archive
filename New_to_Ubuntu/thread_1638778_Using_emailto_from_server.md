---
title: "Using emailto from server"
date: 2010-12-06
forum: New to Ubuntu
---

### Post by Drenriza on 2010-12-06
Hi all.

I have a small question. How do i get emailto to mail to two e-mail addresses by the following commands
```

name="name"
emailto="e-mail"
cat /path | /usr/bin/mail -s "$name $emailto
```

Thanks on advance.
Kind Regards

---

### Post by Born-Thirsty on 2010-12-06
A good thing to try and use are the manual pages for processes.
eg. man mail

It will tell you there that you can append a list of email addresses using the argument '-t' followed by the list. I am uncertain about whether it is a comma separated list or space separated. But I hope this at least helps you get started.

---

### Post by Drenriza on 2010-12-06
The man page, from what i can see.
Is not that useful regarding this matter. Maybe it is my version of the man page, but cannot find much about how to send a e-mail to two different e-mail addresses.

---

### Post by Drenriza on 2010-12-07
Is their no one who can help me?

---

### Post by Drenriza on 2010-12-10
isint it possible in a single line to put someone as e-mail address and one as cc?

---

