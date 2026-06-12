---
title: "linux-headers and ndiswrapper"
date: 2011-03-06
forum: New to Ubuntu
---

### Post by pottzie on 2011-03-06
I've gotten a wireless card working using ndiswrapper. After running "apt-get upgrade", and upgrading to pre-released updates, the wireless doesn't "work." "Work" is in quotations because it shows the wireless working in the package tray, ifconfig and iwconfig both show as working. When I run "modprobe ndiswrapper", it just says that balck listing will be ignored in the future.
 One of the files that the upgrade loaded was linux-headers. I checked back to the guide I used to get the wireless working

[http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html](http://welcometoubuntu.blogspot.com/2007/10/howto-get-airgo-based-wifi-enabled.html)

 and step 5 was getting linux-headers. I've made some headway by running modprobe -m and modprobe -a, but modprobe ndiswrapper still doesn't show anything about modprobe.ko

 Don't know if the new linux-headers clobbered my set up.Anyone have a guess? And what's the secret to keep ndiswraper working through upgrades?

---

### Post by JKyleOKC on 2011-03-06
Do you have the dkms (dynamic kernel module support) package installed? It's what automagically creates the new modules required whenever the headers package gets upgraded. You can go into Synaptic and search for "dkms" to find out; if it's installed, the checkbox for it will be green. If it's empty, check it for installation and hit apply. It will download the files, then work for a while creating the needed headers. When you reboot, all should be well.

Hope this helps!

---

### Post by pottzie on 2011-03-06
Well, I had high hopes....unfortunately(?)dkms was already installed. Thanks, though, it's a help!

---

### Post by JKyleOKC on 2011-03-06
The new headers would not have clobbered your setup, but the new kernel itself probably could have, and did! Kernel modules have to match the version of the running kernel, so the existing ones for ndiswrapper would not work with the new kernel.

I don't use ndiswrapper myself so what follows is mostly guesswork. I suspect you need to repeat the steps in the guide you used before, starting with step 6, to create a new set of modules. The second part of the procedure probably will not need to be done again; the main thing is to create the new ndiswrapper module to match the latest kernel.

---

### Post by pottzie on 2011-03-06
OK, Ill give it a shot. Guess this means that dkms doesn't work when a kernel updates?

---

### Post by JKyleOKC on 2011-03-06
No, it means that dkms only updates modules that were installed from the repositories rather than being built from source. At least that's my best guess; I've not actually gone through the dkms code to find out how it works.

---

### Post by pottzie on 2011-03-06
In the terminal,I'm stuck at:"ndiswrapper is not installed. You can get it by typing 'apt-get install ndiswrapper." Of course, I already have a directory for ndiswrapper in my home directory after tar xvfz'ing it, per the guide. Seems I had the same problem when I first installed the driver, and wound up using the dkms GUI, ("Windows Drivers")which I had also installed.
 The guide starts by uninstalling ndiswrapper, and everything associated with it. Maybe that includes the "Windows Drivers" that I had installed previously. It's still showing in System>Administration, but won't open after I give the permission. It just "flashes" a panel for an instant (less than a second) and then isn't there.
 I installed ndiswrapper-dkms hoping that would get ndiswrapper to show when I ran ndiswrapper -l, but it's still not showing up.

---

