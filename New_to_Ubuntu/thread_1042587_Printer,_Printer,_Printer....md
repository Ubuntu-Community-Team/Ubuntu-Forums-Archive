---
title: "Printer, Printer, Printer..."
date: 2009-01-17
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-01-17
I have a HP 812c  Desk Jet Printer...yes very ancient as is my computer...lol, but my problem is it won't print. It did print a page when I first tried, about half of what was on the page. Now it wont print aanything... I tried the inkblot thing and it say the printer is not conected... I was hopeing that someone could help me please. Not a dire emergancy but I do have something I want to print... Thanx.


Leo

---

### Post by Truefire on 2009-01-17
That sounds like a prob with the printer, not the PC. Try unplugging the printer from both the wall and the PC, then reconnecting both - that's all I've got for the older printers like that.

---

### Post by expatCM on 2009-01-18
If you take the printer to another pc, will it print properly there?

---

### Post by Leo Dragonheart on 2009-01-18
Yes it printed ffine till I installed Ubuntu...

---

### Post by hyperyoda on 2009-01-18
> **Leo Dragonheart said:**
> I have a HP 812c  Desk Jet Printer...yes very ancient as is my computer...lol, but my problem is it won't print. It did print a page when I first tried, about half of what was on the page. Now it wont print aanything... I tried the inkblot thing and it say the printer is not conected... I was hopeing that someone could help me please. Not a dire emergancy but I do have something I want to print... Thanx.


Leo

Hi again Leo!

I have a very similar printer - HP Deskjet 960c. I spent hours trying to get it working in CUPS but keep getting mystifying errors that no one can resolve (such as "Request Entity Too Large") but you can try installing lrp/lpd and using a filter with it such as apsfilter. You could also try installing lprng as your print spooler and use apsfilter or the foomatic filter with it. I hooked up mine to the parallel port so to print a test I made a shell script dumb-print.sh:

#!/bin/sh

# This prints directly to the line printer - /dev/lp0
# It doesn't use any filtering

cat $1 > /dev/lp0

so if you save this and run:

"sh myprint.sh test" 

alternately you can do:  "chmod +x myprint.sh test"
then you can run it as:
"./myprint.sh test"
it should send "test" to your printer and print it if all is setup correctly.

Zach

---

### Post by expatCM on 2009-01-18
and have you installed hplip from Synaptic?

---

### Post by Leo Dragonheart on 2009-01-18
No I haven't installed that but I will now...

---

### Post by alienexplorers on 2009-01-18
Under HPLIP your printer should work fine.
```
Distro	Version	Installer	GUI	Scan3	Fax5	Status	Photo Card4	USB	Parallel	Network1
Ubuntu	5.1	No	Yes	Yes	No	Yes	No	No	Yes	No
Ubuntu	6.06	Yes	Yes	Yes	No	Yes	No	No	Yes	No
Ubuntu	6.10	Yes	Yes	Yes	No	Yes	No	No	Yes	No
Ubuntu	7.04	Yes	Yes	Yes	No	Yes	No	No	Yes	No
Ubuntu	7.10	Yes	Yes	Yes	No	Yes	No	No	Yes	No
Ubuntu	8.04	Yes	Yes	Yes	No	Yes	No	No	Yes	No
Ubuntu	8.10	Yes	Yes	Yes	No	Yes	No	No	Yes	No 
```

---

### Post by Leo Dragonheart on 2009-01-18
Printer is up and printing thanx guys... I installed all the hp things, then went and had to configure the printer but now it is working thanx again...

---

