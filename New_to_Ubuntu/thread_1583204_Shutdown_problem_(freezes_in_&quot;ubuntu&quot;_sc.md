---
title: "Shutdown problem (freezes in &quot;ubuntu&quot; screen)"
date: 2010-09-27
forum: New to Ubuntu
---

### Post by Tumetsu on 2010-09-27
So I was installing Ubuntu Netbook Remix for my friend's laptop today and everything went well except the shutdown of the system won't work correctly. Shutdown process stops in the screen of "Ubuntu" text and won't go away even after a while. Restarting seems to work fine though.

I'm not sure did this happen whole time during the process. It won't work with Live USB either though. I also did some changes like updated the kernel image to the today's version from kernel.ubuntu.com.

The computer model is:
Packard Bell Easynote V5908 D
The live usb shutdowns correctly in my netbook which also has Ubuntu NBR.
It looks like Ubuntu actually shutdowns, since when I press Esc in the screen it finally says "Power down" or something along those lines. So perhaps it's somekind of driver problem?

More information will be provided if needed.

Thanks :)

---

### Post by andrewthomas on 2010-09-28
look in /var/log/messages for the line

```
kernel: Kernel logging (proc) stopped.
``` and note the messages directly before.

Are they close in time?

try to shutdown using

```
sudo shutdown -h now
```

Does this result in the same hang?

---

