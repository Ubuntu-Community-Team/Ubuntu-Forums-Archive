---
title: "How to delete ufw rule"
date: 2010-10-12
forum: New to Ubuntu
---

### Post by karthick87 on 2010-10-12
I have checked my ufw status,it shows the following...
```

karthick@Ubuntu-desktop:~$ sudo ufw status
Status: active

To                         Action      From
--                         ------      ----
80/tcp                     DENY        Anywhere
```

What does it mean..?How to delete the above rule..?

---

### Post by andrewthomas on 2010-10-12
```
sudo ufw  delete 1
```

The rule is denying new (not established from your machine) connections to your machine.  

This should not prevent you from using the internet.

---

### Post by karthick87 on 2010-10-12
Thankyou :)

---

### Post by andrewthomas on 2010-10-12
Glad to be of help.

---

