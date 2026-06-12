---
title: "How to kill the &quot;Connection Established&quot; Popup"
date: 2008-11-15
forum: Networking &amp; Wireless
---

### Post by torstenaf on 2008-11-15
I'm up to Intrepid Ibex with a fresh install.

How do I kill the "Connection Established" popup that appears every time I startup and the network manager connects to the wireless access point?

---

### Post by iponeverything on 2008-11-15
could try this:

[http://ubuntuforums.org/showthread.php?t=982097](http://ubuntuforums.org/showthread.php?t=982097)

---

### Post by loell on 2008-11-15
its a bug in nm-applet, its been addressed (i think) , and will be featured in the next release.

[http://www.nabble.com/can%27t-disable-notification-bubbles-in-nm-applet,-or-configure-at-all-td20494015.html]("http://www.nabble.com/can%27t-disable-notification-bubbles-in-nm-applet,-or-configure-at-all-td20494015.html")

you might not want to disable the notification "balloon" (libnotify) system wide as many programs do use it.

---

### Post by feistybill on 2009-06-27
Removing libnotify doesn't seem a good idea...

> 
$ sudo apt-get remove libnotify1
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  autofsck bluez-gnome fast-user-switch-applet gnome-applets
  gnome-control-center gnome-mount gnome-panel gnome-power-manager
  gnome-screensaver gnome-session gnome-settings-daemon indicator-applet
  indicator-messages jockey-gtk kernelcheck libmbca0 libnotify-bin libnotify1
  liferea metacity nautilus nautilus-share network-manager-gnome
  pidgin-libnotify python-notify rhythmbox seahorse seahorse-plugins
  system-config-printer-gnome transmission-gtk ubuntu-desktop update-notifier
  vino vlc zenity
0 upgraded, 0 newly installed, 35 to remove and 0 not upgraded.
After this operation, 87.8MB disk space will be freed.
Do you want to continue [Y/n]? n


Btw I'm using Jaunty.

EDIT:
Removing notify-osd is also not possible without removing a few other gnome components:

> 
$ sudo apt-get purge notify-osd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-power-manager* notify-osd* ubuntu-desktop* update-notifier*
0 upgraded, 0 newly installed, 4 to remove and 0 not upgraded.
After this operation, 12.7MB disk space will be freed.
Do you want to continue [Y/n]? n


I'll try with a chmod -x ...

---

### Post by feistybill on 2009-06-27
Ok, if anyone else is looking for a solution I managed to disable (not remove) notify-osd with a simple:

> 
sudo chmod -x /usr/lib/notify-osd/notify-osd
pkill notify-osd


btw, there's a dozen pages long bug report at launchpad on this issue...

---

### Post by ScottHW on 2009-11-07
I looked around a bit on this Bug.  I've just Upgraded to Karmic, but this still seems to be an issue, for some reason.

Seems that "Notifications" has been discussed in several places, and quite a while ago...
[http://old.nabble.com/can%27t-disable-notification-bubbles-in-nm-applet,-or-configure-at-all-td20494015.html](http://old.nabble.com/can%27t-disable-notification-bubbles-in-nm-applet,-or-configure-at-all-td20494015.html)

The Bug reports suggest that nm-appler 0.7 had an option added to surpress non-critical notifications, but I don't seem to see that in Karmic.  So, the current work around is...
```

gconf-editor
/apps/nm-applet/
disable-connected-notifications [x]    'mark as TRUE
disable-disconnected-notifications [x]   'mark as TRUE

```

---

### Post by ScottHW on 2009-11-09
I've also noticed that when I resume from Standby, I usually get a Disconnected notification.  So the fix I listed earlier apparently isn't perfect.

---

### Post by Xnyper on 2009-11-23
Whenever I automatically connect to a network I get the popup we're talking about.  It shows up in the upper right corner of my screen.

I assume it shows up there because the default panel location is along the top of the screen.

I keep my panel on the left (vertical space is more valuable to me than horizontal space), but the popup still shows in the upper right hand corner, which looks pretty silly.

I'd be interested in any way to disable the notification as well.

By the way, I'm using Karmic.

Edit: tried ScottHW's workaround, doesn't seem to be working for me.  Still get 'em whenever connecting of disconnecting, not just while going on standby. (thanks though!)

---

