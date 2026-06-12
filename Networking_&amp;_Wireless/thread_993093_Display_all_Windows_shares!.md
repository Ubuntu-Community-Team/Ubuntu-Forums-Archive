---
title: "Display all Windows shares!"
date: 2008-11-25
forum: Networking &amp; Wireless
---

### Post by HishamN on 2008-11-25
Hi

If I tried to mount windows shares via samba I have to specify the folder name!
Can I display all windows share without specify the folder name?

Regards

---

### Post by eder.apt-get on 2008-11-25
I used to edit smb.conf and add the folder in there, and it would never ask me again for the name. Is that what you mean?

---

### Post by pennacook on 2008-11-25
I'd typically do the following:
```
smbclient -L <windows server>
```

---

### Post by HishamN on 2008-11-26
eder.apt-get

I can bookmark it, but sometime my colleuage give me his ip only without share name because in windows when you type at commaned prombt //servername it give you all shares folder.

---

pennacook

Thanks for the command, that what I needed but can I do it on GUI using "connect to remote computer or shared disk"?

Thanks guys

---

### Post by bab1 on 2008-11-26
You can list all the shares available from the command line. Use:```
smbtree
```

---

### Post by HishamN on 2008-11-26
bab1 tthanks for reply, it's great command :)

---

