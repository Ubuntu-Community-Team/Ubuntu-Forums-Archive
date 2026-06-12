---
title: "Ubuntu Tweak Disaster"
date: 2009-09-18
forum: New to Ubuntu
---

### Post by cmcanulty on 2009-09-18
I downloaded Ubuntu Tweak and got all kinds of errors and now can't even open Synaptic. I can just get this error message all else is grayed out I tried force remove and nothing works.
E: The package ubuntu-tweak needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
I tried to report and get not a supported package so can't report. Can't remove as I can't open Synaptic, please help.When i try to remove I get another error that package is  in an inconsistent state please remove but I can't either command line or synaptic.

---

### Post by sandyd on 2009-09-18
type in
```

sudo rm /usr/share/python-support/ubuntu-tweak.private
sudo dpkg --remove --force-remove-reinstreq ubuntu-tweak

```

---

### Post by cmcanulty on 2009-09-19
Solved thanks everyone

---

