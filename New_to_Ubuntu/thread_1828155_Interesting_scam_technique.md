---
title: "Interesting scam technique"
date: 2011-08-18
forum: New to Ubuntu
---

### Post by canam101 on 2011-08-18
This may be obvious to more experienced people, but it is an interesting puzzle to me.

I noticed that if I wanted to go to drudgereport.com but mis-typed it as drudgreport.com, the scammer who registered the domain has it re-direct my browser (firefox) to one or the other of a 'you are a winner' kind of rubbish.

I was able to block the site by putting an entry into the /etc/hosts file of: 

127.0.0.1 drudgreport.com

but I was curious as to how they coded the re-direct command; however it seems it is impossible to see the source code for that url. 

I even did a wget and the 'source code' it returned was '-1'.

The other thing that is interesting is that even with javascript turned off, the damn thing still re-directs you.

If anyone knows how they do the trick, I would be interested to hear.

---

