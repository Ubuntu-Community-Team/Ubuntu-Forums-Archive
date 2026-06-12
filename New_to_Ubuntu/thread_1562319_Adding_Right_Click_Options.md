---
title: "Adding Right Click Options"
date: 2010-08-27
forum: New to Ubuntu
---

### Post by jaycee23 on 2010-08-27
How can I add options to the "right click" context menu?

Specifically when I right click on a file I have the option to "Copy to.."

Currently my options with "Copy to.."  are OtherPane (which is greyed out), Home Folder & Desktop. I would like to add my own option to this submenu.

Any help very welcome. A solution even more so ...    :D

---

### Post by Vaphell on 2010-08-27
install nautilus-actions package
run nautilus-actions-config-tool

add action, name it 'Copy to WHATEVER'
program: cp
parameters: %f /path/of/WHATEVER    (or %M - read the available help and pick suitable symbol)
optionally you can filter which mime-types or extensions should get the option

if the action is valid, it should show up after nautilus restart in rightclick menu
in general if something can be done in terminal, you can transform it to nautilus action.
Unfortunately it doesn't show in the same section as default options.

---

