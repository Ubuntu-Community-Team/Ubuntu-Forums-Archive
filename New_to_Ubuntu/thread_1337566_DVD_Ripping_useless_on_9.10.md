---
title: "DVD Ripping useless on 9.10"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by latinhawk on 2009-11-25
I have spent more than a day already trying to get a DVD ripped without any success. All the available programs fail in one way or another. Left a project running last night and when I checked this morning still not completed. The latest program I used k9copy, Get's stuck at 88% and the time to complete keeps constantly growing yet the percentage remains the same. Any ideas?

---

### Post by Arup on 2009-11-25
Have you tried Acidrip? Works very nicely here on my PC. Also try another movie, maybe the one you are trying to encode has a damaged disc.

---

### Post by hellomoto on 2009-11-25
if you want pure simplicity try [ogmrip]("http://ogmrip.sourceforge.net/en/index.html")

---

### Post by pi.boy.travis on 2009-11-25
Make sure you have libdvdnav, libdvdread, and css installed.

Can you play the DVD with totem?

---

### Post by Tholley on 2009-11-25
I use DeVeDe to encode and copy (creat ISO image)
 
then use K3B to rip to new DVD.
 
that is the only way I have found to work for me, but it does work good.
 
Speed will depend on your chip and so forth.

---

### Post by x C0MMAND0 x on 2009-11-25
I would recommend Handbrake [http://handbrake.fr/downloads.php](http://handbrake.fr/downloads.php) , and if you are up to it the CLI version (command line interface) is MUCH faster and works better.

I even wrote a script for handbrake cli where you simply enter the DVD, double click the script and enter a Title for the file and then hit enter.  Makes it very easy.

But as other users said, make sure you have all of the correct libs to actually play the DVD otherwise you won't be able to copy it.

---

