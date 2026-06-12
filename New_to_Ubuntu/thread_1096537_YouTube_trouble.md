---
title: "YouTube trouble"
date: 2009-03-15
forum: New to Ubuntu
---

### Post by myolbug on 2009-03-15
I'm sure this is something I added that is causing this trouble, but when I watch videos on YouTube I can watch one or two and then on the third one when I click on the link to the next one, the video screen is blank.  I have sound but not video.

Fresh install of Ubuntu 8.10 64 bit on a new computer.  [http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=SYXS-BB-981155](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?Sku=SYXS-BB-981155)

Is this a 64 bit Flash issue?  I amn pretty sure I have all of the Flash items from Add/Remove programs.

However, which ones are needed and which aren't?  What command will display what I have and what I don't

---

### Post by myolbug on 2009-03-15
Bump??

---

### Post by gandaran on 2009-03-15
are you running 64-bits ubuntu and using the 32-bits flash from the apt repositories or have you installed the 64-bits adobe beta flash?

---

### Post by Yashiro on 2009-03-15
[http://ubuntuforums.org/showthread.php?t=772490](http://ubuntuforums.org/showthread.php?t=772490)

---

### Post by myolbug on 2009-03-16
Thanks for the link.  It helped but I still have some issues of it not displaying the screen on YouTube.  However, I installed Opera 9.64 and I haven't had any problems with YouTube, but now I need to install a patch for Quicktime.  Ah well. I pretty much have everything I need now.

---

### Post by Dynaflow on 2009-03-16
You may want to scan through this if you haven't already: [http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

---

### Post by myolbug on 2009-03-19
Hmm, I tried it and I now have a conflict.  Now I receive this error message; **E: Type 'ul' is not known on line 36 in source list /etc/apt/sources.list**


This occurred after I did this:  

**sudo wget [http://www.medibuntu.org/sources.list.d/intrepid.list](http://www.medibuntu.org/sources.list.d/intrepid.list) -O /etc/apt/sources.list.d/medibuntu.list**

**wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update**


**gksudo gedit /etc/apt/sources.list**



[b]deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free
deb-src [http://packages.medibuntu.org/](http://packages.medibuntu.org/) intrepid free non-free[/b]

Finally, close and save the sources file and install the Medibuntu key by copying and pasting the following command into the terminal:

**wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update**

Now I can't check for updates, as  I get the above error message every time

---

### Post by myolbug on 2009-03-19
I fixed the error by deleting the ul features. from line 36 of the sources.list i.e. : ## newer versions of some applications which may provide usefgksudo gedit /etc/apt/sources.list  

It used to have the ul features on the end

---

### Post by gandaran on 2009-03-19
--------------------------------------

---

