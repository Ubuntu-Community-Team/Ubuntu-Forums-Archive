---
title: "Opening wordprocessor takes long time in ubuntu 10.04"
date: 2010-06-22
forum: New to Ubuntu
---

### Post by karthick87 on 2010-06-22
I am using ubuntu 10.04, OpenOffice Wordprocessor takes very long time to open a document..Does anyone face this problem here..?

---

### Post by warfacegod on 2010-06-22
Depends on what you mean by a long time. My OOo Writer usually takes about 7 - 15 seconds. If I have half a dozen or more other apps running, it's not unusual for it to take the better part of a minute.

---

### Post by kerry_s on 2010-06-22
you got to tweak the memory & disable the java.
tools-> options

---

### Post by karthick87 on 2010-06-22
> **warfacegod said:**
> Depends on what you mean by a long time. My OOo Writer usually takes about 7 - 15 seconds. If I have half a dozen or more other apps running, it's not unusual for it to take the better part of a minute.


It takes 1 minute for me to open a word document,its pretty slow na..?

---

### Post by Baneblade on 2010-06-22
Just tested mine now for you. 
9 sec - cold start
2 sec - cached

How long is yours taking roughly?
Also, could you post your machines specs please. It will be easier to give you a rough estimate on what kind of performance you should be expecting.

Note: This test was done on my laptop (Custom-frankenstein'd Core2Duo, 4Gig, 7200rpm; Based on an HP DV2910us) not the system in my sig.

---

### Post by philinux on 2010-06-22
Mine takes about 2 secs to open the writer from cold.

However some peeps are getting very slow results.

[http://ubuntuforums.org/showthread.php?t=1512422](http://ubuntuforums.org/showthread.php?t=1512422)

---

### Post by karthick87 on 2010-06-22
CPU: Intel(R) Core(TM)2 CPU E7400  @ 2.80GHz
RAM: 4GB DDR2

---

### Post by warfacegod on 2010-06-22
That is pretty sluggish for those specs. I'd start by reducing swapiness to amore reasonable level. The default 60 is too high for my taste, go with 20 - 30 or so. I don't even have a swap partition at all. Reducing swapiness will force the system to use more RAM instead of HDD as RAM. See post #3 about how to do that. [http://ubuntuforums.org/showthread.php?t=1454959&highlight=swapiness](http://ubuntuforums.org/showthread.php?t=1454959&highlight=swapiness)

---

### Post by Matt__ on 2010-06-22
You could always try Abiword instead of open office.

It should be in the repositories (not on my linux box atm so I'm not 100% on that) 

```
sudo apt-get install abiword-gnome
```

if not go here

[INDENT][_>>Download Abiword<<_](http://abisource.com/wiki/Install_on_Ubuntu)[/INDENT]



[COLOR="White"].[/COLOR]

---

### Post by Sir Jasper on 2010-06-22
Hi,

Something is very, very wrong. I wonder if it may help to run top or htop or gnome-system-monitor to see if anything seems odd as you load a document.

My regards

---

### Post by karthick87 on 2010-06-22
> **Sir Jasper said:**
> Hi,

Something is very, very wrong. I wonder if it may help to run top or htop or gnome-system-monitor to see if anything seems odd as you load a document.

My regards


No nothing seems to be wrong while loading a document..

---

### Post by bodhi.zazen on 2010-06-22
Personally I find open office to be very slow.

If you do not need all those bells and whistles try an alternate editor.

I use gedit and abiword , once a document is finished, if I need something more, copy -> paste to openoffice.

With that said, one minute sounds too long for OOO to open a document.

---

### Post by Sir Jasper on 2010-06-22
Hi,

Even if you don´t use OO spreadsheets, if you have the program you could try saving a blank spreadsheet and see how long that takes to reload.

I have a 1998 machine (with a 2002 replacement motherboard) which runs @ 2.0 GHz with 640 MB of RAM (my swap file is permanently off). It takes 7 seconds to open OO writer and then about 2 seconds to load a document.

Alternative programs may work well for you, but you will probably want to fix the problem.

My regards

---

### Post by karthick87 on 2010-06-22
Sometimes the system freezes while saving the document.

---

### Post by Sir Jasper on 2010-06-22
Hi,

You might try uninstalling OO then reinstalling it (after first making sure your existing documents are not in any OO folder).

If you try that and it fails - then do seek further advice here.

My regards

---

### Post by karthick87 on 2010-06-23
> **Sir Jasper said:**
> Hi,

You might try uninstalling OO then reinstalling it (after first making sure your existing documents are not in any OO folder).

If you try that and it fails - then do seek further advice here.

My regards

Fine i will try removing it and install it again..

---

### Post by karthick87 on 2010-06-25
Now it works fine and thanks for all the users who helped me :)

---

