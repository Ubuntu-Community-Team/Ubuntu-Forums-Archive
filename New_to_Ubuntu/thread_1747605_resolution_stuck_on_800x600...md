---
title: "resolution stuck on 800x600.."
date: 2011-05-02
forum: New to Ubuntu
---

### Post by Whitecolour on 2011-05-02
my laptop resolution is stuck on 800x600 with ubuntu running.
 
I found something online about this but the directions didn't work.
 
I'm using an asus n73jq if that relavent.

---

### Post by idoitprone on 2011-05-02
```
xrandr -q 
```

see if your monitor support higher resolution

---

### Post by Whitecolour on 2011-05-02
I got:

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 640 x 480, current 800 x 600, maximum 800 x 600
default connected 800x600+0+0 0mm x 0mm
   800x600        61.0* 
   640x480        60.0

---

### Post by inlovewithu on 2011-05-02
May be this thread will help you

[http://ubuntuforums.org/showthread.php?t=690760](http://ubuntuforums.org/showthread.php?t=690760)

---

### Post by KL_72_TR on 2011-05-02
> **idoitprone said:**
> see if your monitor support higher resolution
The monitor is able for 1920x1080 cording to this site: [http://www.notebookcheck.net/Review-Asus-N73JQ-Notebook.40939.0.html](http://www.notebookcheck.net/Review-Asus-N73JQ-Notebook.40939.0.html)
Maybe you should activate the drivers.

---

### Post by Whitecolour on 2011-05-03
> **KL_72_TR said:**
> The monitor is able for 1920x1080 cording to this site: [http://www.notebookcheck.net/Review-Asus-N73JQ-Notebook.40939.0.html](http://www.notebookcheck.net/Review-Asus-N73JQ-Notebook.40939.0.html)
Maybe you should activate the drivers.
 
How do I go about doing that?

---

### Post by EGamerHDK on 2011-05-03
Hit the Super or Windows key and search "Add" and select Additional Drivers. There should be some kind of graphics drivers there hopefully. Select them and activate. Good luck

---

### Post by Whitecolour on 2011-05-03
> **EGamerHDK said:**
> Hit the Super or Windows key and search "Add" and select Additional Drivers. There should be some kind of graphics drivers there hopefully. Select them and activate. Good luck

Ok, thanks. that worked.

---

