---
title: "screen"
date: 2009-09-19
forum: New to Ubuntu
---

### Post by tim fitzgerald on 2009-09-19
I bought a new laptop for my wife, after hers went crazy. So I took hers and installed ubunto 9.04 as the only operating system to try out 9.04. When it started up having never seen ubunto before I started looking for things and realized a lot of necessary things extended beyond the screen and I had no access to the wireless icon and no task bar at all on the bottom. I thought maybe adjusting the screen resolution would help, it did unfortunately now it's worse with things so big I cant even go back to change the resolution because it's even farther off the screen. I thought everything would work right out of the box. Please help I would really like to give ubunto a fare trial.      Thanks

---

### Post by mapes12 on 2009-09-19
Hi

Can you go System>Administration>Hardware Drivers and see if there are any unactivated drivers listed? You will probably need an ethernet cable connected for the drivers to download.

If you can connect with an ethernet cable then post back and we will see what we can do to fix the wifi etc. issues.

For the task bar right click it then select Properties and change the orientation to Bottom.

Best.

Mark

---

### Post by tim fitzgerald on 2009-09-19
Thanks for your prompt answer, I cant do anything because the screen resolution is so low that only one little thing takes up the whole screen and I cant click on it. Should I have bought the os cd instead of down loading it. Nothing seemed to work from the get-go. I'm not a geek but I am good with computers and have changed hardware, installed software' reinstalled os's so I'm not no-tech. I cant even begin to use the beginners guide I downloaded because nothing works. 
Thanks

---

### Post by mapes12 on 2009-09-19
Before you changed the screen res could you get to the task bar with the menu items? If you can then I would suggest running the install again then having a look for those drivers I posted about before.

---

### Post by blackened on 2009-09-19
Hold alt and press F2. This will bring up the equivalent of the Window's Run Dialog. In the subsequent box type "gnome-display-properties" and press enter. From there you should be able to adjust your resolution to something more appropriate to your monitor. If part of the window is off-screen, then you can hold alt while dragging to move it. Good luck.

---

### Post by nothingspecial on 2009-09-19
As a last resort, this will get you back to where you started from.
```

sudo dpkg-reconfigure -phigh xserver-xorg 
```

Log in to failsafe terminal or whatever it`s called to run it.

---

### Post by tim fitzgerald on 2009-09-19
:confused:None of those things worked. Now I have a great big box that says unlock keyring unfortunately only half of the box is showing so I cant type anything into it and I cant drag the box up or down.

---

### Post by nothingspecial on 2009-09-19
That command should have worked. However a couple of suggestions.

Login to your account in the failsafe terminal or recovery mode or whatever it`s called and type this

```
gconftool-2 --set /apps/compiz/plugins/move/allscreens/options/constrain_y --type bool 0
```

Now when you log back in to the gui, if you press Alt while clicked on a window you will be able to drag it off the side, bottom and top of the screen. You should be able to get it to a usable position.

I don`t know if this will help but pressing Ctrl and - (the minus sign) zooms out the current window. Try that.

---

### Post by tim fitzgerald on 2009-09-19
We'll now I have ten or so boxes on the screen that I cant x out nothing works

---

### Post by nothingspecial on 2009-09-19
Alt + F4 will close a window

---

### Post by tim fitzgerald on 2009-09-19
Thanks for your help everyone but nothing seems to do anything right perhaps my download of ubuntu was bad , but I checked it. Everything is really messed up., and I'm stuck I cant go forward and cant go back.  Any ideas would be a great help?

---

### Post by blackened on 2009-09-19
You should not expect this to get resolved if you won't give us feedback.

We need to know exactly what you've tried and exactly what the result was.

Did you try nothingspecial's suggestion of booting into recovery mode and removing the screen's Y constraint then booting back into Gnome and alt+dragging the window? If so, what was the result? 

"It didn't work." is not an answer. Instead you should try "I booted into recovery mode and entered what you suggested, but when I logged back into Gnome I was still unable to move the window around using alt+drag." if that was your experience.

Help us help you.

---

### Post by tim fitzgerald on 2009-09-19
I understand you need feedback to help and im sorry that it sounds like I'm not giving it however I have no access to any thing the keys do nothing not alt., ctrl., I cant even shut down the computer except by holding down the turn on button. It's not lack of respect it's lack of anything that works. Thanks

---

### Post by nothingspecial on 2009-09-19
Do you have another ubuntu box?

---

### Post by blackened on 2009-09-19
> **tim fitzgerald said:**
> ...I have no access to any thing the keys do nothing not alt., ctrl., I cant even shut down the computer except by holding down the turn on button...

That's once the OS boots, but what about recovery mode, are you able to boot into that?

---

### Post by ChrT on 2009-09-19
> **mapes12 said:**
> Hi

Can you go System>Administration>Hardware Drivers and see if there are any unactivated drivers listed? You will probably need an ethernet cable connected for the drivers to download.

Just a fair warning, this application includes PROPRIETARY DRIVERS that infringe on your software freedom and are just as likely to make your system crash entirely as they are to help you.

---

### Post by blackened on 2009-09-19
> **ChrT said:**
> Just a fair warning, this application includes PROPRIETARY DRIVERS that infringe on your software freedom... 

They are in fact proprietary and are ever the subject of ideological debate. 

> **ChrT said:**
> ...and are just as likely to make your system crash entirely as they are to help you.

A subjective statement at best. Your mileage will vary as much with the proprietary drivers as it will with the open source drivers for hugely different reasons.

---

