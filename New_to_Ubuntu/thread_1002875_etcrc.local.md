---
title: "/etc/rc.local"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by matteometto on 2008-12-05
Good evening everyone, I'm a Linux beginner and made a terrible mistake. I own an Acer Aspire One A110L with Ubuntu 8.10 and deleted and saved by mistake everything that was written in the /etc./rc.local- terminal in order to make the LEDs blink. Can anyone tell me what was exactly written there so I can just copy and paste it, please?
Thank you in advance. 
Matteo.:p

---

### Post by philinux on 2008-12-05
If you mean this
```
cat /etc/rc.local
#!/bin/sh -e
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
# **By default this script does nothing.**

exit 0

```

---

