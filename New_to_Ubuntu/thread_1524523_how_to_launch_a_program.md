---
title: "how to launch a program"
date: 2010-07-05
forum: New to Ubuntu
---

### Post by Chad Olson on 2010-07-05
Some times my blueman applet won't work and I get a message that It can't work because bluez is not running. I have to reboot my computer some time up to four times before it will run I was wondering if I can launch the program in the terminal or create a launcher.

---

### Post by -humanaut- on 2010-07-05
you can try this alt+f2 then type /usr/bin/bluez
from a terminal you could type exec /usr/bin/bluez &

---

### Post by Chad Olson on 2010-07-20
That didn't work I need to know exactly where the program is located on my computer.

---

### Post by tarps87 on 2010-07-20
I would suggest uninstalling bluez as they are performing the same task, how did you install it?

---

### Post by rustutzman on 2010-07-20
If you installed it via synaptic package manager you can go back into the manager highlight the package and look at properties. One of the tabs will show you where all of the files were put.

Russ

---

### Post by Chad Olson on 2010-08-31
> **rustutzman said:**
> If you installed it via synaptic package manager you can go back into the manager highlight the package and look at properties. One of the tabs will show you where all of the files were put.

Russ

I got it now I found out that if I unplug then reinsert the bluetooth adapter it relaunches bluez

---

