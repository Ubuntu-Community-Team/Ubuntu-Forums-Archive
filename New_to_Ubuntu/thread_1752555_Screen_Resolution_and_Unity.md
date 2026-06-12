---
title: "Screen Resolution and Unity"
date: 2011-05-07
forum: New to Ubuntu
---

### Post by coronoahcoro on 2011-05-07
Hi everyone I just installed Ubuntu 11.04 on VirtualBox. The max resolution that I can set is 1024 x 768 while my laptop's native resolution is 1366 x 768. What do I need to do to run Ubuntu on the native resolution?

Also after the installation is finished, Ubuntu said that I cannot run Ubuntu. My laptop is only 2 years only, so I found it odd that my laptop cant run Unity. I use this command to test the Unity:

/usr/lib/nux/unity_support_test -p

There are some parts that say 'no' : Not software rendered, GLX texture from pixmap, and Unity supported. Please advise, thanks :)

---

### Post by diablo75 on 2011-05-08
1.  Virtualbox Guest Additions needs to be installed in Ubuntu before it will be able to allow Virualbox to have control over the display resolution.  Once installed, the virtual machine can dynamically increase or decrease screen resolution to fill out whatever size window it's sitting in.

You can follow this guide to install this extra software:  [http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/](http://helpdeskgeek.com/linux-tips/install-virtualbox-guest-additions-in-ubuntu/)

2.  Unity requires hardware acceleration, which may possibly become accessible to the VM once Guest Additions are installed, but I don't know.  It's not exactly a feature you can expect to be as well supported as running directly on graphics hardware, instead of indirectly.  The whole reason it's called a "virtual machine" is because it's not literal hardware your guest OS thinks it's running on top of, but pseudo/simulated hardware.

---

### Post by coronoahcoro on 2011-05-08
Hm that's odd. I believe Guest Additions is already installed since I got the mouse pointer integration message everytime I started Ubuntu. I am able to choose a screen resolution above 800 x 600 but the highest is 1024 x 768. Is this also the limitation of using Virtual Machine?

---

### Post by diablo75 on 2011-05-09
> **coronoahcoro said:**
> Hm that's odd. I believe Guest Additions is already installed since I got the mouse pointer integration message everytime I started Ubuntu. I am able to choose a screen resolution above 800 x 600 but the highest is 1024 x 768. Is this also the limitation of using Virtual Machine?

Whatever version of Guest Additions that comes with Ubuntu by default is slimmed down and isn't compatible with all features in the most recent version of Virtualbox.  You need to replace the old Guest Additions with the latest version and the installation instructions I gave you earlier would have done this had you tried it.  It would appear that since the guide was written the steps you have to take have gotten even simpler; no need to type a command into terminal now that the disc offers you the choice of auto-running it.

Before you start your VM is to open your machine settings and check the display section to make sure 2D and 3D acceleration are enabled (add check marks).  You do this by clicking on the name of the VM you want to run and click the Setting button to bring up the settings panel for that particular machine and then click Display on the left.

After you've got that set and saved, start your VM up, wait for it to fully boot and put your mouse into the title bar of Virtualbox at the very top of the monitor to reveal the menus and click on the Devices menu.  The last item on the list says "Install Guest Additions".  This will mount an ISO as a CD/DVD into the VM and Ubuntu will ask if you want to Autorun the disc.  Tell it YES.  Then tell it YES again and it will ask you to enter your admin password.

A terminal window will open and proceed to remove the old guest additions, install the new ones and compile the necessary kernel modules.  Reboot when it's finished and Unity should work.

I've attached 2 screen shots to show what this looks like during and after the installation of Guest Additions.

---

