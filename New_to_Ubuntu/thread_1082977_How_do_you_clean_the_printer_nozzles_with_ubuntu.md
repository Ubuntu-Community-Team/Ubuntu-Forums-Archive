---
title: "How do you clean the printer nozzles with ubuntu?"
date: 2009-02-28
forum: New to Ubuntu
---

### Post by cptrohn on 2009-02-28
Hi, I just got new ink cartridges for my printer, but I need to clean the printer nozzles...

I can't seem to figure out how to do this with ubuntu(8.10) I am using an Epson CX5000 printer if that helps any at all... everything seems to be working ok with the printer, and it was working just fine before it ran out of ink so it's nothing along those lines...

any help?

---

### Post by steveneddy on 2009-02-28
Here is the manual that you should have received with your new printer in which it describes on pages 12 and 13 how to clean the print cartridges from the buttons on the machine.

_[http://www.google.com/url?sa=U&start=1&q=http://files.support.epson.com/pdf/cx5k__/cx5k__pg.pdf&ei=eoCpSdjLKIS2nQfdp8X2Dw&usg=AFQjCNEtNbyC6HD-v6yxc9INlwNB1w_B9Q](http://www.google.com/url?sa=U&start=1&q=http://files.support.epson.com/pdf/cx5k__/cx5k__pg.pdf&ei=eoCpSdjLKIS2nQfdp8X2Dw&usg=AFQjCNEtNbyC6HD-v6yxc9INlwNB1w_B9Q)_

I don't know if there is a GUI available from Epson that runs on Linux that would help you achieve this goal.

An HP Printer on the other hand can have the print cartridges cleaned from a GUI with HPLIP.

---

### Post by cptrohn on 2009-02-28
> **steveneddy said:**
> Here is the manual that you should have received with your new printer in which it describes on pages 12 and 13 how to clean the print cartridges from the buttons on the machine.

[http://files.support.epson.com/pdf/cx5k__/cx5k__pg.pdf&ei=-X6pSdzAG5C-nQeT0OHmDw&usg=AFQjCNGgcwarNvgLvZQJ7NRiZm2N-z0zIA](http://files.support.epson.com/pdf/cx5k__/cx5k__pg.pdf&ei=-X6pSdzAG5C-nQeT0OHmDw&usg=AFQjCNGgcwarNvgLvZQJ7NRiZm2N-z0zIA)

I don't know if there is a GUI available from Epson that runs on Linux that would help you achieve this goal.

An HP Printer on the other hand can have the print cartridges cleaned from a GUI aith HPLIP.

Ahh ok thank you.. I didn't get this printer new, so I didn't get a manual with it.  But I will look into this more later on today.

---

### Post by steveneddy on 2009-02-28
> **cptrohn said:**
> Ahh ok thank you.. I didn't get this printer new, so I didn't get a manual with it.  But I will look into this more later on today.

well - you have it now.

I believe that you can go to the Epson website and download all of the documentation that is available in a PDF format.

---

### Post by cptrohn on 2009-02-28
Hmmmm..

I did a search and came across this comman ```
-c | --clean-head
``` which is supposed to be a way to clean printer nozzles from a terminal.. but it didn't work and came back as  ```
command not found
```..

Anything like this from a terminal sound familiar to anyone?

---

### Post by wolfen69 on 2009-02-28
```
sudo apt-get install escputil
``` will install epson maintenance utilities.

---

### Post by cptrohn on 2009-02-28
> **wolfen69 said:**
> ```
sudo apt-get install escputil
``` will install epson maintenance utilities.

GREAT thank you VERY much!

---

### Post by cptrohn on 2009-02-28
> **wolfen69 said:**
> ```
sudo apt-get install escputil
``` will install epson maintenance utilities.

Ok, I ran this, but now I can't find where they were installed???

I've looked all over the place and they are nowhere to be found.

---

### Post by cptrohn on 2009-02-28
never mind.... DUH moment... found it, working well.

---

