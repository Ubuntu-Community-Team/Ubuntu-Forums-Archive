---
title: "help modifying this script for emptying the chromium cache"
date: 2010-10-02
forum: New to Ubuntu
---

### Post by rburkartjo on 2010-10-02
i have written a script for emptying the chromium cache. works great

#!/bin/bash
echo  xxxx | sudo -S rm -rf /home/ray/.cache/chromium
notify-send "The script has finished"

how can i make this run every time i close the browser.

tks

---

### Post by TeoBigusGeekus on 2010-10-02
Right click the menus->edit menus.
Find internet, go to Chromium launcher and click edit.
Replace its launching command, which must be something like
```
chromium
```
with
```
chromium; sh /path/to/your/script.sh
```

---

### Post by Hippytaff on 2010-10-02
Will that clear it everytime it starts rather than stops...not trying to pick holes, just learning :-)

---

### Post by TeoBigusGeekus on 2010-10-02
> **Hippytaff said:**
> Will that clear it everytime it starts rather than stops...not trying to pick holes, just learning :-)

After chromium is terminated the script will be run, so, yes, cache will be cleared after chromium stops.

---

### Post by Hippytaff on 2010-10-02
Oh yeah...DOH! *Embaraced face emoticon*

---

