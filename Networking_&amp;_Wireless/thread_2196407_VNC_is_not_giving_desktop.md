---
title: "VNC is not giving desktop"
date: 2013-12-29
forum: Networking &amp; Wireless
---

### Post by xendistar2 on 2013-12-29
I am trying to setup a VNC connection between two linux PC's. I have a fresh install of Lubuntu 13.10 on the PC that I have installed the tightvnc server on and I am using Remmina on the client PC (xubuntu 13.10) to connect to the vnc server. I have started the VNC server on the lubuntu PC with the following command:

vncserver -geometry 1024x768 -depth24 :1

The vnc server replie's telling me what the desktop is called and that a new logfile was situated.

Now when I try to connect to the VNC server via Remmina on the client it connects but all I get is a light grey window, no desktop or icon.

Any thoughts?

---

### Post by Toz on 2013-12-29
> and that a new logfile was situated.
What does this log file say?

Also, what does your ~/.vnc/xstartup file look like? See: [https://help.ubuntu.com/community/VNC/Servers#Customising_your_session]("https://help.ubuntu.com/community/VNC/Servers#Customising_your_session") - there should be some reference to openbox there since lubuntu, I believe, uses openbox as its window manager.

---

### Post by steeldriver on 2013-12-29
^^^ agreed, sounds like you have the default ~/.vnc/xstartup file (which just sets the X root window to plain gray and starts a default WM)

---

### Post by xendistar2 on 2013-12-29
Below is a screen grab of the VNC log file

[ATTACH=CONFIG]249003[/ATTACH]

Here is what the xstartup file says

#!/bin/sh


xrdb sHOME/.Xresources
xsetroot -solid grey
#x-terminal-emulator -geometery 80x24+10+10 -ls -title "SVNDESKTOP Desktop" &
#x-window-manager &
# Fix to make gnome work
export XKL_XMODMAP_DISABLE=1
/etc/X11/Xsession

Is it just simply a case of un hashing x-window-manager line and adding openbox??

---

### Post by steeldriver on 2013-12-29
To get the regular lxde look you probably want to run 'startlxde' rather than a plain openbox-session - here is a fairly generic xstartup file that I use at the moment, basically you set your preferred session using the MODE variable at the top, and it will try to start it (falling back to the default gray root window + xterm if the chosen session is unavailable) **DISCLAIMER I have no idea whether this is a "good" way to do it**, I've seen so many variants including things like ck-launch-session, dbus-launch etc. etc.

```

#!/bin/sh

MODE="lxde"

#Uncommment this line if using Gnome and your keyboard mappings are incorrect.
#export XKL_XMODMAP_DISABLE=1

# Load X resources (if any)
[ -r "$HOME/.Xresources" ] && xrdb "$HOME/.Xresources"

case $MODE in

xfce4)
        if which startxfce4 > /dev/null; then
                exec startxfce4
        fi
        ;;

lxde)
        if which startlxde > /dev/null; then
                exec startlxde
        fi
        ;;

openbox)
        if which openbox-session > /dev/null; then
                exec openbox-session
        fi
        ;;

*)
        echo "Falling back to default minimal X session"
    ;;

esac

xsetroot -solid "#DAB082"
x-terminal-emulator -geometry "80x24+10+10" -ls -title " Desktop" &
x-window-manager &

```

EDIT: note you will need to kill and restart the vncserver for it to take effect (not just disconnect / reconnect the client) e.g.

```

vncserver -kill :1

vncserver -geometry 1024x768 -depth24 :1

```

---

### Post by xendistar2 on 2013-12-30
Thanks for the pointer, I simply added

startlxde & 

to the bottom of my start up script and I now have the lubuntu desktop via vnc.

Thanks for the help guys

---

### Post by Kory_Davids on 2014-01-26
I am having the same issue,  Gray screen. That is all i get and nothing else.

```



#!/bin/sh


# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
exec ck-launch-session gnome-session


[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
x-terminal-emulator -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
x-window-manager &
gnome-session &
```

---

