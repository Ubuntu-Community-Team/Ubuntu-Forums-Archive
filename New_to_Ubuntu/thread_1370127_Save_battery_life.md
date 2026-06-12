---
title: "Save battery life?"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by aceplayer97 on 2010-01-01
Recently I just switched from Windows XP to Ubuntu 9.10. In Windows XP I used to have around 1 hour and 30 minutes of battery life but now in Ubuntu I only have around 40 minutes of battery life. Is there anything at all that I can do to increase my battery life?(Besides dimming my screen because I already do that)

---

### Post by MelDJ on 2010-01-01
maybe try disabling compiz

---

### Post by abq911 on 2010-01-01
System -> Preferences -> Power Management
Might find some useful controls in there, don't have a laptop to check.

---

### Post by Max_Mackie on 2010-01-01
I know that disabling my wifi when I'm not online will increase my battery time by about 2 hours.
EEEPC 1002HA

---

### Post by jbrown96 on 2010-01-01
Use powertop. ```
sudo apt-get install powertop
``` and execute with ```
sudo powertop
```

It's really obnoxious because you need to run it every time you reboot. It will help you extend your battery life and tell you which programs are using it.

---

### Post by ehalls on 2010-01-04
Is there a way to downclock the computer? Because I only wants to read a pdf document, however, the fan is still going nuts...

---

### Post by citro_cell on 2010-02-05
> **ehalls said:**
> Is there a way to downclock the computer? Because I only wants to read a pdf document, however, the fan is still going nuts...

Try right-clicking on the upper panel and using "add to panel".  Find CPU frequency scaling monitor and ADD.  Now you can left-click your new icon and use the "powersave" option.  If you have dual-core, make sure to enable the powersave option on both CPUs.  Select the second CPU by right-clicking the icon and choosing preferences.  Select your other Monitored CPU and then as before change to powersave.  Good luck!!

---

