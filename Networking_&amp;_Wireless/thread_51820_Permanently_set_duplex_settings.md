---
title: "Permanently set duplex settings?"
date: 2005-07-25
forum: Networking &amp; Wireless
---

### Post by milkjam on 2005-07-25
I need my network card forced to half duplex.

I tried ..

```
ethtool -s eth0 duplex half
``` 

... but got ...

```
Cannot get current device settings: Operation not supported
  not setting duplex

``` 

The solution was to use:

```
mii-tool -F 100baseTx-HD
```

What is the best way to now permanently set half duplex? Add the above to /etc/init.d/bootmisc.sh ?

---

### Post by tonysathre on 2005-07-25
Unfortunately there is no way to set this on reboot permanently except by placing it the command in the /etc/rc.local file to let it be run at the very end of the booting process or by creating your own startup script if you need it set earlier.
also try using the -v switch to see the error output verbosely

---

### Post by gruepig on 2005-07-26
You can probably add the line 'up mii-tool -F 100baseTx-HD' (or maybe 'pre-up mii-tool -F 100baseTx-HD') to /etc/network/interfaces for the appropriate iface.

---

