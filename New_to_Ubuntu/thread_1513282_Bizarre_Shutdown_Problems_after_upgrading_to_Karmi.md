---
title: "Bizarre Shutdown Problems after upgrading to Karmic"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by BassKozz on 2010-06-19
After upgrading my NAS box (see sig for specs) from Jaunty to Karmic, I am experiencing a bizarre shutdown problem where my computer won't shutdown completely when the shutdown command is being issued from a Bash script.

Shutdown works fine if I manually click on it from the panel drop-down (top right), it also works fine if I issue it directly:
```

sudo shutdown -h now

```

However it won't shutdown completely when run from a Bash script, even a script as simple as this:
```

#!/bin/bash
sudo shutdown -h now

```

It goes through the motions and shuts down ubuntu and I hear the clicking sort of noise I normally hear when the computer shuts down, the keyboard LED's turn off (num lock)...
except the power LED stays on, on the tower, and I can still hear fans running, and the screen stays on and black (monitor doesn't go into power-saving mode because it thinks its still connected to an active computer). 

Normally this wouldn't be such a big deal, however I use a more complex script to turn my computer off at night: [http://basskozz.wordpress.com/2009/02/04/advanced-shutdown-script-part-2-check-for-running-services/](http://basskozz.wordpress.com/2009/02/04/advanced-shutdown-script-part-2-check-for-running-services/)

I've already tried adding **noapic** to my kernel boot (grub) and that didn't help.  Any other ideas?

Thanks in advance,
-BassKozz

---

