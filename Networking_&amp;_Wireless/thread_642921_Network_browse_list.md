---
title: "Network browse list"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by lintoon on 2007-12-17
Has anyone had any conflicts or problems with the windows browse list/Master browser?

My browse list stops working.  Eg go to "My network places" in windows and nothing appears in the list.  I also get a "You do not have permission....." error message.  Whats strange is if I reboot the ubuntu box everything works.  I can connect to any windows machine and I can log onto the ubuntu box.  
This seems to work for the rest of the day.  When I come in to work tomorrow I will have to restart the ubuntu box again in order to get my browse list back.

I have checked my smb.conf for the master broswer setting and it is commented out.  

Any ideas??

---

### Post by lintoon on 2007-12-18
This must be a good one because no-one has replied.  I'm still stuck though.  Have to restart the ubuntu box every day.

I think i'll uncomment the line in smb.conf regarding master browser and set it to NO.  If that doesn't work I'll set one of the xp boxes to be master browser.  I'll post my results on the off chance it may help someone.  Might be in a couple of weeks though coz I'm jetting off to the sun for christmas. Yeehaaaaa.  Ahem.  Not that I'm excited.

---

### Post by lintoon on 2007-12-20
I uncommented the master browser line in smb.conf and set it to "No".
No change.  I still have to restart the ubuntu box in order to get my browse list back.

Any ideas??

---

