---
title: "[SOLVED] synaptic problem"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by gridd on 2008-12-29
hi synaptic is giving me this when i try to download.Ive tried running the solution in terminal but I'm  probably doing it wrong.

E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

help.

---

### Post by Elfy on 2008-12-29
no - you just aren't using root

```
sudo dpkg --configure -a
```

---

### Post by gridd on 2008-12-29
> **forestpixie said:**
> no - you just aren't using root

```
sudo dpkg --configure -a
```

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up accerciser (1.2.0-0ubuntu2) ...
Upgrade from broken accerciser version detected, running scrollkeeper-rebuilddb...

blink blink

sorry now this I shall let it run.


Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up accerciser (1.2.0-0ubuntu2) ...
Upgrade from broken accerciser version detected, running scrollkeeper-rebuilddb...

Setting up abuse (1:0.7.0-6) ...

Setting up abuse-frabs (2.10-7ubuntu2) ...

Setting up kde4libs-bin (4:4.0.3-0ubuntu5.2) ...
Setting up kdelibs5 (4:4.0.3-0ubuntu5.2) ...

Setting up kdebase-runtime-bin-kde4 (4:4.0.3-0ubuntu2) ...
Setting up kdebase-runtime (4:4.0.3-0ubuntu2) ...
Setting up kfind-kde4 (4:4.0.3-0ubuntu2) ...
Setting up ark-kde4 (4:4.0.3-0ubuntu4) ...

Setting up libkonq5 (4:4.0.3-0ubuntu2) ...

Setting up dolphin-kde4 (4:4.0.3-0ubuntu2) ...

---

### Post by sdowney717 on 2008-12-29
they should change those command error messages to reflect the need for sudo.

---

### Post by gridd on 2008-12-29
Any idea what might have caused this by the way?

---

### Post by nebu on 2008-12-29
if u were downloading/installing updates... and ur computer rebooted for some unforeseen reason.... this seems to happen....

atleast thats what had happened to me....

---

### Post by gridd on 2008-12-29
> **nebu said:**
> if u were downloading/installing updates... and ur computer rebooted for some unforeseen reason.... this seems to happen....

atleast thats what had happened to me....

Ah yes I was doing a clean install and  the updates failed on one or two programs but I elected to carry on OK. That may have been it.


These corrections are taking forever though.

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Setting up accerciser (1.2.0-0ubuntu2) ...
Upgrade from broken accerciser version detected, running scrollkeeper-rebuilddb...

Setting up abuse (1:0.7.0-6) ...

Setting up abuse-frabs (2.10-7ubuntu2) ...

Setting up kde4libs-bin (4:4.0.3-0ubuntu5.2) ...
Setting up kdelibs5 (4:4.0.3-0ubuntu5.2) ...

Setting up kdebase-runtime-bin-kde4 (4:4.0.3-0ubuntu2) ...
Setting up kdebase-runtime (4:4.0.3-0ubuntu2) ...
Setting up kfind-kde4 (4:4.0.3-0ubuntu2) ...
Setting up ark-kde4 (4:4.0.3-0ubuntu4) ...

Setting up libkonq5 (4:4.0.3-0ubuntu2) ...

Setting up dolphin-kde4 (4:4.0.3-0ubuntu2) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place.


Still at least they seem to be working.I will fill in when solved thanks Guys.

---

