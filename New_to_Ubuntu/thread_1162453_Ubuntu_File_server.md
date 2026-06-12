---
title: "Ubuntu File server"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by raygo22 on 2009-05-17
Hello. I am new to the linux world. What I want to do is a file server. I want people using windows, macos and linux to be able to login in some way to the file server and for them to be able to see a folder where they can put their files. I dont want them to be able to see any folder except for the one that they are authorized to see. How can I do that? thanks!

---

### Post by Ropetin on 2009-05-17
> **raygo22 said:**
> Hello. I am new to the linux world. What I want to do is a file server. I want people using windows, macos and linux to be able to login in some way to the file server and for them to be able to see a folder where they can put their files. I dont want them to be able to see any folder except for the one that they are authorized to see. How can I do that? thanks!

The following tutorial might point you in the right direction;

[http://www.howtoforge.com/ubuntu-home-fileserver]("http://www.howtoforge.com/ubuntu-home-fileserver")

---

### Post by raygo22 on 2009-05-17
This one is without authorization. How can I do it with authorization? and also, I already have ubuntu desktop version installed (9.4) Thanks!

---

### Post by pulpinator on 2009-05-17
You'll want to change the smb.conf file to set per-user authorization for each directory. 

Take a look at the Samba documentation:

[http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/](http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/)

---

### Post by pulpinator on 2009-05-18
I realize my previous answer was probably a little vague (there's a lot of documentation!).

I'm not sure how you want to secure your install (restrict to subnet, allow all connections and only user login?).

This chapter has more information on how to do that:

[http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html](http://us6.samba.org/samba/docs/man/Samba-HOWTO-Collection/securing-samba.html)

Also, remember to run

```
root# testparm /etc/samba/smd.conf
```

when you make any changes. It will test the config file to see if you made any syntax errors, etc.

---

