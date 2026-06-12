---
title: "Canon MP 250 - no drivers!"
date: 2011-02-27
forum: New to Ubuntu
---

### Post by brian334 on 2011-02-27
Unable to get my Canon MP 250 printer working with Ubuntu Linux 10.10

Tried all the help and down loaded a driver from Canon Australia web site but how you install it I have no idea (windows is easy/just hit the exe file)

Help (No tech-no-gobbledegook please just plain English) thanks

---

### Post by sydbat on 2011-02-27
> **brian334 said:**
> Unable to get my Canon MP 250 printer working with Ubuntu Linux 10.10

Tried all the help and down loaded a driver from Canon Australia web site but how you install it I have no idea (windows is easy/just hit the exe file)

Help (No tech-no-gobbledegook please just plain English) thanksIt depends on what you downloaded. 

If it is a tar.gz package with .debs inside, right click it and choose 'Extract Here'. 

Then right click the .deb, go to the Permissions tab and check 'Allow Executing File as a Program'. 

Go from there.

---

### Post by walt.smith1960 on 2011-02-27
This looks to be fairly straight forward.  Google found this:
[http://support-my.canon-asia.com/contents/MY/EN/0100236101.html](http://support-my.canon-asia.com/contents/MY/EN/0100236101.html)

toward the bottom is the download link.  I looked in the packages folder, there are 4 .deb files. 2 are for i386 and 2 are for 64 bit. You'll need to extract those.  tar.gz files are like .zip files.  I would guess that you need to right click on the larger of the two appropriate .deb files.  When you right click a .deb file, it should offer to open in Ubuntu Software Center and from there on is about like clicking on an .exe file.

---

### Post by heavy metal on 2011-03-09
Yes there are drivers from here: [http://www.canon.com.my/](http://www.canon.com.my/)

Follow this tutorial, it tells you how to install the drivers and how to make the scanner to work in ubuntu 10.04 (not needed in 10.10 the scanner works out of the box).
[http://harbhag.wordpress.com/2010/04/09/canon-pixma-mp258-or-any-mp250-series-printer-on-ubuntu-debian-fedora-and-arch-linux/](http://harbhag.wordpress.com/2010/04/09/canon-pixma-mp258-or-any-mp250-series-printer-on-ubuntu-debian-fedora-and-arch-linux/)

---

### Post by nomko on 2011-03-09
Drivers can be found here:
_[COLOR=#810081][http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux](http://support-au.canon.com.au/P/search?model=PIXMA+MP250&menu=download&filter=0&tagname=g_os&g_os=Linux)[/COLOR]_
[COLOR=black][/COLOR] 
 
Best to do is using the source file and compile the driver yourself. This way, the file will be compiled specificly for your system. => [http://support-au.canon.com.au/contents/AU/EN/0100303302.html](http://support-au.canon.com.au/contents/AU/EN/0100303302.html)
 
Else, there's also a .deb file => [http://support-au.canon.com.au/contents/AU/EN/0100236101.html](http://support-au.canon.com.au/contents/AU/EN/0100236101.html)

---

### Post by maqtanim on 2011-03-09
- Download the driver from [here]("http://support-my.canon-asia.com/contents/MY/EN/0100236101.html"). It is a .tar.gz file, which is an archived file (like .zip or .rar). 
- Extract it by right click it and select Extract. It will be extracted in a folder with the same name as the .tar.gz file.
- Open the folder. 
- Double click the **install.sh** file.
- And it will do the rest.

---

### Post by pe7er on 2011-09-15
Thank you for this solution!

I was able to get the scanner of MP 250 working with on Ubuntu 10.10 using SANE (Scanner Access Now Easy): [http://www.sane-project.org/](http://www.sane-project.org/)

And the printer with the information in this thread.
btw: you can also start the script from the command line by typing:
```
./install.sh
```

---

