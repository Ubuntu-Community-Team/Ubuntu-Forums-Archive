---
title: "how to refresh NM wifi list?"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by treesurf on 2009-02-23
I am wondering if there is a way to manually make Network Manager rescan for wifi networks.  Sometimes I have to reset my router and it's annoying to wait what seems like several minutes for it to show up in the list.

thanks

---

### Post by swoll1980 on 2009-02-24
> **treesurf said:**
> I am wondering if there is a way to manually make Network Manager rescan for wifi networks.  Sometimes I have to reset my router and it's annoying to wait what seems like several minutes for it to show up in the list.

thanks

I imagine 
```
sudo /etc/init.d/networking restart
```
would do the trick. It's worth a try.

---

### Post by treesurf on 2009-02-24
Thanks, that will probably work.  But I was really hoping for something more elegant than just restarting the whole thing.

---

