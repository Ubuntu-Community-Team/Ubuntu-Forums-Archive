---
title: "Cleaning up Grub menu"
date: 2011-01-07
forum: New to Ubuntu
---

### Post by SuperFreak on 2011-01-07
I seem to be accumulating  new entries to my Grub menu. Unless there is a reason to keep all the old entries (ie Linux 2.6.35.23 Generic) how do I delete them?

---

### Post by hansolo4949 on 2011-01-07
You should run the janitor program on your computer, if you don't have it, you can download it form the software center. Then all of the entries should be gone!

hansolo4949

---

### Post by ajgreeny on 2011-01-07
**Be very careful using Computer janitor** as it will show many apps, some of which you may want to keep, including anything installed manually with gdebi or "sudo dpkg -i *package*".

It is probably safer to look using the search button, name only, in synaptic, with search term **2.6.35-23** and remove the three packages that will probably show there.

Remember that it is worth having the most recent kernel version and the previous one installed at all times just in case something goes wrong with one of them

---

### Post by SuperFreak on 2011-01-07
Thanks ajgreeny

I removed 2.6.35.22 Generic using synaptic but left 2.6.35.23 Generic and  2.6.35.24 Generic. I will mark this solved.

---

