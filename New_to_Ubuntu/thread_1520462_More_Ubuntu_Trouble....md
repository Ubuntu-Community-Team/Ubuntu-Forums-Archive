---
title: "More Ubuntu Trouble..."
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Rybandt on 2010-06-29
So I restarted my computer after installing a nvidia recommended driver. It won't boot. It just flashes my name and "login:" I tried typing my stuff but it doesnt work. So I tried holding shift with the grub screen and tried to repair ( ithink thats how it was worded) and now Im just stuck with the ubuntu symbol. :confused: Very frusturated but I love ubuntu and wish I could figure this out... Should I just frensh install and try again?
 
 
 

Edit: The splash symbol is sort of overlapping itself too. Like on hidden behind it

---

### Post by ajgreeny on 2010-06-29
How did you install the driver?  Did you use **System->Administration->Hardware Drivers**?

Also what do you mean by "I tried typing my stuff but it doesn't work"?  If your username appeared as you typed, but the password did not, that is as it should be; just type password and hit enter; you should login to a command line.  You can then try ```
startx
```but it may not work as the system may think x is already running.

See if you have an xorg.conf file by typing in the command line ```
cat /etc/X11/xorg.conf
``` and if there is a file rename it with ```
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.confbak
```Now try a reboot with ```
sudo shutdown -r now
``` and with luck you will at least get a GUI, even if the performance is not too high.  Come back then for more help, or try installing the nvidia driver again the proper way with System->Administration->Hardware Drivers.

---

### Post by DJonsson2008 on 2010-06-29
What version of Ubuntu are you running?

Earlier versions were infamous for having Nvidia and other proprietary driver problems, only with 9.10 was I able to get Nvidia drivers to work right.

Otherwise think you can roll back via grub to a rescue level/ safe mode type login and get at your xorg.conf file with a text editor and revert to default drivers.

The file you need to get at is,

/etc/X11/xorg.conf

Sometimes using ls you will find that previous versions of 
xorg.conf exist, if so open them up and see if they are running

Running 
sudo dpkg-reconfigure -phigh xserver-xorg is also supposed
to revert to xorg.conf to generic setup, but I'd double 
check that before running it.

Search these forums for more detailed advise.

---

