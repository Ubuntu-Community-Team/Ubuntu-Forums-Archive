---
title: "Desktop effects not enabled  Ubuntu 10.04  nvidia 5200"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by WHICKS on 2011-07-26
Hi.  I've just upgraded the os and I can't seem to get my compiz effects to run.  I followed this guide for installation, 

[http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-10.04-desktop-nvidia-geforce-fx-5200](http://www.howtoforge.com/enabling-compiz-fusion-on-an-ubuntu-10.04-desktop-nvidia-geforce-fx-5200)

as I have had very good luck with Falco's "perfect desktop" series in the past.

I can get to the point where I go to system>preferences>appearance>visual effects and click on "custom", and I get a "Desktop effects could not be enabled" message.

When I check my system>admin>hardware drivers , it appears that the nvidia drivers (173) are installed and active.

What should I do next?  Could the conflict be with other drivers for the on-board video?  Thanks in advance.

(I have found a similar thread and played around for an hour or two with no luck, so I thought I would repost it.  I consider myself a computer illiterate when it comes to linux, but I do follow instructions well, and I appreciate everyone's help)

---

### Post by mikejonesey on 2011-07-26
instead of useing that control to switch to compiz just go ahead and install compiz-manager and switch it with;
```
sudo apt-get install compizconfig-settings-manager
gconftool-2 --type string --set /desktop/gnome/session/required_components/windowmanager compiz
compiz --replace &
```

ps at own risk, usually this error apears when you don't have enough ram...

---

### Post by WHICKS on 2011-07-26
No luck.  Same error message pops up after I try to enable the "extra" .  It looks like it is trying to load a driver and doesn't seem to be enabling.

Any other suggestions?

---

### Post by mikejonesey on 2011-07-27
all the enable setting does is enable certain extra compiz things like wobly windows, just switch them on manually using the compiz manager, you have not installed, in system>preferences menu... :)

---

### Post by WHICKS on 2011-07-28
No, the effects are listed and checked off.  Regardless of where I go into them, they are not enabled.

Any more ideas?  Is there a way I can check to see if the drivers for the on-board video (intel ) are still there and can it be disabled?

---

### Post by mikejonesey on 2011-07-28
really? you go to compiz manage and they are checked off and you can't check them on? if so maybe compiz did not install as a dependancy of the manager, sudo apt-get install compiz-gtk...

---

