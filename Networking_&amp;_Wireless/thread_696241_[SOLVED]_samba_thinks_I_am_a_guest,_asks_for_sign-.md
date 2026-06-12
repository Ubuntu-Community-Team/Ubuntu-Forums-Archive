---
title: "[SOLVED] samba thinks I am a guest, asks for sign-in"
date: 2008-02-13
forum: Networking &amp; Wireless
---

### Post by mandrill on 2008-02-13
Click network shares on Ubuntu, asks for guest password. Can access from xp no problem.
I am not guest, I am owner. Can access xp shares from Ubuntu no problem. How do I fix this?

---

### Post by Iowan on 2008-02-13
I just tried my server and got the same thing... I discovered that if I manually entered the username, password, and workgroup, it let me connect.  After that, it doesn't even ask (probably will tomorrow...).

---

### Post by mandrill on 2008-02-13
> **mandrill said:**
> Click network shares on Ubuntu, asks for guest password. Can access from xp no problem.
I am not guest, I am owner. Can access xp shares from Ubuntu no problem. How do I fix this?

bump

---

### Post by Iowan on 2008-02-14
I notice your problem is solved - what did you find to fix it (or did it just start working - like mine did ;) )?

---

### Post by mandrill on 2008-02-14
sudo smbpasswd -a username

sudo smbpasswd -a root

just turned machine on - still asking me to sign on as guest......

---

### Post by mandrill on 2008-02-14
bump

---

### Post by mandrill on 2008-02-14
Now samba says cannot find share, may have been deleted?

---

### Post by mandrill on 2008-02-14
> **mandrill said:**
> Now samba says cannot find share, may have been deleted?

bump

---

