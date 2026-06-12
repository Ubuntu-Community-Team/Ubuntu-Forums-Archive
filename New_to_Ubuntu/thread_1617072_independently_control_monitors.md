---
title: "independently control monitors"
date: 2010-11-08
forum: New to Ubuntu
---

### Post by baller3c on 2010-11-08
hey guys, 
 
i have a laptop set up with a secondary monitor, running ubuntu 10.04. i already got the bigger, seperate monitor to be the primary, but is there a way to control when each one turns off independently? like, i want the secondary (laptop) monitor to stay on all the time, but the bigger primary (seperate) monitor to turn off after a minute. if i could get some direction as to which files need to be edited, and maybe a little insight into editing read-only system files? thanks!!

---

### Post by LowSky on 2010-11-09
sorry but I don't think that is possible. Maybe f your running two seperate X sessions, but even then the screen will wake if you move the mouse cursor over to it.

---

### Post by baller3c on 2010-11-09
that's fine, we want it to wake up when the mouse is moved. but when the mouse is inactive, we only want one of the monitors to shut off. 
 
is that possible?

---

### Post by cgb on 2010-11-09
Just about anything is technically possible with linux but how easy is another story..  Like LowSky mentioned I would look into running separate x sessions on multiple displays, somewhat of a multiseat configuration minus the extra keyboard and mouse.  The configuration is not that straight forward but I would imagine it could accomplish what you are looking for.

---

