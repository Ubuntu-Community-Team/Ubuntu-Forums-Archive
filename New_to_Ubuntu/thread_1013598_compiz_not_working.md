---
title: "compiz not working"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by ja660k on 2008-12-17
i had compiz and i clicked some option in ccsm ...
then it blacked out my whole screen so i quickly pressed ctrl+alt+f6

and ran
sudo apt-get remove compiz*

then logged back into gnome and reinstalled it
sudo apt-get install compiz*

and when i go to run ccsm through terminal i get this:
```

ja660k@Linux:~$ ccsm 
/usr/lib/python2.5/site-packages/ccm/Constants.py:78: GtkWarning: Unable to locate theme engine in module_path: "aurora",
  Tooltips = gtk.Tooltips()
/home/ja660k/.themes/Dust Aurora/gtk-2.0/gtkrc:465: error: invalid string constant "murrine-panel", expected valid string constant
ja660k@Linux:~$ 

```


what should i do?

---

### Post by Tatty on 2008-12-17
I think removing compiz entirely was a little drastic in this situation.  

Do your basic desktop effects work? System->Preferences->Appearance->Visual Effects.  If so then compiz is working and it may just be ccsm that has got confused.

Try purging then re-installing ccsm.

---

### Post by mrbiggbrain on 2008-12-17
if i remember, ccsm dosn't ship with some pacakges of compiz-fusion, try useing adept and entering ccsm into the search box, one should say "advanced desktop effect settings"

and i had an issue with Compiz where i set a setting too high and my pc kept freaking, i just did a failsafe of KDE4 (where u sue compiz) alt+f2 ccsm and set the setting back down, if you do something dumb, this is the way to fix it, as compiz's config will work, but compiz or kde windows wont run.

---

### Post by ja660k on 2008-12-17
well i dont have visual effetcs, i only have advanced desktop effects settings, and thats what i was fiddling with, and before it made "live" chanegs to my windows. and now it doesnt

---

### Post by Tatty on 2008-12-17
> **ja660k said:**
> well i dont have visual effetcs

If you go to System->Preferences->Appearance it will load up a dialog box, one of the tabs says "Visual Effects".  Under this tab you will see Normal and Extras options.  These switch on some default compiz presets for ubuntu, 
Try selecting them and see if they work.  If they do then we know that compiz itself is working.

---

### Post by mrbiggbrain on 2008-12-17
i had this issue when i wasnt using the ccsm tool, maybe if custom is set, it has to be ccsm, if its not, you cant use ccsm (set to custom to use it) sometimes it will always default back to custom, so check it

---

### Post by ja660k on 2008-12-17
perfect, thanks guys =) visual effects did it 

just before i didnt know how i could turn it off.

thanks alot

---

