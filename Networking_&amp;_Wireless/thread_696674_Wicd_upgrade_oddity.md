---
title: "Wicd upgrade oddity"
date: 2008-02-14
forum: Networking &amp; Wireless
---

### Post by bobterri on 2008-02-14
I'm running Gutsy on a Dell Inspiron laptop with a  Intel PRO/Wireless 2200BG.  A while back I had dumped network-manager for Wicd and was pleased as can be.  However, yesterday I upgraded Wicd and now when I boot my laptop the Wicd icon shows I'm connected and all seems fine but after five minutes the icon shows I'm not connected (though, in fact, I still am connected).  Also, I can't bring up Wicd in the "applications" menu.  Anybody else had this problem?  Any ideas or solutions?

---

### Post by dca on 2008-02-14
Does the /var/log/messages file indicate any anomolies anomilies anything strange around the time WICD exhibits these shenanigans?

---

### Post by bobterri on 2008-02-14
No, not that I could find.

---

### Post by dca on 2008-02-14
If you right-click on the applications menu panel and click 'edit menus'.  It should bring up your menu layout.  Under the internet one does it show WICD without a check-mark?  What I did back with Ubuntu 6.10 (the nm included w/ 7.04 & 7.10 seem better and more solid, knock on wood) is intall WICD and set the session to open the WICD tray on the panel (which is on their webpage to do it) but also add the WICD app itself right next to it on the tray so I have two icons:  the app itself and the monitoring agent.  
 
From what it sounds like I can't tell if it's a glitch within WICD or system specific, hopefully, someone can help us out with it...
 
There's a forum for WICD, also:
[http://wicd.sourceforge.net/phpbb/](http://wicd.sourceforge.net/phpbb/)
(click General, then Troubleshooting)
 
 
...also is Beryl running???
 
...or did you change themes???

---

### Post by bobterri on 2008-02-14
Yes, Wicd does have checkmark in the menu layout.

It was working perfectly before the upgrade.  It must be something with the upgrade.  I followed the directions at the Wicd website to start the Wicd tray on the panel. 

So, if anybody has any ideas?  Thanks DCA for trying.  I'll check the Wicd forum too!

---

### Post by bobterri on 2008-02-16
Just an update.

It appears that the icon behaves properly (showing the proper status) when I use wep encryption, no encryption and a wired lan connection.  The only time the icon says I'm offline when I'm actually online is when I'm using wpa encryption.  

I have posted at the wicd forum but no one has answered it.  

I guess I have three options unless someone knows of a fix:

1) Live with it.  After all, it is connected.

2) Go back to 1.3.1.

3) Use NM.  BTW, the reason I stopped using NM was because often (70%+) on boot NM would logon and then about 15 seconds later it would drop the wireless signal (didn't matter which access point).  I would have to reboot and then it worked perfectly.  Wicd doesn't do this. 1.3.1 worked like a charm.  So much for upgrading, huh?

---

### Post by Whiffle on 2008-02-16
4)  Don't use a status icon. 

I don't have one...it doesn't really bug me.  I do have a wireless readout in my conky though, although its not dead on all the time (tells me i'm connected when I'm not, I think thats because the drivers like to associate even if there is no connection).

---

### Post by imdano on 2008-02-16
Run /opt/wicd/tray.py from a console, and watch the output for an error messages around the time you lose the icon.

---

### Post by bobterri on 2008-02-20
Imdano, I tried that and it didn't show anything.  

Actually, I went back to the prior release (1.3.1) and it's working perfectly.  You know the old adage, "If it works, don't fix it."

---

