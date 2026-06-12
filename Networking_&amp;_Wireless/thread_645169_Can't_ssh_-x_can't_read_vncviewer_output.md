---
title: "Can't ssh -x can't read vncviewer output"
date: 2007-12-19
forum: Networking &amp; Wireless
---

### Post by volkswagner on 2007-12-19
I am trying to remotely administer my mythbuntu 7.10 box.  The machine is connected to a crt tv via s-video, onboard ati 1250.  I am trying to get a GUI administration remotely because the desktop is not readable on the tv, no shocker there.  Currently at 640 x 480 closet to readable.

When I connect with my laptop running ubuntu 7.10

```
ssh -x eric@192.168.1.107
```


```
eric@FamilyRoom:~$ synaptic
```

I get this in return

(synaptic:6413): Gtk-WARNING **: cannot open display:  
eric@FamilyRoom:~$ 

so then try vncserver on the mythbuntu box and vncviewer on my laptop.  With the default settings my forwarded screen is not readable.  It appears as 5 images of my host screen at about ten percent of the size, these are displayed in a horizontal line across my viewer screen.  They also are full of horizontal lines creating an unreadable image.  I have in the past tried varous different screen resolutions when calling the vncserver with no change in outcome.

here is /home/eric/.vnc/FamilyRoom:1.log

Xvnc Free Edition 4.1.1
Copyright (C) 2002-2005 RealVNC Ltd.
See [http://www.realvnc.com](http://www.realvnc.com) for information on VNC.
Underlying X server release 70000000, The X.Org Foundation


Wed Dec 19 18:39:43 2007
 vncext:      VNC extension running!
 vncext:      Listening for VNC connections on port 5901
 vncext:      created VNC server for screen 0
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!
/home/eric/.vnc/xstartup: 12: twm: not found
X Error of failed request:  BadLength (poly request too large or internal Xlib length error)
  Major opcode of failed request:  134 (VNC-EXTENSION)
  Minor opcode of failed request:  1 ()
  Serial number of failed request:  65
  Current serial number in output stream:  65

So I am asking for help to get the x session to forward or a readable vnc output.
Please understand I am a of limited experience.  If you think I would have better luck with another vnc app.  please give details ie get this  "apt-get install somthing better"

Thanks in advance

---

### Post by volkswagner on 2007-12-19
Some additional info which may help.  This is the contents of the servers /.vnc/xstartup file

#!/bin/sh

# Uncomment the following two lines for normal desktop:
# unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc

[ -x /etc/vnc/xstartup ] && exec /etc/vnc/xstartup
[ -r $HOME/.Xresources ] && xrdb $HOME/.Xresources
xsetroot -solid grey
vncconfig -iconic &
xterm -geometry 80x24+10+10 -ls -title "$VNCDESKTOP Desktop" &
twm &

---

### Post by volkswagner on 2007-12-20
bump

---

### Post by stalker145 on 2007-12-20
> **volkswagner said:**
> ```
ssh -x eric@192.168.1.107
```


```
eric@FamilyRoom:~$ synaptic
```

I get this in return

(synaptic:6413): Gtk-WARNING **: cannot open display:  
eric@FamilyRoom:~$ 

So I am asking for help to get the x session to forward or a readable vnc output.
Please understand I am a of limited experience.  If you think I would have better luck with another vnc app.  please give details ie get this  "apt-get install somthing better"

Thanks in advance

You've almost got it there. Using the small x as you are there is actually disabling X11 forwarding. What you need to do is use an X (upper case) thusly ```
ssh -X eric@192.168.1.107 gksudo synaptic
```

I haven't figured out how to forward a program from the remote to the local screen once you're already SSH'd in yet, but I can assure you that combining your two commands as shows will get you what you want.

You can also just ssh in (without the x or anything else) and run aptitude to get your new programs and update. It's a bit quicker but it's also not GUI (which I kinda like the GUI).

Anyway, check back if you need more. I'm sorry I can't help with VNC.

---

### Post by volkswagner on 2007-12-20
Thank you that worked.

I would still like to get vnc working.

---

### Post by timcredible on 2007-12-20
if you don't have firewalls in the way, don't use vnc, use xdm (the same thing that you use when you're on the console).  i have an article [here]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27") about it.

---

