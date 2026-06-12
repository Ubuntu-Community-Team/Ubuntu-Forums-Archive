---
title: "Installing Canon PIXMA MP250 Printer - How?"
date: 2011-04-11
forum: New to Ubuntu
---

### Post by Kazca on 2011-04-11
Hi guys,

I'm a complete newbie to Ubuntu, and any Linux-y OS. My Windows 7 crashed the other day and when it couldn't be fixed I wiped it and installed Ubuntu. I don't understand how anything works, from installing software to using the "Terminal", but I really do like what I've been able to figure out.

I have a Canon PIXMA MP250 Series Printer and I need to get it up and running. I have the install CD for windows, but from what I understand you can't run .exe in Ubuntu. Please lend a gal a hand. [-o<

---

### Post by Rex Bouwense on 2011-04-11
Try checking the Canon web site.  I found this [http://support-asia.canon-asia.com/P/search?model=PIXMA+MP258&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-asia.canon-asia.com/P/search?model=PIXMA+MP258&menu=download&filter=0&tagname=g_os&g_os=Linux)
That is for an MP 258.  Hope that helps.

---

### Post by Kazca on 2011-04-11
Thanks! But now that I've downloaded the tar.gz file, how do I make it work? Do I need to extract it? And once I do extract it, what do I do with it? Is there a step-by-step someone could link me to that's laid out in terms someone who's technologically illiterate would understand?

---

### Post by radwasrad on 2011-12-01
Eyop, not sure if you got an answer, but am in the same boat...  have downloaded and installed the .deb files (using Ubuntu Software Centre), and nothing.  Doesn't show on a printer list and the CD that came with the printer doesn't install.  Can someone please let me know what to do next?  Am using Zorin OS5 (very nice...) if that helps...

Cheers
Adam

---

### Post by winoseti on 2012-01-12
okay a bit quirky but my printers working ...

download the drivers for you including the linux os and processor and 32 or 64 bit version.

open with archive manager

extract to here. or some secure new directory.(printerd)e.g.
you get threeboxed files
open the one for you either cnij....deb... or cnij....rpm...right click the one and open with archive manager

okay for me amd64 and linuxmint 11 so used debian package
go in one level with archive manager to find folder of same name 
go in one further level to get to packages. you might need to extract to here again.

okay right about now or before everything open in the terminal gdebi-gtk or the equivalent rpm package manager.
gdebi window comes up.

back to the game... packages opens up to cnijfilter-common_3.4... right click and open with gdebi... it installs. this will only show the mp220 printerwhen you plug your printer in. remember if you dont get the choice to open with gdebi then you have to extract. beats me why

then you have to go backto the same folder where the common files were extarct and right click open with gdebi again cnij-filter-mp250 3.4...... and install that using gdebi 

after i did that things worked 
the mistake i made the first time was i tried to install the mp250 driver first.without the common files first the driver update doesnt work

havent tried the scanner yet....news i installed xsane and scanner works right off.

.:guitar:

---

### Post by winoseti on 2012-01-12
well anyway i got it working my reply is garbled but i am stoked to have it working.

can take anyone through on chat if need be.

also to find the right drivers for this
 [http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CDEQFjAB&url=http%3A%2F%2Fsoftware.canon-europe.com%2Fproducts%2F0010752.asp&ei=3YsQT8W_B8OI4gSuq_jpAw&usg=AFQjCNF5FavaJb7V23sT2kUoObHL2Q9YiQ](http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&ved=0CDEQFjAB&url=http%3A%2F%2Fsoftware.canon-europe.com%2Fproducts%2F0010752.asp&ei=3YsQT8W_B8OI4gSuq_jpAw&usg=AFQjCNF5FavaJb7V23sT2kUoObHL2Q9YiQ)

the latest drivers need a degree in computer science.

---

### Post by BNZBKK on 2012-01-21
> **winoseti said:**
>  
**[SIZE="2"]okay right about now or before everything open in the terminal gdebi-gtk [/SIZE]**or the equivalent rpm package manager.
gdebi window comes up.

back to the game... packages opens up to cnijfilter-common_3.4... right click and open with gdebi... it installs. this will only show the mp220 printerwhen you plug your printer in. remember if you dont get the choice to open with gdebi then you have to extract. beats me why

then you have to go backto the same folder where the common files were extarct and right click open with gdebi again cnij-filter-mp250 3.4...... and install that using gdebi 

 

***[SIZE="2"]"..okay right about now or before everything open in the terminal gdebi-gtk .."[/SIZE]***

I got this....

**[SIZE="2"] Unable to locate package gdeb[/SIZE]**

so what's my next step ?



There's got to be an easier GUI way. 
My last printer was plugged in, automatically detected, and printed !

---

### Post by BNZBKK on 2012-01-23
Anyone ?

---

