---
title: "Can not run xara extreme"
date: 2008-12-16
forum: New to Ubuntu
---

### Post by gackt on 2008-12-16
hi all, 

When i start the xara extreme, the system give me this error "Lock file '/home/ubuntu/.XARA-XTREME-WX-xaralx-ubuntu' has incorrect permissions."
Any idea? 

Thanks

---

### Post by Michael.Godawski on 2008-12-16
hi gackt, 
let's check the permissions set to the  '/home/ubuntu/.XARA-XTREME-WX-xaralx-ubuntu folder or file.
```
cd /home/ubuntu
ls -la
```
Basically navigate to the directory with the file or folder at hand and run the second command.
Please post output here.

---

### Post by gackt on 2008-12-16
Thank for the quick reply, here is the result ( i'm not copying the whole part, if that is okay):

drwxr-xr-x  4 ubuntu ubuntu     4096 2008-12-16 10:54 .wine
drwxr-xr-x  5 ubuntu ubuntu     4096 2008-11-24 14:41 .winetrickscache
drwxr-xr-x  2 ubuntu ubuntu     4096 2008-11-24 22:49 .xaralx
drwxr-xr-x  2 ubuntu ubuntu     4096 2008-11-24 22:49 .XaraLXFilters
-rwx------  1 ubuntu ubuntu        6 2008-11-24 22:49 .XARA-XTREME-WX-xaralx-ubuntu
-rw-------  1 ubuntu root             120 2008-12-16 08:54 .Xauthority

The wierd thing (wierd because i'm new) is if i hit the ctrl+h i still cannot see the .xara-xtreme-wx-xaralx-ubuntu folder.

Thanks

---

### Post by Michael.Godawski on 2008-12-16
hm 
guessing now, so be cautious :p

```
chmod a+x /home/ubuntu/.XARA-XTREME-WX-xaralx-ubuntu
```and try again to run the app.

---

### Post by gackt on 2008-12-16
Aha! No luck :( Any other ideas?

---

### Post by greedohun on 2009-05-03
I had the same problem and installed "imagemagick" in synaptic. It still gives the error message but at least it starts and works.

---

### Post by conorsulli on 2010-02-18
bump

---

