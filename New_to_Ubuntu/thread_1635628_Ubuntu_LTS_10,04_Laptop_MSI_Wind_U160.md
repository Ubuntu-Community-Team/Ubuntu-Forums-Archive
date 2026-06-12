---
title: "Ubuntu LTS 10,04 Laptop MSI Wind U160"
date: 2010-12-02
forum: New to Ubuntu
---

### Post by SG12010 on 2010-12-02
Hi

When the  AC plug is pulled it saids low battery when it is fully charged.

Also it will go into sleep mode even after canceling the warning icon.

Thanks SG

---

### Post by lancest on 2010-12-02
Google the first part about disable battery indicator. (It's there someplace)

The second problem is more critical. 
Work Around: Press Alt-F2 and use the pop-up to launch gconf-editor.
Navigate to Apps / gnome-power-manager / general.
De-select the option use_time_for_policy.

This will stop an MSI from going to sleep after unplug.
Both my MSI U90 and U230 exhibit same behaviors.

---

### Post by SG12010 on 2010-12-02
> **lancest said:**
> Google the first part about disable battery indicator. (It's there someplace)

The second problem is more critical. 
Work Around: Press Alt-F2 and use the pop-up to launch gconf-editor.
Navigate to Apps / gnome-power-manager / general.
De-select the option use_time_for_policy.

This will stop an MSI from going to sleep after unplug.
Both my MSI U90 and U230 exhibit same behaviors.



Thanks Solved

---

