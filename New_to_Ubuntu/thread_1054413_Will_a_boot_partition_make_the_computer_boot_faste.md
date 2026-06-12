---
title: "Will a /boot partition make the computer boot faster?"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by the8thstar on 2009-01-29
Hello all,

I currently have three partitions:

1. /Home
2. /
3. /swap

I am wondering if adding a /boot partition would make the overall boot time faster. Is that correct? If so, how can I add this partition without reinstalling everything?

Thanks!

---

### Post by mcduck on 2009-01-29
No, it wont. It should have no effect at all.

Reading the data from the disk during boot takes same time regardless if you are reading it from a separate partition or root partition. It's still the same hard disk.

---

### Post by the8thstar on 2009-02-01
Okay then, thanks for your help.

---

