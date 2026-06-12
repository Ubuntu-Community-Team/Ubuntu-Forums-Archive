---
title: "Default Brightness is almost dark"
date: 2011-04-07
forum: New to Ubuntu
---

### Post by janaro on 2011-04-07
I'm trying to alter the default darkness on my ubuntu.

I think it's an issue with the ATI drivers or maybe the lack of drivers...

But all seems to work nicely once I put the brightness up thanks to the keyboard shortcuts. My issue is that I don't want to do this each time a start the computer.

I have tried:

[LIST]
[*]apps > gnome-power-manager > backlight =failed due to read only function
[*]System -> Preferences -> Power Management =the same after restarting
[*]cat /proc/acpi/video/VGA/LCD/brightness =unable to find file...
[*]gksudo gedit /etc/X11/xorg.conf =file is empty
[*]xgamma -gamma 0.8 =the same after restarting
[*]sudo gedit /etc/*default*/*gru added the *GRUB_CMDLINE_LINUX="quiet splash acpi_backlight=vendor"   =restarted to see the same darkness
[/LIST]
Can anyone help me out?

Thanks in advance!!

---

### Post by sleepingdragon on 2011-04-07
There's a handy little install called *xbacklight* - set this up as an autostart program (*Menu - Preferences - Startup Applications) *and go with something like:

[I]xbacklight -set 50

[/I]for the autostart command. The above should give you brightness at 50%, alter the value according to taste. You should find it in Synaptic.

Since you have control over your brightness, I'm going to assume that xbacklight will work.... hopefully... maybe... possibly... won't hurt to try it...

Hope it helps!

---

### Post by janaro on 2011-04-08
Thanks for the quick reply, I such a newbie that I wasn't able to add a simple script into the start-up.

Anyway I found a way round (I believe): I went into the terminal with the following command:
**sudo nano /etc/init.d/local.autostart**

I added the line like you kindly pointed out and restarted, it was better but I still have to **Fn+ Up** 8 or 9 times.

I thought I get clever and add **xgamma -gamma 0.9** and up to **xbacklit -set 160.**

But it didn't make much of a difference :(

Looks like I'm going to have to go back to windows](*,)

---

### Post by sleepingdragon on 2011-04-08
Whoa. That sounds like a load of changes you don't need to do. 

Go back to the Startup Applications menu and click [I]Add.

[/I]Next, fill in the three blanks:

Name: [I]xbacklight
[/I]Command: [I]xbacklight -set 50
[/I]Comment: [I](Not needed, but you can fill in anything you like).

[/I]Click on *Add* to create the new autostart and click on *Close* to finish the Startup dialog. Now log out and back in again, and xbacklight should now do it's thing. 

If it's still too dark, go back to the Startup Applications menu and scroll down the list until you find the xbacklight entry you've just created. Double-click on it and change the value in the command from 50 to 70 (or some other higher value). Click on *Save, *then *Close.* Log out/in again to check the changes.

***xgamma -gamma 0.9*** will make your screen **darker!** Remove this command wherever you put it in.

**xbacklit **doesn't exist; if you mean **xbacklight**, then any value above 100 is meaningless. It's set as a percentage and you cannot go higher than 100%.

---

### Post by janaro on 2011-04-11
Hi,
Thanks for your well explained post.

Unfortunately I have had no success, I changed the settings to 50, 30, 70 and 100 and there is no change. I also erased the **gamma **and **xbacklight**

I'm still able to put it right on the keyboard (**Fn+up** x8) and then I'm able to see the screen.

Could it be something to do with the GPU drivers?

---

### Post by sleepingdragon on 2011-04-11
Hi.

That's a little odd - every laptop/netbook I've come across responds to xbacklight if the Fn keys are working.

Bring up a terminal and use the xbacklight command manually to see if makes any changes:

**xbacklight -set 30 **

should darken the screen. If there's an output from the command, could you post it here please?

Thanks.

---

### Post by janaro on 2011-04-12
Hi,
I tried doing that in the terminal and it asked me to install.

After installing, I tried **xbacklight -set 30** and it said:

**No outputs have backlight property.**

According to this link, it's a driver problem:
[http://old.nabble.com/xbacklight:-No-outputs-have-backlight-property-td15062174.html](http://old.nabble.com/xbacklight:-No-outputs-have-backlight-property-td15062174.html)

The last time I tried to install a GPU driver in ubuntu, I got a black screen...

Thanks for your time and help!

---

### Post by sleepingdragon on 2011-04-12
Well, it was worth a shot. 

Just realised it was an ATi, I've never had much luck with them myself - kept going back to nVidia.

Sorry I can't help you further.

---

### Post by janaro on 2011-04-12
Thanks for your help, I wish it wasn't a portable...I would go out and get an nvidia :D

---

### Post by Sidewinder1 on 2011-04-12
janaro, 
please, please do not consider going back to "Them"!
{Sidewinder bows his head to prevent the tears from shorting-out his keyboard}
I am reasonably certain that with the help of the good folks on this board that you will eventually solve your problem. 
Sometimes it only requires a little patience and perseverance to accomplish what, initially seemed impossible.
Take it from someone whose "been there, done that".

Side

---

