---
title: "After Remote connection no wallpaper"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2009-04-04
I had set up my remote connection to disable the wallpaper when connected. I have since then disconnected. Restarted my computer. Disabled that option. And I still do not have a wallpaper. 
It shows the color wallpaper instead.

---

### Post by joshrobinson on 2009-04-04
Have you tried using remote connect to log back in while the option is disabled?  It should come back then.

There was a bug for this, but it claims to be fixed.  Is your system fully updated?

---

### Post by SpenceMakesSense on 2009-04-04
yes my computer is fully updated. And reconnecting doesn't restore it either.


Is it fixed for ubuntu 8.10 or some other version?

---

### Post by SpenceMakesSense on 2009-04-04
bump

---

### Post by SpenceMakesSense on 2009-04-05
bum p

---

### Post by SpenceMakesSense on 2009-04-06
is there no hope?

---

### Post by mokolo on 2009-04-07
I have the same issue and my Ubuntu 8.10 is fully updated.

Anyone can help?

---

### Post by mokolo on 2009-04-08
Activate the option to disable the wallpaper on connection. Then connect remotely to the PC and close the connection after a few seconds. After these steps your wallpaper should be back, it worked for me! :)

---

### Post by skathrein on 2009-04-10
Same problem for me, but it does it even when there isn't a remote connection.  It seemed to happen after the latest update but I can't remember what was included in that update.  It's weird because when I boot up it will show the wallpaper for a second or so but once the full screen (ie, panel and icons) pop up, the wallpaper disappears and I'm left with just a solid color.  Any help???

---

### Post by skathrein on 2009-04-10
OK, I researched a little more and found an answer [here]("http://ubuntuforums.org/archive/index.php/t-1020524.html").  If someone else finds this problem, here's the fix/workaround:
Go to System Tools-->Configuration Editor
(If Configuration Editor isn't there, add it by going to System-->Preferences-->Main Menu)
Once in Configuration Editor, go to apps-->nautilus-->preferences.  Once there, uncheck show_desktop.  Then you can exit the editor and you might have to restart your computer.  **The big problem is that this will also get rid of all icons on your desktop.  For me, since I have all my icons in the panel, it's not a big deal and I'd rather have the wallpaper.

---

