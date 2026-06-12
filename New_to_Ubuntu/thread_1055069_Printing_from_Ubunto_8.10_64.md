---
title: "Printing from Ubunto 8.10 64"
date: 2009-01-30
forum: New to Ubuntu
---

### Post by Joerice50 on 2009-01-30
HP K80 printer prints headers i.e. The first line of print is:

%!PS-adobe-3.0 ( then skips down a line and prints)
                %%LanguageLevel:  3 ( skips down another line|)
                                     %%DocumentSuppliedResources: (atend)


and then just undertakes an endless round of form feeds

I downloaded and installed a specific driver for the HP K80 from here:
[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html) 

but this has made no difference 

Any suggestions?


Joe Rice

---

### Post by LowSky on 2009-01-30
first turn off printer and detach power cord
then install hplip (its also in the repos)
then reattach printer
if need reboot computer

everything should work, if not you may need to reset the printer
[http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=110&prodSeriesId=30000&prodTypeId=18972&prodSeriesId=30000&objectID=bpu02063](http://h20000.www2.hp.com/bizsupport/TechSupport/Document.jsp?lang=en&cc=us&taskId=110&prodSeriesId=30000&prodTypeId=18972&prodSeriesId=30000&objectID=bpu02063)

---

### Post by Joerice50 on 2009-01-30
I followed your advice and can report 90% success

I installed the recommended drivers and the printer prints the HP Linux imaging test page perfectly.  However, when I tried printing my own test page made up of increasing text strings  in different fonts in an open office document the fault returned!

So I shut down Ubuntu opened XP and loaded a word document and printed it without error.

I then shut down Xp and booted Ubuntu opened the same word document with open office and printed it fine.

I then opened my print test page the fault returned, so its something to do with the fonts and text sizes in my test print document that screws the HP printer

Anyway thanks for your advice 

Cheers

Joe Rice

---

