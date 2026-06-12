---
title: "Unable to increase Ubuntu partition size from unallocated free space"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by PrateekParekh on 2009-05-18
I want to increase the /dev/sda7 partition size by allocating it the adjacent 19.43 Gb unallocated space. However, the resize option is greyed. Only unmount is available. 

Since, the sda7 is active partition, I believe it cannot be unmounted. Does this logic apply to resize option too? Is using the Live CD the only option here? 

Any other suggestions?

---

### Post by pspsampsp on 2009-05-18
i think you have to use a live cd as you cannot edit a mouted partition , that is why it is locked

---

### Post by agustin.g on 2009-05-18
Absolutely. Use liveCD if you still have it OR usb drive.

---

### Post by jowilkin on 2009-05-18
You can't resize if mounted, you can't unmount if active.  Hence you can't be active if you want to resize.

---

### Post by PrateekParekh on 2009-05-18
Thanks for the response. I remember resizing the active partition in Windows once. That led to the confusion.

---

