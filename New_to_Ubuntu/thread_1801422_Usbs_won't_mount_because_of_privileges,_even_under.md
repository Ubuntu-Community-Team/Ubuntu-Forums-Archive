---
title: "Usbs won't mount because of privileges, even under root"
date: 2011-07-10
forum: New to Ubuntu
---

### Post by Mazehero55 on 2011-07-10
Ok so I was having some issues mounting my usb drives, so I reformat them and create entries for them in my fstab like this:
```

UUID=(blahblah) 	  /media/loki 	vfat 		rw,user,noauto,exec	  o	   o
UUID=(blahblah2) 	  /media/ohoh 	vfat 		rw,user,noauto,exec	  o	   o

```
Didn't feel like writing out the uuids.

Anyways now it says I dont have the privileges to mount which shouldn't be right since I have user as an option. But even more bizarre, it gives me same error even under root... Anyone have any ideas?

---

### Post by mikewhatever on 2011-07-10
Could it be because the zeros at the end are really small 'o's?

---

### Post by Mazehero55 on 2011-07-10
Oh sorry, making this post on my phone, they're actually 0's.  Lol
But I think i've solved it, I guess. Just deleted the entries and rm .Hal* inside /media,  now not getting any errors.  Don't know what those hidden files were for, but everything is working fine now

---

