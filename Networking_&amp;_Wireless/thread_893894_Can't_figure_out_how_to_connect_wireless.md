---
title: "Can't figure out how to connect wireless"
date: 2008-08-18
forum: Networking &amp; Wireless
---

### Post by lukethered on 2008-08-18
I regretably did some customizations to my panel, and deleted the one that had the notifications: battery life and network manager, the icon I clicked on to connect to the wireless internet.  After searching for a few minutes, I learned that I only needed to add the notificatinos to the panel in order to bring back the network icon.  However, it disappeared, and now I don't see any way to connect to wireless.
Now, I need a little bit of help.  Rather than just figuring out how to reconnect, I would also like to increase my knowledge about this a little.  Any help would be greatly appreciated.  Thanks

---

### Post by mikewhatever on 2008-08-18
Try: alt+f2, nm-applet.

---

### Post by sefs on 2008-08-18
Systems -> Preferences -> Sessions 

Scroll thru the list of auto started apps and see if network manager is one of them, and if so, is it checked to auto start with your user session.

---

### Post by lukethered on 2008-08-18
> **mikewhatever said:**
> Try: alt+f2, nm-applet.

Didn't do anything, so I ran it in a terminal.
/home/luke/.themes/greenome-0.3/gtk-2.0/gtkrc:1387: Background image options specified without filename

switched themes and it worked just fine.  For some reason, it seems like it just wasn't working with the theme I was running.  Thanks.

---

