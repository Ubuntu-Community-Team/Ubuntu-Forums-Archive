---
title: "Nvidia x-server settings - Monitor resolution"
date: 2009-05-12
forum: New to Ubuntu
---

### Post by wdypdx1 on 2009-05-12
Not quite a beginner, but having difficulty with this issue.

Used gksudo nvidia-settings.

In the gui I changed my resolution from 1280 x 1024 to 1600 x 1200 which happens to be the "auto" setting. 

All is fine, *except*, that the settings will not save and I have to use nvidia-settings to change them back each time I turn my computer back on. 

I took a look at the xorg.conf file and it's not obvious to me what may or may not need changing. Also took a look at the Xorg.0.log file -- no errors, (but 4 warnings related to the keyboard and mouse which work fine?? So not sure if I need to fix?)

So, any tips on how to get my monitor resolution to save and be there when I boot up my computer?

Thanks.

---

### Post by fooman on 2009-05-12
after you ran the gksudo nvidia-settings and made the changes...did you click on "save to x configuration file"?

run gksudo nvidia-settings again....set the resolution,  click "apply"....then click "save to x configuration file".  you may see a warning that not all changes can be applied...click on "apply what is possible",  then log out or restart to see if the changes "stick".

they should.

hope that helps.

---

### Post by wdypdx1 on 2009-05-12
> **fooman said:**
> after you ran the gksudo nvidia-settings and made the changes...did you click on "save to x configuration file"?

run gksudo nvidia-settings again....set the resolution,  click "apply"....then click "save to x configuration file".  you may see a warning that not all changes can be applied...click on "apply what is possible",  then log out or restart to see if the changes "stick".

they should.

hope that helps.

Yes, I tried this, but no luck. I did have the option of "Merge with existing file" in Nvidia-settings which was checked by default, and I saved with that default setting. I did not get any error messages.

Also looked at the xorg.conf file and it appears to have changed as it has this line now: 
Option   "metamodes" "1600x1200 +0+0; nvidia-auto-select +0+0;

However sort of midway through Xorg.0.log there are these lines:
(II) NVIDIA(0):     "1600x1200+0+0"
(II) NVIDIA(0):     "nvidia-auto-select+0+0"
(II) NVIDIA(0):     "1600x1200_65+0+0"

But at the end is this:
(II) NVIDIA(0): Setting mode "1280x1024"

??

---

### Post by donaldt on 2009-05-15
I have the same problem.  Two screens, good graphics capability but will not survive a re-boot.  Have to re-configure the second screen each time I restart my computer.

NVIdia X config is the program that will not retain the chosen settings.  Anyone else have any ideas???

donaldt

---

