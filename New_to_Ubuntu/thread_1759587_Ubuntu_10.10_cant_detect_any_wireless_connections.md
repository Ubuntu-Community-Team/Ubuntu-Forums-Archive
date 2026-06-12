---
title: "Ubuntu 10.10 cant detect any wireless connections"
date: 2011-05-15
forum: New to Ubuntu
---

### Post by da_primo on 2011-05-15
I have a problem with connecting network

It's fine with windows 7 network connections but when I boot on ubuntu, my wireless cant detect any.

I have installed 10.10 on my machine and it seems to not detecting my wireless drive at all

how can I fix this to connect to internet?

---

### Post by garvinrick4 on 2011-05-15
What type of machine?
run this for me and post.
```
lspci -k
```

---

### Post by da_primo on 2011-05-16
Here is further details

---

### Post by garvinrick4 on 2011-05-19
I am sorry I missed your reply.
go to syaptics and open and add
bcmwl-kernel-source
and
b43-fwcutter
right click on to install then hit apply arrow
Then check in System/Admin/hardware drivers (proprietary drivers)
Make sure it is checked enabled.
Here is screenshot for you.

---

