---
title: "Master Boot Record"
date: 2010-06-26
forum: New to Ubuntu
---

### Post by nick_goodfate on 2010-06-26
what is it ? one of my partitions ? and how can i find which of them is my Master Boot Record ?

---

### Post by Bucky Ball on 2010-06-26
You could do a search for 'what is master boot record.' Sheesh!

[http://www.google.com/cse?q=what+is+master+boot+record&sa=Search&cx=partner-pub-9300639326172081%3An71jpcz0370&ie=UTF-8](http://www.google.com/cse?q=what+is+master+boot+record&sa=Search&cx=partner-pub-9300639326172081%3An71jpcz0370&ie=UTF-8)

Generally on the boot partition. System->Administration->Partition Editor should get you there.

---

### Post by philinux on 2010-06-26
> **nick_goodfate said:**
> what is it ? one of my partitions ? and how can i find which of them is my Master Boot Record ?

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by nick_goodfate on 2010-06-26
> **Bucky Ball said:**
> You could do a search for 'what is master boot record.' Sheesh!

[http://www.google.com/cse?q=what+is+master+boot+record&sa=Search&cx=partner-pub-9300639326172081%3An71jpcz0370&ie=UTF-8](http://www.google.com/cse?q=what+is+master+boot+record&sa=Search&cx=partner-pub-9300639326172081%3An71jpcz0370&ie=UTF-8)

Generally on the boot partition. System->Administration->Partition Editor should get you there.

i DID a search but i didnt find how i can figure out which is MBR ... So i thought i could ask here, in ABSOLUTE BEGINNER TALK , i m sorry Mr. expert ... and there is no Partition Editor in lucid menus ...

---

### Post by Rubi1200 on 2010-06-26
If you go to System > Administration > Disk Utility that should give you the information you need.

The link given above by philinux can be used to provide more detailed information about your MBR, partitions, and other useful stuff.

---

### Post by nick_goodfate on 2010-06-26
thank you philinux, thank you Rubi1200 for your help !

---

### Post by Bucky Ball on 2010-06-27
No expert. First part of boot partition, whatever that one is (generally windows if your dual-booting). Good luck with it.

---

### Post by oldfred on 2010-06-27
MBR details including 2TiB limit and GPT link
[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

It is the first sector of a hard drive before any partitions. Most partitions are also set up with a PBR or boot sector that is the first sector of the partition for additional booting data. Windows uses the boot sector for part of its boot sequence.

---

