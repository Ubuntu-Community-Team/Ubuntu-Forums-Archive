---
title: "how to install and make a dlink dwa-642 work"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by nwadams on 2007-04-01
i'm a ubuntu newbie who needs help with a wireless card
i have a dlink dwa-642 it's a pcimia card, (laptop external wireless)

and i would like to know how to make it work in ubuntu

---

### Post by nwadams on 2007-04-02
bump

---

### Post by Floppyjoe on 2007-04-02
Try installing the linux-restricted-modules for your kernel type.

---

### Post by nwadams on 2007-04-02
i'm a newb, how would i go about doing that for ubuntu

---

### Post by Floppyjoe on 2007-04-02
Open a terminal by clicking on Applications/Accessories/Terminal and enter the command:
```
uname -r
``` 
This will show you your kernel type.
Next click on System/Administration/Synaptic Package Manager.
Then search for linux-restricted-modules and install the ones for the kernel type from the uname -r command.

---

### Post by bbabiuk on 2008-02-02
did you ever get the card working?

---

