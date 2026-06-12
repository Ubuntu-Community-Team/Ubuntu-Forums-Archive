---
title: "Dynamic Wallpaper Script.  Very simple!"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by x C0MMAND0 x on 2009-11-25
Hey all,

Attached is a script I just wrote which enables a dynamic wallpaper changing however often you would like.  It's one of my first scripts, so any way to make it simpler or more efficient please let me know.

All feedback welcome.

---

### Post by espanolachat01 on 2009-11-25
i'll try this one out...I've looking for this for some time...

---

### Post by jrrader on 2009-11-26
How about adding an endless loop and sleep?    That way wall papers could change every few minutes.

```

#!/bin/bash
until [ 1 -eq 2 ]; do

#your script

sleep 5m
done
```

Add it to startup applications and you'll have automatic switching every 5 minutes every time you log in.

---

### Post by pbrane on 2009-11-26
> **jrrader said:**
> How about adding an endless loop and sleep?    That way wall papers could change every few minutes.



Here is another version that does this.

```

#!/bin/bash
# script to rotate GNOME backgrounds

# set this to your delay time. see man sleep for info
delay=10m
# set this to you wallpaper directory
pixdir=$HOME/Pictures/wallpaper/

newbkgrnd="$(ls $pixdir | shuf -n1)"

# update gnome backgound in gconf
gconftool-2 -t string -s /desktop/gnome/background/picture_filename "$pixdir$newbkgrnd"

sleep $delay
exec $0

```

---

### Post by x C0MMAND0 x on 2009-11-27
> **jrrader said:**
> How about adding an endless loop and sleep?    That way wall papers could change every few minutes.

```

#!/bin/bash
until [ 1 -eq 2 ]; do

#your script

sleep 5m
done
```

Add it to startup applications and you'll have automatic switching every 5 minutes every time you log in.

In the instructions I wrote I said to add an entry in crontab, which is and endless loop if you set it to run every minute.  I have it set to every 5 minutes and I'm loving it.

---

