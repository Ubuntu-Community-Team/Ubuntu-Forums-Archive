---
title: "How do I make a slave HDD show up on Computer?"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by mattbutsko on 2009-01-17
I have a secondary hard drive I'd like to use for storage that used to show up in my drive list when I hit Places>Computer. 

I formatted that drive to start fresh and it no longer displays so I can open it.

So, what exactly can I do so that this drive shows up?

---

### Post by logos34 on 2009-01-17
follow this:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by mattbutsko on 2009-01-17
thanks, I'll take a look at that.

---

### Post by mattbutsko on 2009-01-17
Could anyone simplify that tutorial for me? I don't understand the /ect/fstab/ part at all.

---

### Post by logos34 on 2009-01-17
[edit: u say 'slave' so it must be internal]

Basically you just need to create a mountpoint and add an entry to fstab so it automounts at boot.

Post the output of these commands:

sudo blkid

sudo fdisk -l

---

### Post by sarath_it on 2009-01-18
or Try gparted/

---

