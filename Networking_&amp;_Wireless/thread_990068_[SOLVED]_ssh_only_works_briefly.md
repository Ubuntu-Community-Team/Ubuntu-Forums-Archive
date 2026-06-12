---
title: "[SOLVED] ssh only works briefly"
date: 2008-11-22
forum: Networking &amp; Wireless
---

### Post by riksweeney on 2008-11-22
Hi,

I'm trying to ssh onto another Ubuntu machine, but ssh is only working briefly, for about, say 20 minutes before I can no longer connect. I've tried pinging the machine too, but this also fails.

The only thing I can do to solve this problem is to disconnect the machine from the router and reconnect it. I can then ssh onto it OK for another 20 minutes or so before I have to disconnect it again.

Does anyone know what might be causing this problem?

DELL 1530M with Broadcom BCM4312

Thanks

Richard

---

### Post by Olivier2371 on 2008-11-22
Don't know if that will help, but have you tried firestarter?

---

### Post by riksweeney on 2008-11-22
It looks like it's a problem to do with the Broadcom Driver. I'm using ndiswrapper.

If I wait long enough then it seems to correct itself for a while. I'm not sure where to look for error messages though.

---

### Post by Olivier2371 on 2008-11-22
I also have a broadcom wireless adapter BCM4312 and I use the restricted driver broadcom B43 wireless driver. 

I have used a month ago firestarter, and it worked well.

---

### Post by riksweeney on 2008-11-22
Yeah, I've noticed that the restricted driver works without the need for ndiswrapper. It all appears to be working at the moment, fingers crossed!

---

### Post by Olivier2371 on 2008-11-22
riksweeney, 

Has your problem been resolved?

If it has, please mark the thread "solved".

Thank's

PS: Thank you for your note of appreciation.

---

