---
title: "start up error kernel panic"
date: 2011-01-20
forum: New to Ubuntu
---

### Post by Jackson7 on 2011-01-20
hi guys. i updated some stuff on my laptop this morning as usual, then i did the restart as suggested so that the updates are complete.

but then i got this message saying: [    0.8.8741] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block

the caps button is blinking also, anyone know how to fix it? im VERY NEW to computers, so if you are able to help please give me a step by step :)

---

### Post by Rubi1200 on 2011-01-22
Hi,
which version are you running?

Please do the following:

Boot the Ubuntu Live CD/USB. Choose the option "Try Ubuntu without any changes." Once the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded, move the boot info script to the desktop.
3. Open a terminal and run the command

```
sudo bash ~/Desktop/boot_info_script*.sh
```

This will create a RESULTS.txt file on the desktop. Paste the _entire_ contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

