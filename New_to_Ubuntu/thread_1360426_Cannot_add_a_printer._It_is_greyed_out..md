---
title: "Cannot add a printer. It is greyed out."
date: 2009-12-20
forum: New to Ubuntu
---

### Post by Sunbirdaz on 2009-12-20
In the Printer Configuration dialog box all the options to add a printer are greyed out.
I'm new to Ubuntu so I don't  have a clue as to what to do. I've checked the forums but hav not found a solution. Using Ubuntu 9.04.
Thanks.

---

### Post by Yvan300 on 2009-12-20
As far as i know, you just plug it in and it get automatically recognized. Worked for me :)

---

### Post by LowSky on 2009-12-20
What Brand and Model Printer?

---

### Post by steveneddy on 2009-12-20
Try typing this address in your browser:

```
http://localhost:631/
```

This is the cups utility in browser form that many find easier to navigate.

---

### Post by Sunbirdaz on 2009-12-21
Thanks for your suggestions. I did a reinstall of Ubuntu and I can now add a printer. 
I have a dual boot Win XP and Ubuntu. My PC connects wirelessly to my router. My printer connects to the router via cat5. In Windows I set up the printer as an IP printer and printing to it works fine. In Ubuntu I have the wireless configured and I connect to the internet through the wireless. When I add a printer in Ubuntu it finds the printer and I attempt to print a test page. The print job goes to the print que and I get a pop up that says the job has printed but nothing comes out of the printer. I can ping the printer from Ubuntu so I know it sees it. 
Thanks.

---

### Post by steveneddy on 2009-12-21
Please mark the thread as solved then.

---

### Post by ramilehti on 2009-12-21
It could be that the cups service is not running.
Either start it via menus or in a terminal window give the command:

sudo /etc/init.d/cups start

---

### Post by Ozdemon on 2010-03-06
> **ramilehti said:**
> It could be that the cups service is not running.
Either start it via menus or in a terminal window give the command:

sudo /etc/init.d/cups start

Thanks, that worked for me.  I was tearing my hair out.](*,)

---

### Post by The_Eddster on 2010-09-20
> **ramilehti said:**
> It could be that the cups service is not running.
Either start it via menus or in a terminal window give the command:

sudo /etc/init.d/cups start

I've tried this but it's still greyed out. I've also tried going to [http://localhost:631/](http://localhost:631/) but I'm pretty lost from there. 

Help me please!

---

### Post by Wim Feijen on 2011-05-02
Hello, I cannot add a printer as well. The option is greyed out. I do am an administrator.

Localhost:631 gives:
"Oops! Google Chrome could not connect to localhost:631"

For some reason, cups does not seem to be installed:

sudo apt-get install cups 

solves the problem for me.

---

### Post by TwistedRotors on 2011-12-01
> **steveneddy said:**
> Try typing this address in your browser:

```
http://localhost:631/
```

This is the cups utility in browser form that many find easier to navigate.

Thank you for this! My "Add a Printer" button was greyed out in Ubuntu 11.10 even though CUPS was installed. Using [http://localhost:631/](http://localhost:631/) allowed me to easily add my printer. 
-John

---

