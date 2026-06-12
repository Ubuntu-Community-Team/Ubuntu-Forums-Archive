---
title: "YouTube no longer plays after upgrade to firefox 3.5"
date: 2009-09-07
forum: New to Ubuntu
---

### Post by Dave W. on 2009-09-07
Hello all,

I recently upgraded to ff 3.5 and now I am required to download the latest flash-player.   Of course, when I do, I cannot install, because I am using a 64 bit system.  My 32 bit system was easy to fix. I just down loaded the i386 architecture.

Does anyone have any suggestions for an easy fix?
Thanks folks,
Dave

---

### Post by TheLions on 2009-09-07
here is the flash for amd_64 (64 bit) :
[http://labs.adobe.com/technologies/flashplayer10/](http://labs.adobe.com/technologies/flashplayer10/)

instructions here:

> 

   1. [[COLOR="DarkOrange"]Download the plugin[/COLOR]]("http://labs.adobe.com/downloads/flashplayer10.html") to begin installation. A dialog box will appear asking you where to save the file. 
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Quit your browser.
   4. Remove all existing Adobe Flash Player installations from the system.
   5. Unpackage the file. A directory with contains libflashplayer.so will be created.
   6. Copy libflashplayer.so to ~/.mozilla/plugins. Create the 'plugins' folder if it does not exist yet.
   7. Launch your brower. To verify installation in Firefox choose Help > About Plug-ins from the browser menu.


---

### Post by Dave W. on 2009-09-07
Thanks,  I'll give this a try.  I am slightly overwhelmed by the whole tar.gz thing and making sure everything else is in place.  I am backed up though.

-Dave

---

