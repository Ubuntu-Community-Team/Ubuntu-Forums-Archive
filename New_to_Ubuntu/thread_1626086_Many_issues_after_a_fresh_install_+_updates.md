---
title: "Many issues after a fresh install + updates"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by Maydie on 2010-11-19
Hi everyone,

So I installed ubuntu 10.10bits, everything went fine. So I log on for the first time and i see no problem.
I then install the updates then I reboot, and the nightmare started.

Here is a recap of the issues:

- the top and bottom panel, also some of the windows' menus are extremely ugly (I don't have that black beautiful panel anymore)

- the gnome terminal have an insane lag when I type, buffer is refreshed every 3 or 4 characters

- If I do ctrl + alt + f1 to go in console mode, I have to wait at least 5 minutes

- Boot time is insane (almost 10min), and I'm on a SSD

- Videos are unwatchable (extremely slow and laggy)


Here is my configuration:
Intel i7 920
6go RAM
OCZ summit 64gb SSD
nvidia gtx 285
creative sb x-fi

I installed ubuntu 10.10 64bits desktop version and the lastest nvidia drivers (260).
I tried a 3D game (Heroes of Newerth) and it ran perfectly fine.

Any clue on my issues?

Thank you very much.

---

### Post by cariboo on 2010-11-20
I would suggest you check  System->Administration->System Monitor, or open a terminal and type:

```
top
```

to see what is eating all your cpu cycles.

---

