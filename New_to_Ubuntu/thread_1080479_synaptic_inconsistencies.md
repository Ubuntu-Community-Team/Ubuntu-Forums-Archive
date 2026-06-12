---
title: "synaptic inconsistencies"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by KCormier on 2009-02-25
I'm running two laptops side by side with 32 bit ubuntu intrepid installed and fully updated.  Software sources are configured identically.  When I go to synaptic to look for a specific library (freeglut3-dev) it shows up on one but not the other.  What's funny is that on the one where it's missing in synaptic, I can still install it using apt-get.  I'm also missing some libraries (on the same machine) related to glui.  Does anyone know a reason why this would happen?

-Kevin

---

### Post by billgoldberg on 2009-02-25
> **KCormier said:**
> I'm running two laptops side by side with 32 bit ubuntu intrepid installed and fully updated.  Software sources are configured identically.  When I go to synaptic to look for a specific library (freeglut3-dev) it shows up on one but not the other.  What's funny is that on the one where it's missing in synaptic, I can still install it using apt-get.  I'm also missing some libraries (on the same machine) related to glui.  Does anyone know a reason why this would happen?

-Kevin

No.

Remember you can always use

apt-cache search <packagename> or aptitude search <packagename>

---

