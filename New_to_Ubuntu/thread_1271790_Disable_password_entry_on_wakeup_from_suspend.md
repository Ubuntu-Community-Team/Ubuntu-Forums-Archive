---
title: "Disable password entry on wakeup from suspend?"
date: 2009-09-21
forum: New to Ubuntu
---

### Post by donsy on 2009-09-21
I have automatic login and timed login enabled. Now is there a way to disable the password prompt upon waking up from suspend?

---

### Post by swoody on 2009-09-21
Press alt+F2 to open the 'Run' dilogue. Type in 'gconf-editor', and press enter.

In gconf-editor, on the left hand side, navigate to:
```
apps>gnome-power-manager>lock
```
and select the 'use_screensaver_settings' option. 

I just tested this out to confirm it works, and it worked on my 9.04 Jaunty install. Please let us know if it works for you, or if you have any issues :)

---

### Post by donsy on 2009-09-21
> **swoody said:**
> Press alt+F2 to open the 'Run' dilogue. Enter 'gconf-editor', and press enter.

In gconf-editor, on the left hand side, navigate to:
```
apps>gnome-power-manager>lock
```and select the 'use_screensaver_settings' option. 

I just tested this out to confirm it works, and it worked on my 9.04 Jaunty install. Please let us know if it works for you, or if you have any issues :)

Yes it worked, thanks.

---

### Post by donsy on 2009-10-30
> **swoody said:**
> Press alt+F2 to open the 'Run' dilogue. Type in 'gconf-editor', and press enter.

In gconf-editor, on the left hand side, navigate to:
```
apps>gnome-power-manager>lock
```and select the 'use_screensaver_settings' option. 

I just tested this out to confirm it works, and it worked on my 9.04 Jaunty install. Please let us know if it works for you, or if you have any issues :)

This worked for 9.04 but doesn't work in 9.10. Anyone have any ideas?

---

### Post by swoody on 2009-11-01
Did you just upgrade from 9.04 or did you do a fresh install of 9.10? Go back into gconf-editor, and double-check that the setting I mentioned above is still selected. Try also going to System>Preferences>Screensaver and make sure the 'Lock screen when screensaver is active' option is not selected. Then test it out. If this still doesn't work, please let us know :)

---

### Post by dndrich on 2009-11-01
There is a graphic way to do this if you are lazy like me. First, go to System, Preferences, Main menu on the upper panel. That gives you the list of applications shown in the applications menu. Click on system tools, and enable configuration editor. Now, when you go to your Applications menu, you can scroll down to system tools, and open configuration editor. From there, you have like 4 choices. One of them is applications. Scroll down to gnome-power-manager, and open that. Below is a choice called "lock". Open that. Uncheck suspend and gnome_keyring_suspend. That will fix the problem. I have to do this every time I install Ubuntu, because I suspend the laptop I use at work all the time.

---

### Post by Coder543 on 2009-11-02
Contrary to popular belief... this does NOT work in 9.10. Remember, it uses DeviceKit and udev, not HAL. I too would like to disable that lock dialog on unsuspend. 

A note to Canonical:
Seriously Canonical, how many versions of Ubuntu have you released? And you mean to tell me you still haven't put a graphical way to disable locking? That's really kind of sad on your part...

[why can't they just put a checkbox! it can't be that hard for them. lol]

---

### Post by dndrich on 2009-11-02
I am surprised to hear you say this, because it works just fine for me on Karmic. I mean, I have 3 Dell Mini 9's running Karmic, and I used the above graphical interface on all 3 to stop that login behavior on suspend, and all 3 work just perfectly. I can suspend and resume to my heart's content without having to log back in. There must be something funny about your set up.

---

### Post by lodravah on 2009-11-02
> **dndrich said:**
> I am surprised to hear you say this, because it works just fine for me on Karmic. I mean, I have 3 Dell Mini 9's running Karmic, and I used the above graphical interface on all 3 to stop that login behavior on suspend, and all 3 work just perfectly. I can suspend and resume to my heart's content without having to log back in. There must be something funny about your set up.

Works just fine. Thanx :) I guess it is from a log-in security aspect that Canonical does not make it easily available to disable password at suspend. But it should just be a check-box in Power-manager or something.

---

### Post by dndrich on 2009-11-02
Ah, well I agree with you there. Seems like most users would want to disable it like we do, and it should be in an obvious place, such as the login menu in the administration section.

---

### Post by donsy on 2009-11-03
> **swoody said:**
> Did you just upgrade from 9.04 or did you do a fresh install of 9.10? Go back into gconf-editor, and double-check that the setting I mentioned above is still selected. Try also going to System>Preferences>Screensaver and make sure the 'Lock screen when screensaver is active' option is not selected. Then test it out. If this still doesn't work, please let us know :)

Yes I did a clean-install (twice) of 9.10, and in System>Preferences>Screensaver > Lock I checked the 'use_screensaver_settings' option. The 'Lock screen when screensaver is active' option is unchecked in  System>Preferences>Screensaver. 

> **dndrich said:**
> There is a graphic way to do this if you are lazy like me. First, go to System, Preferences, Main menu on the upper panel. That gives you the list of applications shown in the applications menu. Click on system tools, and enable configuration editor. Now, when you go to your Applications menu, you can scroll down to system tools, and open configuration editor. From there, you have like 4 choices. One of them is applications. Scroll down to gnome-power-manager, and open that. Below is a choice called "lock". Open that. Uncheck suspend and gnome_keyring_suspend. That will fix the problem. I have to do this every time I install Ubuntu, because I suspend the laptop I use at work all the time.

This didn't work either.

#######

So far I've tried every every combination of settings in  gnome-power-manager > lock and System>Preferences>Screensaver. In Screensaver I even unchecked the 'Activate screensaver when computer is idle' option, but upon wakeup the screensaver still shows (Hypertorus) and the password window still shows up. Right now all settings are unchecked.

---

### Post by donsy on 2009-11-05
Well here's what I finally did to get it to work:

1. Installed Ubuntu Tweak.
2. In Ubuntu Tweak:
   Security > Disable Lock Screen == (check)

---

### Post by kwaanens on 2009-11-21
I also needed Ubuntu Tweak to do this.
So, it is clearly possible, but there should be a way without bringing in that beast of an application, feature wise.

---

### Post by enpjp on 2009-12-14
Hi,

I've needed to download Ubuntu Tweaks in order to disable password entry on wakeup from suspend.  

The computer is a fresh install on a Toshiba Portege R600.

Regards

Paul

---

### Post by photo_ted on 2010-01-05
Is it possible that gconf-editor changes different settings depending on how it's invoked?  The screen-saver password issue was driving me nuts and I thought I had tried everything.  On a terminal window if I entered:[INDENT]sudo gconf-editor
[/INDENT]it seemed the settings were different than when I followed dndrich's instructions posted here on Nov 1 on how to get the configuration editor on the main menu.  Once I followed those instructions, launched the configuration editor from the menu, found the settings under /apps/gnome-power-management/lock and set blank-screen and use_screen_saver_settings to true (checked) and unchecked all the others, it finally worked.  Of course I had the screen saver preference locked set as false.

---

### Post by mcduck on 2010-01-07
> **photo_ted said:**
> Is it possible that gconf-editor changes different settings depending on how it's invoked?  The screen-saver password issue was driving me nuts and I thought I had tried everything.  On a terminal window if I entered:[INDENT]sudo gconf-editor
[/INDENT]it seemed the settings were different than when I followed dndrich's instructions posted here on Nov 1 on how to get the configuration editor on the main menu.  Once I followed those instructions, launched the configuration editor from the menu, found the settings under /apps/gnome-power-management/lock and set blank-screen and use_screen_saver_settings to true (checked) and unchecked all the others, it finally worked.  Of course I had the screen saver preference locked set as false.

well, anything changes depending which user you run it as. ;)

If you run gconf-editor with "sudo" you are starting it as root user, not your own user. And of course every user has his own settings.
(by the way you should never run graphical applications with "sudo", use "gksudo" instead. "sudo" doesn't work correctly for graphical applications and may in some cases result in running things as root but with your normal user's home directory and configuration files, changing the file's ownership to root while doing so).

Anyway, I'm still having this same problem myself, I've disabled the lock in every possible place, both as my own user and as root. And still the screen is locked on suspend.. Which is quite annoying, at least, and even stranger considering that changing the lock dialog theme through gconf-editor (as my own user) works just fine, it's just that disabling the lock doesn't work...

edit: never mind. The problem seems to be related to the Indicator-applet-session, since suspending by any other means works correctly, while suspending with this applet locks the screen regardless of the settings in gconf and in /etc/default/acpi-support...

---

### Post by riseringseeker on 2010-01-25
> **donsy said:**
> This worked for 9.04 but doesn't work in 9.10. Anyone have any ideas?

I've found it sort of works.  If I do a Fn-F1 it will come back without asking for a password, also if I just close the lid.  If, however, I use the indicator-applet (where you would shutdown or switch users) it comes back to a screen saver and kicking it off, asks for a password.

---

### Post by alcarola on 2010-06-10
Check this thread: [http://ubuntuforums.org/showthread.php?t=1468732&page=2](http://ubuntuforums.org/showthread.php?t=1468732&page=2)

The piece

"launch gconf-editor (alt-f2 --> type gconf-editor --> click run).

go to apps->gnome-power-manager->lock->check use_screensaver_settings"

of advice solved the problem for me.

---

### Post by mikeh on 2010-10-15
Arrgh! Problem is back after 10.10 maverick upgrade.
Suspending using the menu from the indicator appplet leads to password prompt on resume.
  And on my desktop PC, suspend button on keyboard does not work, so I have to use the menu.

Any new suggestions for either problem?

---

