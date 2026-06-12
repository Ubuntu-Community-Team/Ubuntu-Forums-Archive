---
title: "How do i run .run files?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by undying23 on 2009-04-15
I've been attempting to enable desktop effects for days, but it hasn't worked so i tried downloading an ATI Driver rather than the NVIDIA driver that i currently have but i don't know how to open it...this is the name of the file: ati-driver-installer-9-3-x86.x86_64.run

---

### Post by billgoldberg on 2009-04-15
You don't have an ATI card, so the ATI drivers won't work.

Use EnvyNG (google it) to install the latest NVIDIA driver.

---

### Post by AXeS on 2009-04-15
do you have an nvidia card or ati card?

to run the .run file you got to use terminal.

---

### Post by Jakey_TheSnake on 2009-04-15
Post the output of:

```
lspci -v | grep VGA
```

please.

---

### Post by AXeS on 2009-04-15
ok what you can do is use nautilus browser to copy that file from wherever to your home directory...then open up your terminal and do this as is in terminial:
```
sudo ./ati-  (push tab after 'ati-' it should fill out the rest of the wording)
``` 
you dont have to change directory.

---

### Post by Jakey_TheSnake on 2009-04-15
Please post output of my command first, in case you don't have an ATI card.

---

### Post by undying23 on 2009-04-15
i have an NVIDIA GeForce Go 6150 (version 180) but i just downloaded the ATI card. However, after rebooting, it came up with an error saying 'Ubuntu is running in low graphics mode: No configuration detected'

---

### Post by Jakey_TheSnake on 2009-04-15
Just downloaded the ATI driver you mean? If you have a nVidia card, then the ATI driver will NOT help you. 

Download nVidia drivers from here:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

edit: I can only see GeForce Go 7 Series, or GeForce 6 Series. Please ```
lspci -v | grep VGA
``` into the terminal and post output. It doesn't take long :)

---

### Post by AXeS on 2009-04-15
only read your other post now...
dont install ati drivers you gona make it worst.

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> Just downloaded the ATI driver you mean? If you have a nVidia card, then the ATI driver will NOT help you. 

Download nVidia drivers from here:

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

edit: I can only see GeForce Go 7 Series, or GeForce 6 Series. Please ```
lspci -v | grep VGA
``` into the terminal and post output. It doesn't take long :)

Alright, cool, thanks sorry i'm a noob to computers, it said 'nVidia Corporation GeForce 6150SE nForce 430 (rev a2)
'

---

### Post by undying23 on 2009-04-15
> **AXeS said:**
> only read your other post now...
dont install ati drivers you gona make it worst.

Okay, i'll uninstall them it's just what some other guy told me earlier so i went ahead and did it

---

### Post by Jakey_TheSnake on 2009-04-15
You installed the ati drivers? Hummm. 

In the folder you installed them from/to there should be an ati-uninstall.sh file or something. Find it, then tell me what its filepath is (it will say at the top of your file browser).

NB: this would be easier if you had MSN or something.

edit: try looking in /usr/share/ati - tell me when you have located it and what it is called.

---

### Post by undying23 on 2009-04-15
> **AXeS said:**
> ok what you can do is use nautilus browser to copy that file from wherever to your home directory...then open up your terminal and do this as is in terminial:
```
sudo ./ati-  (push tab after 'ati-' it should fill out the rest of the wording)
``` 
you dont have to change directory.

oh btw, when i typed sudo ./ati- and pressed TAB it yelled at me and didn't do anything other.

---

### Post by Jakey_TheSnake on 2009-04-15
Please read my post. Are you _sure_ you installed them?

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> You installed the ati drivers? Hummm. 

In the folder you installed them from/to there should be an ati-uninstall.sh file or something. Find it, then tell me what its filepath is (it will say at the top of your file browser).

NB: this would be easier if you had MSN or something.

I had only installed it to my desktop, figuring it was most likely temporary, therefore easily deleted.

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> Please read my post. Are you _sure_ you installed them?

unless it obliterated itself during the reboot, then i'm sure i had installed it

---

### Post by Jakey_TheSnake on 2009-04-15
Look in the folder /usr/share/ati, do you see anything with "uninstall" in its title?

edit: are you sure you mean installed, and didn't just download from the internet to your desktop? After downloading the file, exactly what did you do? Did you use any commands in the terminal?

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> Look in the folder /usr/share/ati, do you see anything with "uninstall" in its title?

edit: are you sure you mean installed, and didn't just download from the internet to your desktop? After downloading the file, exactly what did you do? Did you use any commands in the terminal?
i attempted to use the command ' sh ./ati-driver-installer-9.2-x86.x86_64.run' to no avail
and i didn't find anything with 'uninstall' in the title

---

### Post by Jakey_TheSnake on 2009-04-15
Well if it didn't work, then I don't think you installed it. Did you notice any change in performance after the reboot? 

EDIT: FIRST, was there even a folder called "ati" in /usr/share ?

1. Download this: [http://us.download.nvidia.com/XFree86/Linux-x86/180.44/NVIDIA-Linux-x86-180.44-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/180.44/NVIDIA-Linux-x86-180.44-pkg1.run) to your _DESKTOP_

2. Run: ```
cd ~/Desktop
```

3. Then: ```
sudo sh NVIDIA-Linux-x86-180.44-pkg1.run
```

And follow the prompts on screen. 

Tell me when you've done that.

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> Well if it didn't work, then I don't think you installed it. Did you notice any change in performance after the reboot? 

EDIT: FIRST, was there even a folder called "ati" in /usr/share ?

1. Download this: [http://us.download.nvidia.com/XFree86/Linux-x86/180.44/NVIDIA-Linux-x86-180.44-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/180.44/NVIDIA-Linux-x86-180.44-pkg1.run) to your _DESKTOP_

2. Run: ```
cd ~/Desktop
```

3. Then: ```
sudo sh NVIDIA-Linux-x86-180.44-pkg1.run
```

And follow the prompts on screen. 

Tell me when you've done that.

'You appear to be running on an X server' i'm not using an NVIDIA X driver, so how do i disconnect?
No, there wasn't a folder so i suppose, as you said, i had just downloaded it to the desktop rather than installing it

---

### Post by Jakey_TheSnake on 2009-04-15
> **undying23 said:**
> 'You appear to be running on an X server' i'm not using an NVIDIA X driver, so how do i disconnect?

Eh, sorry I misunderstood, run:

```
sudo /etc/init.d/gdm stop
```

```
cd ~/Desktop
```

```
sudo sh NVIDIA-Linux-x86-180.44-pkg1.run
```

```
cd
```

```
sudo /etc/init.d/gdm restart
```

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> Eh, sorry I misunderstood, run:

```
sudo /etc/init.d/gdm stop
```

```
cd ~/Desktop
```

```
sudo sh NVIDIA-Linux-x86-180.44-pkg1.run
```

```
cd
```

```
sudo /etc/init.d/gdm restart
```

okay, it worked until my computer rebooted,  then it told me it couldn't locate any configuration files because the kernels were missing, so it wanted to go in 'low graphics mode' again

---

### Post by Jakey_TheSnake on 2009-04-15
But it worked absolutely _fine_ until your computer restarted? Can you tell me _exactly_ what it says. If it comes up in a pop-up box, take a print-screen and upload it as an attachment to your post please :)

---

### Post by Jakey_TheSnake on 2009-04-15
Please post your /etc/X11/xorg.conf file. (IMPORTANT)

Try pressing ctrl+alt+backspace now. Tell me what happens. 

Also, please try all of these things: 

> If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

* development tools like make and gcc are installed
* the linux-headers package matching the installed Linux kernel is installed
* the pkg-config and xserver-xorg-dev packages are installed
* the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx does not exist.
If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

DISABLED_MODULES="nv" 

You can google anything in there you're not sure about, and ask here if you can't find it. Make sure you do the "DISABLED_MODULES" bit.

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> But it worked absolutely _fine_ until your computer restarted? Can you tell me _exactly_ what it says. If it comes up in a pop-up box, take a print-screen and upload it as an attachment to your post please :)

**Ubuntu is running in low-graphics mode**

The following error was encountered. You may need to update your configuration to solve this.

(EE) Failed to load module "type 1" (module does not exist, O)
(EE) NVIDIA(O): Failed to initialize the NVIDIA kernel module! Please ensure.
(EE) NVIDIA(O):  that there is a supported NVIDIA GPU in the system and
(EE) NVIDIA(O):  that the NVIDIA device files have been created properly.
(EE) NVIDIA(O):  Please consult the NVIDIA README for details.
(EE) NVIDIA(O):  ***Aborting***
(EE) Screens(s) found, but none have a usable configuration

*i pressed okay and reconfigured the graphics using the default (generic) configuration*

---

### Post by Jakey_TheSnake on 2009-04-15
Xorg.conf please :)

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> Please post your /etc/X11/xorg.conf file. (IMPORTANT)

Try pressing ctrl+alt+backspace now. Tell me what happens. 

Also, please try all of these things: 

 

You can google anything in there you're not sure about, and ask here if you can't find it. Make sure you do the "DISABLED_MODULES" bit.

when i pressed CTRL+ALT+BACKSPACE, it logged me out

etc/X11/xorg.conf file:
# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# Note that some configuration settings that could be done previously
# in this file, now are automatically configured by the server and settings
# here are ignored.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Device"
	Identifier	"Configured Video Device"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
EndSection

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> Please post your /etc/X11/xorg.conf file. (IMPORTANT)

Try pressing ctrl+alt+backspace now. Tell me what happens. 

Also, please try all of these things: 

 

You can google anything in there you're not sure about, and ask here if you can't find it. Make sure you do the "DISABLED_MODULES" bit.

Huh i don't have the xserver-xorg-dev file and i 'don't have permission to change the /etc/default/linux-restricted-modules-common configuration file'

---

### Post by Jakey_TheSnake on 2009-04-15
> **undying23 said:**
> Huh i don't have the xserver-xorg-dev file and i 'don't have permission to change the /etc/default/linux-restricted-modules-common configuration file'

If you type: ```
gksudo nautilus
``` then navigate to that file and open it, you can edit it. 

Also, about you not having xserver-xorg-dev, run: ```
sudo apt-get install xserver-xorg-dev pkg-config build-essential
``` and type "y" then enter at the prompt. 

-----------------------------------------------------

Did you do all the things I said above?

Ctrl+Alt+Backspace is supposed to restart X server =| 

Try putting: ```
Driver       "nvidia"
``` after the "Section   "Device"" part, then restarting. 

To edit your xorg.conf you'll have to use:

```
sudo gedit /etc/X11/xorg.conf
```

If that doesn't work, we'll try a complete nvidia removal, then a fresh install with a command I believe will solve the NVIDIA kernel issue. 

But MAKE SURE you tried all the things I posted in quote marks above, then restarted before we go down that road.


**^ PLEASE NOTE I edited the top half of this post ^**

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> If you type: ```
gksudo nautilus
``` then navigate to that file and open it, you can edit it. 

-----------------------------------------------------

Did you do all the things I said above?

Ctrl+Alt+Backspace is supposed to restart X server =| 

Try putting: ```
Driver       "nvidia"
``` after the "Section   "Device"" part, then restarting. 

To edit your xorg.conf you'll have to use:

```
sudo gedit /etc/X11/xorg.conf
```

If that doesn't work, we'll try a complete nvidia removal, then a fresh install with a command I believe will solve the NVIDIA kernel issue. 

But MAKE SURE you tried all the things I posted in quote marks above, then restarted before we go down that road.

Yeah, i did everything that was on the list and i was able to edit that file but the Driver      "nvidia" code didn't give me a response..oh and i got the xserver file

---

### Post by Jakey_TheSnake on 2009-04-15
> **undying23 said:**
> Yeah, i did everything that was on the list and i was able to edit that file but the Driver      "nvidia" code didn't give me a response..

Hummm. Bugger, I really hate graphics drivers. Well, run these: 

```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
``` 

Then: 

```
cd ~/Desktop
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-180.44-pkg1.run -n -s --x-prefix=/usr/lib/xorg --kernel-source-parth=/usr/src/linux-headers-`uname -r`
sudo /etc/init.d/gdm start
```

Hopefully this will work now. Run each command separately, it's easier that way. Tell me how each step goes!

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> Hummm. Bugger, I really hate graphics drivers. Well, run these: 

```
sudo apt-get --purge remove nvidia-glx* nvidia-kernel-common nvidia-settings
sudo rm /etc/init.d/nvidia-*
sudo update-rc.d nvidia-kernel remove
``` 

Then: 

```
cd ~/Desktop
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-180.44-pkg1.run -n -s --x-prefix=/usr/lib/xorg --kernel-source-parth=/usr/src/linux-headers-`uname -r`
sudo /etc/init.d/gdm start
```

Hopefully this will work now. Run each command separately, it's easier that way. Tell me how each step goes!
step one: was successful

step two told me: rm: cannot remove `/etc/init.d/nvidia-*': No such file or directory

step three told me:  Removing any system startup links for /etc/init.d/nvidia-kernel ...

step four: was successful

step five told me: Could not open  sh ./NVIDIA-Linux-x86-180.44-pkg1.run

step six: was successful

---

### Post by Jakey_TheSnake on 2009-04-15
And step 3 was successful? 

If so, go on to the next stage :)

---

### Post by undying23 on 2009-04-15
> **Jakey_TheSnake said:**
> And step 3 was successful? 

If so, go on to the next stage :)

Thanks for all the help, man, i appreciate it
i'm deprived of sleep, though, so i'm going to go get some

---

### Post by Jakey_TheSnake on 2009-04-15
Did it work? You can't leave me in suspense >_> 

If you do go to sleep before reading this, I probably won't read the thread again unless you draw my attention back to it, so feel free to shoot me a PM or email me at [email]clampstand@gmail.com[/email] 

I believe you should either be done, or have to run ```
cd ~/Desktop
sudo /etc/init.d/gdm stop
sudo sh ./NVIDIA-Linux-x86-180.44-pkg1.run -n -s --x-prefix=/usr/lib/xorg --kernel-source-parth=/usr/src/linux-headers-`uname -r`
sudo /etc/init.d/gdm start
``` 

Hope it works, 

Jake

---

