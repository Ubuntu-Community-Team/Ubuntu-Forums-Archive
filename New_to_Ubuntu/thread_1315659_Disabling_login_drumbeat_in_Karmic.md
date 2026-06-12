---
title: "Disabling login drumbeat in Karmic"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by therieb on 2009-11-05
Hello all,

Just upgraded my eee to Koala and that drumbeat noise on login is back.  I had disabled it in Jaunty in system>>administration>>login screen, but my settings weren't carried over during the upgrade and the option to disable the sound is no longer in system>>adminstration>>login screen.  I have all alert sounds disabled under system>>sounds.  All of the threads I've found relating to the drumbeat are for older versions of Ubuntu.  Any help would be appreciated.

---

### Post by JBAlaska on 2009-11-05
I think the sound file is: /usr/share/sounds/ubuntu/stereo/dialog-question.ogg, I don't know where to disable it though..but with this info you should be able to change it at least.

[COLOR="Blue"]Edit: This seems to be a known bug with Gnome, try this command to disable the login drumbeat:[/COLOR]
```
sudo -u gdm dbus-launch gconftool-2 --set /desktop/gnome/sound/event_sounds --type bool false
```

---

### Post by Konrad Ansehelm on 2009-11-17
The above command worked for me. I was puzzled why turning off the alert sound events did not work, but this command clarified it.

Your settings apply only to your user account, but at the time the login screen appears you are not logged in yet, so your settings are not yet loaded.

What the above command does is turn off the alert sound events for the 'gdm'-user, the virtual user in charge of the login screen. Problem solved!

It is a terminal way of logging in as the gdm-user, loading up gconf-editor, navigating to the sound settings (/desktop/gnome/sound/) and unticking the 'event_sounds' checkbox.

Here's the bug report on launchpad:
[https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/437429)

---

