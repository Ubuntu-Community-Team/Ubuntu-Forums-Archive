---
title: "NetworkManager seems to have disappeared completely"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by RedshiftNova on 2009-07-23
As a learning project, I fiddled around with giving my laptop a static IP by editing the /etc/network/interfaces file through the terminal.  Worked perfectly once I had it set up, and then yesterday I got an error window telling me something about Network Manager...and to my great shame, I didn't actually read the entire thing and instead just clicked &quot;Okay&quot; and continued browsing the internet.  Now, I can't get the nm-applet icon to show up in my system tray.  Without that I can't gain access to my wireless network, and even plugging in a physical cable does nothing.  I tried reversing the changes I made to the /etc/network/interfaces file and rebooting, but no go.  I also restarted networking a couple times using the &quot;sudo /etc/init.d/networking restart&quot; command.  

My current theory is I somehow broke NetworkManager and need to reinstall it.  Any help anyone can give would be awesome.  Thank you.

---

### Post by Matthew Spinks on 2009-07-23
well I'm pretty new at ubuntu as well, but if anything else you can always go to the Synaptic Package Manager and search network-manager-gnome and mark for reinstallation.

---

### Post by wojox on 2009-07-23
Right click panel

+Add to panel

Scroll down to Notification Area

---

### Post by raymondh on 2009-07-23
synaptic ... see if you need to re-install gnome network manager and its' dependencies. If not, add to panel.

---

