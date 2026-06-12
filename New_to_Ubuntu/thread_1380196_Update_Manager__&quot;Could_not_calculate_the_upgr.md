---
title: "Update Manager:  &quot;Could not calculate the upgrade&quot; after updating to 9.10"
date: 2010-01-13
forum: New to Ubuntu
---

### Post by diablo75 on 2010-01-13
A friend of mine upgraded his copy of Ubuntu from 9.04 to 9.10.  As far as I know things went pretty smoothly.  After the upgrade was done, update manager reported that there were more package updates available.  Upon trying to apply them, it says that not all updates can be applied and offers the option of doing a Partial Upgrade.  After opting to do a partial upgrade, an error message appears:

"Could not calculate the upgrade

An unresolvable problem occured while calculating the upgrade:
E: Unable to correct problems, you have held broken packages.

This can be caused by:
*Upgrading to a pre-release version of Ubuntu
*Running the current pre-release version of Ubuntu
*Unofficial software packages not provided by Ubuntu

This is most likely a transient problem, please try again later"

I'm pretty sure he didn't upgrade until well after 9.10 was released so it's a safe bet he's not running anything pre-release.

Any ideas on how to troubleshoot this?

---

### Post by zvacet on 2010-01-14
> E: Unable to correct problems, you have held broken packages.


```
sudo apt-get -f install
```

---

