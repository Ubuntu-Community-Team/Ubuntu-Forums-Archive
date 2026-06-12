---
title: "How do I run a .run file?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by bwallum on 2009-04-27
Hi

Things like nVidia drivers come as a .run executable file. How do I run these files?

E.g. I would like to install a nVidia driver that I have downloaded as a file called> NVIDIA-Linux-x86_64-185.18.04-pkg2.runI am told to use the command 'sh', run as root and with the X server stopped.

Is this a good thing to do in Ubuntu? How do I 'debianise' the file to make it easily installed by Ubuntu?

---

### Post by ohzopants on 2009-04-27
sh is definitely the way to go to install this driver.

First you need to make the file executable:
```
chmod +x NVIDIA-Linux-x86_64-185.18.04-pkg2.run
```

Then press ctrl+alt+f1 to go to a terminal and kill gnome:
```
sudo killall gdm
```

Then run the installer (from the directory in which it is saved):
```
sudo ./NVIDIA-Linux-x86_64-185.18.04-pkg2.run
```

If you are installing your own nvidia drivers as opposed to the prebuilt ones in the repositories you will need to repeat these steps everytime you receive a kernel update.

---

### Post by SentientFluid on 2009-04-27
> **bwallum said:**
> Hi

Things like nVidia drivers come as a .run executable file. How do I run these files?

E.g. I would like to install a nVidia driver that I have downloaded as a file calledI am told to use the command 'sh', run as root and with the X server stopped.

Is this a good thing to do in Ubuntu? How do I 'debianise' the file to make it easily installed by Ubuntu?

Press Ctrl-Alt-F1 to bring up a console window. To stop X from running type ```
sudo /etc/init.d/gdm stop
```
Next enter ```
sudo sh *nameofyourfile.run*
```.

---

### Post by ohzopants on 2009-04-27
FYI - SentientFluid's way of killing X is probably preferable to the way I mentioned.

---

### Post by bwallum on 2009-04-28
Thanks ohzopants and SentientFluid, I have got the nVidia 185 driver running and all appears stable.

I have tried all your commands and also tried booting into recovery mode, which worked. For me the best route was:-

Download the .run file to Desktop. Right click on the file, go to the Permissions tag and check the box to run as executable.

Take note of the following instructions first because after the next step you will lose the gui.

Open a full screen consol (normal windowed terminal will NOT work) with ctrl-alt-F1

Stop the x server with ```
sudo /etc/init.d/gdm stop
```change directory to Desktop with```
cd Desktop
```then run the file with ```
sudo sh YOURFILENAME.run
```Follow the prompts when the file runs and give it time between each option, it can be slow and nothing appears to be happening at times. Allow the installer to re-write your xorg.conf file and compile an nVidia kernel interface. When the installer completes and you return to the prompt, type```
sudo reboot
```and let the system reload to Desktop.

That's it, you should have all details and control of the driver in System>Preferences>NVIDIA X server settings. Note that your driver will NOT show in System>Administration>Hardware Drivers

Thanks again!
Bob

---

### Post by SentientFluid on 2009-04-28
Glad to be of service and thanks for updating us on how it went!  You've most likely just helped someone else by posting that. :)

---

