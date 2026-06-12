---
title: "hey , iso"
date: 2009-11-12
forum: New to Ubuntu
---

### Post by Wraith619 on 2009-11-12
so hey guys i just registered , ubuntu rocks , i am a 9.04 "Jaunty Jacklope" user , makes microsuck's windows look %@%@#%!!!!!
so okay , here is a problem that happens with me , whenever is mount iso files with archive mounter , they appear and everything , but when i enter the mounted disc , it's completely empty

????

THX In advance.

---

### Post by bawilson2 on 2009-11-12
I think you need to use something like Gmount-iso to be able to use the iso as a virtual disk.  Give it a try.

---

### Post by cariboo on 2009-11-12
You can also mount the iso manually in the terminal:

```
sudo mount -o loop <name_of_iso> /mnt
```

Then just open /mnt in the file browser.

---

### Post by Wraith619 on 2009-11-12
> **bawilson2 said:**
> I think you need to use something like Gmount-iso to be able to use the iso as a virtual disk.  Give it a try.
tried that today , and cariboo , i can already mount them , the problem is that when i open the virtual drive , there is nothing inside , not even if u push Crtl + H.

---

