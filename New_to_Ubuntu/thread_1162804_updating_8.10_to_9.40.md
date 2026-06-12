---
title: "updating 8.10 to 9.40"
date: 2009-05-18
forum: New to Ubuntu
---

### Post by Whitsboy on 2009-05-18
I've just been told i can update intrepid 8.10 to jaunty 9.40 by update manager. It won't update to 9.40 it just does the usual updates & takes about 1 minute. I was told the major update should take about 1 hour. When I check the about ubuntu dialog box it still says 8.10. Is there some other way to update to 9.40?

---

### Post by clhsharky on 2009-05-18
Did you hit update or upgrade button, and its 9.04

---

### Post by blazemore on 2009-05-18
To upgrade to 9.04, Run Update Manager and hit Check.
After it's updated the new package information, a button should appear at the top saying "New Distribution Release" or something. Click it to upgrade.

---

### Post by jkorten on 2009-06-03
> **blazemore said:**
> To upgrade to 9.04, Run Update Manager and hit Check.
After it's updated the new package information, a button should appear at the top saying "New Distribution Release" or something. Click it to upgrade.

In fact on my computer - this also doesn't work. I hit update and the only thing I get is the original "Update Manager" with the check button and the close button active.

Is there a property/preference somewhere that has to be enabled?

---

### Post by ready4thebreak on 2009-06-03
It's really simple. Press Alt+F2 and then enter 
```
update-manager -d
```

Hope this gets it working for you.

---

### Post by jkorten on 2009-06-03
> **ready4thebreak said:**
> It's really simple. Press Alt+F2 and then enter 
```
update-manager -d
```

Hope this gets it working for you.

That did it! It appears I have to go revision by revision though (I have 8.04 and it wants me to go to 8.10 which I'm doing. Then I suppose I will see 9.4?)

Thanks!

---

### Post by MrWES on 2009-06-03
> **ready4thebreak said:**
> It's really simple. Press Alt+F2 and then enter 
```
update-manager -d
```

Hope this gets it working for you.

update-manager -d is for devel only. Try alt + F2 and then

```
update-manager dist-upgrade
```update dist-upgrade

---

