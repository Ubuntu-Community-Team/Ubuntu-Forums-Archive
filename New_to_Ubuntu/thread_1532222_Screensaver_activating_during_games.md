---
title: "Screensaver activating during games"
date: 2010-07-16
forum: New to Ubuntu
---

### Post by DrDevice on 2010-07-16
Hello again fellow Ubuntu-ers!

I have a slightly annoying problem that I'd like to see if I can resolve.  Problem:  When I run some games (ET,ETQW, Doom 3 as well as DOSBox) fullscreen, my screensaver will activate after a few minutes, causing me to drop out of fullscreen and most times lose input as well.  I have to Alt-F1 to another terminal and login, then kill the process of the game to return input to the Gnome interface.  I work around this by turning off the screensaver when I play those games, but I'm forgetful and sometimes don't turn it back on.  Is there a way I can set Ubuntu to recognize that my computer is *not* idle and therefore not activate the screensaver?

---

### Post by SnickerSnack on 2010-07-16
> **DrDevice said:**
> Is there a way I can set Ubuntu to recognize that my computer is *not* idle and therefore not activate the screensaver?

Have you tried other screen savers besides gnome-screensaver?

You might also consider writing additional launch scripts that turn off the screensaver automatically when you start a game.  You can do pretty much anything with a script, for example, on my tablet, I have set a keyboard shortcut to rotate the screen and stylus and disable the trackpoint for when I write on it; pressing the button again rotates everything and enables the trackpoint.

If you want to try that, start by finding out how to disable/enable the screen saver from the command line.

---

### Post by mastablasta on 2010-07-16
> **SnickerSnack said:**
>  
You might also consider writing additional launch scripts that turn off the screensaver automatically when you start a game. 
 
A sound advice for a beginner and computer illiterate.
 
 
Screen saver should be turned off automatically. I never heard Windows having this issue in all the years they are arround (well maybe in 3.x - i don't remember that far, but not after 95 ).

---

### Post by DrDevice on 2010-07-16
@SnickerSnack:
I'd like to stick with gnome-screensaver, to keep things simple.  But thanks for the script idea!  I haven't tried those before, but it does sound like that should be my focus.

I've googled around and it seems that the most common solution involves using DBus and Python, but I'm not sure what the scripts do exactly; not enough to tailor them to my specifications.  The documentation for DBus isn't very newbie friendly (at least to me), and I know DBus is very important for communication between programs, so I'm leery to experiment without understanding what might break.

Got some pointers?

@mastablasta:
I'd say I'm far more intermediate than beginner, and *definitely* not illiterate!  :D 20+ years of being a casual Keyboard Cowboy.  Ah, Amiga, how I miss thee...

---

### Post by mike555 on 2010-07-16
There is a little app called "caffeine " that will let you temperately disable power saving and screen saver .....

---

### Post by DrDevice on 2010-07-16
> **mike555 said:**
> There is a little app called "caffeine " that will let you temperately disable power saving and screen saver .....

Success!  Thanks Mike!  Caffeine does indeed do what I need it to do.  Once installed and running, right-click on the coffee-cup icon in your system tray and choose Preferences.  You'll be able to add a process name that Caffeine will look for and automatically suspend the screensaver (in my case "etqw.x86").  I haven't let it run long enough to test powersaving, but I'll post back on that next time I run a game. :D

It can even detect Flash video embedded in a browser and suspend then.  Yay!  Better YouTube experience.

If this program continues to work out, it has my vote for inclusion in the repos. :mrgreen:

---

### Post by SnickerSnack on 2010-07-16
> **mastablasta said:**
> A sound advice for a beginner and computer illiterate.
 
 
Screen saver should be turned off automatically. I never heard Windows having this issue in all the years they are arround (well maybe in 3.x - i don't remember that far, but not after 95 ).

Thanks for being rude and unhelpful.

DrDevice: glad you found what you needed.

---

