---
title: "wine"
date: 2009-02-15
forum: New to Ubuntu
---

### Post by inuit-joe on 2009-02-15
By installing wine dosent that make my computer more ceceptable to viruses
like windows based viruses?


- inuit joe

---

### Post by TCSnyder on 2009-02-15
You have a virtual C:/ drive. 

so any Windows virus has access only to the C:/ drive, which is in the ~/.wine folder, but it cannot get files from all over your computer.

---

### Post by HittingSmoke on 2009-02-16
> **inuit-joe said:**
> By installing wine dosent that make my computer more ceceptable to viruses
like windows based viruses?


- inuit joe

Yes and no. Nothing critical will be changed or damaged.

Read this for more info. [http://ubuntuforums.org/showthread.php?t=72598](http://ubuntuforums.org/showthread.php?t=72598)

The virus did actually manage to dump a bunch of copies in his home folder, but I doubt any damage was done.

---

### Post by SunnyRabbiera on 2009-02-16
There have been people who toy around with windows viruses in wine, some actually do harm but its usally very localized such as the home folder and nothing systemwide.
I have heard of 1 or 2 viruses getting as far as the /usr directory though but no permanent effects.
But really such things are easy to avoid, just dont run any .exe's you dont know under wine...
You can use clamav if you are paranoid though.

---

### Post by Lerxst51 on 2009-02-16
Also, as long as your not running the virus as root, vital files cannot be accessed.

---

### Post by inuit-joe on 2009-02-18
maybe this is just me imagining things but does it slow down ur computer
it seems that way with mine

---

