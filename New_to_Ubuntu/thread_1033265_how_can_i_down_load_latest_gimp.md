---
title: "how can i down load latest gimp"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by blake7 on 2009-01-07
and why can i not do it though package manager 
also so the latest office

thank you

---

### Post by SunnyRabbiera on 2009-01-07
well to start off with what version of ubuntu are you running?

---

### Post by zipperback on 2009-01-07
> **blake7 said:**
> and why can i not do it though package manager 
also so the latest office

thank you


The package manager installs whatever version is available from your repositories.

If you want something that is newer than what is available from your repositories, then you just need to download the application from the developers website and follow the installation instructions.

For the latest version of gimp you can download it from:
[http://gimp.org/downloads/](http://gimp.org/downloads/)

And for the latest version of open office you can download it from:
[http://download.openoffice.org/index.html](http://download.openoffice.org/index.html)

- zipperback

---

### Post by blake7 on 2009-01-07
O  sorry i thought all 8.04 came to this forum

so thier you have it 8.04

cheers

ps is thier any point upgreading to 8.10

---

### Post by SunnyRabbiera on 2009-01-07
> **zipperback said:**
> The package manager installs whatever version is available from your repositories.

If you want something that is newer than what is available from your repositories, then you just need to download the application from the developers website and follow the installation instructions.

For the latest version of gimp you can download it from:
[http://gimp.org/downloads/](http://gimp.org/downloads/)

And for the latest version of open office you can download it from:
[http://download.openoffice.org/index.html](http://download.openoffice.org/index.html)

- zipperback

well for compile free packages, getdeb has the latest gimp:
[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

there are three packages to install but its simple enough.
For Open office its a bit trickier, you can get the packages from open office but there are so many .debs top go though.
For me I find adding this to the repository list does the job:
deb [http://ppa.launchpad.net/openoffice-pkgs/ubuntu/](http://ppa.launchpad.net/openoffice-pkgs/ubuntu/) hardy main

> **blake7 said:**
> O  sorry i thought all 8.04 came to this forum

so thier you have it 8.04

cheers

ps is thier any point upgreading to 8.10
Ubuntu 8.04 should be fine with the instructions I provided.
I only asked on the off chance you used an older version or 8.10 as we have a vast array of users here to cover.
as for Ubuntu 8.10 if your current system works then dont bother with 8.10, 8.04 will be supported for a while now though getting more up to date apps will be a bit tricky in the future, the only real drawback to Ubuntu is if you want to keep current you will need to preform a risky update unless you got hardy set up for backports.
But other then that, Ubuntu is solid.

---

### Post by blake7 on 2009-01-07
just tryed 
[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

and my package intstaller says    dependency is not satisfiable?????

arrr

what is all that is whale like does that mean

---

### Post by albinootje on 2009-01-07
> **blake7 said:**
> just tryed 
[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

and my package intstaller says    dependency is not satisfiable?????

arrr

what is all that is whale like does that mean

Please stop the complaining.

Ubuntu 8.10 does have gimp 2.6
You can also see whether Hardy backports provides it.

For Openoffice 3.0 on Ubuntu Hardy see :
[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

For the rest. Ubuntu 8.04 is a Long Term Support release, which means that it will *not* provide you with the latest software but will focus at stability and security.

---

### Post by SunnyRabbiera on 2009-01-07
> **blake7 said:**
> just tryed 
[http://www.getdeb.net/app/Gimp](http://www.getdeb.net/app/Gimp)

and my package intstaller says    dependency is not satisfiable?????

arrr

what is all that is whale like does that mean

you need to install not just the gimp package, but the others too.
install them in this order:
1) gimp-data
2) libgimp
3) gimp

MAKE sure its the ones for HARDY and not for INTREPID
also try removing your current gimp too.
here is a page with all three installers:
[http://www.getdeb.net/search.php?keywords=gimp](http://www.getdeb.net/search.php?keywords=gimp)

> **albinootje said:**
> Please stop the complaining.

Ubuntu 8.10 does have gimp 2.6
You can also see whether Hardy backports provides it.

For Openoffice 3.0 on Ubuntu Hardy see :
[http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04](http://www.howtoforge.com/how-to-install-openoffice-3.0.0-on-ubuntu-8.04)

For the rest. Ubuntu 8.04 is a Long Term Support release, which means that it will *not* provide you with the latest software but will focus at stability and security.

Hey dont be so rude, he has a valid issue here, hes a newcommer he wont know of things like dependencies,

---

### Post by albinootje on 2009-01-07
> **SunnyRabbiera said:**
> 
Hey dont be so rude, he has a valid issue here, hes a newcommer he wont know of things like dependencies,

The OP is the one being demanding.
You can't expect the newest software being available in a LTS release.

And getdeb is a volunteer project, I've seen several packages there which were stopped being maintained because of lack of time.

---

