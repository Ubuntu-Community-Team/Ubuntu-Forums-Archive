---
title: "/etc/init.d/mysql"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by RobikShrestha on 2011-06-01
I accidentally deleted /etc/init.d/mysql file.
Now I cannot remove or reinstall mysql server 5.1
Could anyone send me that mysql file, so that I could copy it to the init.d directory

---

### Post by lombardoja on 2011-06-02
have you tried ```
apt-get --reinstall install mysql-server
```?

---

### Post by alphacrucis2 on 2011-06-02
If the above doesn't work then just create a dummy file. It could be that the package removal expects the file to exist but may not care what is in the file.

---

### Post by RobikShrestha on 2011-06-02
editted post: I have removed my mail id.

---

### Post by Laforge129 on 2011-06-02
> **RobikShrestha said:**
> It does not work. Could you mail me that file at [email]removed@removed.com[/email]. It would really helpful.

I see you don't care if you get spam?   That is the easiest way to get spam,  posting your email address on forums!!

---

### Post by RobikShrestha on 2011-06-02
I have suffered much more from that init.d thing. Please give me the file.

---

### Post by Laforge129 on 2011-06-02
> **RobikShrestha said:**
> I have suffered much more from that init.d thing. Please give me the file.

I don't have that installed on my system!   

Have you tried:
```
apt-get install -f mysql-server
```

I'm installing the server now to get the file!!

---

### Post by RobikShrestha on 2011-06-02
Well I do not think I actually repaired the situation but I at least got rid of the problem by removing everything related mysql from /var/lib/dpkg/info/

---

### Post by Laforge129 on 2011-06-02
> **RobikShrestha said:**
> Well I do not think I actually repaired the situation but I at least got rid of the problem by removing everything related mysql from /var/lib/dpkg/info/

Do you still need the file?

---

### Post by RobikShrestha on 2011-06-02
No, but thanks. I have xampp

---

### Post by Laforge129 on 2011-06-03
Don't forget to mark this thread as Solved!

---

### Post by RobikShrestha on 2011-06-03
ok Thanks

---

