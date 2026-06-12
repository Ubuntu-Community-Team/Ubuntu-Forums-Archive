---
title: "Loading and running a DVD for course work"
date: 2010-11-18
forum: New to Ubuntu
---

### Post by Syd Martin on 2010-11-18
p { margin-bottom: 0.21cm; }  I need to download and also run a DVD for my course work.
 I understand that the course work is all set up for use in the wonderful Microsoft environments forced on the multitudes of computer users, but I want to use my Ubuntu.
 As a newbee and a somewhat geriatric can anyone help me please.  
 

 I load the disc, go to computer and double click on CD/DVD Drive and then double click on autorun.exe or for that matter double click on install.exe and I get the following message.
 

                                                              
Archive:  /media/DVD00133/autorun.exe 
 [/media/DVD00133/autorun.exe] 
   End-of-central-directory signature not found.  Either this file is not 
   a zipfile, or it constitutes one disk of a multi-part archive.  In the 
   latter case the central directory and zipfile comment will be found on 
   the last disk(s) of this archive. 
 zipinfo:  cannot find zipfile directory in one of /media/DVD00133/autorun.exe or 
           /media/DVD00133/autorun.exe.zip, and cannot find /media/DVD00133/autorun.exe.ZIP, period. 



Hope this is enough information, if I have to use the terminal can I request that you make it idiot proof for me to follow

---

### Post by Mark Phelps on 2010-11-18
You can't just run MS SW in Linux, it doesn't work that way.

You have to install Wine (or something similar) first, and after that is set up, you have to use Wine to run the application.

PLUS, Wine will only work with SOME MS Apps.

Before you try this again, go to the link below and do a search on the app name and version you want to install:

[http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true]("http://appdb.winehq.org/objectManager.php?sClass=application&sTitle=Browse%20Applications&sOrderBy=appName&bAscending=true")

If the search doesn't find anything, or if you get a rating of Garbage or Bronze, you're wasting your time as the app will not do what you want.

---

