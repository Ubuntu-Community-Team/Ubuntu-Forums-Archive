---
title: "Print  PDF in 9.04"
date: 2009-05-14
forum: New to Ubuntu
---

### Post by RobHK on 2009-05-14
I've googled how to print to PDF but none of the stuff I found works for me in 9.04.

Can anyone help, please?

TIA

---

### Post by gandaran on 2009-05-14
choose print to file in the print window then mark the pdf radio button, simple!
or do you mean open office pdf printing?

---

### Post by aeiah on 2009-05-14
or if for some reason that kinda option isnt available you can go to system > administration > services and make sure the print server (cups) is running, and then go system > administration > printing and create a new printer. you'll have the option of selecting 'Generic CUPS-PDF Printer' as your new printer.

PDFs printed with the cups pdf printer get saved in ~/PDF by default.

---

### Post by Didius Falco on 2009-05-14
> **RobHK said:**
> I've googled how to print to PDF but none of the stuff I found works for me in 9.04.

Can anyone help, please?

TIA

Hi,

There is a package in Synaptic Package Manager named **cups-pdf** that works well, once you know the trick to using it. You need to make a directory in your ~/ directory named PDF - the capitalization is required. The program seems to require it, but it does not create the directory itself.

Open Office can natively print to PDF, and so can Firefox, though in the case of Firefox I prefer the output from cups-pdf.

I hope this helps...

Regards,

Didius

---

### Post by Arathorn on 2009-06-01
> **aeiah said:**
> PDFs printed with the cups pdf printer get saved in ~/PDF by default.
I'd like to add that I had to manually create that folder first, or the pdf making would fail.

---

### Post by acosta68 on 2009-06-13
> **RobHK said:**
> I've googled how to print to PDF but none of the stuff I found works for me in 9.04.

Can anyone help, please?

TIA

System/Administration/Synaptic Package Manager and then looking for "cups-pdf" add cups-pdf. Then when you go to add printer you can see "PDF printer"

---

### Post by RobHK on 2009-06-30
Sorry for the delay in replying. 

I've done that and the printer appears to work and says it is saving to my Docments folder. But nothing ever appears there.

I'll probably do a full reinstall soon, so we'll see what happens then.

Thanks.

---

### Post by ellgor on 2009-06-30
Hi, 

You would be better off getting the Adobe Reader app than go round in circles, you can get it like this:

Firstly use synaptic and download an app called "gedbi" (if its not already installed) next use your browser and go to the Adobe site and click on the appropiate app (reader), do not select the offered app instead click on "Different language or operating system" in the new page click on "Select an OS" from the drop down menu choose "Linux-86 (deb)" download this to somewhere you can find it. Once downloaded go to the downloaded package right click on it and select open with "gdebi" (if not already highlighted) from there it will self load and be ready to use, hope this helps.

Regards, Ellgor.

---

### Post by 73ckn797 on 2009-06-30
> **ellgor said:**
> Hi, 

You would be better off getting the Adobe Reader app than go round in circles, you can get it like this:

Firstly use synaptic and download an app called "gedbi" (if its not already installed) next use your browser and go to the Adobe site and click on the appropiate app (reader), do not select the offered app instead click on "Different language or operating system" in the new page click on "Select an OS" from the drop down menu choose "Linux-86 (deb)" download this to somewhere you can find it. Once downloaded go to the downloaded package right click on it and select open with "gdebi" (if not already highlighted) from there it will self load and be ready to use, hope this helps.

Regards, Ellgor.

Gdebi is already installed and can be added to the Applications/System Tools menu via System/Accessories/Main Menu tool.

Acroread for Ubuntu is available, I believe, through ubuntu-restricted-extras found in System/Administration/Synaptic Package Manager.

If you have Ubuntu Tweak installed ([http://ubuntu-tweak.com/downloads](http://ubuntu-tweak.com/downloads)) you can get the restricted stuff there also.

---

