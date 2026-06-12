---
title: "Message after login"
date: 2010-09-25
forum: New to Ubuntu
---

### Post by sudeepk on 2010-09-25
How can I display a message like say "Welcome user" when a user is logged in through the terminal. I need the message to be on terminal.

---

### Post by adit on 2010-09-25
```
gedit ~/.bash_profile
```
Add the following line at the end of the file:

echo "Welcome $USER"

---

### Post by sudeepk on 2010-09-25
Thanks a lot. Its working

---

