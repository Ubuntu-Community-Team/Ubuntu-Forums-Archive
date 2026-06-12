---
title: "Themes don't show up"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by luke0927 on 2008-12-17
OK i have been trying out some themes ive found on the web...what i have found is that most of the .tar.gz files will drag right in and show up and work but not all of them....I have read on some of the other ones that you must place them in the Theme folder....I created a singe directory for one of the themes i want to try i copied the them to the folder in /usr/share/themes/<direcory>/<file name>  but it doesn't show up when i look in apperances themes?

Also i have found some that will not drag into the apperance themes section put if you pull up gdmsetup it drops in there?  the ones in gdm setup seem to only change the login screen is this a differnt type of theme?

---

### Post by Shhnap on 2008-12-17
I would like some help in this area too as I have created some themes via Emerald Theme Manager but have no idea how to set them as my ACTUAL theme.

They look so cool and I would love to have them show.

---

### Post by luke0927 on 2008-12-18
The ones i got to work i just opened system/preferences/appearance/themes and i was able to just drop them in and select them.

---

### Post by hellion0 on 2008-12-18
That works. Sometimes the only way to find some themes installed that way is to open the "Customize" window in Appearance. 

As well, you can extract them and put the resulting folders into /home/(your username)/.themes/ (which works for GTK and Metacity themes) or /home/(your username)/.icons/ (for icon sets). 

As for Emerald themes, I don't use it, so someone else would have to tell you a fool-proof way to make that work.

---

### Post by luke0927 on 2008-12-18
what do you do if you have created the file and unzipped the theme but it doesn't show up when you open the appearance GUI?

---

### Post by appi2012 on 2008-12-18
How did you create the emeral theme? Do you have [Emerald Theme Manager]("apt:emerald") installed? (click to install) Once you have that installed, you can browse for your theme package (compressed) and it will install it. To switch themes, just click on the theme you want, and if that doesn't work, then press Alt+f2 and type: 
```
emerald --replace
```

Hope that helps

---

### Post by luke0927 on 2008-12-18
not sure i downloaded the theme off out art.gnome.org now that i look at it it says login manager does that mean its not a full theme?

---

### Post by appi2012 on 2008-12-18
I see
You downloaded a login manager theme (GDM)
To use it, go to System -> Admin. -> Login Window

Go to the Local Tab, and click Add

Then just find the package and click Open

---

