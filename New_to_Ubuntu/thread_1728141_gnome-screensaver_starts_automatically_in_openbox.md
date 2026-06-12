---
title: "gnome-screensaver starts automatically in openbox"
date: 2011-04-13
forum: New to Ubuntu
---

### Post by a.sarkar on 2011-04-13
Dear all,

I am loading xscreensaver in my openbox system. However, along with xscreensaver, gnome-screensaver also automatically loads itself even if I don't want it to. I want to prevent gnome-screensaver from auto-loading itself. Any help will be appreciated.

My ~/.config/openbox/autostart.sh script is given below.

```

#!/bin/bash

## This shell script is run before Openbox launches.

# ## Adding user's $HOME/bin to path
# if [ -d $HOME/bin ];then
#     PATH=$HOME/bin:$PATH
# fi

## Parse the default applications
if [ -f ~/.default-apps ];then
    source ~/.default-apps
fi

## Set global variables
export LC_COLLATE="en_IN.utf8"
alias nautilus="nautilus --no-desktop"

## Panel
(sleep 3 && fbpanel) &

## Screensaver
(sleep 30 && xscreensaver -no-splash) &

# ## D-bus
# if which dbus-launch >/dev/null && test -z "$DBUS_SESSION_BUS_ADDRESS"; then
#     eval `dbus-launch --sh-syntax --exit-with-session`
# fi

## Make GTK apps look and behave how they were set up in the
## gnome config tools
# if test -x /usr/libexec/gnome-settings-daemon >/dev/null; then
#   /usr/libexec/gnome-settings-daemon &
# elif which gnome-settings-daemon >/dev/null; then
#   gnome-settings-daemon &
# fi

# ## Preload stuff for KDE apps
# if which start_kdeinit >/dev/null; then
#     LD_BIND_NOW=true start_kdeinit --new-startup +kcminit_startup &
# fi

## For xfce-settings
# if which xfce-mcs-manager >/dev/null; then
#     xfce-mcs-manager &
# elif which xfce-settings-manager >/dev/null; then
#     xfce-settings-manager &
# fi

## For terminal emulator
xrdb -load ~/.Xdefaults

## Auto-mount usb-drive
nautilus --no-desktop -n &

## Set wallpaper
eval $(cat $HOME/.fehbg) &

## For desktop icons
(sleep 2 && idesk) &

## Dock
(sleep 3 && wbar -above-desk -pos bottom -isize 40 -nanim 5 -zoomf 1.2 -bpress )&

## For desktop system monitor
conky-startup -d 20s &

## Gnome Power Manager
xfce4-power-manager &

## For network applet
nm-applet --sm-disable &

## Day Planner
(sleep 25 && dayplanner-daemon) &

## Update-notifier
(sleep 35 && update-notifier) &

# Language support (for typing non-english characters)
(sleep 40 && ibus-daemon -rd) &

```

---

### Post by josephmills on 2011-04-13
**system-->preferences--> screensaver**. Move the bar up to two hours or what ever you would like. Then go to **Power management ** and change you settings there too. hope that this helps
Edit: I don't know if that is the same with openbox but at least I tried and bumped you up.

---

### Post by a.sarkar on 2011-04-13
Thanks josephmills. Will try out your suggestion. Will post if this works.

---

### Post by a.sarkar on 2011-04-23
No josephmills. Your suggestion didn't work. gnome-screensaver is still loading itself.

---

### Post by cnbiz850 on 2011-05-13
I actually removed gnome-screensaver.

---

### Post by a.sarkar on 2011-05-14
Yeah @cnbiz850 that thought occurred to me. But I was looking for a solution where I didn't have to remove gnome-screensaver.
[URL="http://ubuntuforums.org/member.php?u=71512"]
[/URL]

---

