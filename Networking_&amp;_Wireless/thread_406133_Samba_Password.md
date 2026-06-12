---
title: "Samba Password"
date: 2007-04-10
forum: Networking &amp; Wireless
---

### Post by dareofficer on 2007-04-10
Hello, started samba and can't figure out how to create, a name password to access it?

---

### Post by Tylo on 2007-04-10
Supposedly if you type:
> 
sudo adduser username          (Where username is the user you want to make)

and

> sudo smbpasswd -a username           (Where username is again the user you want to change the password of)

you can set the password there.

I've tried this, but it doesn't work for me. It might work for you.

---

### Post by dareofficer on 2007-04-10
Thanks, is worked like a charm!

---

### Post by Tylo on 2007-04-11
Hey, it finally ended up working for me too. I think my problem may have had something to do with my unix password and samba password being the same. I ended up just changing my samba password to something different, and it finally worked.

---

