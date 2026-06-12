---
title: "How to turn off bluetooth"
date: 2006-11-26
forum: Networking &amp; Wireless
---

### Post by goneskiing on 2006-11-26
How do I turn off bluetooth - I didn't see it anywhere in the services menu.  
thanks.

---

### Post by Iowan on 2006-11-26
One quick/dirty way might be to change **/etc/rc2.d/S25bluez-utils** to **/etc/rc2.d/s25bluez-utils**

---

### Post by sflinter on 2006-11-29
How about:

```
$ sudo /etc/init.d/bluetooth stop
```

> **Iowan said:**
> One quick/dirty way might be to change **/etc/rc2.d/S25bluez-utils** to **/etc/rc2.d/s25bluez-utils**

---

### Post by Iowan on 2006-11-29
> **sflinter said:**
> How about:

```
$ sudo /etc/init.d/bluetooth stop
```
If you want to stop the services for current session... otherwise, you'd need to re-run the command each time you started the machine.  I don't have bluetooth - perhaps there's another link in the **rc** directory that could be changed - I suspect there's a cleaner way to disable the service (but don't know what it is...)

---

### Post by hesee on 2007-01-08
> **Iowan said:**
> If you want to stop the services for current session... otherwise, you'd need to re-run the command each time you started the machine.  I don't have bluetooth - perhaps there's another link in the **rc** directory that could be changed - I suspect there's a cleaner way to disable the service (but don't know what it is...)

Does anyone have solution to this permanent disabling of bluetooth?

---

### Post by grenness on 2007-01-08
Would be really cool to have a GUI tool for this.
I mean, for all those making the switch from Windows to (Ubuntu) Linux, it would be a nice familiarity to see the blue BT logo in the systray with an option to right click and quickly turn on/off or configure.

Anyone know of such a tool?

~Christopher

---

### Post by grenness on 2007-01-08
> **sflinter said:**
> How about:

```
$ sudo /etc/init.d/bluetooth stop
```

It looks like this did the trick for me, however the bluetooth light on my Thinkpad X60s is still lit.

~Christopher

---

### Post by goneskiing on 2007-01-10
well I upgraded to Edgy and there is a bluetooth option on the services menu which I turned off.

---

### Post by dmizer on 2007-01-11
sorry i was too late for you goneskiing, but for future users with this problem:

see this thread: [http://www.ubuntuforums.org/showthread.php?t=89491](http://www.ubuntuforums.org/showthread.php?t=89491)

you can use sysv-rc-conf to change/disable any of the boot processes (including bluetooth).  however, it is very dangerous if you are not careful, so read and follow the above guide's suggestions carefully.

---

