---
title: "Loading Ubuntu error"
date: 2010-01-27
forum: New to Ubuntu
---

### Post by dimzamatic on 2010-01-27
Okay, So. Lets Start from the beginning. 

I Grabbed Ubuntu 9.10 and installed it without error using the entire disk. I didn't encrypt the home directory or do the install with the extra encryption and LVM. I am running a Gateway FX 7805u notebook, 4g ddr3, habatchi 280g hard, dual core intel, Nvidia 9800m gts. The problem is that once it is installed and at the end of the installation it asks to remove the disk so the the system can restart and you can go to the desktop for the first time. I remove the disk, let it restart, the Grub loads, the screen (RGB external monitor plugged in to the side of the laptop because the laptops screen is broken and removed) flashes to a darker black, then flashes back to a brighter gray and has the Ubuntu symbol on it as if the os is just about ready to load to the desktop, then the screen flashes to a darker black again and thats it. Im curious if the problem is that im running a external monitor and the os IS loading completely but it not showing up on the plugged in monitor and trying to show up instead on the the actual laptop screen that is non-existent. 

I have tried downloading different ubunto iso's and installing off them, have tried different tweaks such as ext2, ext4, ntfs. Nothing seems to fix this problem. Is there something i am overlooking? I have tried Gparted and setting up the partions myself prior to install (primary ext2 with / runline, and swap) but that failed also. I was running Winows 7 rc client prior to switching over to ubuntu. I need my notebook up and running to file mine and my gfs taxes. Help would be most appreciated. 

Ps. If i try to run the live cd the same problem with the load hanging after the ubuntu system happens and also with the graphical installation option. I can only open the Text installation.

---

### Post by cariboo on 2010-01-27
Your system is loading properly, you have a video problem. Start in recovery mode, and once at the menu choose drop to root prompt, once at the prompt type:

```
nvidia-xconfig
```

the above command creates a new /etc/X11/xorg.conf file. Once the program has finished running type: exit, then select resume from the menu. This should get you to the desktop. 

You didn't really specify what type of monitor you are using, if you are using a crt, you may have to adjust the horizontal sync and vertical refresh rates. You can get these specifications from your monitor manufacturer's web site.

While still at the prompt open the /etc/X11/xorg.conf file by typing:

```
nano /etc/X11/xorg.conf
```

and change the Horizontal sync and vertical refresh rates to match the ones for your monitor.

If you've never used nano before, you'll see in the menu below the main editing window commands that look like this:

```
^O writeout
```

in this case ^=Ctrl-o to save.

---

### Post by dimzamatic on 2010-01-28
Thank you. I will be going home in a little bit and will attempt this fix. Its is a non CRT monitor. I will post the results and let you know if we have achieved lift off or just another challenger incident.

---

### Post by dimzamatic on 2010-01-28
No go. It reads 
 
```
The program 'nvidia-xconfig' can be found in the following packages:
   * nvidia-glx-173
   * nvidia-glx-185
   * nvidia-glx-96
Try: apt-get install <selected package>
nvidia-xconfig: command not found
```

---

### Post by dimzamatic on 2010-01-28
I have tried a few other options and still no luck. Is there any other input from me that you guys would need to find a fix?

---

