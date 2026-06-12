---
title: "conky start up"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by rm06 on 2009-08-16
I recently upgraded my computer and am now running 64 bit 9.04. I can't seem to find a way to get my conky to start the way I have previously configured it.

I was having troubles with borders around the conky display and had .conky_start.sh on my startup programs to delay execution:

#!/bin/bash
sleep 20 && conky;
chmod a+x .conky_start.sh

My startup program command appears correct:

/home/me/.conky_start.sh

But it is not executing. Via terminal I can manually execute by either "sh .start_conky.sh" or simply entering "conky" and it comes up properly.

---

### Post by stoogiebuncho on 2009-08-16
There's an esier way to get rid of the window shadowing, and then you can just start conky normally (with the "conky" command) on startup.

1) install [compizconfig-settings-manager]("apt:compizconfig-settings-manager")

2) Open it (System > Preferenecs)

3) Go to (or search for) Window Decoration

4) Under "Shadow Windows", add this ```
(any) & !(class=Conky)
```

That's it.  I attached a screenshot so you can see the settings.

---

