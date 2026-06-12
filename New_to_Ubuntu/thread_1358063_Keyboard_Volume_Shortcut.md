---
title: "Keyboard Volume Shortcut"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by killer 8 bit on 2009-12-17
ok I'm trying to figure out how to change my keyboard shortcut to increase the headphone jack volume instead of the master volume any help?

---

### Post by wesleybailey on 2009-12-18
You need to add a custom keyboard shortcut for the Headphone volume up/down

Add a Shorcut:
1. System->Preferences->Keyboard Shortcuts
2. Click "Add"
3. For the first shortcut name it "HP Volume Up"
4. For the command use **amixer set 'Headphone',1 5+**
5. Then choose a key combination i,e Ctrl-Alt-+

You can also add a shortcut to decrease the volume, use this command instead.
**amixer set 'Headphone',1 5-**

---

