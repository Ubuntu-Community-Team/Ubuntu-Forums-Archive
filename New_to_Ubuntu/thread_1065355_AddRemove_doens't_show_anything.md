---
title: "Add/Remove doens't show anything"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by Atrus6 on 2009-02-09
Title says it all.  And I'm sorta curious as to why it does that.  Synaptic shows everything just fine.

Thanks for the time, and letting me abuse this forum with questions ^^

---

### Post by drs305 on 2009-02-09
Try fixing it with this:
```

sudo apt-get install --reinstall app-install-data app-install-data-commercial

```

---

### Post by Paqman on 2009-02-09
I had that a little while ago. I just reinstalled Add/remove (it's actually a package called gnome-app-install) and everything was ok.

---

### Post by unplugged23 on 2009-02-09
try and run```
sudo apt-get update
```
let me know if it still does that after :)

---

### Post by 2hot6ft2 on 2009-02-09
Did you just install Adobe Air and/or the new BBC iPlayer Desktop?

Since you've already been told how to fix it now you know why it happened.

---

### Post by Atrus6 on 2009-02-09
drs305's solution worked ^^

And yes, adobe air....evil, pure evil.

---

