---
title: "can not get my nvidia graphics card to work"
date: 2009-09-23
forum: New to Ubuntu
---

### Post by Ecto Kid on 2009-09-23
Hi I am a a total newbie to Linux I heard and read a lot about  ubuntu and went for ubuntu studio 9.04, I have installed it but now my graphics card does not work.

My system is as follows:-

abit nf7-s motherboard
amd athlon 2800 xp processor
1gb of ram
agp fx 5600 nvidia graphics card

I have gone to the main menu, then system, then adimistration and click on hardware drivers option it comes up with 2 drivers i have tried installing both, but I can not get ether one to activate.

Then i went through the same menus but clicked on nvidia x server setings and I get a message You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server. 

So as i said in the beginning I am a total newbie to Linux so if any can help me with this issue I would appreciate it very much, but what I need is a step by step guide.

Many thanks in advance

---

### Post by 73ckn797 on 2009-09-23
Sometimes you will have to log out or restart to get the video driver to work. I assume you have tried that?

---

### Post by Ecto Kid on 2009-09-23
My bad I forgot to mention that, but yes I did restart the system but no joy.

---

### Post by overdrank on 2009-09-23
> **Ecto Kid said:**
> My bad I forgot to mention that, but yes I did restart the system but no joy.

Hi and you may try and update your system, then enable the nvidia drivers and if it fails after reboot then try the xfix option.
If you are unable to boot after attempting changes, you can reboot, choose the recovery mode in the boot menu, and then select the 'xfix Try to fix X server' option on the Recovery Menu. This should restore your X windows configuration to a usable condition and allow you to boot normally.

---

### Post by Ecto Kid on 2009-09-25
> **overdrank said:**
> Hi and you may try and update your system, then enable the nvidia drivers and if it fails after reboot then try the xfix option.
If you are unable to boot after attempting changes, you can reboot, choose the recovery mode in the boot menu, and then select the 'xfix Try to fix X server' option on the Recovery Menu. This should restore your X windows configuration to a usable condition and allow you to boot normally.

Yes thanks of your reply, but I have done this, but still my graphics card does not work.

Many Thanks.

---

### Post by fluxlizard on 2009-09-25
your card uses version 173. open System-administration---synaptic and search nvidia and make sure that you have nvidia-173-kernel-source checked and not some other version. If you have another version (sounds likely and probably 180), check the correct one and install it.

Reboot and it should work.

If not we can manually install the appropriate file from nvidia's website.

edit-- forgot to add that after reboot, you may have to go into appearance preferences to activate the driver- right click on desktop, select change desktop background, go to the visual effects tab, select normal and away you go.

PS- if you are new to linux, you may want to start with linux mint rather than ubuntu or ubuntu studio. It is still ubuntu, but auto sets up all the drivers, flash, etc right out of the box. I've used ubuntu several years and tried mint out a few weeks ago and it makes a huge difference over ubuntu on my machine- the graphics are faster for some unknown reason and everything is much simpler and just works and I still have access to all the ubuntu stuff- just install it and pretend it's ubuntu.

---

### Post by Ecto Kid on 2009-09-28
> **fluxlizard said:**
> your card uses version 173. open System-administration---synaptic and search nvidia and make sure that you have nvidia-173-kernel-source checked and not some other version. If you have another version (sounds likely and probably 180), check the correct one and install it.

Reboot and it should work.

If not we can manually install the appropriate file from nvidia's website.

edit-- forgot to add that after reboot, you may have to go into appearance preferences to activate the driver- right click on desktop, select change desktop background, go to the visual effects tab, select normal and away you go.

PS- if you are new to linux, you may want to start with linux mint rather than ubuntu or ubuntu studio. It is still ubuntu, but auto sets up all the drivers, flash, etc right out of the box. I've used ubuntu several years and tried mint out a few weeks ago and it makes a huge difference over ubuntu on my machine- the graphics are faster for some unknown reason and everything is much simpler and just works and I still have access to all the ubuntu stuff- just install it and pretend it's ubuntu.

Thank you for your reply, but I have solved my graphics card issue by uninstalling ubuntu studio and installing ubuntu desktop, the auto driver downloaded and installed and activated with no problems.

Many Thanks to everyone who gave their suggestions and help.

---

### Post by 73ckn797 on 2009-09-28
You can still install the programs for Ubuntu Studio from Synaptic.

ubuntustudio-graphics = A collection of applications aimed at 2D/3D creation and editing.

ubuntustudio-video = A collection of applications aimed at video creation and editing.

---

