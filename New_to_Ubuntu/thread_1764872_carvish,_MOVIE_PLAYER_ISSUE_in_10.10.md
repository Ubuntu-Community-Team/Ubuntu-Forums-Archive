---
title: "carvish, MOVIE PLAYER ISSUE in 10.10"
date: 2011-05-22
forum: New to Ubuntu
---

### Post by carvish on 2011-05-22
Hi all, I hope you can help me out,

I'm having conflict issues with any movie player that I install. Ever since I installed DEVEDE or BRASERO ( not sure which one is causing the problem), and had VLC or MOVIEPLAYER on my system, when I go to open my downloads folder or any other folder, instead of opening the file to view what's in there VLC or MOVIEPLAYER tries to play the folder. Usually resulting in an error or playing the first MP4 that it comes to. If I remove the player, I can open the folder and view its content.
I know it's not the os (Ubuntu 10.10)which is running superbly , is there a player that will play nicely with DEVEDE or BRASERO? Or a fix for VLC or MOVIEPLAYER? Can I open the terminal and type;
 Apt-get play nicely? I really like DEVEDE, it works well and easy to use.

---

### Post by ajgreeny on 2011-05-22
Open nautilus with Alt+F2 if you can not do it from a launcher.  Once it's open, right click on any folder and click on "**Open with- Other application**.." and then choose nautilus/file manager or however it is described.  Make sure the "Remember this application for folders" or similar comment is selected.

---

### Post by mc4man on 2011-05-22
> "Remember this application for folders" or similar comment is selected. 
If you are updated as far as nautilus that option will no longer be there. Was removed recently to help prevent the problem you're having, but the update doesn't correct if already there.

If just choosing open folder doesn't fix then  go to 
home folder > (view > show hidden files) > .local/share/applications
open mimeapps.list and delete this line entirely and backspace
 
inode/directory=
or if you rather, then edit to just this
```
inode/directory=nautilus-folder-handler.desktop;
```

---

### Post by carvish on 2011-05-22
I reinstalled VLC and it's doing the same thing, so I pressed alt/f2, typed in nautilus, right clicked on my downloads folder, no Nautilus there to choose from.
Tried to open "my folder", I was able to navigate to the movie I wanted to watch, how ever,afterwards, when I click on "places" then any folder I still get that movie thing happening, and there is no "home folder" to click on except the one under "places"

---

### Post by fritz269 on 2011-05-22
> **carvish said:**
> I reinstalled VLC and it's doing the same thing, so I pressed alt/f2, typed in nautilus, right clicked on my downloads folder, no Nautilus there to choose from.
nautilus is what you open when you press ALT + F2

---

### Post by mc4man on 2011-05-22
open a terminal and either of these 2 commands
```
 gedit ~/.local/share/applications/mimeapps.list
```

or
```
nautilus .local/share/applications/
```

Edit the mimeapps.list file or if using the latter command you can edit it or just outright delete it.

---

### Post by carvish on 2011-05-23
Thanks mc4man, did the latter command in the terminal, held my breath and deleted the one marked "mimeapps.list file". Everything seems to be good now. Thank you all for the help. Now there did that "solved" button go?

---

### Post by Ionic-user on 2012-05-15
[COLOR=black]B[/COLOR]elated thanks to mc4man for guiding this newbie through the system, allowing me to edit the mime.apps.list and substitute "vlc.desktop;" for the totem thing in the line concerning video. Worked a charm.

---

### Post by oldos2er on 2012-05-15
Old thread closed.

---

