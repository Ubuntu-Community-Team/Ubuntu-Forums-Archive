---
title: "MATLAB Problems"
date: 2009-08-04
forum: New to Ubuntu
---

### Post by sharkllama on 2009-08-04
Hi,
   I followed the instructions from [https://help.ubuntu.com/community/MATLAB](https://help.ubuntu.com/community/MATLAB) to get matlab installed on my machine and functioning.  Prior to downloading the icon and installing the launcher application MATLAB worked fine.  After downloading the icon and the launcher app MATLAB no longer shows the file menus and the editor is completely useless (see the attached screenshot).  Any ideas on how to fix this?  Anyone else encounter this issue?
Thanks,
-Brant

---

### Post by barnex on 2009-08-04
Hi,
I've had a similar problem. I had to turn of compositing ("desktop effects"), after which matlab worked fine.
 
I think there was also some java option somewhere that can fix this, but I forgot... Anyway, now I use octave instead of matlab.

hope this helped.

---

### Post by sharkllama on 2009-08-04
Yeah, 
   Apparently the composting was the issue.  My issue with that is that I would like to run avant window navigator as I like the docking features.  Unforutunately this requires a composting window manager, which interferes with MATLAB.  So, for the time being I will run no visual effects and no dock so that I can use MATLAB, but another workaround would be helpful.  Thanks!
-Brant

---

### Post by sharkllama on 2009-08-04
Alright, 
   So thanks to this thread the issue is partially solved.  I've re-enable visual effects and am using the avant window manager and can now see all of the important components of the MATLAB desktop and editor.  The graphical fronted of matlab is usable again, but I have some funky coloring as you can see in the screenshot.  
  The fix entailed editing the shell script that starts matlab.  I added:

export MATLAB_JAVA=/usr/lib/jvm/java-6-sun-1.6.0.03/jre

as the first command of the script.  Any ideas on how to fix the coloring appreciated!
Thanks,
Brant

---

### Post by Hospadar on 2009-08-04
I'm running matlab in KDE with composting (from KWin) and everything works fine, not sure how awn works in kde, if it needs compiz or can use the kwin context, but might be worth a try.  Besides, if you want pretties, kde is all about that.

---

### Post by barnex on 2009-08-05
This is just a guess, but did you enable "java window fix" under "workarounds" in the compiz config settings (ccsm)? Perhaps this helps, perhaps not...

---

