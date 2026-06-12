---
title: "Compiz issues"
date: 2011-06-29
forum: New to Ubuntu
---

### Post by Manhippo on 2011-06-29
Hi there folks,

So,  I used Unity for a month or so, then decided it was just too clunky and limiting, so I have switched back to the classic gnome version with my old friend AWN taking on dock duties.

However, Awn has been displaying wierdly since i tweaked something in compiz (i turned on the desktop cube and it did all manner or troubling things to my desktop)

I have since reinstalled Ubuntu, but AWN still misbehaves, just showing a white square behind the icons.

So I decide to run compiz --replace in the terminal, which does the trick re awn, but seems to freeze at run_command_terminal_key. If I try to shut down the terminal at this point, ubuntu warns me that it is still doing stuff, but it isn't. If I reboot, Awn has the same problem unless I run the replace command in the terminal again.

Any thoughts?

cheers,

j

---

### Post by falko on 2011-06-29
Can you try
```
compiz --replace &> /dev/null
``` instead? This should send the job to the background.

---

### Post by ajgreeny on 2011-06-29
> So I decide to run *compiz --replace* in the terminalI think this is the possible problem.  Run that command in the Alt+F2 run command box and you will not be left with a terminal running in the background.

If the overall problem is more to do with natty, then I'm afraid I can not help any further as I do not run it, except for a test partition I boot to occasionally, and even then my machine is too old to run unity.  I do seem to remember reading that the version of compiz in natty is causing problems, or regressions of some of the plugins, or something similar, and some users are downgrading to the version of compiz from maverick.
[https://launchpad.net/~guido-iodice/+archive/compiz-0.8.6-natty](https://launchpad.net/~guido-iodice/+archive/compiz-0.8.6-natty)

---

### Post by Manhippo on 2011-06-29
Thanks for that, ajgreeny. However, isn't the alt f2 command line just a dressed up version of the console that doesn't show its working? In other words, if I run it there won't the same thing happen, but invisibly?

I'll give it a try anyway. At the moment, i need to do this incomplete compiz install everytime i reboot. I suppose if canonical are committed to not supporting gnome in future releases, I might need to go looking for a new distro to call home.

---

### Post by Manhippo on 2011-06-29
thanks for the reply.

The problem is that the compiz --replace command is not completing, and so the terminal is hanging. The solution you suggest hides the working of the operation, but the result is the same. The command prompt never reappears, and on reboot the operation has to be done again to make AWN work properly...

Anythoughts as to why the command process wouldn't be completing. I have, obviously, tried running it with root priveleges, but that doesn't seem to make any difference

---

### Post by beew on 2011-06-29
Well if you want to always use Compiz as your desktop manager then you shouldn't be running compiz --replace at all. This means you start up in some other desktop manager and then switch to Compiz, but why start with other if you are not going to use it anyway?

This is the correct way of doing it:
Create a file call .gnomerc with gedit in your home directory with this command on it:
```
export WINDOW_MANAGER=/usr/bin/compiz
```EDITED: Also there appears to be some bugs in Compiz 0.9 for the classic desktop so if you are not using Unity at all you can downgrade Compiz to 0.86 by adding the Compiz 0.86 ppa and "upgrade" Compiz (the package is relabelled so that it appears to be a higher version than 0.9 in Natty but it is actually an older version,--0.86)

```
sudo add-apt-repository ppa:guido-iodice/compiz-0.8.6-natty
``` But be warned: **This will remove Unity so only do it if you are sure that you don't want Unity at all.**

---

### Post by Manhippo on 2011-06-29
awesome. Thankyou beew. That first tip did the trick, and cleared up my understanding of how the window manager business works. I hadn't realised that what I was doing was loading compiz afresh each time.

Thanks for the second tip as well. I seem to have everything working pretty stably now, so I will just leave it as it is, I think. Don't imagine I'll go back to unity, buy hey. I'll just make sure not to try and activate the desktop cube again...

---

### Post by beew on 2011-06-29
> **Manhippo said:**
> awesome. Thankyou beew. That first tip did the trick, and cleared up my understanding of how the window manager business works. I hadn't realised that what I was doing was loading compiz afresh each time.

Thanks for the second tip as well. I seem to have everything working pretty stably now, so I will just leave it as it is, I think. Don't imagine I'll go back to unity, buy hey. I'll just make sure not to try and activate the desktop cube again...

Actually you should be able to activate the desktop cube in the classic desktop with no issue. I have tried that briefly and there was no complication. It is in Unity that it is a bit tricky because disabling desktop wall would disable Unity and crashes Compiz so you have to reactivate all the plugins. But I am using Unity (with the cube!), I have never logged in to the classic desktop since I first installed.

---

### Post by Manhippo on 2011-07-07
Ok, i'd love to know how you did it. When i turned on the cube it disabled a whole bunch of other stuff and turned off most of my desktop. I'm, still unpicking the mess. it also seems to have bled elements of my kubuntu install into my gnome desktop (for example, the fold down menu on my calendar on the top panel now displays Kde style even under gnome). To be honest, I', fairly new to this game, so it's left me all a bit flumoxed. I'm not going to fiddle any more as I need to just get on with using the computer, not troubleshooting the os... Thanks for all your help though!

---

### Post by beew on 2011-07-07
[http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/](http://reformedmusings.wordpress.com/2011/05/05/howto-get-the-compiz-desktop-cube-in-ubuntu-11-04-natty-and-unity/)

---

