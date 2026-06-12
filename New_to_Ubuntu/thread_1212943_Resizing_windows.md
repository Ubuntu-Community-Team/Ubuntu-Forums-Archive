---
title: "Resizing windows?"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by ltwinner on 2009-07-14
I know you can resize windows with alt+middle click but that is awkward on my mouse as the scroll wheel acts as the middle button. So is it possible to change the alt+middle click to alt+right click which would be alot handier for me?

---

### Post by Hospadar on 2009-07-14
Probably, I think that's an option to be changed in compiz.

First you need to install the compizconfig settings dialog, either grab it in synaptic or ```
sudo apt-get install compizconfig-settings-manager
```
Then go to System->Preferences->compizconfig (i think is the name?)

Somewhere in there you'll see the resize windows plugin (you can search for it) and you should be able to set up your hotkeys there.

---

### Post by wojox on 2009-07-14
Try Alt+F8

---

### Post by ltwinner on 2009-07-15
> **Hospadar said:**
> Probably, I think that's an option to be changed in compiz.

First you need to install the compizconfig settings dialog, either grab it in synaptic or ```
sudo apt-get install compizconfig-settings-manager
```Then go to System->Preferences->compizconfig (i think is the name?)

Somewhere in there you'll see the resize windows plugin (you can search for it) and you should be able to set up your hotkeys there.

OK, you were correct mate, it can be changed in compiz settings manager. The problem though is that when I set it it is not being saved. 

When I change it to "<Alt>Button3" it says "The new value for the button binding for the action Initiate Window Resize in plugin Resize Window conflicts with the action Window Menu of the General Options plugin. Do you wish to disable Window Menu in the General Options plugin?"

Then no matter what option I select here it doesn't matter, the setting still doesn't get saved. If I go out of the Resize Window page and go back into it, it has reverted to <Alt>Button2.


How can I get this setting to save?

---

### Post by carml on 2009-07-15
Try choosing a different combination of keys :)

---

### Post by ltwinner on 2009-07-15
Ive tried different keys, the problem is that it doesn't save.

---

