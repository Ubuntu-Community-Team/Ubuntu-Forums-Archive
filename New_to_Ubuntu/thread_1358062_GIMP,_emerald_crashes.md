---
title: "GIMP, emerald crashes"
date: 2009-12-17
forum: New to Ubuntu
---

### Post by bobin on 2009-12-17
GIMP crashes shortly after starting ie by the time i open a image. To be more accurate the entire system crashes such that i have to press the power button. Emerald doesn't evene last this long. click on the icon and poof the system crashes( since i downloaded the packages myself, i suspect this might be due to missing packages)

---

### Post by ~sHyLoCk~ on 2009-12-17
Launch from a terminal and post the errors.

---

### Post by bobin on 2009-12-18
emerald ---
emerald: Screen 0 on display ":0.0" already has a decoration manager; try using the --replace option to replace the current decoration manager.

gimp---
no output for gimp . should i try
~$gimp > somename.txt 
  ?????????

---

### Post by lidex on 2009-12-18
You're trying to run two window decorators at once. Do you have CCSM (CompizConfig Settings Manager) installed? If not, install it.
Run CCSM, click the "Window Decoration" button under "Effects". Enter ```
emerald --replace
``` in the "Command" field. That will allow Emerald to run automatically. For current session enter that same command in a terminal.

For Gimp, go into synaptic and search "gimp", right-click and mark for re-installation all gimp related packages. Click apply. Are you using the development version? If so, you may need to downgrade.

---

