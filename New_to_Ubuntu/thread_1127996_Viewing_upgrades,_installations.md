---
title: "Viewing upgrades, installations"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by patman0623 on 2009-04-17
Is there a command line or GUI program/command for which I can view which I can view my upgrades and installations on? 

(on a note: I need this, as, among other things, I am worried I have both 64 bit flash installed as well as nspluginwrapper :oops:)

---

### Post by Elfy on 2009-04-17
You could use this in terminal - gives line with i if package installed

```
dpkg-query -l *packagename*
```

Or you could use aptitude in a terminal
```
sudo aptitude
```

Or you could use synaptic from the sys admin menu.

---

