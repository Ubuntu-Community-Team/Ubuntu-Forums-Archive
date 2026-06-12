---
title: "Problems with nvidia graphics card"
date: 2011-06-05
forum: New to Ubuntu
---

### Post by condorw on 2011-06-05
So i'm attempting to make the switch to linux and began by installing Ubuntu 11.04 on my laptop today. The first thing I thought to do was make sure my graphics card (a nvidia 310M, laptop is a Toshiba Satellite M645 btw) was properly configured, since I got a startup message telling me my hardware was not good enough for Unity. I accessed the System>Administration>Additional Drivers and found that my nvidia driver was installed but "Not in use." I then opened up the Nvidia X server thing where it told me that the nvidia driver was not properly configured in the xconfig file, and told me to run nvidia-xconfig from root, which I did. Afterwards i rebooted (sudo reboot) and after the boot screen I get... well, a whole lot of nothing. I have a couple of lines of what appears to be initialization info (a checklist of [OK]s or [fail]s) and then blank screen that echos keystrokes but does nothing else. I can still access the terminal via Ctrl-Alt-F1, but as to how to get my graphics card working properly, alas, I have no clue. Any suggestions?

---

### Post by papibe on 2011-06-05
Is it a M645-S4050?

If so, there's bad news. You have [Optimus]("http://www.nvidia.com/object/optimus_technology.html"), that it's not yet supported on Linux.

One possible solution would be to look an option in the BIOS to either disable Optimus or disable the Nvidia card (so you can use just the Intel graphic core).

For more information search Optimus in the forums.

Regards.

---

### Post by Finalfantasykid on 2011-06-05
It looks like your nvidia card uses optimus technology.  What this means is that you have you nvidia card for things like games and watching HD videos, but you also have an intel integrated graphics for everything else.  This can greatly extend the battery life, but unfortunatly it also means that in Linux, it is pretty tricky to get access to the nvidia card.

If you are lucky, you can disable the intel integrated chip in the bios, so you are only using the nvidia card, but most likely this won't be the case.

Lately, there has been alot of work to get this working on Linux, and the most promising one is bumblebee ([https://github.com/MrMEEE/bumblebee](https://github.com/MrMEEE/bumblebee)).  It is still in pretty early stages, and for me, I have experienced quite a bit of crashes, and in one case I had to reinstall the OS(because of an unfortunate typo).  So just as a heads up there if you are going to try this.

---

### Post by condorw on 2011-06-05
dang, I was afraid of this. Well, that unfortunately limits what I wanted to do, but I'll see if  I can find some sort of workaround with using just the nvidia card (since games and movies are about 50% of what I use my laptop for!). Thank you both so much for your help!

---

