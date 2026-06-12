---
title: "Digital camera is plugged but window does not pop up on screen as is usual"
date: 2009-07-07
forum: New to Ubuntu
---

### Post by hanzj on 2009-07-07
[COLOR=#204A87]**[SIZE=3][/SIZE]**[/COLOR]I've plugged in my digital camera to the usb cable but why isn't the window popping up on my screen, as it usually does?

---

### Post by OzzmanNT on 2009-07-07
Open any file browser window and click on Edit then Preferences. Check out the tab labeled "Media."

Hope this helps. Defaults are posted below.

[IMG]http://lh6.ggpht.com/_86Fhv_5TTr4/SlLwQkNVlwI/AAAAAAAAAcM/F1AmtUPko1E/s400/Screenshot-File%20Management%20Preferences.png[/IMG]

---

### Post by hanzj on 2009-07-07
Thanks. "Photos" was set to "Open folder". I changed it to "Ask what to do". I then got the Window, where I then put in "Open Folder".

It works now, but I'm wondering: Why did I have to undo and then re-do?

---

### Post by The Cog on 2009-07-07
Maybe due to this bug?

[http://ubuntuforums.org/showpost.php?p=7205851&postcount=4](http://ubuntuforums.org/showpost.php?p=7205851&postcount=4)

---

### Post by hanzj on 2009-07-24
I had the option to "Ask what to do" but it won't give me a pop-up screen! I've even tried to put it to "Open folder" and then back to "Ask what to do", but nothing works.

What's going on?

---

### Post by hanzj on 2009-07-24
Cog, I've tried the workaround you suggested at [http://ubuntuforums.org/showpost.php?p=7205851&postcount=4](http://ubuntuforums.org/showpost.php?p=7205851&postcount=4)

>  			 				sudo killall gvfs-gphoto2-volume-monitor 			 		

But it doesn't work.

---

