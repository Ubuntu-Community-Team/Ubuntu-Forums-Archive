---
title: "Printer driver install"
date: 2010-03-30
forum: New to Ubuntu
---

### Post by newport_j on 2010-03-30
Today my laser printer stopped printing Ubuntu files. It only printed a file when I was in gedit before. I guess that I need to install the printer's driver again. I am unsure how to do this. Is this written down somewhere?

I know all of the particulars (make, model etc.), but I am unsure how to proceed. 

What are the steps for installing a printer driver in Ubuntu?

Newport_j

---

### Post by talonmies on 2010-03-30
> **newport_j said:**
> Today my laser printer stopped printing Ubuntu files. It only printed a file when I was in gedit before. I guess that I need to install the printer's driver again. I am unsure how to do this. Is this written down somewhere?j

I would have thought it very unlikely that you need to re-install anything. In is much more likely that the printer queue is in error because of a problem with either the hardware or a print job. Usually simply removing any stuck jobs from the queue or remedying whatever is wrong with the printer will fix it.

There is an printer administration application which can be run from System->Administration->Printing. It will show you the status of your printer and you should be able to see what/why there is an error condition which has stopped the print queue. It can be things like jobs with the wrong paper size or corrupted postscript, or cabling, or the printer itself (toner, ink, paper whatever).

---

### Post by mikeyphi on 2010-03-30
Have a look here:
[http://www.openprinting.org/printers](http://www.openprinting.org/printers)

otherwise repost with printer details!

---

### Post by newport_j on 2010-03-30
Other user in my office group have been able to use it. I used to be able to print out files when I was in GEDIT mode, nice color source code usually. Now, I cannot even do that. 

When it prints something the page is simply blank.

How do I look in the queue? I have gone the admin->printer route and nothing seems out of place. The biggest clue that I can give is that the printout is blank or a white sheet of paper. I know from that it is acting on print commands, but not printing. Anything else, I do not know.


Respectfully,

James M. Yunker

---

### Post by talonmies on 2010-03-30
The printer administration tool will let you print out a test page. If you select the printer (it should have a green tick if the queue is working), then printer->properties from the dialogue tool menu, you will get a dialogue box with a button "Print Test Page".

Try that and see what it does. There are two possibilities here - one is the print system is broken, the other is that the application generating the print job is broken. The test page eliminates the former.

---

### Post by newport_j on 2010-03-30
I have the addres and the port number right on the setup. It says that I have connected to a Xerox Phaser 6115 MFP Foomatic.

Someone in my office who has it working, but has it connected as 

Xerox Phaser 6250DP foomatic/Postscript. 

However, when I select the printer (address 129.190.170.247 with port 9100) and then select forward on the installation the choices include the following :

Xerox Phaser 6115 MFP Foomatic

It does not include among the Xerox printer model choices the
Xerox Phaser 6250DP Foomatic/Postscript. That is the model that I want and it is not included among the models to select! It selects the other one that I have listed above. It evens says recommended on the line next to it 6115MFP. However, this does not work. I do not know why. I am pretty sure that the mold 6250DP will work. So how do I force an installation of this driver, and where do I find that driver?



Newport_j

---

