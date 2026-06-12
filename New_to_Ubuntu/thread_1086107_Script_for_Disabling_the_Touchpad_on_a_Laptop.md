---
title: "Script for Disabling the Touchpad on a Laptop"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Qsl1pknotp on 2009-03-03
This should be a relatively easy problem, but I can't seem to figure it out.  I have created two separate scripts.  One Disables my TouchPad, while the other Enables it.  However, I would like to have it Disable if I plug in my USB Mouse, and have it Enable when I take the mouse out of the Laptop's USB Port.  I am using "Sudo modprobe -r psmouse" to remove, and "sudo modprobe -a psmouse" to enable it.  Thanks for any help :).

---

### Post by Roanoke on 2009-03-03
Well, it seems you know the necessary commands. See this [guide](http://ubuntuforums.org/showthread.php?t=502864) to find out how to run commands when a device is plugged in. You just have to make two bash scripts, which would look something like this:
```

#!/bin/bash

[insert command here]

```

---

### Post by Qsl1pknotp on 2009-03-03
> **Roanoke said:**
> Well, it seems you know the necessary commands. See this [guide](http://ubuntuforums.org/showthread.php?t=502864) to find out how to run commands when a device is plugged in. You just have to make two bash scripts, which would look something like this:
```

#!/bin/bash

[insert command here]

```


Hey, thanks for the help.  Unfortuneately, I still can't get the script to work properly.  My code is

```

ACTION=="add", SUBSYSTEM=="usb_device", SYSFS{idVendor}=="041e", SYSFS{idProduct}=="1053", RUN+="/home/(name)/bin/DisableTPad"

```

However, when I plug in my mouse, the TouchPad doesn't disable unless I manually run the script.  Is there anything else I can try? Once again, thanks for the help.

---

### Post by llamabr on 2009-03-03
I'm afraid you're no longer an absolute beginner.  If no one comes along to answer this, you might consider taking it to a more appropriate forum.  I think there's one for peripherals up there.

Good luck.

---

### Post by Qsl1pknotp on 2009-03-03
Oh ok.  Thanks a lot.  (How do I close a thread so no one else will be wasting time answer the question?)

---

### Post by Roanoke on 2009-03-03
Is your script chmoded correctly (+x)? Maybe your home dir is only readable by you?

---

### Post by Qsl1pknotp on 2009-03-03
My scripts are all executable by Anyone accessing my computer. (775 was what I used). If this wasn't right, what should I use?

> **Roanoke said:**
> Is your script chmoded correctly (+x)? Maybe your home dir is only readable by you?

---

### Post by llamabr on 2009-03-03
It's not a permissions issue.  The script works fine, but it isn't being called by plugging or unplugging the mouse.  So you have to do it manually.

I'm not sure how to have it called by plugging in the mouse.

---

### Post by Qsl1pknotp on 2009-03-03
> **llamabr said:**
> It's not a permissions issue.  The script works fine, but it isn't being called by plugging or unplugging the mouse.  So you have to do it manually.

I'm not sure how to have it called by plugging in the mouse.

Ok.  Thanks for the help :).  I'll go ahead and move it to another forum.  Thanks though :).

---

