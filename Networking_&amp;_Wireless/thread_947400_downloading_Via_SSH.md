---
title: "downloading Via SSH"
date: 2008-10-14
forum: Networking &amp; Wireless
---

### Post by Tobywuk on 2008-10-14
i have installed openSSH server on my ubuntu system and i can ssh into it remotely from my Macintosh laptop.

Once im logged in via ssh how do i download files from the remote ubuntu box to my local computer (Macintosh)? 

thanks. :)

---

### Post by rickh57 on 2008-10-14
If you have ssh access, you should be able to use [scp]("http://en.wikipedia.org/wiki/Secure_copy") to copy files to/from the server.

---

### Post by macness on 2008-10-14
All you need is to use the scp command from your Mac (no need to SSH first)

To get files from the Ubuntu to the Mac
```
scp user@server:file1 user@macintosh:somedir 
```

To get files from the Mac to Ubuntu
```
scp /dir/file.txt user@server:somedir
```

---

