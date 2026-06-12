---
title: "mounting a windows network drive"
date: 2008-09-17
forum: Networking &amp; Wireless
---

### Post by brnetonboy on 2008-09-17
I have been searching google and these forums for hours, but i can't find what I need.

Basically I want to write a script to automatically back up a windows folder on my linux computer. 

Ubuntu can see the windows folder I want, Nautilus tells me it is here:

```
smb://scythe/mydata/
```

But I am unable to use that as a location in the shell. I tried this:
```
cp smb://scythe/mydata/ /usr/home/brenton/backupdata
```

but i think it wants me to mount the network drive first. 

how do i mount the drive so that the shell can talk to it?

---

### Post by ethan961 on 2008-09-17
Press alt-f4

---

### Post by brnetonboy on 2008-09-17
> **ethan961 said:**
> Press alt-f4

that closes a window in windows... what does it do in linux?

---

### Post by dmizer on 2008-09-17
> **brnetonboy said:**
> how do i mount the drive so that the shell can talk to it?

Please see the second link in my sig.

---

### Post by Joeb454 on 2008-09-17
> **ethan961 said:**
> Press alt-f4

> **brnetonboy said:**
> that closes a window in windows... what does it do in linux?

It does exactly the same

---

