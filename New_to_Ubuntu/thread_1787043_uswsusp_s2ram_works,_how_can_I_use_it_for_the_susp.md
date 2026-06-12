---
title: "uswsusp s2ram works, how can I use it for the suspend option in the menu ?"
date: 2011-06-20
forum: New to Ubuntu
---

### Post by ilkerk on 2011-06-20
I found some info on the forums but I guess they are for previous versions of Ubuntu. I have a 11.04 Natty. 
and there is no script as 
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux

thanks
thanks.

Edit: I found it : /usr/sbin/pm-suspend

---

### Post by Toz on 2011-06-20
According to the documentation, you should be able to edit (create if it doesn't exist) the file **/etc/pm/config.d/defaults** and add to the file:```
SLEEP_MODULE="uswsusp"
``` and if you need to force or use any options, you need to add:```
S2RAM_OPTS="--force -<option1> -<option2>"
```

Then reboot and test.

The other, less desirable option, is to replace the /usr/sbin/pm-suspend script with your own script that calls s2ram.

---

