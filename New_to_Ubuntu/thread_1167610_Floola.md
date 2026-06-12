---
title: "Floola"
date: 2009-05-23
forum: New to Ubuntu
---

### Post by dunbrokin on 2009-05-23
When I plug in my ipod, Floola opens about 6 or 8 versions of itself. The same happens with my Mobile Phone...it opens about 8 versions of image viewer.

This if from my log

May 22 20:03:13 pj-indulgence kernel: [18481.482336] Floola[26257]: segfault at 24 ip b61ca5ad sp b52b0c1c error 6
May 22 20:03:14 pj-indulgence kernel: [18482.148325] Floola[26258]: segfault at 24 ip b62385ad sp b531ec1c error 6
May 22 20:03:14 pj-indulgence kernel: [18482.471268] Floola[26259]: segfault at 24 ip b638f5ad sp b5475c1c error 6
May 22 20:03:14 pj-indulgence kernel: [18482.791823] Floola[26260]: segfault at 24 ip b621a5ad sp b5300c1c error 6
May 22 20:03:15 pj-indulgence kernel: [18483.000461] Floola[26261]: segfault at 24 ip b633b5ad sp b5421c1c error 6
May 22 20:03:15 pj-indulgence kernel: [18483.138671] Floola[26262]: segfault at 24 ip b63905ad sp b547cc1c error 6
May 22 20:03:15 pj-indulgence kernel: [18483.327367] Floola[26263]: segfault at 24 ip b62a55ad sp b5391c1c error 6
May 22 20:03:15 pj-indulgence kernel: [18483.957616] Floola[26264]: segfault at 24 ip b627d5ad sp b5369c1c error 6
May 22 20:03:16 pj-indulgence kernel: [18484.450406] Floola[26265]: segfault at 24 ip b61aa5ad sp b5296c1c error 6
May 22 20:03:16 pj-indulgence kernel: [18484.859840] Floola[26266]: segfault at 24 ip b63405ad sp b542cc1c error 6

---

### Post by blueridgedog on 2009-05-24
Can you run floola from the command line or menu normally?

Have you tried removing the association and just running floola when you plug in your device?

---

### Post by dunbrokin on 2009-05-25
I think it may have to do with the fact that I have a USB dock, coz when I plugged in a USB disk today, it opened 4 windows showing the disk.

---

### Post by blueridgedog on 2009-05-25
I bet you are right.  If you remove the dock and the problems stops, you have found the cause.

---

### Post by dunbrokin on 2009-05-25
> **blueridgedog said:**
> I bet you are right.  If you remove the dock and the problems stops, you have found the cause.

Indeed...but I need the dock as I only have 2 USB ports...that eliminates the problem....but does not eliminate the problem , so to speak :)

---

