---
title: "crontab queries"
date: 2009-10-16
forum: New to Ubuntu
---

### Post by smileyguy on 2009-10-16
Why does the directory in which my user crontab file is located keep changing name? One minute it's at /tmp/crontab.SYbSMw/ the next minute (I assume after a change) the last bit of the directory name gets changed to some seemingly similarly arbitrary string?

ALSO - When I enter a new task in the Gnome-Schedule GUI, it doesn't get saved in that crontab file, but when I change the crontab via the nano editor (code: crontab -e) It appears sucessfully in Gnome-Sechedule? It seems that the GUI is doing something differently with it, like using 2 different cron files? Can I see that other cron file?

---

### Post by smileyguy on 2009-10-16
Sorry - just discovered it's only the "one off" tasks that don't get saved in my crontab file.

I know the one off tasks use the "at" command, so where do they get saved?

---

### Post by CharlesA on 2009-10-16
> **smileyguy said:**
> Sorry - just discovered it's only the "one off" tasks that don't get saved in my crontab file.

I know the one off tasks use the "at" command, so where do they get saved?

The reason the location changes is due to it being in the tmp folder. 

What command are you having problems with saving?

---

### Post by smileyguy on 2009-10-16
No more problems - just curiosity! I want to know where the "at" task commands get saved. I know recurrent tasks get saved in the crontab files (as I enetr them in Gnome-Schedule they appear when I check via crontab -e) **but** when I save a "run once" only task, it doesn't appear in the crontab file but still runs. Is it just magic or is it saved in a different file (than crontab)?

---

