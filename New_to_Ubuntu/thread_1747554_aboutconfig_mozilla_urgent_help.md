---
title: "about:config mozilla urgent help"
date: 2011-05-02
forum: New to Ubuntu
---

### Post by fatharraxman on 2011-05-02
while I was trying to solve a previous problem to brows html I went to [http://kb.mozillazine.org/Register_p...#Linux_and_Mac]("http://kb.mozillazine.org/Register_protocol#Linux_and_Mac") and I screwed it really I want a way to bring things to normal or default again note that I don't remember what did I changed there exactly but I need help urgently

---

### Post by dniMretsaM on 2011-05-02
It would delete your entire profile (passwords, favorites, addons, etc.) but you could delete ~/.mozilla and it would fix it. I'll search around for less drastic measures. If you just want a temporary fix, simply rename that folder to .mozilla_old or something and restore it later when you find a better fix.

---

### Post by markjensen on 2011-05-02
[http://kb.mozillazine.org/Resetting_preferences](http://kb.mozillazine.org/Resetting_preferences)

> You can reset user preferences to the default values by manually removing the preferences file from the profile folder, as follows. (This will not affect any data stored in other files, such as toolbar data stored in the "localstore.rdf" file or any file-opening associations stored in the "mimeTypes.rdf" file.)

Important: Although this will also work in Mozilla Suite/SeaMonkey and Thunderbird, it is not recommended because all mail account settings and access to saved mail and passwords will be lost.

[LIST]
[*]Exit Firefox completely
[*]Open the Firefox profile folder. Caution: There is also a folder named "profile" in the Firefox installation directory that contains program defaults, which some users mistake for the Firefox profile folder that stores user data. Windows users should read this to find the profile folder that contains your user data and preference settings.
[*]Delete (or move to backup) the prefs.js file. (If you find multiple numbered prefs.js files or a read-only "prefs.js.moztmp" file, delete those files as well and see this article).
[*]Delete the user.js file, if found, or move it to a backup location (this file does not exist by default). 
[/LIST]
When you next reopen Firefox, it will rebuild the prefs.js file from program defaults. This will restore the default values of preferences displayed in about:config and restores the default theme. 

---

### Post by dniMretsaM on 2011-05-02
Ok, here is how to reset your settings to default (including your about:config changes). To open FF in safe mode, run:
```
firefox -safe-mode
```(Not sure if there is point-and-click way to open FF in safe mode, so I hope you don't mind using the command line.)
When it opens, a dialog box will open with 5 options. Check "Reset All User Preferences to Firefox Defaults" and hit the "Make Changes and Restart" button and there you go.

EDIT: 200th post!!!! Yay!

---

### Post by fatharraxman on 2011-05-02
no one of the above answers worked with me & I didn't find a dialog after terminal order

---

### Post by dniMretsaM on 2011-05-02
Hmm... That's odd.

---

### Post by fatharraxman on 2011-05-02
> **dniMretsaM said:**
> Hmm... That's odd.

Thank you dialog box needed closing firefox to show up and it is solved 
love terminal

---

