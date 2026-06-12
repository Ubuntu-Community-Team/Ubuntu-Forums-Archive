---
title: "error opening synaptic in Ubuntu"
date: 2011-06-08
forum: New to Ubuntu
---

### Post by MR. X holland on 2011-06-08
hey, i have a problem with synaptic.
when i try to start it, a window pops up, which says:
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.
can anyone please help me out?

---

### Post by Rubi1200 on 2011-06-08
Hi and welcome to the forums :-)

Open a terminal and post the output of this command please:

```
cat /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
```

---

### Post by MR. X holland on 2011-06-08
cat /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main
ain

---

### Post by el_koraco on 2011-06-08
> **MR. X holland said:**
> cat /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
# deb [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main
# deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main
ain

click ALT F2 and run the command ```
gksudo gedit /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
```

A gedit window will open. Then look at the line 

> # deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main
ain

and delete the "ain" portion, so that you have 


> # deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main

Save the file, and run a 

```
sudo apt-get update

```

in the Terminal. Synaptic will work.

---

### Post by Rubi1200 on 2011-06-08
Hi,

use this command to edit the file:

```
gksudo gedit /etc/apt/sources.list.d/team-xbmc-ppa-maverick.list
```

> deb-src [http://ppa.launchpad.net/team-xbmc/ppa/ubuntu](http://ppa.launchpad.net/team-xbmc/ppa/ubuntu) maverick main
[COLOR=Red]ain[/COLOR] 	

Remove the ain from the last line then save and close.

Hopefully this should resolve the problem.

---

### Post by MR. X holland on 2011-06-08
yes, it worked, thank you very much!

---

### Post by Rubi1200 on 2011-06-08
Excellent! Glad it worked for you :-)

Please mark this Solved using the Thread Tools near the top of the page.

---

