---
title: "Help installing video driver"
date: 2009-04-06
forum: New to Ubuntu
---

### Post by IvanK35 on 2009-04-06
I need help, I have an ASUS A7N266 VM mother board which has Nvidia GeForce2 MX integrated VGA technology.  I have 512MB of memory. I installed Ubuntu ver. 8.10 with no problems, but my screen resolution is 800x600 and no option to set it higher.  I went to System, Administrator, Hardware Drivers and it found an Nvidia driver that was tested by Ubuntu and recomended.  It does not function properly.  It set the screen resolution to the higest value.  I can see the top bar (Applications   Places   System ...), but most of the rest of the screen is horizontal lines.  I can click on System and get a drop down window but it is horizontal lines.  If I move the mouse down into the window it will clear up and I can click Preferences and its drop down is horizontal lines.  I can some times move the mouse down and see Screen Resolution and select a lower resolution, but none help.  The system will also lock up and I have to use the power off button to restart.

I changed the BIOS from 64MB to 128MB for the display driver.  This did not help.  I went to the Nvidia web site and found a driver for the GeForce2 MX in their legacy driver section and downloaded it.  This is my first time using Linux.  I double cliked the driver and it said it has to be run by root.  Read enough to find that I would have root privileges if I typed sudo in front of the file (in Terminal mode)  This started the program but than it quits with an error saying that it will not work in X level.  Nvidia indicates that I should run the program at Runlevel 3.  It also says that I need to change the system so that when it restarts after installing, the system will still need to be in Runlevel 3.  The instructions that they give do not seem to match the Ubuntu distribution.

Can you give me instructions on how to run the downloaded driver program.  The Program name is:  "NVIDIA-Linux-x86-96.43.11-pkg1.run".  The version that Ubuntu loads is 96.43.09.

Ivan

---

### Post by jbrown96 on 2009-04-06
First you need to get some packages to build the driver.

1) ```
sudo apt-get install build-essential
```

switch to a virtual terminal. Press Ctrl+Alt+F1 and then login.

Then you need to kill your display
This takes care of the run level 3 warning.
3) ```
sudo /etc/init.d/gdm stop
```
If you are using kubuntu, then change gdm to kdm. 

Install the driver
4) ```
sudo sh ./Desktop/DRIVER NAME
``` You may need to change Desktop to something else, depending on where you downloaded the file. If you are having trouble finding the file, press the tab key to list the current files. It also works as a auto-completion.

Just answer yes to all the questions, and make sure that you let it create a new xorg.conf file for you, so the driver will be activated. 

Then reboot. 
```
sudo reboot
```

---

### Post by IvanK35 on 2009-04-06
Thanks for your information.  I was able to get the driver to install but it did not help.  I will look some more on the Nvidia site to see if there is a different driver.

Ivan

---

### Post by jbrown96 on 2009-04-06
Nvidia releases several different versions of the same driver. It's for various kernels, I believe. You want the one that ends in pkg2.run

---

### Post by IvanK35 on 2009-04-06
I can not find a pkg2 version of the driver.

Ivan

---

### Post by acexcat on 2009-08-09
I'm having a similar problem with the same MoBo (Asus A7N266-VM)... nVidia doesn't seem like it wants to play nice.  The drivers that install automatically as well as the drivers that I installed from EnvyNg...
(found here: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) )
...still produce the same problem.

(Also, "sudo get-apt install build essential" failed, sorry)

I've got pretty much all of Jaunty 9.04 installed, and everything except the display seems to be working fine.  The display looks like it's trying to do a hybrid of 680x480 or whatever that ratio is and then pastes the normal wallpaper onto the screen at either 800x or 1200x resolution; also, any windows that open doesn't display content until a button is mouse-over'ed.  Using the GUI is kinda like a cross between that echo-y screen or melty-screen screensaver and a bad dream because that's how it's currently opperating.

Command line functions fine.

I know scripting, but tweaking and installing is really not my thing; this is my first official install of Linux, and to make it worse, it's FOR another Linux n00b (that's n00b with two capital zeros, never used (or even SEEN) it before) we need help.

Can anyone help?

---

### Post by acexcat on 2009-08-09
edit:

I tried installing the drivers from the nVidia website as well (DL'ed onto other computer, installed from disc) and while it cured that weird behavior, it no longer allows for 1024x780 resolution; max res is 800x600 again.

Is there any way to (Ge)Force that integrated nVidia vidoe piece to WORK, or am I going to be condemned to purchasing a 3rd party video card?

---

### Post by oldos2er on 2009-08-09
If you go to menus System, Administration, Hardware Drivers, are you able to install the drivers?

---

### Post by Garrovick on 2009-08-09
I had problems with my onboard 6100 nVidia card and poor screen resolution.  I found a dollar 6200 nVidia PCI card at the flea market, installed the card and the Ubuntu provided drivers.  Resolution problems were over.

No "terminal" trial and error silliness needed.  At least for me.

---

### Post by acexcat on 2009-08-09
I tried this:

> **oldos2er said:**
> If you got to menus System, Administration, Hardware Drivers, are you able to install the drivers?

...yes, and I even "enabled" the nVidia specific graphics package, but after activating the driver effects and whatnot, I had to use recover mode to UNupgrade it; unresponsive blank screens are not a happy thing.

Sorry it didn't work, but thanks for the suggestion; anything else we can try?

---

### Post by oldos2er on 2009-08-10
"(Also, "sudo get-apt install build essential" failed, sorry)"

 Should be **sudo apt-get install build-essential**

 Do you have source code repositories enabled?

---

### Post by acexcat on 2009-08-10
> **oldos2er said:**
> Should be **sudo apt-get install build-essential**
Do you have source code repositories enabled?

I'll try the command again, but I'm pretty sure I got it right in entereing it on the other computer... checked spelling and caps and all real careful.  Myeh... nobody's perfect, and if that's all I missed, I'll count my blessings.

Source Code Repositories... dunno about that.  Tell me more?

---

### Post by oldos2er on 2009-08-12
> **acexcat said:**
>  Source Code Repositories... dunno about that.  Tell me more?

 System, Administration, Software Sources, check the box next to 'Source Code'.

---

