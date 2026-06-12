---
title: "Im having a hard time getting files off my linux machine to windows."
date: 2008-04-23
forum: Networking &amp; Wireless
---

### Post by Stickey1123 on 2008-04-23
I have a laptop and PC running ubuntu and 2 windows machines. I can get files off my windows mach. but when I try to get files off of ubuntu it ask for a username and password, in which I tried my linux login which didnt work. How would I go about changing the username PW or even finding out what it would be.

---

### Post by Monicker on 2008-04-23
> **Stickey1123 said:**
> I have a laptop and PC running ubuntu and 2 windows machines. I can get files off my windows mach. but when I try to get files off of ubuntu it ask for a username and password, in which I tried my linux login which didnt work. How would I go about changing the username PW or even finding out what it would be.

You have to configure the users and passwords for authentication.

Try this guide:  [http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-samba-server-on-ubuntu/")

---

### Post by Stickey1123 on 2008-04-23
It let me install it but it wont let me configure it. I put in the command and it said comman not found

---

### Post by Monicker on 2008-04-23
> **Stickey1123 said:**
> It let me install it but it wont let me configure it. I put in the command and it said comman not found

Eh?  You tried what command, which resulted in exactly what error?

---

### Post by dmizer on 2008-04-23
this is a very very common problem.

there could be multiple causes, first is that your ubuntu username is not added in the samba group.  that may sound like greek, but the fix is simple.  just perform the following in the terminal:
```
sudo smbpasswd -L -a [COLOR="Red"]ubuntu_username
[/COLOR]sudo smbpasswd -L -e [COLOR="Red"]ubuntu_username[/COLOR]
```
replace [COLOR="Red"]ubuntu_username[/COLOR] with your actual ubuntu user name

the other common cause for this problem occurs because of firewalls.  if you've installed firestarter on your ubuntu machine, you will run into this problem unless you configure the ports correctly.

---

