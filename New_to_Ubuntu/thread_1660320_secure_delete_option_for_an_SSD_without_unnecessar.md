---
title: "secure delete option for an SSD without unnecessary life reduction"
date: 2011-01-05
forum: New to Ubuntu
---

### Post by sundol on 2011-01-05
Googling told me that single pass deletion is good enough for SSD and more than one pass deletion just reduce the life of SSD with no benefit.

"man sfill" was not clear for me how to do a single pass deletion.

How to delete a partition with only a single pass?
(or What is the best option to delete securely a partition of SSD while minimizing reduction of SSD life?)

$> sfill -l -l /a_partition/

Is this a just enough to delete securely a partition on an SSD?

---

### Post by seawolf167 on 2011-01-05
[See if this helps you]("http://www.windowsitpro.com/article/file-systems/q-how-can-i-reset-a-solid-state-disk-ssd-to-a-fully-erased-clean-state-.aspx")

---

### Post by Spyderkid on 2011-01-05
Run this to secure delete the data on your SSD

(cd to the directory above your device
```

shred -n 1 -v [device name]

```

replace [device name] with the device don't type in the []'s

(Replace the number with how many passes you want but you said 1 would be ok so I said 1)

---

