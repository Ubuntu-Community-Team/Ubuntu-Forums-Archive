---
title: "Startup applications"
date: 2009-05-27
forum: New to Ubuntu
---

### Post by birdwin on 2009-05-27
Can anyone tell me what the default startup applications are for Ubuntu Desktop (or point me to where a list can be found)? I (rather naively) disabled a bunch and am having some trouble. They can be found in System->Preferences->Startup Applications.

-Matt

---

### Post by presence1960 on 2009-05-27
just tick the ones you want to enable. see attached screenshot

---

### Post by birdwin on 2009-05-27
Eh, I removed them apparently, so they're not even on the list. A list of the entries and their commands would be greatly appreciated.

---

### Post by xavierp94 on 2009-05-27
> **birdwin said:**
> Eh, I removed them apparently, so they're not even on the list. A list of the entries and their commands would be greatly appreciated.

AT SPI Registry Wrapper
/usr/lib/gnome-session/helpers/at-spi-registryd-wrapper

Bluetooth Manager
bluetooth-applet

Check for new hardware drivers
sh -c 'test -e /var/cache/jockey/check || exec jockey-gtk --check 60'

Evolution Alarm Notifier
sh -c "sleep 30; exec /usr/lib/evolution/2.26/evolution-alarm-notify"

GNOME Keyring Daemon
gnome-keyring-daemon --start

GNOME Login Sound
/usr/bin/canberra-gtk-play --id="desktop-login" --description="GNOME Login"

GNOME Settings Daemon
/usr/lib/gnome-settings-daemon/gnome-settings-daemon

GNOME Settings Daemon Helper
/usr/lib/gnome-session/helpers/gnome-settings-daemon-helper

GNOME Splash Screen
/usr/lib/gnome-session/helpers/gnome-session-splash

Indicator applet
sh -c "sleep 60 && python /usr/share/gnome-panel/add-indicator-applet.py"

Network Manager
nm-applet --sm-disable

Power Manager
gnome-power-manager

Print Queue Applet
sh -c "sleep 30; exec system-config-printer-applet > /dev/null 2> /dev/null"

Remote Desktop
/usr/lib/vino/vino-server

Seahorse Daemon
seahorse-daemon

Update Notifier
update-notifier --startup-delay=60

User folders update
xdg-user-dirs-gtk-update

Visual Assistance
gnome-at-visual -s

---

### Post by birdwin on 2009-05-27
Thanks a ton!

---

### Post by kpkeerthi on 2009-05-28
To restore the startup applications to defaults, delete the contents of ~/.config/autostart and reboot.

---

