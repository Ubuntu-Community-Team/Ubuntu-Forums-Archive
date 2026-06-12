---
title: "3x Ubuntu on boot up"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-06-30
So I have win7 and ubuntu dual booted.  When it goes to the option for to pick which OS i want to use I've noticed that ubuntu keeps growing.  1st there was on then 2 and now 3(plus 3 recovery).  Does anyone know what is going on?  I know I don't keep reinstalling it over and over.


Thanks

Kevin

---

### Post by KdotJ on 2010-06-30
Hello, 
What you have described is nothing to worry about

If you look, the numbers in each entry are different. This is due to the kernel for each one being different. Each time you get an update that contains a new linux kernel, they new kernel is added to the boot list. The most recent kernel is listed in the top most Ubuntu entry.

This is so, if you have problems with the new kernel (e.g. your system does not work the same, or you have issues since the latest kernel update) you can opt to boot into an older kernel version. 

It's not a different version of Ubuntu itself, your files and config is not different in each of these entries.

---

### Post by Kirkland14 on 2010-06-30
OH! Well that's pretty awesome.  Thanks for the knowledge.

Kevin

---

### Post by KdotJ on 2010-06-30
No problem.
You can infact remove them from the list, by editing certain files. But it's honestly not worth it, they don't do any harm being there and you never know, you might even need to use them lol.

---

