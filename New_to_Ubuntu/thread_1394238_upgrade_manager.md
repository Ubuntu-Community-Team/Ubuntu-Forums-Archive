---
title: "upgrade manager"
date: 2010-01-30
forum: New to Ubuntu
---

### Post by senorian on 2010-01-30
I saw the notice this moring in the task bar and clicked on" apply"
Nothing seemed to happen and so I started to look at all the apps that were to be upgraded and saw many that said
"dummy upgrade for FF3.5"
WTH is going on?

---

### Post by dearingj on 2010-01-30
Dummy upgrades are normal for Ubuntu. It allows the developers to rename a package, by uploading one with the new name and a dummy under the old name, and the dummy instructs your computer to install the new package. Nothing to worry about.

As for the updates apparently not being applied, what happens when you open up a terminal and enter (copy & paste): ?
```
sudo aptitude update && sudo aptitude safe-upgrade
```

---

### Post by senorian on 2010-01-30
Many thanks for the info about dummy upgrades and also the cli code for updating.
As soon as I supplied my password the updating began; and it is much more interesting than the GUI way.
I had to use google to find out which language your sig was written in..
Occitan
thanks

---

### Post by dearingj on 2010-01-30
Glad to hear the update seems to be working, at least with the cli :)
I don't know why nothing seemed to happen when you used the graphical updater. If you continue seeing this problem with the GUI version, I'd recommend filing a bug report on [launchpad.net]("http://www.launchpad.net/").

Did you also find out which book the quote in my sig is from?

---

