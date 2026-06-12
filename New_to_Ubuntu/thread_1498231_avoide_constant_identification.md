---
title: "avoide constant identification"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by AlanAbbott on 2010-05-31
I upgraded to 10.4 and someware down the line I said yes to something that every so ofen (very often) request that I enter my password. 
I work with a number of systems at a time on each of two or three PC's.
At times I may take over a couple of hours before I get back to something, and this may only be checking what is already displayed.
It is mandatory that I disinstall this, I don't know what it is and were to start looking.

---

### Post by ajgreeny on 2010-05-31
If this is work done in the terminal you can get a root permission terminal with ```
sudo -i
```and then as long as that terminal is open, you will not be asked for a password again.

If using GUI apps you can use ```
gksudo appname
``` eg gksudo nautilus and that will give you root privileges while that window is left open.

Be careful, however, as it is easy to forget you are root, and do a lot of harm quite easily this way.

---

### Post by AlanAbbott on 2010-05-31
What I want is to identify which is the packege that is timeing out and locking the machine. 
This is new since I upgraded. 
I want to disable or uninstall it. 

Thank you for your sugestion.

Alan

---

### Post by sisco311 on 2010-05-31
it's the screensaver. System -> Preferences -> Screensaver -

---

### Post by AlanAbbott on 2010-06-01
Thank you very much SISCO313, it was that that was bothering me, the screensaver.

This is solved.

---

