---
title: "Installing HP Laserjet P1007"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by pkj on 2010-01-10
Hi,

Unable to make HP Laserjet P1007 work with Ubuntu 9.10

Installation shows succesfull and the printer icon also appears in the list of available printers. However, on firing a print, the job appears in the printer queue for a few seconds and thereafter vanish, withoud printing the actual page

Tried HPLIP also, but installation remains unsuccessful with the following error at BUILD and INSTALL stage
error: Configure failed with error: General/unknown error

Any help

pkj

---

### Post by oldos2er on 2010-01-10
There's no need to compile hplip, it's in the repositories. ```
sudo apt-get update && sudo apt-get install hplip
```

---

### Post by Methuselah on 2010-01-10
Another user had a similar problem and it was a permissions issue.
It seems that the default permissions in 9.10 doesn't put users in lp group.
AFAIK, the current version of CUPS **requires** permission of root:lp 0660 on /dev/lp0 so you won't be able to print unless you are root or a member of lp.

Open a terminal and do

```
sudo gpasswd -a **yourusername** lp
```
You know what to substitute for the bolded item. 
[There is also a GUI way to do this but I don't remember]

That should add your user to lp so it can access the printer device node.
Print something to test after doing that and mark thread solved if that fixed your problem.

All the best!

---

### Post by warfacegod on 2010-01-11
Make sure the printer is enabled.

System> Admin.> Printing> right click the printer icon> check enabled

---

### Post by pkj on 2010-01-11
Hi,

Printer seems to have been installed...However, when i fire a test page i get the message that the page has been successfully printed..However, no printout actually comes out...The print queue also shows job in the queue and it vanishesh after a while without actually printing

pkj

---

### Post by kanishkdudeja on 2010-09-21
Dude i had the same problem half an hour back. I checked the log of installation of hplip. Although the printer seemed to have got installed, still due to the absence of a network connection some packages were not downloaded by hplip. Check your log. After the installation does it tell u to replug ur printer ?

---

### Post by hencha on 2010-12-09
Hi
This worked for me.  Thanks a mill.

gabriel

---

### Post by hencha on 2010-12-09
Hi

THis worked fine for me.  THanks a mill.

gabriel

---

