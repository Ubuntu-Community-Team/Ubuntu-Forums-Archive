---
title: "Google Earth"
date: 2011-02-04
forum: New to Ubuntu
---

### Post by SivaCoHan on 2011-02-04
I download Google Earth form google.
I use "sudo ./GoogleEarth " install it.
but it doesn't work.
I can find it from appcations - web -google earth
but it can't be opened.

My OS version is Ubuntu 10.04 32bit
could you tell me how to fix it?

---

### Post by howefield on 2011-02-04
Last time I installed GoogleEarth, I used these instructions...

[http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html](http://www.webupd8.org/2010/11/install-google-earth-6-in-ubuntu-linux.html)

[http://www.uluga.ubuntuforums.org/showthread.php?t=1663259](http://www.uluga.ubuntuforums.org/showthread.php?t=1663259)

---

### Post by waynefoutz on 2011-02-04
[http://www.google.com/earth/download/ge/agree.html]("http://www.google.com/earth/download/ge/agree.html")

Just go here and download the 32 bit .deb file.

---

### Post by Wtower on 2011-02-04
Very good information. I tried installing the latest Google Earth and it worked ok except for a font issue that all text looked like chinese, so I would like ot share my finding with the community. To overcome that you need to install ttf-mscorefonts-installer from multiverse, which is also included within the wine metapackage anyway, if you have wine installed.

---

### Post by JC Cheloven on 2011-02-04
Hi, 
What I did was to install the package ```
googleearth-package
``` from the  repository and follow the instructions in the readme file. Basically, by it's an assisted process in which you create a .deb package for googleearth (it will download the googleearth binary from google at a point). Is the generated .deb package what tou can install afterwards.

All this mess is because of liseccing issues, but it's not so bad.

---

### Post by SivaCoHan on 2011-02-10
> **waynefoutz said:**
> [http://www.google.com/earth/download/ge/agree.html](http://www.google.com/earth/download/ge/agree.html)

Just go here and download the 32 bit .deb file.
Right,I got it from that URL

---

### Post by SivaCoHan on 2011-02-10
> **Wtower said:**
> Very good information. I tried installing the latest Google Earth and it worked ok except for a font issue that all text looked like chinese, so I would like ot share my finding with the community. To overcome that you need to install ttf-mscorefonts-installer from multiverse, which is also included within the wine metapackage anyway, if you have wine installed.
Ok,I am Chinese. 
Would you like to share your experience with me ?

---

### Post by treesurf on 2011-02-10
You may need to install lsb-core before installing Google Earth.  You will find good instructions here on both installation methods.  You'll probably want to uninstall your current installation before trying again.  Instructions on how to do this are also on this same page.

[https://help.ubuntu.com/community/GoogleEarth](https://help.ubuntu.com/community/GoogleEarth)


EDIT:  I just tried replicating your steps and received the same result.  Installing lsb-core before attempting to install the .deb of google-earth-stable (by simply double clicking on it) solved the problem.  I suggest you try this.

---

### Post by Wtower on 2011-02-11
> **SivaCoHan said:**
> Ok,I am Chinese. 
Would you like to share your experience with me ?

Ni hao :)

Just open the Software Centre and install ttf-mscorefonts-installer package, reboot (maybe logout-login is enough but anyway) and launch google earth again, should be ok.

---

### Post by Cracklepop on 2011-02-11
I've always been a little surprised whenever I see someone ask this,
 but anyway, it's now even easier: Google now gives you a .deb file - download it, doubleclick it, done. 
 
I'm using the 64 bit version right now.

---

