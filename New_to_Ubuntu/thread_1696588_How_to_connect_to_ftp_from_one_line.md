---
title: "How to connect to ftp from one line?"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by kramer65 on 2011-02-27
Hello,

I want to setup some syncing using rsync with Grsync. In Grsync there is one line on which I can insert the local folder or a remote folder through ftp (see screenshot). The problem is that I don't know how to insert the info to log into the ftp correctly into that one line. I tried it (as you can see on the screenshot), but I don't know how to insert the password and the address in it since I've also got an '@' in my ftp username.

So lets say my info is like this:

username: [email]sync@mydomain.nl[/email]
password: syncftppassword
address: ftp.mydomain.nl
remote folder: /sync/Muziek

How would I insert this info in one line so that it correctly logs into my ftp account?

---

### Post by aktiwers on 2011-02-28
Normally you log into your domain directly by typing:
```

username:password@domain.nl 

```

I don't know how that works when you have a @ in the username - try it or maybe you could change your username?

---

### Post by TechWiz2100 on 2011-02-28
> **aktiwers said:**
> Normally you log into your domain directly by typing:
```

username:password@domain.nl 

```

I don't know how that works when you have a @ in the username - try it or maybe you could change your username?

You were correct initially, the domain is stuck to the end of the username to show server domain. Since he is connecting via FTP he can just set the port number or make it username: [email]password@ftp.mydomain.nl[/email]

If it is a case where the username does in fact require the @ then you can usually put it in single quotes like this
'username@mydomain.nl': [email]password@ftp.mydomain.nl[/email]

[edit] stupid smilies...

---

