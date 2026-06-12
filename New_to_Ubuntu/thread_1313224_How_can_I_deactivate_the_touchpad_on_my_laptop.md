---
title: "How can I deactivate the touchpad on my laptop?"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by sdim on 2009-11-03
Hi,everyone.
Been using Karmic these past few days,and I can't seem to be able to find a way to deactivate the touchpad on my laptop.I used to be able to do that in Jaunty by going to Preferences-->Mouse-->Disable touchpad.
By going to the same place now,I only see something about disabling the touchpad while typing,but I don't want to do that.I use a mouse,so I'd like to determine when to activate the touchpad and when not.
Many thanks in advance.

---

### Post by sdim on 2009-11-03
Found [this]("http://ubuntuforums.org/showthread.php?t=1298198&page=2").Someone suggested this as a way.So,I suppose,they have made it more detailed this time,but there isn't a setting to completely disable the touchpad,as there was in 9.04...I don't understand this...

---

### Post by 64bitguy on 2009-11-04
Hi

I too tried the above fix(es) unsuccessfully.  
To cut to the chase, I used "System, Administration, Synaptic Package Manager) to find, mark and install "gpointing-device-settings".

I then opened "Applications, Accessories, Terminal"  and ran "gpointing-device-settings" to bring up the GUI and changed the first drop down to indicate "Touchpad Off" and "Ok" to close.  

I had already gone into "System, Preferences, Mouse" and in the "Touchpad" tab, had unchecked both "disable touchpad while typing" and "enable mouse clicks with touchpad" checkboxes to no avail (it didn't disable anything).

So after the gpointing-device-settings part, all is well with the touchpad finally off (and doesn't start again on its own 5 minutes later), **until I reboot**.  Then it simply comes back on again and I must go back into terminal and re-run "gpointing-device-settings" to disable the touchpad.

This is literally a clean build of 9.10 and after reading the many posts on the subject (even the ones inaccurately marked "Resolved").  **I can find no permanent solution**.  

***If I had a "What if?" request ***(or if you will, a fix) from the user perspective it would consist of a simple checkbox option (inside the "System, Preferences, Mouse" section) that would "disable touchpad when other pointing device is present" (as is the case with most Touchpad/mouse drivers in Windows and "other" Operating Systems out there).  

In Windows, this rule is created and maintains an active relationship with the touchpad (which is always off from the user perspective) mainly because during a hibernation caused (for example) by a low battery condition, an exception to this rule is enacted that allows users to restore power (by simply touching the touchpad).  

In this case, the touchpad is only necessary because the USB port (that the external mouse is plugged into) would be unpowered and thus, (in that state) would conflict with the system power management rule of utilizing "Mouse/Keyboard" actions to restore from hibernation, which is why the touchpad is restored (conditionally) to satisfy that power management capability.  

Once the USB (or whatever port) power is restored (during the wake up from hybernation) and the external mouse is recognized, the touchpad turns itself off again automatically satisfying the Mouse driver rule.

Edit:  In closing, I want to mention that I see this as a **[COLOR=Red]critical bug[/COLOR] from a business perspective**.  My particular scenario includes thousands of Dells, Gateways and HP **laptop** computers that _**MUST**_ have the touchpad disabled in the conditional (power management and external mouse relationship) manner that I have described above.  Anything less is a show-stopper.

---

### Post by sdim on 2009-11-05
Personally,this is how I did it (based on a quick solution provided in the link I gave above):
Right-click on the panel and Add Launcher-->Application in Terminal,giving this as a command:
```
sudo modprobe -r psmouse
``` 
to deactivate the touchpad,and this 
```
sudo modprobe psmouse 
```
as a command to activate it again.
Thus,having these launchers on your panel,you switch on and off the touchpad,whenever you want to.
I know,Ubuntu should have placed a Disable Touchpad option,like they had done in Jaunty...Don't know why they didn't,this time...

---

### Post by joanmunoz on 2009-11-13
> **sdim said:**
> Personally,this is how I did it (based on a quick solution provided in the link I gave above):
Right-click on the panel and Add Launcher-->Application in Terminal,giving this as a command:
```
sudo modprobe -r psmouse
``` 
to deactivate the touchpad,and this 
```
sudo modprobe psmouse 
```
as a command to activate it again.
Thus,having these launchers on your panel,you switch on and off the touchpad,whenever you want to.
I know,Ubuntu should have placed a Disable Touchpad option,like they had done in Jaunty...Don't know why they didn't,this time...

Well, I did in a more rough way... I simply added the application "gpointing-device-settings" to the "System" --> "Preferences" --> "Start applications" menu. Thus, everytime I boot I get the chance to disable the touchpad.

Regards

Joan

---

### Post by ww2 on 2009-12-17
A better way to do it:

[http://ubuntuforums.org/showpost.php?p=8515451&postcount=15](http://ubuntuforums.org/showpost.php?p=8515451&postcount=15)

---

### Post by Kapone on 2009-12-25
> **sdim said:**
> Personally,this is how I did it (based on a quick solution provided in the link I gave above):
Right-click on the panel and Add Launcher-->Application in Terminal,giving this as a command:
```
sudo modprobe -r psmouse
```to deactivate the touchpad,and this 
```
sudo modprobe psmouse 
```as a command to activate it again.
Thus,having these launchers on your panel,you switch on and off the touchpad,whenever you want to.
I know,Ubuntu should have placed a Disable Touchpad option,like they had done in Jaunty...Don't know why they didn't,this time...

Hey,

I have ran a few flavours of Linux, all from live disk. Linux Mint is the first I had the least number of issues with and felt safe adding as a dual boot so I did not have to use the god awful Windoze Vista. My laptops touch-pad was so sensitive I was editing my mistakes more than anything and when running Windoze I could just click Function F9 to enable/disable this since I always use my trackball mouse. I found a lot of different scripts that were for this purpose but me being a "newbie" to the world of Linux I was looking for something simpler. Yours worked PERFECT for me and I have not had to edit this post once because my palm hit the touch-pad making the cursor end up god knows where.

Thank You,

[FONT=Georgia]**[COLOR=Navy]K  A  P  0  N  E[/COLOR] **[/FONT] :cool:

---

### Post by MusicGenic on 2009-12-25
Recently ive installed call of duty 4. For some reason im unable to click ON anything.. so i can use the keyboard to select join game, yet im sure you can see how its kinda hard to play without a mouse. I hope there is a command for the terminal i can enter otherwise im baffled. Please Help!

---

