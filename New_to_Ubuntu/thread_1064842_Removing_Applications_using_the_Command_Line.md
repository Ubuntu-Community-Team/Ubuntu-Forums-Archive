---
title: "Removing Applications using the Command Line"
date: 2009-02-09
forum: New to Ubuntu
---

### Post by sillyboy on 2009-02-09
How does one remove an application with the command line?  I found this page ([http://www.ss64.com/bash/](http://www.ss64.com/bash/)) in the forums, but it does not give the whole command.  I am having problems with Glipper.  Every time I boot, I get the message that Glipper did not load correctly. This causes Firefox to freeze (monitor goes dim). Glipper does not show up in the Add/Remove Applications, though it is installed.  I get this message: **There is no matching application available.** Klipper shows up in the Add/Remove Applications, but I can't find it anywhere in Ubuntu to use it.  Using 8.04  Need help.  Thanks

---

### Post by drs305 on 2009-02-09
To remove it, you can run:
```
sudo apt-get purge glipper
```

If you want to find the run command:
```

which glipper

```

To find all the file locations:
```

whereis glipper

```

---

### Post by sillyboy on 2009-02-09
Thank you drs305.

---

### Post by sillyboy on 2009-02-09
I typed in **sudo apt-get purge glipper** and then rebooted.  Glipper is still in the Add To Panel list, and yes, I can still add it to the panel.
I'm lost...:(

---

### Post by drs305 on 2009-02-09
> **sillyboy said:**
> I typed in **sudo apt-get purge glipper** and then rebooted.  Glipper is still in the Add To Panel list, and yes, I can still add it to the panel.
I'm lost...:(

How did you install glipper?  If you run the *whereis* command do you get a result?

How about the results of this command - what is the result:
```

dpkg -l | grep "glipper"

```

---

### Post by sillyboy on 2009-02-09
I installed Glipper with SPM.  When I run "whereis glipper" I get this: **glipper: /usr/lib/glipper /usr/share/glipper**  When I run "dpkg -l | grep "glipper" I get: **ii  glipper                                    1.0-1ubuntu1                                         Clipboard manager for the GNOME panel**

Is there supposed to parenthesis around the app name? ](*,)

 Thanks

---

### Post by drs305 on 2009-02-09
Well, glipper is certainly still installed. I have poked around looking for a solution and there have been numerous bug reports submitted. Here is a possible solution - it won't remove glipper but it may get it working for you. It delays the startup time. If 8 doesn't work, increase it to 30 (or just try 30 first):

Backup and open for editing:
```

sudo cp /usr/lib/glipper/glipper /usr/lib/glipper/glipper.bak
gksudo gedit /usr/lib/glipper/glipper

```

Insert the lines in bold, then save the file:
```

#!/usr/bin/env python

# Glipper - Clipboardmanager for GNOME
# Copyright (C) 2007 Glipper Team
#
# This library is free software; you can redistribute it and/or
# modify it under the terms of the GNU Lesser General Public
# License as published by the Free Software Foundation; either
# ..... Omitted in post
# ..... continues below
# Free Software Foundation, Inc., 59 Temple Place - Suite 330,
# Boston, MA 02111-1307, USA.
#


[COLOR="DarkRed"][B]import time # <-- This line is new
time.sleep(8) # <-- This line is new. Change the 8 to for instance 30 if it did not help
[/B][/COLOR]
import gobject
gobject.threads_init()

# ... file contents continue....

```

---

### Post by sillyboy on 2009-02-09
OK drs305, I added those two lines and saved.  What does the 8 and 30 represent?  Thanks

---

### Post by sillyboy on 2009-02-09
I see...seconds.  Thanks again!

---

