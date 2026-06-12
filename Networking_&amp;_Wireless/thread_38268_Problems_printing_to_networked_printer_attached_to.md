---
title: "Problems printing to networked printer attached to windows machine"
date: 2005-05-30
forum: Networking &amp; Wireless
---

### Post by zoolfoos on 2005-05-30
I have an HP DeskJet 810C networked on a computer running Windows 2000. I have installed Print Services for Unix on the computer running windows and initially everything was fine. I set up another printer and created an LPD port for it. I then connected to it from the computer running Ubuntu (Hoary Hedgehog) I told it to connect via LPD (not SMB) and it worked fine. Then I went to print something today and most of the time the print job would get to the printer (I checked it on the other computer) but it would never print. I tried printing to the LPD printer from the windows computer but would have the same problems. I have tried connecting via SMB and updated Samba, but to no avail. Any help you can offer me will be appreciated.

Thanks!
Kevin

---

### Post by zoolfoos on 2005-05-30
Well, I fixed the problem. I uninstalled the Unix Printing Services, reinstalled them and then just started over again. No problems yet. To those of you who have taken the time to read my post, I thank you.

**EDIT**Continue below please... I seem to have been mistaken.**EDIT**

---

### Post by zoolfoos on 2005-05-31
I spoke too soon. 

Whenever the windows computer is shut down the LPD server does not work quite right the next time the computer is started, and has to be reinstalled. 
Often the print job doesn't get from my ubuntu system to the printer at all. When I tried printing via LPD from the windows computer I got an error in the printers queue It said: "Printer busy or error" and I noticed that under the "size" menu it would say something to the effect of "72.5 bytes/201K" which leads me to believe that it's not getting the entire print job for some reason. Reinstalling the LPD server does fix the problem but it's a huge pain to do that all the time. Again, I would greatly appreciate any advice or ideas that you have because, quite frankly, I have no idea what the problem is.

Thanks again!

---

