---
title: "Installed ubuntu on a virtual machine with vmware, will not boot."
date: 2009-08-14
forum: New to Ubuntu
---

### Post by ABagOfFritos on 2009-08-14
It gets to white writing on black background and gives me some error messages, and then simply says at the bottom "initramfs" (this could be slightly misspelled) and allows me to type here.

The OS did boot initially, and downloaded several updates, and while applying the updates, the screen went blank and I was unable to do anything but reboot the virtual machine.

If any further information is needed, please let me know what you need and I will do what I can to get you that information.

Thanks.

---

### Post by SoftwareExplorer on 2009-08-14
Does it ever say something like press esc to enter the menu, Grub booting? If so, that's probably what you want to do. If you can get in, what options does it list?

---

### Post by ABagOfFritos on 2009-08-15
Ubuntu 9.04, Kernel 2.6.28-14-generic
Ubuntu 9.04, Kernel 2.6.28-14-generic (recovery mode)
Ubuntu 9.04, Kernel 2.6.28-11-generic
Ubuntu 9.04, Kernel 2.6.28-11-generic (recovery mode)
Ubuntu 9.04, memtest86+

---

### Post by SoftwareExplorer on 2009-08-15
Try doing Ubuntu 9.04, Kernel 2.6.28-11-generic. If that doesn't work, will have to resort to one of the recovery mode ones. I'm guessing that the computer froze while installing a new kernel or some other component required to start up, and so we'll try an older version and if the older version works, then we can fix the new version from it.

---

### Post by ABagOfFritos on 2009-08-15
Successfully booted from where you said to go.

Hit me with my next steps.

EDIT: I'm also having troubles with my mouse when it boots up, its really choppy and laggy in its movement, if you know a reason why this might be, let me know, and hopefully let me know a solution as well.

---

### Post by SoftwareExplorer on 2009-08-15
See if you can finish installing any updates. There might be errors we have to work through because of half-installed packages, but then again it could just work. I might go to bed soon, so if I quit responding and you get errors, search the forums and if you can't figure it out, then it's ok to post another thread about package installing errors.

---

### Post by SoftwareExplorer on 2009-08-15
> **ABagOfFritos said:**
> 
EDIT: I'm also having troubles with my mouse when it boots up, its really choppy and laggy in its movement, if you know a reason why this might be, let me know, and hopefully let me know a solution as well.
I don't really know why it would be doing that, I guess I'm still learning and don't know it all (unluckily)

---

### Post by ABagOfFritos on 2009-08-15
> **SoftwareExplorer said:**
> See if you can finish installing any updates. There might be errors we have to work through because of half-installed packages, but then again it could just work. I might go to bed soon, so if I quit responding and you get errors, search the forums and if you can't figure it out, then it's ok to post another thread about package installing errors.

When I get logged in to the older version, it does not begin any updates, and I can't seem to find out where to go to manually start the updates either.

---

### Post by JKyleOKC on 2009-08-15
> **ABagOfFritos said:**
> When I get logged in to the older version, it does not begin any updates, and I can't seem to find out where to go to manually start the updates either.To manually start updates, click the "Applications" button and from that menu, select System. From the System menu, select "Update Manager" and when it asks for the password, type in your login password. The Update Manager should load and give you a dialog window that has a button marked "Check" (this is the same window that you get automatically when you're notified of new updates) so click that button to check for new updates. It will download all the repository files anew, and check them. If it finds any updates you'll get a list of them and can proceed from there.

The choppiness of your mouse movement is probably because you're running in a virtual machine and may not have enough RAM to achieve full speed for the virtual CPU. My VMWare box has 2 GB of RAM and I've given half of it to the virtual machine; my Virtualbox systems have much less RAM (256 MB and 512 MB respectively) and they do show a bit of lag in response to mouse movements...

---

### Post by SoftwareExplorer on 2009-08-15
> **ABagOfFritos said:**
> When I get logged in to the older version, it does not begin any updates, and I can't seem to find out where to go to manually start the updates either.
If you are on Xubuntu, then follow JKyleOKC's directions. If you are on Ubuntu, Go to System->Administration->Update Manager.

---

### Post by ABagOfFritos on 2009-08-16
> **JKyleOKC said:**
> To manually start updates, click the "Applications" button and from that menu, select System. From the System menu, select "Update Manager" and when it asks for the password, type in your login password. The Update Manager should load and give you a dialog window that has a button marked "Check" (this is the same window that you get automatically when you're notified of new updates) so click that button to check for new updates. It will download all the repository files anew, and check them. If it finds any updates you'll get a list of them and can proceed from there.

The choppiness of your mouse movement is probably because you're running in a virtual machine and may not have enough RAM to achieve full speed for the virtual CPU. My VMWare box has 2 GB of RAM and I've given half of it to the virtual machine; my Virtualbox systems have much less RAM (256 MB and 512 MB respectively) and they do show a bit of lag in response to mouse movements...

The VM has 512 MB ram, I can't imagine that not being enough to run the mouse.

Thanks for these instructions though, and you too, SoftwareExplorer, I'm going to boot up the VM now and see if I can get this going.

---

### Post by ABagOfFritos on 2009-08-16
Good news - Mouse works fine now, not that I did anything, it just does. :)

Bad news - I still cannot connect the virtual machine to the internet, even with a wired connection.  I have to go to bed and then work in the morning though, I'll post up some details when I can get back to this.

---

