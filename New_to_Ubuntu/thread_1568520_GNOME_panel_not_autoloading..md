---
title: "GNOME panel not autoloading."
date: 2010-09-05
forum: New to Ubuntu
---

### Post by fslezak on 2010-09-05
Hi.

After a "problem", ([http://ubuntuforums.org/showthread.php?t=1563822](http://ubuntuforums.org/showthread.php?t=1563822)), my panel stopped loading. No messages, no nothing except my desktop.

Right now, I am loading the panel from Startup Applications, but I would like a failsafe way to get my panel to load, without relying on the Startup Applications.

---

### Post by chopinhauer on 2010-09-05
> **fslezak said:**
> 
Right now, I am loading the panel from Startup Applications, but I would like a failsafe way to get my panel to load, without relying on the Startup Applications.


Usually the Panel is started from the list of applications saved by the Session Manager. You can save this list in Startup Applications Preferences > Options by clicking on Remember Currently Running Applications. This way you won't need to add them manually to the Startup Applications.

The GNOME Session Manager has a [failsafe feature](http://live.gnome.org/SessionManagement/RequiredComponents) that should run the Window Manager, Panel and File Manager no matter how screwed your startup configuration is.

Since the panel disappeared from your session something broke this failsafe mechanism. Run:
```
gconftool-2 -R /desktop/gnome/session
```
in a terminal to discover what happened. The reference output should be:
```

 required_components_list = [windowmanager,panel,filemanager]
 default_session = [gnome-settings-daemon]
 idle_delay = 5
 /desktop/gnome/session/required_components:
  filemanager = nautilus
  windowmanager = metacity
  panel = gnome-panel

```

---

### Post by fslezak on 2010-09-06
Failsafe works, it is just the standard session.

---

### Post by chopinhauer on 2010-09-06
The [failsafe feature](http://live.gnome.org/SessionManagement/RequiredComponents) I was talking about does not depend upon the type of session you are running (standard or failsafe).

In a nutshell you have to start the standard session, type:
```
gnome-session-save
```
in a terminal (or click Remember Currently Running applications in the Startup Applications Preferences).

In GNOME there are two types of Startup Applications: those statically configured to start (in *~/.config/autostart* and those dynamically saved when you log out (in *~/.config/gnome-session/saved-session*) if the option is checked in Startup Applications Preferences).

The second kind is better since the Session Manager allows not only starts these applications, but he allows them to retrieve some data from their previous session. For example Totem remembers the playlist.

---

