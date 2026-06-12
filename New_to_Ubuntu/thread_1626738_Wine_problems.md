---
title: "Wine problems"
date: 2010-11-20
forum: New to Ubuntu
---

### Post by wannabeterminalpro on 2010-11-20
I know this is in the wrong category but I can't use my computer while this problem persists. Any help would be greatly appreciated.

Whenever I try to browse my "C" drive it gives me "error file not found". It also gives me the same error whenever I try to open a folder under "places". The problem goes away if I uninstall wine. I've uninstalled and reinstalled wine several times only to get the same effect with wine.
Is there a way to somehow stop wine accessing anything else than the drive_c or turn it off for a while?

---

### Post by blazemore on 2010-11-20
You can completely remove wine and all its config files with the following command:
```
sudo apt-get --purge remove wine*
```

---

### Post by ivarn on 2010-11-20
Or you can just delete .wine (/home/name/.wine) and go to Applications>Wine>Configure Wine. When you open configure wine, wine will restore the folders.
If you have important stuff in your wine folder, back them up, and overwrite them again after youve got your .wine folder back.

---

### Post by wannabeterminalpro on 2010-11-20
Thanks for both the answers! Answer No 1: I don't want to delete wine because I use it to play a whole lot of games (and know how to do that anyway)
Answer No 2: I tried that but after deleting /home/y/.wine I tried to open Home Folder under Places again and wine just reconfigured itself and I still got the same error

---

