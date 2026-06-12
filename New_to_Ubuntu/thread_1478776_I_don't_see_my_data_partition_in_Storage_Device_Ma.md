---
title: "I don't see my data partition in Storage Device Manager"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by kramer65 on 2010-05-10
Hello,

I installed the Storage Device Manager (SDM) and opened it. I see all the partitions, except te one which I want to auto-mount at startup: sda4 (/media/Opslag).

I named the sda4-partition "Opslag", could that be a reason I don't see it in SDM?

---

### Post by Ocxic on 2010-05-10
you might need to run SDM as root with gksu

---

### Post by kramer65 on 2010-05-10
Thanks for the tip. I tried running "gksudo pysdm", but sda4 or /media/Opslag still doesn't appear, while all the other partitions do show up.. :S

Any other ideas..?:???:

---

### Post by kramer65 on 2010-05-10
I  solved it by doing it manually.

Thanks for thinking with me anyway!

---

