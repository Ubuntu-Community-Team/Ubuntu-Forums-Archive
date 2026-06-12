---
title: "GNOME will not load ,daemon problem"
date: 2009-06-26
forum: New to Ubuntu
---

### Post by politico34 on 2009-06-26
Ubuntu 9.04 will not load. When I run the recovery mode the phrase in my subject line is listed with a red FAIL next to it. I did recently install a win98 driver for my dwl-510 D-link card. The computer was running fine after the install but would not load the next time it was restarted. Any help would be greatly appreciated.
Here is the full error:

[COLOR="Red"]Starting avahi mDNS/DNS-SD Daemon avahi-daemon
Timeout reached wating for return value
Could not receive return value from daemon process[/COLOR]

---

### Post by antikristian on 2009-06-26
Does the booting stop at this point, where you see the mDNS error? Because that is not related to wireless drivers directly.

Where does it stop, could you emphasise what you mean by > Ubuntu 9.04 will not load

---

### Post by politico34 on 2009-06-26
Ubuntu will not load= I see the ubuntu loading screen, then it go to the desktop wallpaper and the "working" mouse cursor and never moves beyond that. I saw the error message when I pushed crl+alt+f1 in recovery mode.

---

### Post by antikristian on 2009-06-26
do you get a commandprompt/login console when you press ctrl+alt+f1 or ctrl+alt+f2?

If you do, then you could check the logs, or try to start x manually from the commandprompt

start x manually:
```
sudo /etc/init.d/gdm stop
startx
```

---

### Post by politico34 on 2009-06-26
When I used the startx command the desktop loaded and then immediately froze with this error:

Panel encountedered a problem while loading 
OAFIID:Gnome_Indicator Applet
There was an option to delete or not delete but like I said the computer was frozen. 
What should I do?

---

### Post by carml on 2009-06-26
Ctrl + Alt + Canc then select Recovery mode followed by Repair broken packages,doing so you'll be able to boot again your system, without making use of the driver you tried to install. :)

---

### Post by politico34 on 2009-06-26
I'm sorry, I'm to new to know what the third button is to push in ctl+alt+canc

Also, I have run the restore broken pkgs. in recovery before and it has done nothing. Will using crtl+alt+canc be different?

---

### Post by carml on 2009-06-26
My bad sorry: Ctrl + Alt + Delete (my keyboard is italian,so sometimes I forget to translate something to english :roll: )

---

### Post by politico34 on 2009-06-26
Still, nothing is working! 
Gnome is locked up at login. I have read that the indicator-applet is probably only a sign of a larger issue, but I can not get any logs to run. Where should I go from here!?

---

### Post by antikristian on 2009-06-26
restart the computer (hold in the power button if necessary), and go back to the command-prompt. Do a ```
sudo /etc/init.d/gdm stop
```

Now do not start the desktop yet, Let's see if this problem is caused by currupt user environment, or something completely diffrent.

run ```
sudo su -
startx
```

this will start gnome as the root user, you do not want to use this as a default, but if this brings you into the gnome desktop, then there is something wrong with your user account.

If it still crashes, then we could check if the problem is caused by software not having had time to configure properly during a software-upgrade.

```
sudo dpkg --configure --pending
```

If nothing happens, than my hunch may be wrong, if it starts to configure some packages, then try to run ```
startx
``` once they are finished.


There are still other things we could try, but lets start off with these.

---

### Post by politico34 on 2009-06-26
Thank you so much for your help antikristian!
Unfortunately, I did not have any success with those command lines. 
 Any other ideas?
Really appreciate it.

---

### Post by antikristian on 2009-06-26
so gnome crashes even if you fist run "sudo su -" and then startx?

---

### Post by politico34 on 2009-06-26
yes. The desktop is there and there is the error messages. One about HAL and the other either about "user switching" or the indicator applet problem.
ideas?

---

### Post by antikristian on 2009-06-27
the indicator applet always dies when you run startx, so that's not the problem. hal on the other hand could be a pretty serious problem, could you write the error message you are getting?

---

### Post by politico34 on 2009-06-27
The HAL message has always been hidden behind the indicator message. I only happened to see it randomly once when I used "startx". It was very short something like could not initiate HAL. Is there a command line I could use to bring up a helpful and relevant error log?

---

