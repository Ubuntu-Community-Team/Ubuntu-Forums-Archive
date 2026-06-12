---
title: "gimp plugin"
date: 2009-11-09
forum: New to Ubuntu
---

### Post by dzon65 on 2009-11-09
Does anyone know which Gimp plugin I need to colorize multiple images at once?I've got david's batch installed but it doesn't seem to do the job.

---

### Post by Paddy Landau on 2009-11-09
I don't know the answer, but if you can't get an answer and you're comfortable using the terminal, check *convert* and *mogrify*. You may have to install *imagemagick* first (in the repositories).

---

### Post by dzon65 on 2009-11-09
Paddy,I installed imagemagick but couldn't find any of the others.Perhaps they aren't available in 9.10 anymore.

---

### Post by Paddy Landau on 2009-11-09
> **dzon65 said:**
> Paddy,I installed imagemagick but couldn't find any of the others.
*convert* and *mogrify* are part of ImageMagick. If you've installed *imagemagick*, then you have *convert* and *mogrify*.

Go to terminal and enter the commands *man convert* and *man mogrify* to find out how to use them. (They're almost identical, except that *convert* makes a modified copy, whereas *mogrify* changes the file itself.)

Also enter *man imagemagick* to find out what else is available.

---

