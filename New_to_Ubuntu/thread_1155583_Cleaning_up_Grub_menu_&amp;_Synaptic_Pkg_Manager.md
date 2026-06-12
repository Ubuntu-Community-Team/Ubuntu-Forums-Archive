---
title: "Cleaning up Grub menu &amp; Synaptic Pkg Manager"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by iClouseau88 on 2009-05-10
Hi everyone,

I am looking for a way to efficiently clean up Grub menu and Synaptic Manager at the same time.  Currently following each update or upgrade, in order to delete older linux header or linux image files I have to manually do this for each file in Grub and Synaptic.

Thanks in advanced.

---

### Post by BGFG on 2009-05-10
For general cleaning you can try this :
[http://buck-nasty.blogspot.com/2009/01/bleachbit.html](http://buck-nasty.blogspot.com/2009/01/bleachbit.html)

also deborphan.

and i use Start Up Manager(in the repos) to manage grub, but for simultaneous management, I'm stumped.

---

### Post by freeman2000 on 2009-05-11
You can clean Grub & Synaptic simultaneously.  Here are the steps:

1. Find out the kernel you are running currently, by typing in a Terminal window (without the ")  "uname -r"   and note down the version number.

2. Open Synaptic (from System -> Administration menu) and search for "linux-image".  A green box on the left indicates that the package is installed. 

3. Right-click on those kernels you no longer need and select 'Mark for Complete removal' (leave the kernel you found in Step 1 unselected)

4. Click Apply

All your old/unused kernels should be gone and GRUB will also be automatically updated.

Reboot and verify your GRUB.  Good Luck.

---

