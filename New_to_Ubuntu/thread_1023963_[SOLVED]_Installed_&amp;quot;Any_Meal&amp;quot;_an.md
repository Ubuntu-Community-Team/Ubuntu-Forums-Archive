---
title: "[SOLVED] Installed &amp;quot;Any Meal&amp;quot; and the text is not visible in the menu's?"
date: 2008-12-28
forum: New to Ubuntu
---

### Post by scotttie on 2008-12-28
Hi everyone,
just installed "Any Meal" and the text is missing from the menu's, all thats there is the underscore, if you click the mouse on it you briefly see the text but it's too fast to read.
any help greatly appreciated
thanks
Scottie

---

### Post by scotttie on 2008-12-28
Bump

---

### Post by gettinoriginal on 2008-12-28
This helps in OO3, don't know about Any Meal, but worth a try.  

System > Pref > Appearance > Fonts set rendering to "subpixel smoothing" then go to details set smoothing to "subpixel" and hinting to full.

---

### Post by scotttie on 2008-12-28
Thanks gettinoriginal,
I tried that but no difference, looking more closely it seems the text could be the same colour as the background but I am not entirely sure this is the case.
thanks

---

### Post by gettinoriginal on 2008-12-28
Is there and option area where you can choose font color ??

---

### Post by scotttie on 2008-12-28
Hi gettinoriginal,
I had a similar problem with Wine (seems it is a common problem with Wine) but found some screen shots which enabled me to "blindly" count and navigate through the menus to reset the fonts but unfortunately I cannot find any shots for "any meal" and as I cant see the text I am beat and cant see options tab.
thanks

---

### Post by gettinoriginal on 2008-12-28
I don't cook  LOL, but I will install it to see what I can find, be back in awhile. :P

---

### Post by ajgreeny on 2008-12-28
Try running without compiz enabled and you may see the text again.  It seems to happen with some programs and hardware when compiz is running certain plugins, so perhaps experiment with compizconfig-settings-manager and see if you can get everything working as you want.

---

### Post by scotttie on 2008-12-28
thanks ajgreeny,
I have tried that but no success, it seems its only with this one application, I have also tried uninstall and reinstall, all to no avail, thanks anyway

---

### Post by gettinoriginal on 2008-12-28
I installed it, there is no options or configure tabs, so font cannot be changed.  I did not go through the complete installation of downloading the DB, as it gave me lots of errors.  But I did find this, which lets you choose your distribution, and gives links to other like programs.  Sorry I could not be more help:

[http://packages.ubuntu.com/intrepid/anymeal](http://packages.ubuntu.com/intrepid/anymeal)

---

### Post by scotttie on 2008-12-28
Thanks very much gettinoriginal,
Thanks for the info, I have found some other changes that could be made to correct the Wine problem, a change in the registry E.g. [HKEY_CURRENT_USER\Software\Wine\X11 Driver]"ClientSideWithRender"="N"
I was wondering if I changed "Wine" to "AnyMeal" if this would invoke the change required, but I am unsure as I am a Newbie to Ubuntu (3 days ago) and I think I read somewhere Wine has its own Registry so this could cause a problem (maybe?)
thanks
 Scottie

---

### Post by gettinoriginal on 2008-12-28
Wine is an installation program for windows based applications, ie .exe files on linux.  According to Wareseeker.com, although Anymeal can be installed on windows, it is a gnu based program, so would work better on linux.  With all the problems involved so far with anymeal, maybe you could try one of the other apps:
Similar packages:
    * krecipes
    * krecipes-doc
    * krecipes-data
    * gfaim-data
    * phpmyadmin
    * rekall
    * gourmet
    * gfaim
    * qtstalker
    * gcfilms
    * eskuel

---

### Post by scotttie on 2008-12-28
Thanks gettinoriginal,
I think I will take your advise,thanks for your help.

Scottie

---

