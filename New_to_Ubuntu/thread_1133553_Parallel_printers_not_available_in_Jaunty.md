---
title: "Parallel printers not available in Jaunty"
date: 2009-04-23
forum: New to Ubuntu
---

### Post by luvinit on 2009-04-23
Hi, I am trying to install my printer (HP deskjet 550c) via system>administration>printing in Jaunty but parallel printers, LPT#1 don't seem be available. I have tried all combinations of packages, but it makes no difference. Anyone have any ideas on how to get this to work?

---

### Post by Terrycymru on 2009-04-23
> **luvinit said:**
> Hi, I am trying to install my printer (HP deskjet 550c) via system>administration>printing in Jaunty but parallel printers, LPT#1 don't seem be available. I have tried all combinations of packages, but it makes no difference. Anyone have any ideas on how to get this to work?

Select "Other" and enter this in the box:
parallel:/dev/lp0

You will then get a list of Manufacturers. Good luck!!

I had temporary printing problem after upgrade to Jaunty but a reinstall of printer and reboot solved the problem.

---

### Post by luvinit on 2009-04-23
Thank you very much.  :)

---

### Post by luvinit on 2009-04-23
Ok, I was able to select the drivers, of which there is the usual big choice that you get in Ubuntu, but the "busy" light stays on on the printer and I get a not connected message when I try to print. The printer works fine on other OS's but not Ubuntu Jaunty.

---

### Post by pancho2500 on 2009-04-24
i have the same problem, in dev folder there isn´t a lp0. We need help please

---

### Post by lkraemer on 2009-04-24
I am using the following USB to Parallel Cable with my Desktop and
my HP 712C with Ubuntu 8.04LTS.  It works great!  What about trying
a cable like this?

[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1270853&CatI](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1270853&CatI)

lkraemer

---

### Post by pancho2500 on 2009-04-24
the problem is with the 9.04 version with 8.04 and 8.10 the parallel port of the mainbord works very well, 9.04 the printer asistant doesn´t have the lpt option :(

---

### Post by luvinit on 2009-04-25
I have submitted a bug report about this to launchpad. The suggestion of the usb parallel cable is useful; I didn't even know that they existed, but it is better to have a proper solution.

---

