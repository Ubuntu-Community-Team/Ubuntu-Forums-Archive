---
title: "change language settings"
date: 2009-05-07
forum: New to Ubuntu
---

### Post by hollowtd on 2009-05-07
So I have xubuntu installed on a dell. I'm getting ready to donate it to a school here in Morocco, but I need to change the language from English to French.Is there a way to do this without reloading the live CD? Is there a way to change the keyboard to a French one too? 

Cheers

---

### Post by sisco311 on 2009-05-07
First you have to install language-pack-fr and language-support-fr, then you can select the language at the login screen.

You can change the keyboard layout form: Menu -> Settings -> Xfce4 Settings Manager -> Keyboard -> Layout tab

Or you can install language selector (a GUI for installing language packs):
```
sudo aptitude install language-selector
gnome-language-selector
```

---

### Post by hollowtd on 2009-05-07
Wow, thanks for that. I will try all of that. I know how to do the terminal commands for the language selector, but what about ther Language-pack-fr? Do I do that from Terminal too or insert the live cd?

---

### Post by sisco311 on 2009-05-07
Well, you can use your package manager of choice. If you prefer the GUI (point-and-click), then search for/install the packages(language-pack-fr,language-support-fr, language-selector) from Synaptic or Add/Remove...

language-selector should show up somewhere in the Xfce4 Menu, but don't ask me where.

from the terminal is faster :)
```
sudo apt-get install language-selector language-pack-fr language-support-fr
```

---

### Post by hollowtd on 2009-05-07
Yes, that is what I'm looking for. Thanks for that!

---

### Post by hollowtd on 2009-06-04
I just updated to 9.04. How in the heck do I adjust the computer volume (not from the keyboard but on the screen)? Cheers again

---

