---
title: "Samsung Printer Drivers and Wine"
date: 2009-11-28
forum: New to Ubuntu
---

### Post by wannabegeek on 2009-11-28
Good day all, thanks for reading...

I have a Samsung monochrome laser printer, 2851 ND, which works OK with the generic driver. However, I cannot get the duplex feature to work. I have seen a printer option under System, Admin., Printing....but this doesn't help.

I have the Samsung driver CD which has a Linux driver, can't get anything to happen with that. 

I installed WINE and considering using it to run my printer driver...however this also requires some more background knowledge than I currently have.

All suggestions are welcome, I would like to work this problem out. So far the transistion has been rough, but worth it.

peace,
wbg

---

### Post by Zzl1xndd on 2009-11-28
It appears that Samsung has a Linux driver for this Printer, So you may just need to installer there drive. They also List Linux as a supported OS so they might be able to assist you with the issue.

[http://www.samsung.com/au/consumer/print-solutions/print-multifunctions-copiers/mono-laser-printer/ML-2851ND/XSA/index.idx?pagetype=prd_detail&tab=support](http://www.samsung.com/au/consumer/print-solutions/print-multifunctions-copiers/mono-laser-printer/ML-2851ND/XSA/index.idx?pagetype=prd_detail&tab=support)

---

### Post by wannabegeek on 2009-11-28
Hey thanks tweaked....I have been to the Samsung before, and it seems they have improved the model specific page a lot...I am downloading  the universal driver now...

wbg

---

### Post by Mark Phelps on 2009-11-29
> **wannabegeek said:**
> I installed WINE and considering using it to run my printer driver...however this also requires some more background knowledge than I currently have.

Wine is only an interface layer that allows running SOME MS Windows programs.  It can not be used to install MS Windows-based drivers.

---

### Post by wannabegeek on 2009-12-19
Hi all,

Since I am nearing done with finals, I am back to trouble shooting (learning to use Ubuntu)...

I downloaded the Samsung Universal driver and got it to work. At first I was connecting it with the ethernet cable for the configuration, which didn't work. When I switched to USB, the printer was detected automatically and setup went smooth.

New issue is getting printer to work through wireless router. The configurator asks me to choose a connection method. There USB, Parallel and network, choices. When I selected network, such as 
socket:\\   or any of them, the OK button was grayed out. The only choice that worked was USB.

any ideas,

thanks you very much,

wbg

---

### Post by wannabegeek on 2009-12-19
In case any other newbie has trouble getting their network printer to go wireless, I'd thought I'd post my solution.

The Samsung Universal Print Driver needs to be configured through the USB port.
Although it has an option through the driver to select a port, only the USB or parallel work work from the driver. 

In Ubuntu's System menu, Printer, one can change the Device URI. By clicking the change
button, Ubuntu searches for attached devices. Eben though I don't really understand what all any of this means, I recognized my IP address as an option and that did the trick.

My 2851ND printer is working through my router, with double sided printing and everything...

I am so glad that I switched to Ubuntu, every obstacle has been slowly overcome.

Now to fix my mp3 player...



wbg

---

