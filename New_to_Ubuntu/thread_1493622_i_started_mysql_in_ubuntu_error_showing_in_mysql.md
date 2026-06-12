---
title: "i started mysql in ubuntu error showing in mysql"
date: 2010-05-26
forum: New to Ubuntu
---

### Post by kiranpulsar2007 on 2010-05-26
i started mysql in ubuntu

sudo /etc/init.d/mysql start

later after entering the password it showing 

[sudo] password for pa1: 
pa1 is not in the sudoers file.  This incident will be reported.


whats this mean how can i overcome this ?

please suggest me 

thank u

---

### Post by cariboo on 2010-05-26
Is user pa1 a member of the admin group? to check login as that user , open a terminal and type:

```
groups
```

you should see something like this:

```
groups
me adm dialout cdrom plugdev lpadmin admin sambashare
```

If pa1 isn't a member of the admin group add  him using the following command:

```
sudo gpasswd -a admin pa1
```

---

