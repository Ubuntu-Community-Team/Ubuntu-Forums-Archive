---
title: "Desktop effects could not be enabled"
date: 2009-05-13
forum: New to Ubuntu
---

### Post by TheCrazyAnon on 2009-05-13
I tried to change log in screen then everything screwed up. Now my Graphics card isnt detected and I cant use any of the effects. Even my screen resolution is stuck at 800*600!

---

### Post by Crafty Kisses on 2009-05-13
We need more information than this. What kind of video card do you have? What are your system specs?

---

### Post by TheCrazyAnon on 2009-05-13
Its  128MB Nvidia GeForce FX Go8400 GS... system specs are 2GB ram and 1.7Ghz Core 2 Duo processor....

---

### Post by Crafty Kisses on 2009-05-13
Not sure if you're on a 32-bit or 64-bit machine, so I'll provide links to both of the proper official nVidia driver provided on nVidia's website.

[LIST]
[*]32-bit: [http://www.nvidia.com/object/linux_display_ia32_180.51.html](http://www.nvidia.com/object/linux_display_ia32_180.51.html)
[*]64-bit: [http://www.nvidia.com/object/linux_display_amd64_180.51.html](http://www.nvidia.com/object/linux_display_amd64_180.51.html)
[/LIST]

Now remember, before I go into this, I want you to backup your X just in case anything happens, so run the following:
```
sudo cp /etc/X11/xorg.conf ./xorg.conf.backup
```
Now download the proper driver for your architecture, once you have done that, follow my instructions and you should be on your way, remember to remove the old nVidia driver you have installed on your machine now, I'm pretty sure you can uninstall the driver you have now by running:
```
sudo apt-get --purge remove nvidia-glx-180 nvidia-kernel-common nvidia-settings
```
In some cases you might have to add the following line in the Linux restricted modules file, you can do that by running the following in the Terminal:
```
sudo gedit/etc/default/linux-restricted-modules-common
```
Then find the line that says the following:
```
DISABLED_MODULES=""
```
Then replace that with the following:
```
DISABLED_MODULES="nv nvidia_new"
```
Remember I'm assuming you installed the 180 nVidia driver via Synaptic and you are using the "180" driver. Now once you have downloaded the driver, you need to press Control-Alt-F2, then enter the following:
```
sudo /etc/init.d/gdm stop
```
Then once you've done that you need to run the following, remember I'm just guessing the file is called NVIDIA-Linux and it's saved to your desktop, so remember substitute your information:
```
cd ~/Desktop
chmod +x NVIDIA-Linux.run
sudo ./NVIDIA-Linux.run
```
Once it has installed and you have confirmed everything in the nVidia installer, you need to run the following:
```
sudo /etc/init.d/gdm start
```
If the driver isn't working properly for you, you need to stop the X server, and run the following:
```
sudo sh NVIDIA* --uninstall
```
Where the * is, you need to put the correct driver information. You might have some errors while you're trying to build the nVidia drivers, but if you do you might need to install the "build-essential" package, which can be installed by running the following command:
```
sudo apt-get install build-essential
```
Once you have the nVidia driver installed you can configure the video card by running the following:
```
gksudo nvidia-settings
```
Then from there you can add and edit settings to your video card.

---

### Post by TheCrazyAnon on 2009-05-13
Hey sorry for the late reply... i was upto the step where run the NVIDIA linux package... but then it said it didnt have a kernel or sumthing... so it compiled a kernel in gcc 4.2, but i had gcc4.3 soit said proceed if u know what you are doing... :P...So as I didnt, I quit the install. Then removed gcc 4.3, that changed the menu.lst file somehow... and then the grub... and now my comp keyboard and mouse not detected at startup... so i figure i start afresh... :P... any way thanks for ur help... will definately need it 2nd time round... :)

---

