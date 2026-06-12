---
title: "[SOLVED] Gutsy: NM Applet not refershing networks afte suspend ?!"
date: 2007-10-23
forum: Networking &amp; Wireless
---

### Post by yamagami on 2007-10-23
After upgrading to Gutsy (7.10) I noticed that after i put my laptop into suspend and change locations (i.e., leaving the net caffe and going back home) the applet doesn't always refresh the networks to show my home one, and stays locked on the (now unavailable) network it was on before the suspend.
In 7.04 all was quite perfect....

Has anyone ran into this problem as well?
Thanks
Harel

---

### Post by Rotarychainsaw on 2007-10-25
ME! What kind of wireless do you have? I have ipw3945 (or whatever it is).

---

### Post by jzimm on 2007-10-26
I confirm, same thing here (ipw3945, amd64). I have not yet traced the source of this problem.

---

### Post by janno on 2007-10-28
Yeap, same here - dell d620 with ipw3945 wireless.

Anyone has a solution for that?


J.

---

### Post by tommoyer324 on 2007-10-29
The solution I have discovered (somewhere on the forums here) was to create a script that basically resets the module and NM upon resume. Here is the file

```
#!/bin/sh

# Stop NetworkManager
/etc/dbus-1/event.d/25NetworkManager stop

# Unload the ipw3945 driver
/sbin/modprobe -r -f ipw3945

# Reload the ipw3945 driver
/sbin/modprobe ipw3945

# Restart NetworkManager
/etc/dbus-1/event.d/25NetworkManager restart
```

This file should go in ```
/etc/acpi/resume.d/
```.  I call it *99-reload-wireless.sh* and make it executable

```

sudo chmod 755 /etc/acpi/resume.d/99-reload-wireless.sh

```

What this does is when the acpi event for resuming occurs this script is executed.  It will stop NM, unload and reload the ipw3945 driver, and then restart NM.  It takes a second, but it works for me.

---

### Post by toorima on 2007-11-02
I don't have /etc/acpi.d/resume.d/ but I do have /etc/acpi/resume.d/ and when I put the script in there my suspend works somewhat better, before, wireless would just hang no matter what I did, no its enough with a modprobe ipw3945

---

### Post by yamagami on 2007-11-12
THANKS for that script. i had to change the driver name to ipw2200 on my toshiba m55 but other than that it works perfectly. until this issue is sorted its gonna save the hassle of restarts...

---

### Post by MetroPietro on 2008-03-22
Thanks for the detailed solution! For those of us who are newbies and want to find out the name of the module we should unload/reload, I think it is most useful to use the lsmod command. pecking though the manpages, my first guess was to use modprobe -c, but the (massive) output does not identify the module.

---

