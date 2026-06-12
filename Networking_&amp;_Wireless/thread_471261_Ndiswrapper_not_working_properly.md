---
title: "Ndiswrapper not working properly"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by celeron D on 2007-06-11
I installed ndiswrapper on ubuntu 6.06 LTS dapper drake (x86 version) and it installed correctly. I did ndiswrapper -i and installed the .inf file from the driver CD of my wireless PCI card. Then, when I did ndiswrapper -l (i think it was -l) anyway, it said that the driver was invalid. So, I tried the drivers from the CD for Win. 2000/XP/98/95/me...and none of them worked. I tried Firefox, but it said "cannot find the server" What else can I try to get my PCI network card working?

Thanks:)

---

### Post by kevdog on 2007-06-11
First consult the documentation at the ndiswrapper site.  This should get you started
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,installation/)


You need to know the make or your card,
Chipset: Find with lspci
Revision: Find with lscpi -n

Taking this info, go to the list of supported cards and find yours. Download the driver they recommend and install it.  Please re-read their comments on the driver, sometimes it contains some tricks!
[http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/](http://ndiswrapper.sourceforge.net/joomla/index.php?/component/option,com_openwiki/Itemid,33/id,list/)

---

### Post by celeron D on 2007-06-11
When I installed ndiswrapper, I looked at that page and that entire wiki part of that website, and i did lspci and lspci -n, and I found the PCI I.D. and all that. After I got the driver, (I tried the driver from the site, and from the card's driver CD) after ndiswrapper -l, it said "Driver Invalid" and it did not work. Is there anything else I can try?

Thanks for your help so far

---

### Post by carcioni on 2007-06-11
I just installed ndiswrapper on my Dell laptop, and I just 'borrowed' the .sys and .inf  files from the driver that Windows was using. Seems to be working ok. You do need both files available, and I am not sure what the behaviour of ndiswrapper is if it can't find the .sys file.

Cheers
C

---

### Post by celeron D on 2007-06-11
I copied the .sys file that device manager in Windows was using from the C:\WINDOWS\System 32\... and I got the .inf file from the CD, and it still doesn't work saying  "Invalid Driver" Is tehre any other method that I can use to get my wireless PCI card recognized on ubuntu?

Thanks

---

### Post by kevdog on 2007-06-11
If you are getting the correct version of the driver -- I urge you to make sure you have the correct version -- make sure your ndiswrapper package is OK.  You may to compile from source if you are using an old version.

---

### Post by celeron D on 2007-06-11
Yes, the driver version is correct, and is the latest driver, and ndiswrapper is O.K., and correctly working. Could the problem just be that my card is not fully supported, even though it is on the list on ndiswrapper's site?

---

### Post by kevdog on 2007-06-12
Not to be rude but you havent told us anything about your wireless card, or chipset.  Sounds definitely like a driver problem, however I dont even know what driver you are using.

---

### Post by Sendervictorius on 2007-06-12
Have you already got an invalid driver loaded in error? 
"ndiswrapper -l" will give you a list of all drivers loaded up, invalid or not. "ndiswrapper -r <driver>" to remove a <driver>.

---

