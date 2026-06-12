---
title: "Is it possible to run cron tasks silently??"
date: 2009-04-30
forum: New to Ubuntu
---

### Post by geokok1981 on 2009-04-30
Hey, I have created some automated backup tasks using rsync. 
I added these to cron using "Schedule tasks" app from add/remove.

Everything works like a charm but everytime rsync is being automatically
executed a terminal pops up and showing what is going on.

I was wondering if there was a way to still have the tasks executed
completely in the background, without terminals or any other indications. 
(or at least without requiring to hit enter to close the terminal window).

Thanks in advance.

---

### Post by Pisi-Deff on 2009-04-30
You could try adding '> /dev/null' (without the quotes) at the end of the task/command. This would send all the text into... nothingness.

I don't know if it will work though ;)

---

### Post by geokok1981 on 2009-04-30
> **Pisi-Deff said:**
> You could try adding '> /dev/null' (without the quotes) at the end of the task/command. This would send all the text into... nothingness.

I don't know if it will work though ;)

The app has already ticked /dev/null/ 2>&1 so I guess that's not it my friend.

---

### Post by abhiroopb on 2009-04-30
What is the rsync command? I am running about three rsync commands using cron (albeit with gnome-schedule manager as a front end) and it works fine, the command never show up.

---

