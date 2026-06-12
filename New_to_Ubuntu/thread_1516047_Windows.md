---
title: "Windows"
date: 2010-06-23
forum: New to Ubuntu
---

### Post by richard.scott-ettrick on 2010-06-23
Is there any way of using ubuntu to run Windows Programs. I am stuck with Virtual machine. I do not understand how it works. Is there anything else I can try? This is not to run games this is for farm office applications from Farmplan.

---

### Post by rraj.be on 2010-06-23
check out wine

---

### Post by phr0ze on 2010-06-23
An easy virtual machine system is VirtualBox. It's very friendly and easy to setup.

---

### Post by phr0ze on 2010-06-23
Ohh, and Wine is the alternative to a virtual machine. However, first you should try to find the program in the wine database on the wine website. It will tell you if the program runs at all or if you are wasting your time. It will also tell you any needed tricks to get the program to run. I try to only use wine for Platinum and Gold supported programs because silver is just too buggy.

Finally,

I like to see if I can find an alternative program that runs in ubuntu, instead of trying to get windows programs to work.

---

### Post by Picro on 2010-06-23
WINE should solve your problem. Do check out [http://appdb.winehq.org/](http://appdb.winehq.org/) for a searchable list of compatible programs, with easy to understand ratings: Platinum/Gold/Silver/Bronze/Garbage.
To install, simply fire up your terminal and enter 
```
$sudo apt-get install wine
```

Cheers!

---

### Post by ronnielsen1 on 2010-06-23
> WINE should solve your problem. Do check out [http://appdb.winehq.org/](http://appdb.winehq.org/)  for a searchable list of compatible programs, with easy to understand  ratings: Platinum/Gold/Silver/Bronze/Garbage.
You can try it but it's rated garbage which means it probably won't work.

[http://appdb.winehq.org/objectManager.php?sClass=application&iId=3471](http://appdb.winehq.org/objectManager.php?sClass=application&iId=3471)
[http://appdb.winehq.org/objectManager.php?sClass=application&iId=10980](http://appdb.winehq.org/objectManager.php?sClass=application&iId=10980)

---

### Post by bwallum on 2010-06-23
Farmplan won't run in Wine and the software vendors won't help either. They will try to sell you a Windows box however...

---

### Post by philinux on 2010-06-23
> **richard.scott-ettrick said:**
> Is there any way of using ubuntu to run Windows Programs. I am stuck with Virtual machine. I do not understand how it works. Is there anything else I can try? This is not to run games this is for farm office applications from Farmplan.

I would suggest dual booting and stick with windows for this software.

---

### Post by richard.scott-ettrick on 2010-06-23
Wine doesn't work with Farmplan Programs.

---

### Post by bwallum on 2010-06-26
> **richard.scott-ettrick said:**
> Wine doesn't work with Farmplan Programs.
Virtual Box does although you need an authentic Windows licence and the commercial FarmPlan software.

---

