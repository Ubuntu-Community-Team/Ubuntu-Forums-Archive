---
title: "running already installed games."
date: 2009-06-19
forum: New to Ubuntu
---

### Post by brianhillman on 2009-06-19
i have many games installed on windows partition and was wondering how to play the POW doesnt seem to have a feature to play preexisting games. I tried wine and the screen flashes quickly 3-5 times then it goes back to normal. The game is COD4

---

### Post by Hospadar on 2009-06-19
You really can't run games installed on your windows partition in wine, due to config locations, registry setup, etc, etc.

You'll have to actually install the game in wine, this will put a copy of the game in your ~/.wine/drive_c/somewhere and you should be able to run it (assuming it works in wine)

You might want to go to the wine website and check the "appdb" for program compatability

---

### Post by 123456789123456789123456 on 2009-06-19
not only that, but since Wine, Crossover, and other programs are emulation in some sorts, the configuration files are sometimes converted so Ubuntu can understand them, it is the same issue, as where you can't take preinstalled windows games from one partition and play them in another windows partition, assuming you have two differnt copies of windows on a machine, the only exception to this rule, would probably be solitare, it may be possible to play games called portable apps in wine, as they don't have to be installed to run.

---

