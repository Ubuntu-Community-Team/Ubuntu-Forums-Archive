---
title: "Touchpad Help?"
date: 2009-08-15
forum: New to Ubuntu
---

### Post by Kyllikki2009 on 2009-08-15
I just installed Xubuntu on my G60-445DX (HP Laptop).  I have been having problems with the Synaptic touchpad.  I found drivers (at least I think I did) to correct this problem, and I do not know how to install them.  I downloaded and extracted them.  There was a how-to installation file, but this is all that it said:
to install from CVS:

 * checkout kdesdk/scripts and put it in the path
 * checkout kdereview/ksynaptics
 * cd /tmp
   svn2dist --i18n-module kdereview -v 0.2.2 -l -m -b -g /home/kombrisn/Project/kdereview/ ksynaptics
 * a ksynaptics-0.2.2 directory with a configure script has now been created

to install a tar ball:

 * ./configure && make && sudo make install

Did I get the right drivers (ksynaptics), or do I need others?  How do I install drivers on Xubuntu?  Any help would be greatly appreciated.  Thanks.

---

### Post by stoogiebuncho on 2009-08-16
What version of Xubuntu are you running?

I believe newer versions of Xubuntu use gsynaptics for touch pad stuff, but they should be installed by default. 

I don't really know, but ksynaptics sounds like it would be for KDE, not XFCE.

---

