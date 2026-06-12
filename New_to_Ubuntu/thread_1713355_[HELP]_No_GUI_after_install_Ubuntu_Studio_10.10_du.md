---
title: "[HELP] No GUI after install Ubuntu Studio 10.10 dual boot Windows 7"
date: 2011-03-24
forum: New to Ubuntu
---

### Post by jazzroom on 2011-03-24
Hi, to all Ubuntu gurus :) 

i am an absolute beginner so please bare with me :

Trying to install Ubuntu Studio 10.10 on partition on Windows 7 box ( Intel Pentium 3.4Khz 1Gb RAM / Realtek HD Audio/ Radeon X300/X550/X1050 series Video Card / ASUS P5GD1 Motherboard) ) my interes is the Audio packages of Ubuntu Studio.

All installed well exept the Audio Packages failed to install from the ISO of Ubuntu Studio 10.10

After reboot i could choose Ubuntu in the Grub bootloader but Ubuntu doesn't load GUI
at all instead just the terminal login window.....

i am new to Linux and dont know any commands by heart...


What am i doing wrong and How to make Ubuntu Studio GUI to work? :confused:



thanks in advance for your help

---

### Post by Zzl1xndd on 2011-03-24
If you had some packages fail on install it might have just been a bad install (or a problem with the Medium you used to install).

Once you get to the terminal login enter your information then try 

```
startx
```

and let us know what happens?

---

### Post by jazzroom on 2011-03-24
> **tweakedenigma said:**
> If you had some packages fail on install it might have just been a bad install (or a problem with the Medium you used to install).

Once you get to the terminal login enter your information then try 

```
startx
```

and let us know what happens?

i tried to type in 
starx   
get no command found

than i've tried to type : start x

get: Unable to connect to system bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory



have no idea what i do wrong..... :( ?


Why is it so hard to properly install Ubuntu 10.10 on Windows 7 mashine .... ?

i am strugling for two days with failing attempts

even tried to install Ubuntu from a CD using Wubi but it fails to complete installation after rebooting.... :(

---

### Post by Zzl1xndd on 2011-03-24
If you got no command found it sounds like the xserver wasn't installed when setting up this is required for the GUI. 

When you tried to install with Wubi were you using the same disk? If so it may just be a bad disk. You might wanna try re-burning it at a slower speed or you could try

```
sudo apt-get install ubuntustudio-desktop
```

---

