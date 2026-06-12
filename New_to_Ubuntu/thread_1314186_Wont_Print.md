---
title: "Wont Print"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by daniell59 on 2009-11-04
I installed the printer and it wont print.
HP Laserjet 1020

Ubuntu 1020

---

### Post by danill2008 on 2009-11-04
Have u checked in CUPS?

---

### Post by ukripper on 2009-11-04
> **daniell59 said:**
> I installed the printer and it wont print.
HP Laserjet 1020

Ubuntu 1020

Is it turned on?

If it is turned on and still doesn't print then use this link - [http://hplipopensource.com/hplip-web/install_wizard/index.html](http://hplipopensource.com/hplip-web/install_wizard/index.html)

---

### Post by ukripper on 2009-11-04
Your printer is supported by ubuntu, look screenshot:

---

### Post by daniell59 on 2009-11-04
> **danill2008 said:**
> Have u checked in CUPS?

what is cups?

---

### Post by ukripper on 2009-11-04
> **daniell59 said:**
> what is cups?

[http://en.wikipedia.org/wiki/CUPS](http://en.wikipedia.org/wiki/CUPS)

[http://en.wikipedia.org/wiki/File:Gnome2.26-printing-dialogue.png](http://en.wikipedia.org/wiki/File:Gnome2.26-printing-dialogue.png)


Can you see your printer if you open firefox and type:
localhost:631/printers

---

### Post by daniell59 on 2009-11-04
> **ukripper said:**
> Your printer is supported by ubuntu, look screenshot:

I got confused after I downloaded the file.
I did not know what to do in the terminal

---

### Post by daniell59 on 2009-11-04
> **ukripper said:**
> [http://en.wikipedia.org/wiki/CUPS](http://en.wikipedia.org/wiki/CUPS)

[http://en.wikipedia.org/wiki/File:Gnome2.26-printing-dialogue.png](http://en.wikipedia.org/wiki/File:Gnome2.26-printing-dialogue.png)


Can you see your printer if you open firefox and type:
localhost:631/printers

I can see the printer there.

---

### Post by ukripper on 2009-11-04
> **daniell59 said:**
> I got confused after I downloaded the file.
I did not know what to do in the terminal

You don't need to download anything. Your printer is supported out of the box in ubuntu 9.04/9.10

Just click on your System-->Administration-->Printing Can you see printer there?

---

### Post by ukripper on 2009-11-04
> **daniell59 said:**
> I can see the printer there.

That means you printer drivers are loaded and it should work fine.

Check your printer whether it is on and try to print again.

---

### Post by daniell59 on 2009-11-04
> **ukripper said:**
> That means you printer drivers are loaded and it should work fine.

Check your printer whether it is on and try to print again.

I just tried it in Vista and it works. I again tried it in Ubuntu, and it does not work.

---

### Post by daniell59 on 2009-11-04
I don't understand. There were two choices. HP Laserjet 1020 and HP Laserjet 1020-2. I enabled the latter and it worked. Someone please explain to my what is happening.

---

### Post by mgmiller on 2009-11-04
It sounds like you installed the printer twice.  It got name -2 for the second one which works.  You can just remove the first one that doesn't work and you should be ok.

System > Administration > Printing

Right click the one that does not work and select "Delete".

---

### Post by daniell59 on 2009-11-04
> **mgmiller said:**
> It sounds like you installed the printer twice.  It got name -2 for the second one which works.  You can just remove the first one that doesn't work and you should be ok.

System > Administration > Printing

Right click the one that does not work and select "Delete".

Thanks

---

### Post by CJay554 on 2009-11-12
[FIXED]
I seem to have needed to reinstall the driver for it to be fixed.

I have an OfficeJet -K60 printer, used to work flawlessly in 9.04 but since i re-installed 9.10 from scratch it doesnt work, i see the printer both in System > Prefs and at the localhost cups server, it can see my print job, but the printer does not respond at all, any ideas?

---

