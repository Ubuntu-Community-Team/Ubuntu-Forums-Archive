---
title: "[SOLVED] Share folder on a mounted Fat32 partition"
date: 2008-09-28
forum: Networking &amp; Wireless
---

### Post by xchronox on 2008-09-28
I've been trying to accomplish this for quite sometime. I have a Fat32 partition set up with my music in it so I can access it from both windows and linux.

That's all fine and dandy, but I want it so well I'm in linux I can share that partition over the network and have my laptop access all the music in it.

I am able to view the share folder, but when i try to access it, after I enter the user name and password, it comes up with 

```
Failed to mount Windows share
```

I have another folder on the local linux ext3 partition that seemingly works fine... So I'm stumped. 

Any help or suggestions will be greatly appreciated :)

---

### Post by xchronox on 2008-09-29
Bump, this has really stumped me

---

### Post by xchronox on 2008-10-31
So I solved it myself, it was just a matter of providing permission for samba to access the partition. It prompts for it and should give you the code.

---

