---
title: "Says I'm not the owner"
date: 2009-10-15
forum: New to Ubuntu
---

### Post by masontgreen on 2009-10-15
I just reformatted my external hard drive as ext3 but I can put anything on it as it says I'm not the owner...?:confused:

---

### Post by beastrace91 on 2009-10-15
Your thread is now marked as solved, did you resolve your issue then?

~Jeff

---

### Post by The Cog on 2009-10-15
Assuming the external disk gets mounted as /media/disk:
> sudo chmod 777 /media/disk
will make the it read/writeable by everybody.

---

