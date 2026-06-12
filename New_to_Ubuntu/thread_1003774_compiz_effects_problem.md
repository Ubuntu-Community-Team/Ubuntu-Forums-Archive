---
title: "compiz effects problem"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by LouisChappell on 2008-12-06
Hello, I've just installed ibex done the updates etc, I installed Desktop Effects in add/remove and I get an option saying 'Install Desktop Effects' above the effects level, however when I click the box I get a 'Command not found' error, so I can't change the effects to standard, extra or custom. I am using the Nvidia graphics driver version 177. 
I have spent about an hour looking on other topics and searching for some answers to no avail...
Please could someone let me know what the problem is and how to remedy it?
Thanks in advance.

---

### Post by lovelyvik293 on 2008-12-06
I think you don't have the drivers for your card.So just search for these graphic card drivers or look at system->administration->hardware drivers for the restricted drivers.

---

### Post by LouisChappell on 2008-12-06
I don't understand what you mean, I'm using the 177 driver, is that the problem? I have tried using the 173 driver but that doesn't make a difference, I would have thought it had more to do with a missing file I needed to install or something along those lines.

---

### Post by lovelyvik293 on 2008-12-06
Ohh you enabled the driver.No there is no problem with the drivers.But you ever tried the effect without the driver activation???My friend have the same driver but he is using the desktop effect without the drivers.If you have installed the Compiz configuration manager.??

---

### Post by LouisChappell on 2008-12-06
No I haven't tried it without the use of drivers yet, I'm not sure how to install compiz configuration manager as sudo apt-get install ccsm doesn't work, it just says 'E: Couldn't find package ccsm'

---

### Post by Kevbert on 2008-12-06
You can install the Compiz Manager by going to Applications-Add/Remove and search for CCSM and then select it and apply.  If you can't run compiz you may need to run compiz-check which can be found [[COLOR="Red"]here[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check").

---

### Post by LouisChappell on 2008-12-06
Thanks Kevbert, thats sorted it! Feel like such an idiot now haha, I as expecting more terminal goodness....
 Thanks too vik for the help.

---

