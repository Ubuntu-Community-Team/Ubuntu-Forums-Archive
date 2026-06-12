---
title: "What happened to dropdown menu in top panel?"
date: 2010-06-30
forum: New to Ubuntu
---

### Post by archkidd on 2010-06-30
In Ubuntu 10.4 there used to be a dropdown menu in the top RH corner which allowed me to log off, suspend, shutdown etc.  Somewhere in the last updates (?) it has disappeared. Using the Add To command for the panel only allows me to add a 'Shutdown' object, which literally only does that.  Is there some other way to get the 'suspend' command back?

---

### Post by drs305 on 2010-06-30
> **archkidd said:**
> In Ubuntu 10.4 there used to be a dropdown menu in the top RH corner which allowed me to log off, suspend, shutdown etc.  Somewhere in the last updates (?) it has disappeared. Using the Add To command for the panel only allows me to add a 'Shutdown' object, which literally only does that.  Is there some other way to get the 'suspend' command back?

The one you are looking for is the Indicator Applet Session. It *should* be available for adding by right clicking the top panel and selecting "Add to Panel". If you add it and still don't have the Suspend and Hibernate options let us know. It could be that your *swap* isn't enabled (run "free -m" to check) or some other issue which prevents your system from executing these options.

---

### Post by archkidd on 2010-06-30
Thank you. That solved it :)  I did not recognize the Indicator Applet Session when I looked earlier. I don't know why not as it states quite clearly what it does!  I just saw the shutdown object.

---

