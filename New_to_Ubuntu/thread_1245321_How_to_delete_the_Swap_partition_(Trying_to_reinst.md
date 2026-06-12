---
title: "How to delete the Swap partition? (Trying to reinstall Jaunty in a new configuration)"
date: 2009-08-20
forum: New to Ubuntu
---

### Post by swarup on 2009-08-20
I just booted to the livecd and deleted the Jaunty partition so I can reinstall it manually in a different configuration. But when I then highlight the 3 GB swap partition to delete it, the "delete" and "resize" buttons are not highlighted i.e. cannot be used. So how can I delete the swap partition?

---

### Post by Penguin Guy on 2009-08-20
You will need swap it off first (swapoff is the equivalent of unmounting). I believe the command is [COLOR="Green"]swapoff /dev/????[/COLOR] (where ???? is the partition identifier) will do the trick.

---

### Post by Merk42 on 2009-08-20
> **Penguin Guy said:**
> You will need swap it off first (swapoff is the equivalent of unmounting). I believe the command is [COLOR="Green"]swapoff /dev/****[/COLOR] (where **** is the partition identifier) will do the trick.

If you're using the Partition Editor GUI program from the LiveCD you can swapoff the partition there too.  It's under the same right click menu as delete and resize.

---

### Post by LewRockwell on 2009-08-20
```
swapoff /dev/yourswappartitionhere
```

.

---

### Post by Cheesemill on 2009-08-20
The Live CD will automatically use any swap space that it finds, that's why your swap is mounted.
 
In gparted just right-click on your swap partition and select unmount.

---

### Post by swarup on 2009-08-20
You've all made the matter very clear. Thank you! :)

---

