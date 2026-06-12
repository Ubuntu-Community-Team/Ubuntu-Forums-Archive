---
title: "Swap partition"
date: 2009-06-08
forum: New to Ubuntu
---

### Post by celticbhoy on 2009-06-08
Just a quick one - how do I change the swap partition to a new partition already created and formated to linux swap?

---

### Post by LewRockwell on 2009-06-08
when *nix distros boot up they normally mount all available swaps

---

### Post by abhiroopb on 2009-06-08
[http://ubuntuforums.org/showthread.php?t=5223](http://ubuntuforums.org/showthread.php?t=5223)

Thread is a little old, but seems to address this issue. Try it out. I know it worked for me, but many years ago. Cannot guarantee if this is the best solution.

---

### Post by celticbhoy on 2009-06-08
So as I have both partitions already formatted rockwell, I should just be able to delete the one I want to remove ?

---

### Post by abhiroopb on 2009-06-08
From my experience it hasn't done it automatically, but like I said it was a while back...so may not be the case any longer.

---

### Post by Hospadar on 2009-06-08
As far as I know, the above poster is correct, all swap partitions available will be mounted automatically.

You could try:
delete the swap
boot up - does it work?
Yes -> continue your adventure on page 36
No - > re-create the swap partition and try something else

---

