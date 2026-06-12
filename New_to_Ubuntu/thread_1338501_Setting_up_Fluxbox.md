---
title: "Setting up Fluxbox"
date: 2009-11-26
forum: New to Ubuntu
---

### Post by EmperorWilli on 2009-11-26
Hey, 
I just decided to replace the Windows Hdd of my eeePC and to install Linux instead. A friend of mine told me to use the Ubuntu Netbook Remix as it's all perfectly configured just for the hardware and so far I'm really comfortable with it.
The only problem I had was that I felt a little strange with this Gnome interface and therefore installed Fluxbox. As far I managed to set the most things up just as I want them to be but there are still a few things that bite me.
- Is there for example a possibility to add something like a "Alt-Tab" - Menu to Navigate through the different windows?
- Where are these popups configured that show up when new network connections are made or somebody msgs me.. I think they look pretty cool but they apear somewhere on the top right corner in  the middle of the screen and that's kinda odd.. additionally they disappear whilst I'm with my mouse over them and reappear when I leave.. is there a way to move them or turn this off?
- Are there any volume managers for the toolbar out there (I tried the one of gnome but it doesn't really fit) or do I have to use one for the slit.
- Which scripts do I have to call when I want to Lock the Screen or Change the User... I already found the two for hibernate and standby (eventhough i have to enter my password when i want to do so... )

Greetings, Tobias

---

### Post by scorp123 on 2009-11-26
You could customize Fluxbox a bit to make it more "comfortable". Want to try that?

There should be a folder "**.fluxbox**" underneath your home directory (please note the dot at the beginning of its name). Files and folders with a dot at the beginning of their names are usually hidden in Nautilus, so to see them in your file manager you'll need to press **Ctrl+H** ...

So in that "**.fluxbox**" folder you should see these files:
```

~/.fluxbox > ls -al
total 144
drwxr-xr-x  5 zoe zoe  4096 2009-11-20 11:10 .
drwx------ 82 zoe zoe 20480 2009-11-26 19:21 ..
-rw-r--r--  1 zoe zoe    71 2009-09-23 00:12 apps
drwxr-xr-x  2 zoe zoe  4096 2009-02-16 08:57 backgrounds
-rw-r--r--  1 zoe zoe  3836 2009-11-20 11:09 init
-rw-r--r--  1 zoe zoe   945 2009-09-23 00:12 keys
-rw-r--r--  1 zoe zoe    62 2009-11-20 11:10 lastwallpaper
-rw-r--r--  1 zoe zoe    66 2009-02-16 08:57 menu
-rw-r--r--  1 zoe zoe    89 2009-09-23 00:12 overlay
drwxr-xr-x  2 zoe zoe  4096 2009-02-16 08:57 pixmaps
-rw-r--r--  1 zoe zoe     0 2009-11-20 11:12 slitlist
-rw-r--r--  1 zoe zoe  1279 2009-11-20 11:10 **[COLOR="Red"]startup[/COLOR]**
drwxr-xr-x 17 zoe zoe  4096 2009-02-16 08:58 styles
-rw-r--r--  1 zoe zoe   168 2009-09-23 00:12 windowmenu
```

The one I'd customize is highlighted in red: **~/.fluxbox/startup**

That one can do a lot of things for you and make life with Fluxbox more attractive. I'm posting my "**~/.fluxbox/startup**" file here and I've added comments so you can understand what each line does (and therefore decide if you want to leave it away or not):

```
# fluxbox startup-script:
#
# Lines starting with a '#' are comments and this being ignored.

# Eye-candy:
#
# The following line activates the "X Composition Manager"
# so we get a bit of eye candy:
# -drop shadows
# -smooth animations
# -smooth window transitions
# -transparency effects
#
# Despite these few minor effects Fluxbox will remain
# snappy and fast. Those few minor effects are nowhere
# as heavy on the system as Compiz and its effects-orgies ...
#
# This package needs to be installed separately
# as it is likely not installed per default:
#
# sudo apt-get install xcompmgr

xcompmgr -c -C -f -F &

# You can set your favourite wallpaper here if you don't want
# to do it from your style.
#
# fbsetbg -f /home/zoe/pictures/wallpaper.png
#
# This sets a darkslategray background

/usr/bin/fbsetroot -solid darkslategray

# This shows the fluxbox-splash-screen
# fbsetbg -C /usr/share/fluxbox/splash.jpg

# Other examples. Check man xset for details.
#
# Turn off beeps:
xset -b

#
# Increase the keyboard repeat-rate:
# xset r rate 195 35
#
# Your own fonts-dir:
# xset +fp "/home/zoe/.fonts"
#
# Your favourite mouse cursor:
# xsetroot -cursor_name right_ptr
#
# Change your keymap:
# xmodmap "/home/zoe/.Xmodmap"

# Applications you want to run with fluxbox.
# MAKE SURE THAT APPS THAT KEEP RUNNING HAVE AN ''&'' AT THE END.
#
# unclutter -idle 2 &
# wmnd &
# wmsmixer -w &
# idesk &

# Load the GNOME settings manager so
# the GNOME applications that might get
# used from time to time (Firefox, Pidgin, Exaile ...)
# don't look ugly and get their proper styles
# and themes loaded ...

gnome-settings-daemon &

# Load the GNOME power manager so resume & suspend
# settings work just as they would in GNOME

gnome-power-manager &

# Load the volume manager so GNOME applications
# get their sound levels right as they would in GNOME

gnome-volume-control-applet &

# Load the Network-Manager Applet so we can
# manage networks, WiFi etc. just as we would
# be able to on GNOME

nm-applet &

# Load the "parcellite" clipboard manager ...
# Not shipped per default:
# sudo apt-get install parcellite

parcellite &

# Load the GNOME bluetooth stuff so we
# can work with Bluetooth just as we would
# be able to on GNOME

bluetooth-applet &

# And last but not least we start fluxbox.
# Because it is the last app you have to run it with ''exec'' before it.

exec /usr/bin/fluxbox
```

With above lines added Fluxbox is still very very very fast and yet all my GNOME applications look correct (they get the theme they are supposed to have) and I even get a few minimum desktop "bling bling" effects that are not too heavy on the system.

.
.
.

---

### Post by tweaksource on 2010-01-22
> **EmperorWilli said:**
> Hey, 

- Is there for example a possibility to add something like a "Alt-Tab" - Menu to Navigate through the different windows?


~/.fluxbox/keys

> 

- Are there any volume managers for the toolbar out there (I tried the one of gnome but it doesn't really fit) or do I have to use one for the slit.


I used to use wmix in the slit. Now I just bind gamix (or alsa-mixer, or pavucontrol, or whatever) to a key combo so i can call it up quickly.

> 
- Which scripts do I have to call when I want to Lock the Screen or Change the User... I already found the two for hibernate and standby (eventhough i have to enter my password when i want to do so... )



I use xlockmore to lock the screen. xscreensaver works too.

To change users? Ctrl+Alt+Backspace.

---

