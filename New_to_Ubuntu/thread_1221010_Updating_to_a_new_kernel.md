---
title: "Updating to a new kernel"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by Odin8778 on 2009-07-23
Alright, I'm getting more and more accustomed to Ubuntu, but I humbly request more help :) I'd like some assistance and guidance on installing Ubuntu so that when Karmic comes out I can keep the contents of my /home folder intact (ie. programs and preferences and such) and then update the kernel. I would attempt it myself, but I'm sure I'd end up with a blank screen :D
 
Anyway, any help is appreciated, or if anyone can point me to a good guide that would be cool too.
 
Peace!

---

### Post by swoll1980 on 2009-07-25
You have to manually partition the drive. You need to allocate like 10 GB, and mount it as / check the format option ticker. Then you can use the rest of the space, minus 2x the size of your RAM for the /home partition. If you have 1 GB RAM save your self 2GB after the end of the second partition. Mount this second partition as /home, and check the format ticker. Use the final space you left yourself for your swap. When you update, you do it the same way, except you don't format the /home. This will install the new version, but keep your /home folder intact.

---

### Post by snowpine on 2009-07-25
When Karmic is released in October, the Update Manager will prompt you to upgrade your system to the new release (including the new kernel). You'll get to keep all of your personal documents, installed applications, settings, etc. when you upgrade. 

Keeping a separate /home partition (as described above) is always a good idea for many reasons. 

[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Some users choose to re-install fresh every 6 months (instead of upgrading), and a separate /home makes this really easy.

---

### Post by Odin8778 on 2009-07-31
Very informative, thanks!

---

