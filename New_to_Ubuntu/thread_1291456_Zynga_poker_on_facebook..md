---
title: "Zynga poker on facebook."
date: 2009-10-14
forum: New to Ubuntu
---

### Post by mastermael on 2009-10-14
I have a facebook account and one of my friends invited me to play poker, when i try to access it no tables came up, and i was wondering if anyone could help me.

---

### Post by servicetech on 2009-10-14
Try switching user agent to Windows in firefox.

---

### Post by mastermael on 2009-10-15
> **servicetech said:**
> Try switching user agent to Windows in firefox.
can you explain how to do this?

---

### Post by BullHorn on 2009-10-17
I have the exact same problem and I have no idea what you just said.

---

### Post by Joeb454 on 2009-10-17
This is the only game I ever use on Facebook. I've yet to find anything that works (including changing the user agent).

From what I can gather it's something to do with flash, because it will partly load, then just not display any tables. If it's any consolation, it works fine if you're running windows in virtual box ;)

---

### Post by BullHorn on 2009-10-17
I've tried the User Agent Switcher but had no success. Any more ideas?

---

### Post by BullHorn on 2009-10-17
Forgive the double-post but I would like to add that I have more problems with Flash. I can't pause/play/change-volume/etc in videos on youtube as well... It's got to be a related Flash issue.

---

### Post by Joeb454 on 2009-10-17
> **BullHorn said:**
> Forgive the double-post but I would like to add that I have more problems with Flash. I can't pause/play/change-volume/etc in videos on youtube as well... It's got to be a related Flash issue.

Are you running Ubuntu 9.04 (Jaunty) or 9.10 (Karmic)? I know there's still some small issues such as that in Karmic, however I had no issues in Jaunty with flash

---

### Post by BullHorn on 2009-10-17
I'm on Jaunty 9.04 but don't mind that post... Tinkering for an hour got the issue solved. I found the sticky with the 5 steps to installing everything needed for playing multimedia and after trying everything, the last solution worked (Where I apparently uninstalled everything flash-related and then used the libflashplugin.so from the Adobe site).

Regarding Zynga Poker, same issue persists...

---

### Post by squiddy on 2009-11-01
use flash player v,9 instead of v.10

download v.9 [http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/licensing/linux/install_flash_player_9_linux.tar.gz)

extract, and sudo cp libflashplayer.so /usr/lib/mozilla/plugins

---

### Post by c0rrupt0r on 2009-12-21
I have been trying to figure this out for a few months now and I finely crossed a web browser that works for the most part. Arora Web Browser was very easy to install and right away it worked with no installing of any flash or anything. the only down fall is while in the tables and so on in zynga poker it flickers the screen off and on but it surely fully worked for me.

To install this web browser you can simply go to synaptic package manager and do a search for it in there.

To note: I am running Ubuntu 9.10 Karmic

---

### Post by anand_30 on 2009-12-29
I also had the same problem and finally adobe has the solution now.Just go to adobe website and download flash player 10.1 plugin and install it using synaptic package manager and you are done.
I can play poker now using firefox.
Hope this helps.

---

### Post by LuisGMarine on 2009-12-29
+1 for the post above me.

I was having problems with many games that are through Facebook that are generally flash based.  What I did to fix this was removed whatever flash I had on my system.  You can do so by opening up the Ubuntu Software Center and searching for "Flash" and remove everything that comes up that you have installed on your system.

After you do that just head over to the adobe.com website and download the .deb for Ubuntu 8.04+.  Just double-click it to install the .deb and make sure all your browsers are closed.

---

