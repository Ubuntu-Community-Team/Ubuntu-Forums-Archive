---
title: "Cannot access home from Places menu"
date: 2009-08-06
forum: New to Ubuntu
---

### Post by P235 on 2009-08-06
Greetings, I have been using Ubuntu Linux for a while now and like it a great deal.  I recently upgraded from 8.04.1 to 9.04 by keeping my /home partition and formatting my root.  The installation was quick and my wireless worked without any need of intervention on my part.  I wished I could say I shed a tear at that moment, but I had no tears to spare at the time!

Despite this though, I have a relatively small issue about my 'Places' drop down box menu.  When I click 'Places', click on the selections for 'Home Folder', 'Desktop', 'Documents', etc. I receive the following notice:
> 
Could not open location 'file:///home/<my user name>'

Failed to execute child process "feh" (No such file or directory)

I am sure this is a small fix in the scheme of things (hopefully the only one!), but I have had no luck in solving it on my own.  Any guidance is very much appreciated.

---

### Post by drs305 on 2009-08-06
Open nautilus, right click on your home folder, select Open With, Other Application, and choose "File browser", Open.  See if that fixes things.

---

### Post by P235 on 2009-08-06
I see, for whatever reason the default program to open folders has become 'feh', an image viewing program.  I have done as you suggested, but the 'feh' program still sits on top of the list so it is the first program used to try to open folders.  I have yet to find a way to shift the File browser up the priority list so that it is used instead of 'feh'.

---

### Post by drs305 on 2009-08-06
> **P235 said:**
> I see, for whatever reason the default program to open folders has become 'feh', an image viewing program.  I have done as you suggested, but the 'feh' program still sits on top of the list so it is the first program used to try to open folders.  I have yet to find a way to shift the File browser up the priority list so that it is used instead of 'feh'.

Okay, in that case try to repeat the above, and when you select "Open Folder" at the bottom open "Use custom command" and type in: nautilus.

---

### Post by P235 on 2009-08-06
Hi dr, unforunately the result was the same as the 'File browser'.  This is odd in the sense that I can open folders on the desktop normally, but the 'Places' drop down menu is the only place where the 'feh' program is used as default.

---

### Post by P235 on 2009-08-06
oops

---

### Post by drs305 on 2009-08-06
Do you use 'feh', an image viewer? If not, and it is installed, try uninstalling it. Even if you do, I'd uninstall it and see if Places starts working.

You could also check the ~/.local/share/applications/mimeapps.list and see if 'feh' is listed therein.

Sorry to be taking you down so many paths - the first fix normally works.

---

### Post by P235 on 2009-08-06
Feh was uninstalled as I just upgraded, but now that it is installed the notice no longer comes up.  Here is the contents of mimeapps.list:

> [Added Associations]
video/x-ms-wmv=gnome-mplayer.desktop;userapp-mplayer-ZWPXLU.desktop;mplayer.desktop;
video/x-msvideo=gnome-mplayer.desktop;userapp-mplayer-KZOGLU.desktop;
inode/directory=userapp-feh-3QKLLU.desktop;userapp-feh-9PEQLU.desktop;userapp-feh-LJ5RLU.desktop;nautilus-folder-handler.desktop;nautilus-browser.desktop;userapp-nautilus-4SWEYU.desktop;
video/x-ogm+ogg=userapp-mplayer-KZOGLU.desktop;
text/html=firefox.desktop;
application/x-flash-video=userapp-gnome-mplayer-HEHONU.desktop;vlc.desktop;
video/mpeg=gnome-mplayer.desktop;
text/x-troff-mm=userapp-freemind-7NO9OU.desktop;
video/mp4=userapp-gnome-mplayer-HEHONU.desktop;
video/x-matroska=userapp-gmplayer-0E9JWU.desktop;


---

### Post by drs305 on 2009-08-06
> **P235 said:**
> Feh was uninstalled as I just upgraded, but now that it is installed the notice no longer comes up.  Here is the contents of mimeapps.list:

I think this is your problem:
> inode/directory=[COLOR="DarkRed"]**userapp-feh-3QKLLU.desktop;userapp-feh-9PEQLU.desktop;userapp-feh-LJ5RLU.desktop;**[/COLOR]nautilus-folder-handler.desktop;nautilus-browser.desktop;userapp-nautilus-4SWEYU.desktop;

Change the line to:
> 
inode/directory=nautilus-folder-handler.desktop;nautilus-browser.desktop;userapp-nautilus-4SWEYU.desktop;


---

### Post by P235 on 2009-08-06
Wonderful, that did the trick, drs!  Thank you for taking the time to help me.

---

