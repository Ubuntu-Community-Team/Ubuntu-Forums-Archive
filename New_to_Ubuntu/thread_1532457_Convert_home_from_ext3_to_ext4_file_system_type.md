---
title: "Convert /home from ext3 to ext4 file system type"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by cwmoser on 2010-07-16
My / root is ext4 on /dev/sda4
My /home is ext3 on /dev/sda3
My prior OS was Jaunty on /dev/sda1 - which I will only use if I cannot boot Lucid.

How do I convert my /home from ext3 to ext4?

Is this recommended?

I'm running Ubuntu 10.04 64-bit version.

Carl

---

### Post by bodhi.zazen on 2010-07-16
You can either back up your data and reformat to ext4 or convert to ext4

[http://ubuntuforums.org/showthread.php?t=973701](http://ubuntuforums.org/showthread.php?t=973701)

That is an old thread, but the procedure is the same.

If that looks too complicated, just back up your data, reformat, and then restore your data.

---

### Post by noidian on 2010-07-16
The warnings on the thread are enough to possibly inhibit anyone to try it, just save the data and reformat the drive. :-)

---

### Post by Jerry N on 2010-07-16
> **cwmoser said:**
> 
How do I convert my /home from ext3 to ext4?


Why?

Jerry

---

### Post by John Bean on 2010-07-16
> **Jerry N said:**
> Why?

Good question, and one that the OP needs to think about. I use ext4 with Lucid and it works flawlessly, but when I originally tried it under Jaunty - on the same hardware - I had almost immediate problems that got worse very quickly. I restored ext3 and all was well again.

So, if it ain't broke...

PS: I kept Jaunty for a while, just in case, but it's long gone now. Lucid was solid from day one on my hardware and of course still is :-)

---

