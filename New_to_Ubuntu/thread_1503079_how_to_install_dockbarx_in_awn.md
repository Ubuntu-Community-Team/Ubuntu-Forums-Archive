---
title: "how to install dockbarx in awn?"
date: 2010-06-06
forum: New to Ubuntu
---

### Post by AndyP79 on 2010-06-06
Hi Ya'll,
 Anyone figured out how to get dockbarx running in the new awn yet?

---

### Post by M7S on 2010-06-07
1) Install dockbarx the normal way, via ppa or gnome-look.
2) Download dockbarx from gnome-look and extract or copy the content of the folde AWN to ~/.config/awn/applets
3) Open AWN preference and add the dockbar applet to awn.

---

### Post by AndyP79 on 2010-06-09
Cool, it works now. Thanks for the info.

---

### Post by clicker4721 on 2010-08-15
When I do it, nothing happens. The applet opens with a frowning face, and restarting it does nothing.

---

### Post by murderslastcrow on 2010-08-15
Are you using the PPA or the source packages, clicker?

---

### Post by AndyP79 on 2010-08-17
Curently, I am using 10.04, so I don't how how it goes on anything else. Install Ubuntu Tweak. Activate the PPA for Stable AWN, as it has Lucindo and all the major goodies now. Then activate the PPA for DockbarX. Run your updates, just to be sure. Go into synap and search DockbarX and add the extra themes, cause for some reason it does not add them automaticly. You should now be able to start AWN, and add DockbarX from the list. Hope this helps

---

### Post by clicker4721 on 2010-08-18
> **murderslastcrow said:**
> Are you using the PPA or the source packages, clicker?

Hahaha, sorry I'm so late! :P I didn't think anyone would ever bother to answer the thread; I though it was dead! Anyway, I installed the panel applet through the PPA, and downloaded the library from GNOME-Look. I can't explain it, it just randomly started working. I don't know how many times I cut-and-pasted the files in the ~/config/awn/applets/ folder, but this last time, it just randomly started working! :confused: I don't think I changed anything, but it works just fine, now. :)

EDIT: Oh, I just noticed! AndyP79, I wanted to thank you for starting off with "Hi Ya'll". I am from Texas, and I use y'all like normal.

---

### Post by lloydsmart on 2010-10-03
Hi. I'm having problems with dockbarx and awn.

I'm running the maverick release candidate.

I have awn (0.40) installed, along with dockbarx 0.39.7. Awn seems to be loading up fine, but the dockbarx module just appears for a brief moment, displays a green tick, then vanishes. It doesn't matter how many times I remove it and replace it in the awn settings, it still happens. I've tried removing, purging and reinstalling awn and dockbarx but it makes no difference.

The strange thing was, when I first installed all this it worked perfectly, until I rebooted. Then it all went wrong.

Any ideas?

P.S. Despite purging all the packages, when I reinstall via apt, all my settings are restored exactly as I left them. I'm thinking this might be the problem as maybe a bad setting somewhere isn't getting deleted when I reinstall. Can anyone provide a list of all the locations where awn and dockbarx store their data and settings? It would be very handy so I can delete them and try a reinstall. At this rate, it looks like I'm going to have to do a whole OS reinstall just to get these two apps working!

---

### Post by M7S on 2010-10-03
Run avant-window-navigator from terminal and post the errors.

---

### Post by lloydsmart on 2010-10-03
Unbelievable - when I did that it just worked! I feel so stupid now. I've been trying for like 3 hours to get it working, tried all sorts of crazy things, and just quitting and relaunching it did the trick. I have NO idea how that's possible, but thanks for your offer of help anyway.

D'oh!

---

### Post by lloydsmart on 2010-10-04
Hmmm... it seems I spoke too soon. After a reboot it stopped working again and now I can't get it to work at all no matter what I try. Here is the output when running it from a terminal:

```
lloydsmart@lloydsmart-desktop:~$ avant-window-navigator
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
Screen is composited
** (avant-window-navigator:2873): DEBUG: Updating dialog colours
** (avant-window-navigator:2873): DEBUG: Spawned awn-applet[2875] for "yama.desktop", UID: 1286121114, XID: 29360174
** (avant-window-navigator:2873): DEBUG: Spawned awn-applet[2877] for "showdesktop.desktop", UID: 1286033277, XID: 29360175
** (avant-window-navigator:2873): DEBUG: Spawned awn-applet[2878] for "DockBarX.desktop", UID: 1286117160, XID: 29360176
** (avant-window-navigator:2873): DEBUG: Spawned awn-applet[2879] for "indicator-applet.desktop", UID: 1286037462, XID: 29360177
** (avant-window-navigator:2873): DEBUG: Spawned awn-applet[2880] for "weather.desktop", UID: 1286033304, XID: 29360178
** (avant-window-navigator:2873): DEBUG: Spawned awn-applet[2881] for "cpufreq.desktop", UID: 1286032778, XID: 29360179
** (avant-window-navigator:2873): DEBUG: Spawned awn-applet[2882] for "cairo-clock.desktop", UID: 1286121188, XID: 29360180
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
(awn-applet:2879): Indicator-Sound-DEBUG: At start-up attempting to set the image to audio-volume-muted-panel

(awn-applet:2879): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.sound on /org/ayatana/indicator/sound/menu: Could not get owner of name 'org.ayatana.indicator.sound': no such name

(awn-applet:2879): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.messages on /org/ayatana/indicator/messages/menu: Could not get owner of name 'org.ayatana.indicator.messages': no such name

(awn-applet:2879): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.me on /org/ayatana/indicator/me/menu: Could not get owner of name 'org.ayatana.indicator.me': no such name
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.

(awn-applet:2879): LIBDBUSMENU-GLIB-WARNING **: Unable to get property proxy for org.ayatana.indicator.session on /org/ayatana/indicator/session/menu: Could not get owner of name 'org.ayatana.indicator.session': no such name
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
(awn-applet:2879): Indicator-Sound-DEBUG: about to connect to the signals
(awn-applet:2879): Indicator-Sound-DEBUG: indicator-sound: new_volume_slider_widget
(awn-applet:2879): Indicator-Sound-DEBUG: VolumeWidget::volume_widget_init
(awn-applet:2879): Indicator-Sound-DEBUG: volume_widget_set_twin_item initial level = 0.000000
(awn-applet:2879): Indicator-Sound-DEBUG: volume_widget_parent_changed
** (awn-applet:2879): DEBUG: new_application_item ("Chat")
** (awn-applet:2879): DEBUG: new_application_item ("Mail")
** (awn-applet:2879): DEBUG: new_application_item ("Compose New Message")
** (awn-applet:2879): DEBUG: new_application_item ("Contacts")
** (awn-applet:2879): DEBUG: new_application_item ("Broadcast")
** (awn-applet:2879): DEBUG: new_application_item ("Broadcast")
** (awn-applet:2879): DEBUG: entry hint: Post to: facebook...
** (awn-applet:2879): DEBUG: entry_maybe_show_hint, nothing in the entry or not focused, so setting the hint to: Post to: facebook...

(awn-applet:2879): GLib-GObject-WARNING **: /build/buildd/glib2.0-2.26.0/gobject/gsignal.c:2275: signal `destroy' is invalid for instance `0x221c190'
(awn-applet:2879): Indicator-Application-DEBUG: Connected to Application Indicator Service.
(awn-applet:2879): Indicator-Application-DEBUG: Setup proxy signals
(awn-applet:2879): Indicator-Application-DEBUG: Connect to them.
(awn-applet:2879): Indicator-Application-DEBUG: Request current apps
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
** (awn-applet:2879): DEBUG: Updating username label
** (awn-applet:2879): DEBUG: Using user icon for 'Guest Session' from file: (null)
** (awn-applet:2879): DEBUG: Username width 78px
** (awn-applet:2879): DEBUG: Font size 11.000000 pt
** (awn-applet:2879): DEBUG: Screen DPI 96.000000
** (awn-applet:2879): DEBUG: Username width 5.318182em
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:107: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
/home/lloydsmart/.themes/Humanity/gtk-2.0/gtkrc:162: Murrine configuration option "gradients" is no longer supported and will be ignored.
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)
** Message: pygobject_register_sinkfunc is deprecated (AwnOverlay)

** (DockBarX.py:2878): WARNING **: Trying to register gtype 'WnckWindowState' as enum when in fact it is of type 'GFlags'

** (DockBarX.py:2878): WARNING **: Trying to register gtype 'WnckWindowActions' as enum when in fact it is of type 'GFlags'

** (DockBarX.py:2878): WARNING **: Trying to register gtype 'WnckWindowMoveResizeMask' as enum when in fact it is of type 'GFlags'
1286117160 1

** (cpufreq.py:2881): CRITICAL **: awn_icon_expose_event: assertion `priv->icon_srfc' failed

** (cpufreq.py:2881): CRITICAL **: awn_icon_expose_event: assertion `priv->icon_srfc' failed
DockBarApp.__init__()
dockbarx.__file__ =  /usr/lib/pymodules/python2.6/dockbarx/__init__.pyc
 uid =  1286117160 
 panel_id=  1
Dockbarx init
Dockbarx reload
Traceback (most recent call last):
  File "/usr/share/avant-window-navigator/applets/DockBarX/DockBarX.py", line 46, in on_idle
    self.db.reload()
  File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 283, in reload
    self.add_launcher(identifier, path)
  File "/usr/lib/pymodules/python2.6/dockbarx/dockbar.py", line 710, in add_launcher
    if l[0] in ('sudo','gksudo', 'gksu',
IndexError: list index out of range

```

:-(

---

### Post by M7S on 2010-10-04
Reading the code around that error I would guess you have added a launcher that isn't working (a desktop file is missing the exec row, which makes it quite meaningless to use for a launcher). Are you able to load dockbarx in a gnom-panel? Try that first. After that you can try removing the gconf key /apps/dockbarx/launchers

Inform me if it works or not, I think I must add some error handling for weird .desktop files.

---

### Post by lloydsmart on 2010-10-04
> **M7S said:**
> try removing the gconf key /apps/dockbarx/launchers

That did the trick, thanks!

---

