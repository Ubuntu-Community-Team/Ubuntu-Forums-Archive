---
title: "HP Deskjet 3420 problems"
date: 2010-07-04
forum: New to Ubuntu
---

### Post by Trinity1976 on 2010-07-04
Up until recently I had no problem printing with my Deskjet 3420 on 9.10. However, when I upgraded to the latest version of Ubuntu, it stopped working. For that and other reasons I have no returned to Ubuntu 9.10. However, it still won't work and the green power light is continuously flashing. I've tried unplugging it and replugging it in but it still keeps flashing.

The error I get when I try to print it this:

> Print Error.

There was a problem processing document

I have tried the following method recommended in another thread:

[http://hplipopensource.com/hplip-web/install/install/index.html](http://hplipopensource.com/hplip-web/install/install/index.html)

When I try to print a test page during the set-up wizard I get the following error:

> Printer Error.

Printer is busy, offline, or in an error state. Please check the device and try again.

Does anybody have any advice? If not, can anyone recommend me an inexpensive printer/scanner combi that is definitely supported by Ubuntu 9.10?

---

### Post by bumanie on 2010-07-04
Once had a similar problem - I uninstalled the printer and then went back to 'add printer' and after the driver downloaded it worked fine - at that point, the hplip driver from HP didn't work for me either. That printer should work in ubuntu. Hope the solution works.

---

### Post by rburkartjo on 2010-07-04
trinity i did what bum did. i had a similar problem and his fixed worked for me. good luck/cheesemaker

---

### Post by Trinity1976 on 2010-07-04
bumanie,

Can you walk me through what you did, in case I'm missing something? The printer has been removed through Administration->Printing, and re-added several times, to no avail. Is that what you did? 

Occasionally I also get a message saying there is a problem with a print cartridge but I think that's a red herring!

---

### Post by bumanie on 2010-07-04
Looks as though you are doing what I did - it was sort of a last ditch effort, that fortunately for me, worked. I had tried hpilip universal installer, I tried cups debugging etc, to no avail. If that's not working and the hplip installer from the HP site, isn't working, I have no solutions off the top of my head. But that printer is listed as being supported on the HP site, so there will be a solution - it's just finding it, unless something has gone wrong with the printer.
You could try [HP support]("http://hplipopensource.com/hplip-web/support.html") or look at the [troubleshooting page]("http://hplipopensource.com/node/224") - it may help. Sorry I can't be of more help.

---

