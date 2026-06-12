---
title: "ipw2100 monitor mode"
date: 2007-10-22
forum: Networking &amp; Wireless
---

### Post by sporanox on 2007-10-22
I am running a T42 with Ubuntu 7.04 and ipw2100 wireless card.  I cannot put the card in monitor mode.  It takes the command, but when I run iwconfig eth1 - it shows managed mode.  I am not sure if this is a driver issue, but i am somewhat of a noob.  Thanks in advance.

---

### Post by Lambert on 2007-10-23
> **sporanox said:**
> I am running a T42 with Ubuntu 7.04 and ipw2100 wireless card.  I cannot put the card in monitor mode.  It takes the command, but when I run iwconfig eth1 - it shows managed mode.  I am not sure if this is a driver issue, but i am somewhat of a noob.  Thanks in advance.

Try this. 

Take interface down
```

sudo ifdown eth1

```

Unload the driver
```

sudo modprobe -r ipw2100

```

Releoad the driver with mode parameters
```

sudo modprobe ipw2100 mode=2

```

Bring up the interface again
```

sudo ifup eth1

```

Check to see what mode is displayed now.

---

