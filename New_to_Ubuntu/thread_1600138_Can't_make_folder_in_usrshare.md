---
title: "Can't make folder in /usr/share/"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by brawd on 2010-10-18
Hi all,

I want to make a folder called pk2 in /usr/share, hence

sudo mdir /usr/share/pk2

I get a message back saying

Can't open /dev/fd0: No such device or address
Cannot initialize 'A:'

Now I'm not very good at command line stuff but I thought that might do it.

Can anyone let me know my mistake please?

regards,

OOps I did put my password in at the request for sudo.

---

### Post by marin123 on 2010-10-18
sudo mkdir /usr/share/pk2

its mkdir, not mdir...

you could try running (alt+f2) "gksu nautilus" and you can start nautilus (file browser) with root access...

---

### Post by JackNocturne on 2010-10-18
its mkdir

---

