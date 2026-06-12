---
title: "Superuser privalege"
date: 2009-04-09
forum: New to Ubuntu
---

### Post by PGrey on 2009-04-09
Ho do I get superuser privalege in the terminal. I am doing pkg--configure -a and it wont let me because of it.

---

### Post by abn91c on 2009-04-09
**sudo** dpkg --configure -a

---

### Post by drs305 on 2009-04-09
When it asks for your password with the above command, type your logon password. You won't see anything as you type - it's a security feature. Just type it out and hit ENTER when you are done.

Here's a link about running sudo - just general information:
[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

