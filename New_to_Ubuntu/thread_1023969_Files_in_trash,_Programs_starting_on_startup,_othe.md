---
title: "Files in trash, Programs starting on startup, other misc problems."
date: 2008-12-28
forum: New to Ubuntu
---

### Post by I[AM]SMRT on 2008-12-28
1. In my /home/.trash-0 folder I have four files (Dz6.003, Dz7.004, Dz8.005 and Dz9.006) that are ~1 gb each. Are these important? Can I delete them?

2. For some reason my banshee media player starts every time I startup Ubuntu even though it's not in my startup programs in my sessions. What can I do about it?

3. I'm using the main menu button on my taskbar, I notice that when I first try to open it up it takes a few clicks before it recognizes that I'm clicking. Anyone else have this problem?

-SMRT

---

### Post by ajgreeny on 2008-12-28
I just looked on my machine (8.04.1) and I don't have a*  /home/.trash-0* folder in my home folder so I'm a bit baffled about that.  Perhaps you can just delete the folder by holding down shift so as not to send it to trash again, but I would wait until you hear from others about that.  You could also restore the files to a folder in your home and see what is in them, if possible, though it may not be easy to read them being that size, unless they are video files of some sort, or archives of something.

banshee probably starts up at boot time because you left it running when you shut down somewhen, and your gdm starts up the last session by default.  You can probably stop it by happening by firstly making sure everything is shutdown properly.  Now in your */home/.nautilus* folder delete the *saved-session-xyxyxyxy* files and then go to *System > Preferences > Sessions* and in the *Session Options* tab click on the *Remember Currently Running Applications* button, and also the *Automatically remember running applications when logging out*.  Now log out and back in, (hopefully nothing extra will start up this time) go to the Sessions utility again and this time uncheck the Automatically remember running applications when logging out button.  This has certainly worked for me a few times when I have messed up my session options in the past.

The menu problem, which I assume must be the gnome main menu rather than the menubar, on my machine takes a couple of seconds to open the first time I use it in a session but after that it is almost immediate.  I have edited the menu quite a bit and wonder if that has anything to do with it, but it's not a major problem to me so I've never bothered to look further.  Perhaps you also need to click once and wait two secs to see if it appears.

---

### Post by I[AM]SMRT on 2008-12-29
1. I'm dualbooting XP if that means anything.

2. I tried that...about 30+ times and now I have a nautilus session starting up with my banshee session. This is making me 
start to hate Ubuntu.

EDIT: Tried uninstalling banshee, deleting all of its config files and reinstalling but that didn't work either.
EDIT: After time #50 it worked, not sure why and I'm not going to ask questions.

3. Yea, you're right it just takes a little while to respond to that first click.

---

### Post by cariboo on 2008-12-29
I would suggest closing all programs you have running and the go to System-->Preferences-->Sessions-->Options and make sure that Automatically remember running applications is unchecked. Then log out adn log back in again to see if anything has changed.

Jim

---

