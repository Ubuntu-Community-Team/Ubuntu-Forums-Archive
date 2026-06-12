---
title: "Intrepid Workgroup"
date: 2008-10-29
forum: Networking &amp; Wireless
---

### Post by briansvgs on 2008-10-29
I recently upgraded to intrepid. Looking around, I don't see an easy way to configure the workgroup of your computer anymore like there was in Hardy. Has this gui dissapeared in intrepid? I have noticed that the network management program that used to be used to do this has been replaced by network manager, and while definitely a better system, I can not find this feature. Am I missing something?

---

### Post by cariboo on 2008-10-30
There are two ways to change it. Open a terminal and type:

```
gconf-editor
```

then go to System-->Smb and change the workgroup there, or install samba and change it in smb.conf.

Jim

---

