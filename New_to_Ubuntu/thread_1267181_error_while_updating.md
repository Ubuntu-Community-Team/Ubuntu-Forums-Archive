---
title: "error while updating"
date: 2009-09-15
forum: New to Ubuntu
---

### Post by April1212 on 2009-09-15
**Getting "error" when updating** 			
 			 			 		   		 		 		I have 278 updates that need to be fixed and when i go to get the updates  a window pops up saying:

E: dpkg was interrunpted, you must manually run 'dpkg --configure -a' to correct the problem
E: cache -> open0failed, please report

Can anyone help me.????? 

Thank you very much!
April

---

### Post by Perfect Storm on 2009-09-15
Close the updater/Synaptic/add&Remove (important)

Open the terminal (Applications ---> Accessories ---> terminal)

Type;
```
sudo dpkg --configure -a
```

---

### Post by April1212 on 2009-09-15
wow!!! finally something happened.

But this is what it is saying at the bottom?

dpkg: error processing cupsys (--configure):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting configuration.
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-22-generic

---

### Post by Perfect Storm on 2009-09-15
Can you please post more of the output, so I can see which cupsys that have a hiccup?

If it is "cupsys" only. You can go to synaptic package manager, search for cupsys, right click on it and choose "Re-installation"

---

### Post by April1212 on 2009-09-15
Tried to update after i posted my last reply here and man it took for ever but i was able to update all 281 updates!!!!!!!!!!!!!!  Thank you so much. I didnt know to go to my applications tab?  Again thanks a bunch!

April

---

### Post by Perfect Storm on 2009-09-15
My pleasure. I'll then mark the thread solved.

---

