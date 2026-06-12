---
title: "Video Card Problem on a Fresh install"
date: 2009-09-30
forum: New to Ubuntu
---

### Post by nominal on 2009-09-30
I'm almost positive this is a video card problem because ubuntu (9.04) is almost running visually slower than vista...which is impossible.

Here is what terminal gave me:

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)

I'm not really sure where to go from here, besides find drivers?

admin-->hardware drivers does nothing for me

---

### Post by wdzieczny on 2009-09-30
You can try setting you're boot parameters to ```
linux resolution="1024x738" noprobe
``` that might help you to to atleast see if its a video card problem or not.

---

### Post by nominal on 2009-10-01
> **wdzieczny said:**
> You can try setting you're boot parameters to ```
linux resolution="1024x738" noprobe
``` that might help you to to atleast see if its a video card problem or not.

i google-d around, its a common problem. thanks for the advice though.

i just reverted back to an old driver release...until a new one gets announced

---

