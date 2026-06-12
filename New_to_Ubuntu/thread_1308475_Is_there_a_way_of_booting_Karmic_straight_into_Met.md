---
title: "Is there a way of booting Karmic straight into Metacity?"
date: 2009-10-31
forum: New to Ubuntu
---

### Post by CountryFan on 2009-10-31
After upgrading to Karmic, my system locks up almost as soon as the desktop appears. I suspect this may be due to some sort of problem with Compiz refreshing the desktop display. I'd like to try Metacity, but the system always locks up before I have time to type "metacity --replace", and won't accept any input.

Is there a way of making the boot sequence go straight into Metacity, without Compiz loading?

---

### Post by Turtle.net on 2009-10-31
Great idea.
I had the Blank Screen problem.
Looks like it is a compiz issue.
Here is what I have done (maybe not really clean but let me logged into gnome )
When you boot, instead of launching a gnome session launch a xterm one.
Then 
```
cd .config/gnome-session/saved-session
ls -l
```
then edit .desktop files
```
nano -w 10xxxx.desktop
```
You should have something like this
> [Desktop Entry]
Type=Application
then replace compiz by metacity in the correct file and you are done.
Exit xterm (Ctrl+d) and launch a gnome session :)

---

### Post by Turtle.net on 2009-10-31
In the end my .desktop file looked like this
> 
[Desktop Entry]
Type=Application
Encoding=UTF-8
Name=Metacity
Exec=metacity
NoDisplay=true
# name of loadable control center module
X-GNOME-WMSettingsModule=metacity
# autostart phase
X-GNOME-Autostart-Phase=WindowManager
X-GNOME-Provides=windowmanager
# name we put on the WM spec check window
X-GNOME-WMName=compiz
# back compat only 
X-GnomeWMSettingsLibrary=metacity
X-GNOME-Autostart-startup-id=10e6f0fc2c7b0954d4125358147825332400000050400035

---

### Post by kerry_s on 2009-10-31
> **CountryFan said:**
> After upgrading to Karmic, my system locks up almost as soon as the desktop appears. I suspect this may be due to some sort of problem with Compiz refreshing the desktop display. I'd like to try Metacity, but the system always locks up before I have time to type "metacity --replace", and won't accept any input.

Is there a way of making the boot sequence go straight into Metacity, without Compiz loading?

right after your bios loads, start pressing "escape(esc)" before the ubuntu logo appears in the center of the screen, you should then be able to select recovery-> root shell
then you purge compiz or what ever.

---

### Post by CountryFan on 2009-11-02
Thanks for all the help. :)

On my system, the Compiz window manager worked best with 8.10, gave a few problems with pointers and progress bars "sticking" on 9.4, but seems to be unworkable on 9.10. It locks up the system almost immediately after the desktop appears, and prevents mouse or keyboard input.

I like the gnome environment, and may continue trying later - but I've since tried kubuntu, and found the k window manager gives no problems on my system - so for everyday work at the moment, I'm going with that.

---

