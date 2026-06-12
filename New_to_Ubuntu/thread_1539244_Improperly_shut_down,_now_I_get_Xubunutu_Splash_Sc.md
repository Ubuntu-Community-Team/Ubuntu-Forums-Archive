---
title: "Improperly shut down, now I get Xubunutu Splash Screen, cammand prompt no GUI"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by USFMD82 on 2010-07-26
I tried Ubuntu in the past and my biggest issue with it was it was a pain in the butt when it is improperly shut down to get it back to working, however i was extremely please with how reliable it had in that department, it would still load up perfectly.. well until last night.
[B]
What happened before the issue[/B]
So here is the last thing I remember. I was trying to get MP3's to play on exaile, so I DL'ed G streamer ugly package (in synaptic), restarted and the player was working with MP3's. later on the computer froze up and wouldn't let me load the shutdown screen. so I just held my power button down to shut off the computer. I try to load it up this morning and it shows the splash screen wit the mouse and then rather then the GUI log in it gives me the command prompt and requests a log in. I log in and have tried a few things.

**Things I have tried**
Restart and boot windows XP and do a full shutdown/restart and choose Xubuntu on the restart - for some reason this has worked rather well in the past for me.

Run checkdisk on the drive inside windows, restart it didnt return any issues and it didnt work

> From the prompt type
ls /etc/init.d
and look for the gdm entry - if you can't find it type
sudo apt-get install gdm.
if it is there then you may need to reconfigure your video driver - type
sudo dpkg-reconfigure xserver-xorg
then choose defaults except for the video driver - choose vesa for safety first - it's a failsafe driver
then type
startx - let us know how it goes pls 

No luck with this
got an error similar to this (not exact wording) " error while loading shared libraries: libatk1.0:""

> sudo apt-get install Xubuntu-desktop
startxfce4

after the install desktop line,it goes and acts like its installing it and what not but then when I try the "Startxfce4" it runs a bunch of commands and the last two lines are
" error while loading shared libraries: libatk1.0.so.0: cannot open shared object file: Input/output error agent pid 15252 killed" " waiting for X server to shut down ddxSigGiveUp: closing log

> sudo service gdm start

The screen just flickers and then returns back to command prompt with a blank lien for me to do another command

Thanks in advance

---

### Post by USFMD82 on 2010-07-26
Update, the Check disk did not work it found no errors, I restarted and same thing, back to command prompt.

---

### Post by USFMD82 on 2010-07-26
> sudo dpkg-reconfigure xserver-xorg
select vesa driver
leave the other options as they are
run

sudo /etc/init.d/gdm restart

When I type "sudo dpkg-reconfigure xserver-xorg" and press enter it just goes to another command line but blank like its waiting for the next command

> sudo /etc/init.d/gdm

I get a 

"Warning Failed to acquire org.gnome.Displaymanager: Connection ":1.37" is not allowed to own the service "org.gnome.Displaymanager" due to security policies in the configuration file
Could not acquire name, bailing out

---

### Post by USFMD82 on 2010-07-26
> sudo service gdm start

The screen just flickers and then returns back to command prompt with a blank lien for me to do another command

---

### Post by USFMD82 on 2010-07-26
I have read a few things that mention that it could be my video card or it could be related to having to many sessions. After I select Xubuntu on the dual boot screen I get a menu with 7 different selections. 

Ubuntu, Linux 2.6.32-24 -Generic
Ubuntu, Linux 2.6.32-24 (recovery mode)
2 more instance of the -Generic / Recovery Mode
Windows XP

Anyone know if this has anything to do with my issues?

P.S. If i need to update anything, I am unable to access the web since I cant turn on my wifi,please let me know if the net is needed when doing whatever is suggested.

---

### Post by USFMD82 on 2010-07-26
Is there anyone that has any thoughts on this issue? Ive tried many different things I have seen suggested around here, is there any other information I can provide?

---

### Post by 4Orbs on 2010-07-27
Have you tried to boot from one of the older kernels in your Grub menu? Use the arrow down key to highlight the previous kernel (maybe 2.6.32-22 -Generic), hit enter and see if it will boot into the login screen.

---

### Post by USFMD82 on 2010-07-27
Thank you for helping!

I have tried that and the same issue appears it loads up to the command prompt.

---

### Post by USFMD82 on 2010-07-27
So i plugged it into a hard network connection and ran the commands again.
```
sudo apt-get install Xubuntu-desktop
startxfce4
```

I got a bunch of lines but it gave me these errors

> <stdin>:1:3: error: invalid preprocessing directive #Those
<stdin>:2:3: error: invalid preprocessing directive #or
<stdin>:3:3: error: invalid preprocessing directive #Xft
<stdin>:4:3: error: invalid preprocessing directive #Xft

anybody got any ideas?

---

### Post by linux18 on 2010-07-27
```

-choose recovery mode at grub
-drop to a root prompt
-type " telinit 3 " and login
-then type " xinit "
-when xinit starts type: " metacity & " - for ubuntu OR " compiz & " - if you have it OR flux/openbox & - if you have it OR " fvwm " & - for xubuntu
-then type " gnome-panel & " -for ubuntu OR " xfce4-panel & " -for xubuntu
-lastly type " nm-applet & " -for networking

```
I saved this code to a text file because it's so helpful for any boot failing problem.

---

### Post by USFMD82 on 2010-07-27
Thank you, I was getting somewhere, it all was working up to the point where I was supposed to type xfce4-panel

I typed in fvwm (I had to d/l the package first) then it runs abunch of lines and then I got a bunch of "couldnt load image from menu.[www.xpm](www.xpm) and a couple of other www." then it says a few more lines of code  Fvwm - themes-root not found and missing font charsets

Then it just hangs there it doesn't give me a command line to type xfce4-panel in.

---

### Post by linux18 on 2010-07-27
fvwm might require too many dependencies for this kind of setup, try fluxbox or openbox in the meantime and I'll see if I can isolate the right way to start fvwm.

p.s. if you choose openbox, type " xfdesktop & xfce4-panel & " after " openbox & " to get something very very close to xubuntu, until I figure out xfwm.

---

### Post by ST3ALTHPSYCH0 on 2010-07-27
While I can't help you with this issue, I can give you the proper shutdown command for frozen Linux.

Hold ALT+PRNT SCRN+ (type these in order)
for shutdown: R-E-I-S-U-O
for reboot: R-E-I-S-U-B

---

### Post by 4Orbs on 2010-07-27
Some of the commands you're using are not even addressing the problem, and they aren't going to solve it. There is no need to download and install a different window manager (openbox, fvwm, etc.) because that has nothing to do with the initial cause of the problem. Be cautious about using a random bunch of commands for troubleshooting.

When you first installed xubuntu: Did you use the wubi installer (from inside Windows), or did you create a "real" dual-boot by partitioning the hard drive and installing it next to Windows?

What version of Xubuntu are you using? (I'm assuming 10.04).

Did you install from a live cd or from a usb stick?

What graphics card is inside your computer, ATI or Nvidia?

Did you activate the recommended proprietary driver for your graphics card by going to System>> Hardware Drivers in the main menu?

---

### Post by linux18 on 2010-07-27
> **4Orbs said:**
> Some of the commands you're using are not even addressing the problem, and they aren't going to solve it. There is no need to download and install a different window manager (openbox, fvwm, etc.) because that has nothing to do with the initial cause of the problem. Be cautious about using a random bunch of commands for troubleshooting.

When you first installed xubuntu: Did you use the wubi installer (from inside Windows), or did you create a "real" dual-boot by partitioning the hard drive and installing it next to Windows?

What version of Xubuntu are you using? (I'm assuming 10.04).

Did you install from a live cd or from a usb stick?

What graphics card is inside your computer, ATI or Nvidia?

Did you activate the recommended proprietary driver for your graphics card by going to System>> Hardware Drivers in the main menu?
actually the commands can help ( a lot ) if your computer isn't getting to the desktop then something is broken along the way, by using every command to bring up the desktop you can reveal which part of the startup is broken, then reinstall and restart. Fluxbox/openbox should be on every ubuntu comp anyway because a backup WM means you don't have to use another computer to ask for help when xfce/gnome/kde breaks.


EDIT:  [USFMD82]("http://ubuntuforums.org/member.php?u=401216") the command is " xfwm4 & " I didn't post the "4" try it again and it should work.

---

### Post by 4Orbs on 2010-07-27
The OP isn't even getting to the login screen (gui), so the window manager doesn't have any influence on the problem. On the other hand, I agree that Openbox is fabulous and everyone should at least give it a try... after they have their main Desktop Environment working properly.

---

### Post by linux18 on 2010-07-27
> **4Orbs said:**
> The OP isn't even getting to the login screen (gui), so the window manager doesn't have any influence on the problem. On the other hand, I agree that Openbox is fabulous and everyone should at least give it a try... after they have their main Desktop Environment working properly.
most of the time, my script works when ( like the OP ) your stuck at a blank or splash screen because thats when the DE & WM are loading. the problem it that plymouth and the splash screen prevent terminal output like " error: xfwm4 failed to load" so the comp stays at the same screen as it silently crashed in the background. running my commands manually load the DE and WM so that a reboot can bring the computer back. If he can get to the terminal, then the only thing broken is the DE.

---

### Post by USFMD82 on 2010-07-27
Im using 10.04 installed throuhg Wubi, I didnt have any issues with the graphics, I believe it is ATI. but it was workign fine until I installed Gstreamer ugly, and it restarted just fine butthen stopped.

The propreitary drivers I activated to get my wifi to work.

I tried ```
$xfwm4 &
``` ```
$ xfwm4
```

I got errors on both, I got the "error loading shared libraries, libatk-1.0.so.0 cannot open shared object file:no such file or directory

thank you everyeone for the suggestions.

Ill give the openbox suggestion a try tomorrow no wired internet connection

---

### Post by USFMD82 on 2010-07-28
So I was able to hookup and install Open box 
```
$ sudo apt-get install openbox
```

it ran through all the lines said it was dl it and what not

then i did ```
$ openbox
```

I got the error Openbox-message unable to find a valid menu file "var/lib/openbox/debian-menu.xml"


Gosh I must of really screwed this thing up huh?

---

### Post by linux18 on 2010-07-28
```
 openbox --replace & 
```

---

### Post by USFMD82 on 2010-07-28
Thanks for continuing to help!

I got the same error: Openbox-message unable to find a valid menu file "var/lib/openbox/debian-menu.xml"

---

### Post by USFMD82 on 2010-07-28
does it have to do with this libatk that keeps popping up?

---

### Post by USFMD82 on 2010-07-29
Any other ideas? would it be easier if I just wiped it and started again? I am interested in learning what went wrong so that I can fix it in the future, but it appears it is quite a difficult fix. Let me know what you think, I prefer to work at it and fix it but if I am taking to much of every bodies time I dont mind just reinstalling it.

---

### Post by linux18 on 2010-07-29
```
 sudo apt-get install obmenu 
```

---

