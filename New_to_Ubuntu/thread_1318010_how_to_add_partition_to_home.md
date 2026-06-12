---
title: "how to add partition to \home"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by virgu on 2009-11-07
[SIZE=2]I'm a linux newbie and I've been using ubuntu 9.04 and winxp sp2 in dual boot.Recently I cut about 20Gb from windows and reformatted it in ext3 with Gparted.Now I want to add this partition to \Home.But I don't know how to do it.[/SIZE]
 
 
[SIZE=2]Any idea how to do it?[/SIZE]
 
[SIZE=2]Thanks in advance.[/SIZE]

---

### Post by nothingspecial on 2009-11-07
If you mean you want to make it your /home partition have a look [[COLOR="Magenta"]here[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

If you mean you want to add the 20gigs to your home partition you would have to delete it and grow your home partition into it.

Back everything up first.

---

### Post by profeta81 on 2009-11-07
hello

/home is a directory, you cannot "add" a partition to a directory, you can "mount" a partition on a directory if you wish, in which case when you list the content of that directory you'll see the files contained on that partition (remember that if your directory did contain some stuff already, that stuff will not be accessible any more, so long as the partition is mounted)...

---

### Post by virgu on 2009-11-09
Solved! I've moved the /home directory to my new patition. It's working nice.

Thanks to you guys for replying.

---

### Post by nitrousjames on 2009-11-09
> **nothingspecial said:**
> If you mean you want to make it your /home partition have a look [[COLOR=Magenta]here[/COLOR]]("http://www.psychocats.net/ubuntu/separatehome")

If you mean you want to add the 20gigs to your home partition you would have to delete it and grow your home partition into it.

Back everything up first.


thnx mate :D

---

