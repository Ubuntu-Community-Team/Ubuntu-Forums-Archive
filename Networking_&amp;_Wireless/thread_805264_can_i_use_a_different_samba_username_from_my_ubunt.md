---
title: "can i use a different samba username from my ubuntu username?"
date: 2008-05-23
forum: Networking &amp; Wireless
---

### Post by dupersuper on 2008-05-23
lets say my ubuntu username is "john"
but the username used on the windows network is "johndoe"
is there a way for me to access my samba shares?
thanks for any help!
:)

---

### Post by superprash2003 on 2008-05-23
you want to use the username "johndoe" in your samba shares? so that people from windows machines use the "johndoe" account to access your shares?

---

### Post by gkffjcs on 2008-05-23
The answer is Yes! But this can be challenging. The way that samba/cifs(common internet file system the windows name for samba) works is that when a client tries to access a samba share the client (in your case your windows computer) tries to access the samba server (your ubuntu computer) it (your windows box) tells the server the username and password of the user that is currently logged into window. If you have set security = user in the [global] section of your /etc/samba/smb.conf then it won't matter what the user name is. However it is not the best idea to set security = share so keep it user. By default if the windows box tries to connect to the samba share and the password/username are not correct the windows computer will just ask you for the right user name and password. This should work. One little extra that took me a long time to figure out is that with the setting security = user what ever username you give the prompt must exist as a user on the computer that the server is on. But more importantly, and here is the trick to remember, even if john has a username and password on the ubuntu computer they don't have a username in the samba server. For this you need to run sudo smbpasswd -a username before john will be able to login to the server from a remote computer. Also when running sudo smbpasswd -a username username must allready exist as a valid user on the system. 
Hope this all helped!

---

### Post by Iowan on 2008-05-24
Samba has (or had) a **username map=** parameter that lets you convert from Windows usernames to Unix usernames.

---

### Post by dupersuper on 2008-05-24
thanks guys for the replies :guitar:

turns out it was a undue worry.:lolflag:
when i accessed the shared drive on the vista pc, nautilus prompted for the username and p/w to be used (which could be different from the ubuntu username and p/w)

---

