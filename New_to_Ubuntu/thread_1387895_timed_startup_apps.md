---
title: "timed startup apps?"
date: 2010-01-22
forum: New to Ubuntu
---

### Post by bobin on 2010-01-22
How do I time my startup apps, like beagle starts after 10 sec of startup , the conky script after 20 sec? 
Is there any way to automate the visual effect( snow effect) in compiz at startup. Right now I have to press <super>F3 which is a bit tedious.

---

### Post by chewearn on 2010-01-22
You can add a script to the Start-up program list.  In the script, launch each program, followed by sleep # command, where # is the desired number of seconds to delay.  To simulate a Super+F3 key press, use xdotool.

Something like this:
```

#!/bin/bash

sleep 10
beagle &
sleep 10
conky &
sleep 10
xdotool key Super+F3

```

---

