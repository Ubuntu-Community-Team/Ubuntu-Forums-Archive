---
title: "bios reset defaults accident"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by jumpingjaxs on 2009-06-21
hi im new to linux and made a small problem much bigger. please bear with me and let me know what info you need..
i have intrepid ibex.

what happened: my monitor had been quietly squealing & a friend suggested the screen resolution might be not set right. 

i went to preferences, screen resolution, and tried a different option in the list, which didnt fit at all, made the windows impossible to navigate (oops). when tried to set back to original resolution, screen went black and could do nothing. 

rebooted computer. windows still wonky and impossible to navigate, tried again to choose proper screen res, black screen- had to restart again. 

friend suggested undo everything by setting defaults. i thought i knew what he meant (huge oops).. i went into bios where i remembered seeing an option regarding defaults, found it, and chose to 'set to failsafe defaults'. 

computer tries to restart but upon loading: 'error 17' and is stuck on start up page.

can only find vague differing info about error 17. 

please help me undo my stupid mistake so my pc will operate again.

---

### Post by Legace on 2009-06-21
You changed the order of your harddisks/cd-drives in BIOS by restoring the default settings. Try to change them back to the way they were..

You could also try to reinstall GRUB: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#Quick%20Start)

If above don't work, boot into Ubuntu Live CD, and post contents of /boot/grub/menu.lst and the output of the following command:```
sudo fdisk -l
```

---

