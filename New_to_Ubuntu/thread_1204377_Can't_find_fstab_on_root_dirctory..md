---
title: "Can't find /fstab on root dirctory."
date: 2009-07-04
forum: New to Ubuntu
---

### Post by falsepride on 2009-07-04
Hi all, ):P

I'm a perfectly raw newbie to Ubunu 8.1 Intrepd and to this forum bare with me please.
Question. How can I access fstab or mtab files when my root directory doesn't recognize them or either I get an access denied from my terminal using sudo.
I need to mount my CD/DVDs and can't mount them because they're not found in these files.  Can someone help! TNX much 8-[

---

### Post by wojox on 2009-07-04
Try 

```
/etc/fstab
```

---

### Post by The Cog on 2009-07-04
The file is /etc/mtab, as wojox said.

You should be able to mount CDs from the menu Places->Computer and the CD icon. I really don't think removable media should belong in /etc/fstab.

---

### Post by Michael.Godawski on 2009-07-04
> **falsepride said:**
> Hi all, ):P

I'm a perfectly raw newbie to Ubunu 8.1 Intrepd and to this forum bare with me please.
Question. How can I access fstab or mtab files when my root directory doesn't recognize them or either I get an access denied from my terminal using sudo.
I need to mount my CD/DVDs and can't mount them because they're not found in these files.  Can someone help! TNX much 8-[

What do you mean by "my root directory doesn't recognize them"?

What happens if you run 
```
cat /etc/fstab
```
or
```
gksudo gedit /etc/fstab
```

---

