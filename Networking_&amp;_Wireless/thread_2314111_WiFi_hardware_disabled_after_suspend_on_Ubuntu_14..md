---
title: "WiFi hardware disabled after suspend on Ubuntu 14.04 on HP Pavilion 15 ab030tx"
date: 2016-02-18
forum: Networking &amp; Wireless
---

### Post by arjunil.pathak on 2016-02-18
Hello,
My wifi gets hardware disabled each time i resume from suspend.
lsmod | grep wl returns no output either

Here's some more info.


Before suspend.
```
rfkill list all
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no



```




After suspend.


```
 rfkill list all
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes



```


Let me know if any other info is needed to suggest a solution.

---

### Post by Hadaka on 2016-02-18
Hi, please post the output of..
*including "file not found"
```
cat /etc/modules
cat /etc/rc.local
cat /etc/pm/config.d/config
lsmod | grep cfg80211
lspci -n | awk '/0280/{print$3}'
```
thanks

---

### Post by arjunil.pathak on 2016-02-21
Sorry for the delay. Here's the output



```
cat /etc/modules# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.


lp
rtc



```

```
 cat /etc/rc.local#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


exit 0



```

```
 cat /etc/pm/config.d/config
cat: /etc/pm/config.d/config: No such file or directory



```

```

lsmod | grep cfg80211
cfg80211              524288  2 mac80211,rtlwifi



```

```
lspci -n | awk '/0280/{print$3}'
10ec:b723



```


Thanks

---

