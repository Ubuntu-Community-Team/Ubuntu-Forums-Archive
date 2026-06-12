---
title: "pRoBlem in installing nvidia GT218 [GeForce310] at sony vaio S series"
date: 2010-07-07
forum: New to Ubuntu
---

### Post by erinvocavich on 2010-07-07
i'm new with this ubuntu 10.4 and i almost spend 2 weeks just trying to get this nvidia work. i already tried several steps coming from ubuntu forum but still i don't get it...just what i need is to work with this visual effects with my laptop. hope that  somebody would care to help me with this...thanks in advance!

---

### Post by overdrank on 2010-07-07
Hi and welcome, What is the model of the graphics card and some system specs may help?

You can use the command ```
lspci | grep VGA
``` to identify your graphics card.
The terminal is located under applications, accessories. 

Moved to Absolute Beginner Talk

---

### Post by Aloon on 2010-07-08
To install 310M card in Ubuntu 10.04 do the following:

Download this driver that works (many don't).

[http://www.nvidia.com/object/linux-display-amd64-195.36.24.html](http://www.nvidia.com/object/linux-display-amd64-195.36.24.html)

Save it to a folder that you know where it is.

[B]Uninstall Nvidia drivers from the past:

[/B]> sudo apt-get purge nvidia*

[B]Remove the nouveau driver that is the default:
[/B]
> sudo apt-get --purge remove xserver-xorg-video-nouveau 
[I]
[/I]
*Lastly, make some notes of the steps  below – you can’t read it and install at the same time!*
  Move  your downloaded Nvidia driver into your home folder. Just the home  folder. Not into any other folder. 



It often doesn't work to use the "hardware driver installer" while in X windows as you have probaly found out by now ... so you have to switch to a virtual terminal.

  
[LIST]
[*]Press 'CTRL+ALT+F1'
[*]You will  need to login with your user-name and password
[*]Type the following: 'sudo service gdm stop' (Minus  apostrophes') This closes X window.
[*]Press return/enter
[*]Type: 'sudo sh  ./NV'
[*]Press the tab button tol auto-complete the rest of the  name.
[*]Hit return/enter
[/LIST]
  During the following  process you will want to agree (that’s press ‘Ok’, yes, sure, why not,  etc) to the following things
  
[LIST]
[*]License  Agreement
[/LIST]
  Now, I'm pretty certain that you'll want to  agree to this - you can't complete installation without doing so. Press  the left-arrow key so 'Yes' is highlighted. Press Enter. 
  You may be prompted with a dialogue informing you that
  
[LIST]
[*]**"There appears to be a driver already installed"**
[/LIST]
  If you get this, agree by selecting 'Yes'. The current driver  will be uninstalled and then replaced with the new one.
  *The  kernel module is then built and the driver installed.*
  
[LIST]
[*]**"replace  current xorg.profile"**
[/LIST]
  ***MAKE SURE***  you agree to it updating your xorg.profile. If you don’t then you’ll be  greeted with a low-graphics, blinking bash-shell nightmare!
  **Finishing Up**  
   You'll be returned to the "command line" whereby you need  simply type 
[LIST]
[*]sudo reboot
[/LIST]
    to restart your machine. 



Now you should not have the split screen or a screen saying low res only. Next when your desktop comes in go to "system-->preferences --> appearances and go to the tab that says "visual effects" and change it from none to one of the two better settings. It will look for drivers and either it will work or it will say "cannot enable desktop effects". If it says the latter please post and I can try and help more.


If the driver works I would recommend installing "Ubuntu Tweak" so you can control your desktop effects better.


> 
sudo add-apt-repository ppa:tualatrix/ppa 
sudo apt-get update sudo apt-get install ubuntu-tweak


After its installed it can be found in: Applications—>System Tools—>Ubuntu Tweak

Next you need to do some editing of scripts to get your Nvidia 310M recognized properly. Follow the instructions on this thread exactly:

[http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup](http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup)

>     [IMG]http://www.gstatic.com/codesite/ph/images/star_off.gif[/IMG]       **NVIDIASetup**         *Setting up X11 with  NVIDIA's driver for the Vaio's new display using an EDID file*
    
  **Introduction[¶]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup#Introduction")**

There are a few necessary changes  to get the NVIDIA driver up and running. Make sure you are using version  >=195.36.15. 
**EDID Configuration[¶]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup#EDID_Configuration")**

As of Feb 9, the latest NVIDIA  drivers do not support the screen on the Vaio automatically. It is  required to explicitly specify the EDID dataset which actually is  available via the /proc filesystem. 
**Configure xorg.conf[¶]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup#Configure_xorg.conf")**

Add the following two lines to the  "Device" section of your xorg.conf: 
    Option         "ConnectedMonitor" "DFP-0"
    Option         "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"**Sample xorg.conf[¶]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup#Sample_xorg.conf")**

For example, a complete "Device"  section might look like this: 
Section "Device"
        Identifier      "InternalCard"
        Driver          "nvidia"
        Option          "ConnectedMonitor" "DFP-0"
        Option          "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
        Option          "RegistryDwords" "EnableBrightnessControl=1"
EndSection**Install uvesafb[¶]("http://code.google.com/p/vaio-f11-linux/wiki/NVIDIASetup#Install_uvesafb")**


[LIST]
[*][Ubuntu directions]("http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/")
[/LIST]


Do just like it says , edit xorg.conf:

> sudo gedit /etc/X11/xorg.conf

If you don't have gedit: sudo apt-get install gedit

When gedit opens the xorg.conf file , paste this part:

> Section "Device"
        Identifier      "InternalCard"
        Driver          "nvidia"
        Option          "ConnectedMonitor" "DFP-0"
        Option          "CustomEDID" "DFP-0: /proc/acpi/video/NGFX/LCD/EDID"
        Option          "RegistryDwords" "EnableBrightnessControl=1"
EndSection 

Press save in gedit and close it.

Before trying the below fix for your startup resolution , try installing gnome startup manager. It is suppose to do what is below , but its a simple gui. If startup manager doesnt make your starups nice then go to the part below.
> sudo apt-get install startupmanagerIf that doesn't work go to this link:

[http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/](http://idyllictux.wordpress.com/2010/04/26/lucidubuntu-10-04-high-resolution-plymouth-virtual-terminal-for-atinvidia-cards-with-proprietaryrestricted-driver/)

Do everything it says exactly.

Let me know if this helps you. I just went through the same thing. I know for a fact that the driver version I list above works for the 310M on a Sony Vaio F111

Good luck.

---

