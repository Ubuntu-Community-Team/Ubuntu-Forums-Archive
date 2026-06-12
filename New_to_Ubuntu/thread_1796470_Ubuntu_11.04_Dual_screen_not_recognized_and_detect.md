---
title: "Ubuntu 11.04: Dual screen not recognized and detect monitors has no effect"
date: 2011-07-03
forum: New to Ubuntu
---

### Post by Darth_Sy on 2011-07-03
I just updated from 10.10, where I had my external monitor plugged into my laptop, working fine. After upgrade, the dual screen is no longer recognized. Heading to monitor preferences, 'detect monitors' produces no response. My laptop monitor is listed as 'unknown', if that makes a differences. 

I'm reading various discussions of editing xorg.cfg and such to deal with monitors, but this all seems to deal with screen resolution, which is not a problem (yet).

Thanks!

---

### Post by Darth_Sy on 2011-07-03
Problem solved: I ran sudo nvidia-settings, it was disabled there.

---

### Post by wildmanne39 on 2011-07-04
> **Darth_Sy said:**
> Problem solved: I ran sudo nvidia-settings, it was disabled there.Hi,would you please go to the top of the page and mark this thread solved be clicking on thread tools. Thank you so much.

---

