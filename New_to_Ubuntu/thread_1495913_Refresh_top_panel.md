---
title: "Refresh top panel"
date: 2010-05-28
forum: New to Ubuntu
---

### Post by cosaki on 2010-05-28
Hi,

At every boot (Lucid), my top panel looks like the attached screenshot.  The WiFi indicator is cut off, the battery indicator is on there 1.5 times, and the volume indicator is on there twice.  The battery and volume indicators that are on the right side don't do anything.  How do I get rid of them?  I am afraid of trying to remove them because I couldn't find them on the list under "add to panel"

Thank you!

---

### Post by cariboo on 2010-05-28
Try:

```
killall gnome-panel
```

in a terminal, to see if that solves your problem.

---

### Post by daimaru on 2010-05-28
I have experienced the same problem .. double volume control etc. Kinda weird bug.:popcorn: First time I saw this was with 10.04. Laptop has same problem. Weird. Both have nvidia. Nobody else experienced this problem yet ?

---

### Post by MCVenom on 2010-05-28
I've had weird panel corruption when booting up sometimes also. Sometimes a reboot will fix it or I'll just remove and re-add the panel elements.

---

### Post by Miljet on 2010-05-28
Had the same thing a couple of weeks ago. A reboot fixed it and it hasn't shown up again, ----yet.  I have Intel graphics though so it is not just an Nvidia problem.

---

### Post by cosaki on 2010-05-28
> **cariboo907 said:**
> Try:

```
killall gnome-panel
```

in a terminal, to see if that solves your problem.

Thanks :P This worked great!  I will mark the thread solved.

---

### Post by daimaru on 2010-05-29
> **cosaki said:**
> Thanks :P This worked great!  I will mark the thread solved.
well its not relly solved now is it .... just restarting my panel is not what i call a fix .. if it happpens everytime i start ubuntu.. well guess that works for u but i would sure like to have a real bug fix here that does not make this problem show up in the first place

---

### Post by wojox on 2010-05-29
> **daimaru said:**
> well its not relly solved now is it .... just restarting my panel is not what i call a fix .. if it happpens everytime i start ubuntu.. well guess that works for u but i would sure like to have a real bug fix here that does not make this problem show up in the first place

Try:

```

gconftool --recursive-unset /apps/panel
pkill gnome-panel

```

---

### Post by daimaru on 2010-05-29
thanks [wojox]("http://ubuntuforums.org/member.php?u=802919") next time the problem  creeps up ill give it a  try .

---

