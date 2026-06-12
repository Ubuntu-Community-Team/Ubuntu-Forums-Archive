---
title: "Problems in  internet Access"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by hsalihba on 2010-06-29
My computer connected to WAN I have access internet when i boot into Windows but i cant access when i boot into Ubuntu 10.04 I suspect some one change my default access .How can i repair it

---

### Post by lkjoel on 2010-06-29
Is you Internet Card up to date?
You might need to buy a new one.

---

### Post by anewguy on 2010-06-29
It's most probably that there is no driver installed in Ubuntu for your adapter.  There are literally thousands of posts in this forum on wireless and getting it working, so you may want to search for those.  In the mean time, please do the following:

- open a terminal window (applications/accessories/terminal)

- type:

lshw -C network <press enter>

lspci <press enter>

*if* you are using a laptop, or if the adapter is USB, please also:

lsusb <press enter>

Post the output from all of those back here and we can go from there.

Dave ;)

---

