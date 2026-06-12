---
title: "Basic Samba Server"
date: 2009-05-25
forum: New to Ubuntu
---

### Post by fattymatty on 2009-05-25
So today i setup one of my pc's to be a samba server, installed 9.04 64bit server edition. then setup my networking and host files.

after that was done i setup my samba server.

which at the moment is working in that it shows up on my other pc in the network field but i can get into it. when i double click it it says "\\SERVER1\media is not accessible. You might not have permision to access this network resource...
" but i have set this up to that the samba server was public so it didnt need any user name although i did make 2 usernames to see if that worked but when trying to login it comes up that they are invalid on my vista pc


here is my smb.conf

[Global]
workgroup = MSHOME
security = share

[Media]
path = media/store
browseable = yes
guest = ok

---

### Post by ddnev45 on 2009-05-25
I usually have to use:

```
security=user
```

and then set up a samba user account.

[Samba server howto]("http://ubuntuforums.org/showthread.php?t=202605&highlight=samba")

---

### Post by Celauran on 2009-05-25
> **fattymatty said:**
> ```

[Media]
path = media/store
browseable = yes
guest = ok
```
I've only ever seen path as absolute. Try changing it to path = /media/store and see if that helps.

---

