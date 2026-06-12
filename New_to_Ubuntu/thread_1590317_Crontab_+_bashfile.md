---
title: "Crontab + bashfile"
date: 2010-10-07
forum: New to Ubuntu
---

### Post by Hippytaff on 2010-10-07
Is it possible to use a bash file that looks like this

```

#!/bin/bash
sudo apt-get update && sudo apt-get upgrade

```

to schedule that command with crontab?

---

### Post by lykwydchykyn on 2010-10-07
It's better to use cron-apt and create and action file for dist-upgrading.

I do this on several low-priority servers and it works well unless there are circumstances where I need to specially confirm an action (like installing unsigned software, etc).

Basically:
 - install cron-apt from the repository
 - Create a file "/etc/cron-apt/action.d/9-dist-upgrade"
 - Put this in the file:
```

dist-upgrade -y -V -o Dpkg::Options::=--force-confold

```

That should get you upgrading automatically.

---

### Post by Hippytaff on 2010-10-07
> **lykwydchykyn said:**
> 
```

dist-upgrade -y -V -o Dpkg::Options::=--force-confold

```That should get you upgrading automatically.

will this do the same as doing the sudo apt-update etc in the terminal?

---

### Post by lykwydchykyn on 2010-10-07
Yes.  By default, cron-apt just does the update part.  Adding the file I specified will make it do a dist-upgrade as well.  If you just want to do "safe upgrades" you can change "dist-upgrade" to "safe-upgrade".

---

