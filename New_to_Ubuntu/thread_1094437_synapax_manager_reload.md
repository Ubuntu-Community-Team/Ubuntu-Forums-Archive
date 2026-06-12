---
title: "synapax manager reload"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-03-12
hi i reloaded the synapax manager and now most stuff i can search for on my other ubuntu computers are not showing up on this on. is their any way to undo this?


p.s. i meant synaptic

---

### Post by SunnyRabbiera on 2009-03-12
You mean synaptic?
Did you change any settings?

---

### Post by Ravernomina on 2009-03-12
I hit the reload button :l

---

### Post by drs305 on 2009-03-12
Do you have "All" selected in the left pane? Did you enable the same repositories you had selected previously (Settings, Repositories) and then hit "Reload"?

Edit: OK, forget the "Reload" part if you have done it. ;-)

---

### Post by Ravernomina on 2009-03-12
i still cannot find compiz manager or rkhunter in synaypic :l

---

### Post by Ravernomina on 2009-03-12
Itsonly shwoing things i have installed :L

---

### Post by SunnyRabbiera on 2009-03-12
compiz manager is listed as compizconfig-settings-manager in the repos
as for rkhunter if you use ubuntu 8.10 try not to use quick search as much and use the regular search button instead.

---

### Post by Ravernomina on 2009-03-12
its just showing what i have installed :l

---

### Post by SunnyRabbiera on 2009-03-12
try closing off synaptic and open a terminal and copy this command into it:
sudo apt-get update

---

### Post by avtolle on 2009-03-12
In Synaptic, in the left-hand column, is All selected or is Installed selected (when you are doing your search)?

---

### Post by Ravernomina on 2009-03-12
everything is on all

---

### Post by Ravernomina on 2009-03-12
the code did not work

---

### Post by SunnyRabbiera on 2009-03-12
Make sure synaptic is closed off before trying any commandline.
after the apt-get update command try another reload.
Something is screwy here though, maybe there is something wrong somewhere

---

### Post by Ravernomina on 2009-03-12
still not working

---

### Post by Ravernomina on 2009-03-12
ok now i can see everything when i do not search, but when i searc not i only see installed items

---

### Post by ajgreeny on 2009-03-12
I would ignore the "quick search" box and hit the "search" icon to bring up the full search box; it works much better.

---

