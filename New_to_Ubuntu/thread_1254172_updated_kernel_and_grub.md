---
title: "updated kernel and grub"
date: 2009-08-31
forum: New to Ubuntu
---

### Post by eddski on 2009-08-31
I am not sure what I am doing when my machine updates. When I update, I see kernel updates sometimes. Now when the updates are installing I get a popup asking if I want to keep the original menu.list, and I am not sure what to do so I check keep the current one. How can I check how many kernels are loaded(updated) and should I choose something else to chang the menu.list file?

---

### Post by Michael.Godawski on 2009-08-31
I guess there is nothing wrong with keeping the old kernels. Sometimes this will save your life when there are problems with a newer one, you are still able to boot into the older one.

You can check the menu.lst file to see which kernels are currently available:

```
cat /boot/grub/menu.lst
```

---

### Post by eddski on 2009-08-31
how can I tell which kernels I have availabe in my system because when I did updates I chose not to change the menu.lst because I wasnt sure what it would do. But I do know I do know I have updated kernels, but they are not in menu.lst list. Thanks for the info

---

