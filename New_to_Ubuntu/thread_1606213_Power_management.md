---
title: "Power management"
date: 2010-10-26
forum: New to Ubuntu
---

### Post by tmcthree on 2010-10-26
Hi, I'm very new to Ubuntu, so be gentle with me.

I use my computer mostly for rendering graphics. As I'm sure you know, this involves the computer sitting alone for a few hours. I was wondering if there's any way to set the computer to switch off after. 

I've tried to use the power management settings. But it seems to consider "idle" as time when there is no user input. So it will switch off during the rendering. Is there any way to get it to switch off after the cpu becomes idle for a certain amount of time, or something like that?

---

### Post by TeoBigusGeekus on 2010-10-26
[http://ubuntuforums.org/showthread.php?t=530973]("http://ubuntuforums.org/showthread.php?t=530973")

---

### Post by lavinog on 2010-10-26
Save the following to a file called waitidle.py:
```

#! /usr/bin/env python


IDLE_LOAD=0.2
DELAY_MINUTES=5

import os
import time

def isidleload():
	"""Returns True if all three loadavg's
	are less than IDLE_LOAD"""
	
	for loadavg in os.getloadavg():
		if loadavg >= IDLE_LOAD:
			return False

	return True


if __name__ == '__main__':
	while not isidleload():
		time.sleep(DELAY_MINUTES * 60)

```

You can then do something like:
```

sudo -i
python waitidle.py; halt

```

---

