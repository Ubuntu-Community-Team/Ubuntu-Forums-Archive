---
title: "Configuring UpdateManager"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by talonstriker on 2008-12-12
Is there a way to configure the UpdateManager applet (GNOME) so that it only runs* once per week or so?  UpdateManager is taking up quite a bit of memory and I don't want it running all the time.

*By runs, I mean runs.  Not check for updates.

---

### Post by PriceChild on 2008-12-12
5Mb of memory?

You could stop it starting up at all and get updates manually by starting it from system admin?
To do this, system > preferences > settings, and uncheck update notifier there.

---

### Post by Izek on 2008-12-12
> **PriceChild said:**
> settings

*cough* sessions

You also may want to uncheck bluetooth and assistive visual whatever it is, and the remote desktop too. (if you don't use them)

---

### Post by RomanIvanov on 2008-12-12
Applications -> System -> Synaptic Package Manager
menu Settings -> Repositories -> tab "Updates"

---

### Post by talonstriker on 2008-12-14
> **PriceChild said:**
> 5Mb of memory?

You could stop it starting up at all and get updates manually by starting it from system admin?
To do this, system > preferences > settings, and uncheck update notifier there. The reason why I wanted it to run once per week or so was because if I completely disable the applets, I'll probably never bother to update.

---

### Post by Izek on 2008-12-14
[http://gnome-schedule.sourceforge.net/](http://gnome-schedule.sourceforge.net/)

In terminal: **sudo apt-get install gnome-schedule**

[Found Out About It Here](http://maketecheasier.com/easy-way-to-schedule-and-automate-tasks-in-ubuntu/2008/06/16)

---

