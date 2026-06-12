---
title: "Network manager latest update- Can't launch any applications"
date: 2008-09-30
forum: Networking &amp; Wireless
---

### Post by myotis on 2008-09-30
I have just allowed network manager (0.7 on Hardy)to auto-update, which then required a reboot.

On rebooting I got two "Panel encountered an error" error, s one for

OAFIID: Gnome_fastUserSwitchApplet and

OAFIID: Gnome_mixer_applet.

With an option to delete the files. Searching the forum here suggested just deleting them and then reinstating with sudo aptitude install gnome-applets, which I did, but not until later, because at that stage nothing worked. 

Having deleted these applets, I now cannot launch any applications, not even terminal.

However, I am connecting through a wireless connection, which Network manager is still seeing OK. 

Switching to a wired connection, initiated a second Network Manager update, and I also re-instated the applets. Everything seemed to work, so I tried the wireless connection again, and it was just the same - no applications will launch.

Is this just a Network Manager bug, and I need to patiently wait for a fix, or is there something I can maybe do to get it working.

Is there any advice about not updating with a wireless connection as this is the 2nd time this has happened. Upgrade via wireless, broken wireless, connect with wire, immediate 2nd auto-update, and wireless working again. Except this time, the 2nd update hasn't fixed it.

Thanks,

Graham

---

### Post by myotis on 2008-09-30
Well, to reply to myself, and update has fixed it. 

Graham

---

