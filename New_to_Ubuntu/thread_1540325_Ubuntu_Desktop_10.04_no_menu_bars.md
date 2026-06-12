---
title: "Ubuntu Desktop 10.04 no menu bars"
date: 2010-07-27
forum: New to Ubuntu
---

### Post by b.bill.p on 2010-07-27
No menu bars appear at the top of bottom of the screen.  The system boots automatically to my desktop screen that is blank, no icons.  I built my own command line icons using right click create launcher.  Alt-F1 brings up system, file and App menus momentarily so I can execute built-in commands but there is not menu bar for Mail, Clock, Apps, Shutdown, Trash Can.

The installation was from a new ISO CD image to a Dell Optiplex.  Installation was clean and the first time used after booting the new installation displayed a very nice desktop with menus and Icons for standard apps.  I system shutdown through the SYSTEM menu was performed but the next and all subsequent boots just bring up a blank orange/purple desktop so I eventually learned to make my own icons to run Firefox and build up some folders for various notes otherwise no  crashes, everything I run seems to work.

So my question is: how do I restore the top and bottom menu bars???  Everything is stock, what ever the stock GUI is called, its what is running ....

NOTE: the only advantage is that there is NO Paging so this runs pretty fast.

---

### Post by typal on 2010-07-27
According to, [http://ma65p.wordpress.com/2008/06/23/how-to-restore-the-original-panel-and-menu-bar-in-ubuntu/](http://ma65p.wordpress.com/2008/06/23/how-to-restore-the-original-panel-and-menu-bar-in-ubuntu/), this should replace both without having to re-log.
```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by Goodseeker on 2010-07-27
Based on my experience with a different Ubuntu version on a different machine:

if nothing else works, I'd  try to change the screen resolution, perhaps one tick lower than the maximum allowed by the hardware.

---

### Post by b.bill.p on 2010-07-27
Thanks for the code but what does it do? Will I loose the ICONs/launchers that I've built onto my desktop?  

The suggestion to change my screen resolution, how is that done ????  I don't see anything for video or audio adjustments ....however I am using thisUbuntu here and the Creative Soundblaster SB16 is working.  Many thanks .... Bill

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

---

### Post by b.bill.p on 2010-07-28
Thanks for the advice, I tried changing the screen resolution and the bottom bar appeared then I got brave and ran the code then rebooted ..... THANKS, the code worked and all is well. Right now I finished running Software UPdate manager and see 240 files downloading and updating the system ....  just like WinXP !!

.... Bill

---

### Post by pithdillinja on 2010-07-28
Just like winxp indeed - but only a million times awesome-er, because it's ubuntu. And on top of that, it won't restart your computer without your permission either (which windows xp tends to do by default)

---

