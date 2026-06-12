---
title: "Toshiba T115"
date: 2010-05-04
forum: New to Ubuntu
---

### Post by chuck_d on 2010-05-04
Hello,

I'm brand new to Ubuntu.  I recently purchased a Toshiba T115, and I am thinking of installing Ubuntu Netbook Edition on it.  However I have been seeing some things written that Ubuntu doesn't work very well on Toshiba, especially this line.  

Does anyone have success getting Ubuntu to run properly on this specific laptop already?  If anyone knows of any workarounds I will need to do from the standard installation of Ubuntu your advice would be much appreciated.

Thanks in advance.

Chuck

---

### Post by warfacegod on 2010-05-04
I have a Toshiba Satellite P25-s607 and I have had zero issues with the hardware.

My advice to you is this. Download unetbootin and use it to create a LiveUSB of Ubuntu. With that you can try Ubuntu without installing it to your HDD. If everything works fine in Live then your likely to have no issues installing and running Ubuntu.

If you don't have a USB jump drive then make a LiveCD of Ubuntu.

---

### Post by chuck_d on 2010-05-05
Thank you.  I did exactly that and now I am up and running and installed version of Ubuntu on my new laptop.  I have much work ahead learning all the tweaks I want to make, including getting the infamous cube up and running, but my critical functions are all working fine.

---

### Post by warfacegod on 2010-05-05
I have a puny nVidia GeForce 5200GO 64 MB and I had no problem getting Compiz running with Cube.

I suggest simple-ccsm for starting out with Compiz Cube. You can find it in System> Admin.> Synaptic Package Manager.

Before that though, go to: System> Admin.> Hardware Drivers (AKA Jockey) and activate the recommended video driver. And wireless if one is there.

---

### Post by chuck_d on 2010-05-05
Thanks again.  I had already activated the ATI display driver but wasn't sure yet what the proper method for install compiz was.  I did that and then turned on the cube and rotate cube, but the ctrl-alt-arrow wasn't working.  I rebooted and upon logging in the display gets shifted upwards.  I cannot see the, i forget the name for what Windows would call the taskbar at the top (panel?).  The top of my screen is at the menu bar for Opera, (File / Edit/ View...)  Also I cannot rotate the cube with ctrl-alt either.  hrmm... more reading to do

---

### Post by warfacegod on 2010-05-05
Yes, its called a panel.

My Toshiba automatically has rotate set to use Left+Right Touchpad buttons and move the pointer.

You'll also want to get the compizconfig-settings-manager from Synaptic. Its the advanced version of simple-ccsm. It can be rather overwhelming at first. That's why I suggested simple-ccsm.

Can't help you with ATi drivers, I refuse to use ATi in Linux. There driver support is awful but getting better.

---

### Post by chuck_d on 2010-05-05
Great, got it working with the open source radeon drivers now.  Thanks once again.  I still have a lot of playing to do with all these compiz plugins :D

Most all of my linux experience is in a shell, so all these GUI stuff is new to me now that I'm using it on a laptop.

Ditched those proprietary drivers since it seems they aren't necessary.

---

### Post by warfacegod on 2010-05-05
Cool. Glad to hear it.

A few Toshiba users have found that their cooling fans don't work properly. Some have found that fnfxd in Synaptic fixed the problem. It has some other uses too that you may find useful, have a look.

Post a screenshot of what you come up with for Compiz. Here's mine. Not bad for a 64 MB video card huh?

---

### Post by chuck_d on 2010-05-06
Thanks for the heads up on the fan, I had heard something about that, but my fan is at least running.  I can stick my ear up to the vent and it blows on it.  So romantic.  

Awesome screenshots, I have a way to go, but here's where I am after getting this laptop just this morning.

---

### Post by warfacegod on 2010-05-06
I like the reflection with that Skydome. This site has lots of stunning window themes, icon themes, pointers... etc. [http://gnome-look.org/]("http://gnome-look.org/")

---

