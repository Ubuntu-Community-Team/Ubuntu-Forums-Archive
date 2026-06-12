---
title: "Will I lose my applets when i upgrade to 11.04? see pic"
date: 2011-04-28
forum: New to Ubuntu
---

### Post by SebSmith on 2011-04-28
Will i lose this look of ubuntu ive come to know and love through my customization?

obviously i will lose it on unity, but what about "classic mode"?

upgrading from update manager

---

### Post by SebSmith on 2011-04-28
and i was also thinking, is there some way i could put a second taskbar on the bottom using unity that i could put applet- like icons? ie cpus, cpu temp, temp, etc

---

### Post by jakslev on 2011-04-28
Yes - say goodbye to those :(

---

### Post by Mad-Halfling on 2011-05-02
You can whitelist apps so they appear in the notification area
[http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/](http://www.omgubuntu.co.uk/2011/03/how-to-hide-or-show-app-tray-applets-in-ubuntu-11-04/)
this is quite simple and works fine - I've currently put pidgin and dropbox in there

```
gsettings get com.canonical.Unity.Panel systray-whitelist
```

will list your current whitelist, you can then add entries and then use

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Wine', 'Dropbox']"
```

to update it, for example mine currently reads

['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'Pidgin', 'Dropbox']

so this would be 

```
gsettings set com.canonical.Unity.Panel systray-whitelist "['JavaEmbeddedFrame', 'Mumble', 'Wine', 'Skype', 'hp-systray', 'Pidgin', 'Dropbox']"
```

this doesn't fix the dreadful lack of a taskbar (I am _really_ missing that) but it helps a bit

---

