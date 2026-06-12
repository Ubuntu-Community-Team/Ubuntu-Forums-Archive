---
title: "Chmod"
date: 2010-09-14
forum: New to Ubuntu
---

### Post by Diametric on 2010-09-14
So, what do you find is the easiest way to change permissions in a terminal? I've seen some use the number method, some who use +x etc...if I wanted to memorize this, what would be the easiest way?
 
Thanks!

---

### Post by uRock on 2010-09-14
The numeric way is probably the best. 
You have 3 digits, the first is for the owner, the second is for the assigned group and the last is for other.

0= no permissions granted
1= execute only
2= write only
3= write and execute (1+2)
4= read only
5= read and execute (4+1)
6= read and write (4+2)
7= read, write and execute (4+2+1)

I hope this helps,
uRock

---

### Post by Rubi1200 on 2010-09-14
I found this useful:
[http://ss64.com/bash/chmod.html](http://ss64.com/bash/chmod.html)

---

### Post by endotherm on 2010-09-14
> **Diametric said:**
> So, what do you find is the easiest way to change permissions in a terminal? I've seen some use the number method, some who use +x etc...if I wanted to memorize this, what would be the easiest way?
 
Thanks!
the numbers are I guess a little more powerful (certianly cleaner), but probably aren't as easy to memorize. I also like the way 'u+x'  changes only the specific part of the permission that you are interested in changing.

---

### Post by Diametric on 2010-09-14
Thanks for the replies - this gives me some idead.  I think I like the numeric menthod most.  I agree with however said it was cleaner...might just take a little while longer to get.
 
Cheers!

---

