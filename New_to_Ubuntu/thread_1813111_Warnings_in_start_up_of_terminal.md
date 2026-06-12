---
title: "Warnings in start up of terminal"
date: 2011-07-27
forum: New to Ubuntu
---

### Post by nishantgoswami on 2011-07-27
hi guys...

i am new in ubuntu...i did try to install NS 2.33 in my system..but now when ever i open my Terminal it shows me following in the terminal...
so what can i do to resolve it..?


declare -x COLORTERM="gnome-terminal"
declare -x DBUS_SESSION_BUS_ADDRESS="unix:abstract=/tmp/dbus-8ZYGewtPcv,guid=318572cab484449fc0e856e04e2ff8ac"
declare -x DEFAULTS_PATH="/usr/share/gconf/gnome.default.path"
declare -x DESKTOP_SESSION="gnome"
declare -x DISPLAY=":0.0"
declare -x GDMSESSION="gnome"
declare -x GDM_KEYBOARD_LAYOUT="us"
declare -x GDM_LANG="en_US.utf8"
declare -x GNOME_DESKTOP_SESSION_ID="this-is-deprecated"
declare -x GNOME_KEYRING_CONTROL="/tmp/keyring-BNR4be"
declare -x GNOME_KEYRING_PID="1447"
declare -x GTK_MODULES="canberra-gtk-module"
declare -x HOME="/home/nishant"
declare -x LANG="en_US.utf8"
declare -x LIBGL_DRIVERS_PATH="/usr/lib/fglrx/dri"
declare -x LOGNAME="nishant"
declare -x MANDATORY_PATH="/usr/share/gconf/gnome.mandatory.path"
declare -x OLDPWD
declare -x ORBIT_SOCKETDIR="/tmp/orbit-nishant"
declare -x PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
declare -x PWD="/home/nishant"
declare -x SESSION_MANAGER="local/ubuntu:@/tmp/.ICE-unix/1465,unix/ubuntu:/tmp/.ICE-unix/1465"
declare -x SHELL="/bin/bash"
declare -x SHLVL="1"
declare -x SPEECHD_PORT="7560"
declare -x SSH_AGENT_PID="1501"
declare -x SSH_AUTH_SOCK="/tmp/keyring-BNR4be/ssh"
declare -x TERM="xterm"
declare -x USER="nishant"
declare -x USERNAME="nishant"
declare -x WINDOWID="75497476"
declare -x XAUTHORITY="/var/run/gdm/auth-for-nishant-OP0UXN/database"
declare -x XDG_CONFIG_DIRS="/etc/xdg/xdg-gnome:/etc/xdg"
declare -x XDG_DATA_DIRS="/usr/share/gnome:/usr/local/share/:/usr/share/"
declare -x XDG_SESSION_COOKIE="d4b8b577e321f970845a568b4d5dacd4-1311766700.117754-1799304277"
bash: 2.34/tcl8.4.18/unix:/home/nishant/ns-allinone-2.33/tk8.4.18/unix: No such file or directory

---

### Post by SoFl W on 2011-07-27
What is "NS"?  Network Simulator?  My first guess would be something in your ".bashrc" file.  Go into the terminal and rename the .bashrc file.  "mv .bashrc WAS.bashrc", exit and start up terminal again and see if you still get the information displayed.  If it is still displayed rename it back ".mv WAS.bashrc .bashrc"  Don't forget the period.

---

### Post by kerry_s on 2011-07-27
open your file manager, press ctrl+h, check your ".bashrc" file.

---

### Post by nishantgoswami on 2011-08-01
It has been solved...

i did edit .bashrc file... 

XGRAPH=/home/nishant/ns-allinone-2.33/bin:/home/nishant/ns-allinone-2.33/tcl8.4.18/unix:/home/nishant/ns-allinone-2.33/tk8.4.18/unix


this should be in one line...


Thank you guys...!!!

---

