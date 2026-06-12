---
title: "Nvidia driver issues"
date: 2010-02-23
forum: New to Ubuntu
---

### Post by spookfish on 2010-02-23
hi, 
i'm trying to install my Nvidia GeForce FX5900XT graphics card into Ubuntu 9.10, but each time i reboot after the install i get the flash of the basic terminal login and then nothing for between 5 and 10 seconds, then the flash again, this just goes on and on

i've tried both the drivers listed in "Hardware Drivers" (not at the same time) but the same thing happens with each

the rest of the computer is:

Abit AV8 3rd eye Motherboard
AMD Athlon 64 3500+
2Gb memory

any help i could get would be great

---

### Post by cariboo on 2010-02-24
Boot into recovery mode, and once at the menu, select drop to root prompt. Once at the prompt type:

```
nvidia-xconfig
```

The above command will create a new /etc/X11/xorg.conf, and backup the old one. Once the new file has been created, reboot by typing:

```
reboot
```

at the prompt.

---

### Post by spookfish on 2010-02-25
i've tried, but i can't even get into recovery mode,  is there any way i can switch across to the hard disc file system from the terminal window on the live cd?

---

### Post by 23dornot23d on 2010-02-26
Try booting from the hard drive to where it flashes and press Ctrl + Alt + F1

This should open a console screen where you can do the command .... 
nvidia-xconfig
then reboot it .........

---

### Post by spookfish on 2010-02-26
ok, i finally managed to Ctrl + Alt + F1 into recovery mode (doh!! thanks 23dornot23d)
but "nvidia-xconfig" doesn't seem to help the situation, although in my grub list i appear to have 2 versions of ubuntu (4 if you count the recovery modes), one's called "Ubuntu, Linux 2.6.31-19-generic" and the other's the same but with 14 instead of the 19

i have next to nothing on the computer, so i'm thinking about cheating an reinstalling ubuntu, but that won't help with the graphics card driver situation, it's been suggested to me in a pm that i download and install the nvidia drivers myself instead of letting ubuntu do it

sorry for making a story of all this, i'm sure you'd prefer i just got to the point ;)

---

### Post by 23dornot23d on 2010-02-27
I would like to see the xorg.conf file if its possible now .....

/etc/X11/xorg.conf 


In the console type ........... this command just displays the file  ..........



less /etc/X11/xorg.conf



return will take you through it a line at a time

q will get you out ( to quit )



This is where the information for the Nvidia card should reside to get it working ....

Then we can see what is happening ...... its always the first place I look when the

screen does not work properly .....

If you can get a screenshot ( even a few digital photos ) ..... or copy the file and show it here ..... it may help

you said its a Nvidia GeForce FX5900XT graphics card into Ubuntu 9.10

( but what monitor do you use and what size display are you trying to set up ?  )

and have you had it running successfully before .... 

as usually in the etc/X11/

directory there may be a backup file of your original settings - these will be saved if you did a upgrade .....

ok hope this helps ........... a little ...... 

as it may just be a case of copying the right file back again ...... if it worked properly before .......

---

### Post by spookfish on 2010-02-27
hmmm, there doesn't appear to be a x11 directory in the etc directory, and, since i've reinstalled ubuntu several times because of this same problem with the graphics drivers, i'm guessing it's never been writing that directory, it would be nice to know why it keeps failing to complete the install

the monitor's just a basic cheap tft, max res 1280 x 1024, no obvious name, but it's been working fine with so far

---

### Post by 23dornot23d on 2010-02-28
Its a CAPITAL .....  X in ......... X11

You should have this directory ...... as it holds all the files for X windows to work ... at all ....

the xorg.conf might be empty though ...... have a quick look again ...... please ....

as I would expect it to be there ......

here is a link that may be useful too .......



$ **cvt 1280 1024** ( is one line you need to change in the option below .......  for your monitor .....  hope it helps )


[COLOR=Lime][http://ubuntuforums.org/showthread.php?t=1346125](http://ubuntuforums.org/showthread.php?t=1346125)[/COLOR]

the resolution can be set using the method above to check ......

but if it goes into the xorg.conf file it will be there every time you start up ...

which it also shows you how to do this - in the above link  ..........

---

