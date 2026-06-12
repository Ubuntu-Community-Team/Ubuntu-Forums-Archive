---
title: "Printer may not be connected ????"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by celticbhoy on 2008-12-28
Having a problem getting my Epson D92 printer to go in Ibex. when I plug it in Ibex finds it ok and installs a driver, however when I go to print the document print status applet says that the printer may not be connected, even though it is. I have tried setting the printer up manually using a driver I know to work (D68) but still get the same results.

Does anyone have any ideas on how to fix ???

BTW the printer works ok under a different distro on my dual boot.

](*,)

---

### Post by sqrooup on 2008-12-28
If all the drivers are present try the following (it worked for me on a Lexmark Z605):

Applications>Accessories>Terminal and type in; 

sudo /etc/init.d/cups restart

(If this doesn't work, try;

sudo /etc/init.d/cupsys restart

this is for earlier versions of Ubuntu and Linux, the filename was changed to "cups" for Ibex)

Let me know if this works

---

### Post by celticbhoy on 2008-12-28
Sorry no dice sqrooup.

I dont know if this may be a part of the problem, but I am using an Acer Aspire One netbook, and have installed the eee netbook applet, even though I dont actually run it. there were also some other fixes to get bits and bobs working as they should on the netbook, so as I say I dont know if one or more of these has messed about with something ???

---

