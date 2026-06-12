---
title: "Shutdown issues and replacing the Kmenu icon"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Coolsaber57 on 2009-04-03
Hi guys, Kubuntu 8.10 and KDE 4.2

2 questions:

1. My shutdown does not seem to be working.  It just gets rid of my panels and sits there at a black screen. I can move the mouse around and even see my Cairo-dock if I mouse over that, but it gets stuck there. How do I fix this? Or even diagnose it?

2. I've been trying to change the kmenu icon but nothing works.  I've tried replacing the kde.png and kmenu.png in several /usr/share/icons/[different themes] folders, but it doesn't ever change.  I'm using the "Glassify" theme, but I don't see that listed in the /icons folder.  Is this even the right themes or should I be looking for the "icon theme." If this is the case, there are only 2 themes, oxygen and crystalxp(or something similar).  However, I replaced the .png in the oxygen folder already, but no dice. I'm stumped.  Has anyone done this? Can you shed any light on the subject?

Thanks!

---

### Post by Armor Nick on 2009-04-03
for question 1, try typing 'sudo halt' in a terminal and tell us what it says.

for question 2, it's probably best to wait for jaunty to be released. KDE 4.2 is much easier to configure.

---

### Post by Coolsaber57 on 2009-04-03
> **Armor Nick said:**
> for question 1, try typing 'sudo halt' in a terminal and tell us what it says.

for question 2, it's probably best to wait for jaunty to be released. KDE 4.2 is much easier to configure.

For sudo halt - what does this do? How is it different from shutting down via the menus?

I'm actually already using KDE 4.2, unless you mean it's easier to configure WITH Jaunty. Even with 4.2 I don't see an option for it, the only method I've seen is to replace the .png file, but replacing the correct one is where I'm having trouble.

---

### Post by anewguy on 2009-04-03
Could be wrong, but I think you'll find 2 things:

- shutdown halt doesn't power off the system

- you will get visible messages on your terminal window during the shutdown, which could point to a process that couldn't be killed by the shutdown command.


You could also try, but I don't if it will be any different:

sudo shutdown -r now

This tells the system to shutdown now, meaning kill all processes now regardless of their status, and the -r means to reboot.

Dave ;)

---

### Post by Coolsaber57 on 2009-04-03
> **anewguy said:**
> Could be wrong, but I think you'll find 2 things:

- shutdown halt doesn't power off the system

- you will get visible messages on your terminal window during the shutdown, which could point to a process that couldn't be killed by the shutdown command.


You could also try, but I don't if it will be any different:

sudo shutdown -r now

This tells the system to shutdown now, meaning kill all processes now regardless of their status, and the -r means to reboot.

Dave ;)

Thanks, I will give this a try tonight!

I get this feeling that it will be Cairo-dock that it can't kill :???:

---

### Post by Coolsaber57 on 2009-04-03
Ok, i've tried both the:

sudo halt 
and
sudo shutdown -r now

and ironically, the sudo halt shut it down fine, and the shutdown -r now did the same thing as hitting the shutdown button.

However, it shut down my Terminal, so any services that it couldn't shut down, I can't see it.

I'm kinda lost now, is there a "shutdown log" or something I can check to see where it got stuck?

---

### Post by anewguy on 2009-04-04
I'm not familiar with Kmenu - is that a KDE thing?

At any rate, I've been looking around the net and have a couple of things for you to try, but I have no idea if they will work:

1.  Before shutting down, exit what ever you are using for a network manager, then see if it will do it correctly.

2.  Find the PID for cairo-dock and use sudo kill -kill <PID> to kill it, then see if it will do it correctly.

I'll keep looking and let you know if I find something that is promising. 

Dave ;)

---

### Post by Coolsaber57 on 2009-04-04
> **anewguy said:**
> I'm not familiar with Kmenu - is that a KDE thing?

At any rate, I've been looking around the net and have a couple of things for you to try, but I have no idea if they will work:

1.  Before shutting down, exit what ever you are using for a network manager, then see if it will do it correctly.

2.  Find the PID for cairo-dock and use sudo kill -kill <PID> to kill it, then see if it will do it correctly.

I'll keep looking and let you know if I find something that is promising. 

Dave ;)


Well, we've found the problem and it's what I had suspected.  Shutdown isn't killing cairo-dock.  How do I fix that? Is it a line I have to add to the "shutdown program" or something? And if I do that, how do I get Cairo-dock to start when it boots up again?

---

### Post by Christmas on 2009-04-04
In order to change the KMenu, it's easy. The icons you want to replace are called *start-here-kde.png* and are located in:
```
/usr/share/icons/oxygen/128x128/places/start-here-kde.png
/usr/share/icons/oxygen/64x64/places/start-here-kde.png
/usr/share/icons/oxygen/48x48/places/start-here-kde.png
/usr/share/icons/oxygen/22x22/places/start-here-kde.png
/usr/share/icons/oxygen/16x16/places/start-here-kde.png
/usr/share/icons/oxygen/32x32/places/start-here-kde.png
```
Of course, replace *oxygen* with the name of your theme. Copy the necessary *.png files in those folders, go to System Settings, Appearance -> Icons, change the theme to something else, than change the theme back to Oxygen (or the theme for which you changed the start-here-kde.png icon). Hope this helps (it worked for me in KDE 4.2.2).

Regarding the shutdown: I can't remember when this *actually worked* on Kubuntu, but it must have been a long, long time ago ;) Just use the shell to reboot or shutdown it.

---

### Post by Coolsaber57 on 2009-04-04
> **Christmas said:**
> In order to change the KMenu, it's easy. The icons you want to replace are called *start-here-kde.png* and are located in:
```
/usr/share/icons/oxygen/128x128/places/start-here-kde.png
/usr/share/icons/oxygen/64x64/places/start-here-kde.png
/usr/share/icons/oxygen/48x48/places/start-here-kde.png
/usr/share/icons/oxygen/22x22/places/start-here-kde.png
/usr/share/icons/oxygen/16x16/places/start-here-kde.png
/usr/share/icons/oxygen/32x32/places/start-here-kde.png
```
Of course, replace *oxygen* with the name of your theme. Copy the necessary *.png files in those folders, go to System Settings, Appearance -> Icons, change the theme to something else, than change the theme back to Oxygen (or the theme for which you changed the start-here-kde.png icon). Hope this helps (it worked for me in KDE 4.2.2).

Regarding the shutdown: I can't remember when this *actually worked* on Kubuntu, but it must have been a long, long time ago ;) Just use the shell to reboot or shutdown it.


Thank you so much for the .png locations, I will definitely try that.

As for the shutdown thing #-o

So much for linux being ready for primetime (or at least Kubuntu).  My xbox is out of warranty and just broke too..not a good week :(

---

### Post by anewguy on 2009-04-05
I know there are files for the various run levels, which I believe would also include a shutdown.  Unfortunately I don't know what they are right now.  If we can find the correct one, we could have it run a script containing the kill as per this link:

[http://http://www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line/]("http://http://www.howtogeek.com/howto/ubuntu/kill-a-process-by-process-name-from-ubuntu-command-line/")

I'll try to see if I can find out more on those files, but in the mean time maybe someone else already knows and can answer.

dave :)

EDIT:  Found this link which explains run levels (looks like you would be interested in run level 0 and run level 6).  You should be able to make a script file as per the previous link and then load it into both of the run level folders.

[http://http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html]("http://http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html")

---

