---
title: "How to use smbpasswd in silent mode?"
date: 2011-08-08
forum: New to Ubuntu
---

### Post by Guruprasad on 2011-08-08
I want to modify samba password of user USER1 using -s option. i.e. I do not want to enter old password, new password, rewrite new password separately. Every thing should go in a single line command.

---

### Post by Guruprasad on 2011-08-08
Yes.. Got it..

> (echo "Old Password"; echo "New Password"; echo "New Password") | smbpasswd -s -U User1

---

