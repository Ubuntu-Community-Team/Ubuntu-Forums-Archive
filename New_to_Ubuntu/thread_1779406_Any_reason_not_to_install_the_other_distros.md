---
title: "Any reason not to install the other distros?"
date: 2011-06-10
forum: New to Ubuntu
---

### Post by TerribleLIar on 2011-06-10
I'm perfectly happy with Ubuntu 11.04, but I'm just curious to see what the other variants of Ubuntu look like and how they handle compared to Ubuntu. Is there any reason not to do it, aside from taking up extra space? I want to try Kubuntu, Xubuntu, and Lubuntu. None of them, especially Lubuntu, will replace any of the others will they? And if space ever does get tight, will uninstalling the (X)ubuntu-desktop file uninstall all of the programs they add, like all of the KDE variants of Ubuntu programs? And finally, does Edubutnu have its own special interface, or does it just add the educational programs? I might try it too, just for kicks. Thanks in advance!

---

### Post by papibe on 2011-06-10
Do you mean in the same machine?

---

### Post by ratcheer on 2011-06-10
No reason at all why you can't do that. The main problem that could occasionally occur is that a new addition might take over your boot loader. For instance, Fedora added and configured legacy grub and did not detect my main Ubuntu system. So, I had to boot to a Live CD, chroot to my Ubuntu partition, and install-grub. This both put me back on grub2 and also supported the Fedora installation.

Go for it. Have fun.

Tim

---

### Post by Elfy on 2011-06-10
IF you mean adding (for example xubuntu) with apt-get install xubuntu-dekstop or from synaptic then you need to do more than uninstall xubuntu-desktop.

You will if you do that end up with lots and lots of menu entries for the apps each variant uses.

IF you have enough memory might be worth doing it in a virtual machine line virtualbox - then you will only see it as it would be installed on it's own.

More information about installing the *buntu-dekstops and removing them can be seen here - [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Look at the Playing around section - xfce = xubuntu, kde = kubuntu lxde = lubuntu (I think)

---

### Post by oldos2er on 2011-06-10
Since the only difference between Ubuntu, Kubuntu, and Xubuntu is the desktop environment, you can simply install the appropriate *buntu-desktop package and then choose which one to run at login.

kubuntu-desktop
xubuntu-desktop
lubuntu-desktop
edubuntu-desktop

for example.

---

### Post by Blasphemist on 2011-06-10
I'll guess from what you've said that you want this all in one actual installation/partition. I say that because of asking about the k program removal. If you add the other desktop environments to the existing install, you'll get more options for session type at the login screen and will have programs for all de's mixed. Programs for KDE will not be removed by removing KDE were you to do that.

The way to keep all clean would be to install in separate partitions but that will require disk space for all installations.

---

### Post by ppv on 2011-06-10
The distros that you mention all are based on Ubuntu and have the same underlying stuff. The major differences across these distros is the DE (This does not include Edubuntu). Ubuntu uses Gnome, Kubuntu KDE, Xubuntu XFCE and so on.

You can install all of them on the same machine as long as there is space. It would also be suggested to backup all your important files before installing/uninstalling.


You could just create a live USB of the various distros and try it out. This way you won't have to do all the partitioning and installation nor would you have to do any uninstalling. Just format the USB drive. This way you can still keep your original system as is and yet check out other distros.

To create a live USB, download the iso from the website and use a program like unetbootin or Ubuntu's builtin USB creator to create live USBs.

---

### Post by uRock on 2011-06-10
Edubuntu is Ubuntu with a bundle of extra applications and it does have some theme packages. It is not a separate desktop environment.

Marking the *ubuntu-desktop package for removal in Synaptic Package Manager does not offer to uninstall any other packages.

You can install all four DEs in one install, but your menus will become very cluttered.

---

### Post by TBABill on 2011-06-10
Sometimes it's just fun to test others out in their own partition. I keep 3 on one machine for that very reason. One install that I never touch except to get work done, another running Debian and a third for whatever interests me. Funny thing is I always come back to Ubuntu, Mint and Debian. I should just install LMDE, Ubuntu and Debian and be done with it, but I love to tinker. Plus it's fun to learn when you try different distros with different package management tools, hardware tools (or lack of), etc. No better way to learn than to break and fix it :)

---

### Post by TerribleLIar on 2011-06-10
Thanks for all the quick responses! Too many to reply to even! For right now, I'm just going to stick with Ubuntu variants. Maybe when I get a new PC, I'll install other stuff like Fedora and Mint, when there's nothing on the hard drive that I'd care to lose if I ever screw things up. The psychocats link looks very helpful!

---

### Post by ppv on 2011-06-10
> **TerribleLIar said:**
> Thanks for all the quick responses! Too many to reply to even! For right now, I'm just going to stick with Ubuntu variants. Maybe when I get a new PC, I'll install other stuff like Fedora and Mint, when there's nothing on the hard drive that I'd care to lose if I ever screw things up. The psychocats link looks very helpful!

Linux Mint is also based on Ubuntu.

---

