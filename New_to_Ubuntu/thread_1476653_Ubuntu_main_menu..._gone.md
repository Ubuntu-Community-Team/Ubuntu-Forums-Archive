---
title: "Ubuntu main menu... gone?"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by FakeJake93 on 2010-05-08
I decided to attempt to install the Sims 3 onto my laptop (Ubuntu 9.10).  I managed to get through the installation using Wine, but when I tried to start the exe file with Wine, it told me it could not load the program.  Through google, I discovered I needed an updated Nvidia video card.  I couldn't get the new version I found to install, and I figured out I needed to turn off my X server in order for it to be able to work.  

The command "etc/init.d/gdm stop" did not turn it off (on a screen loaded through Ctrl+Alt+F2), but I found one that said "sudo service gdm stop" that seemed to work.  However, after I did this, all of my previous entires disappeared and I was left with "Reloading Postfix configuration..."  And it froze.  F7 would not get me back to the desktop, and I could not type anything else into the command prompt.  So I restarted.

When it turned out, the GNOME menu bar was gone.  There is no longer a way for me to access any of my programs, documents, files, etc.  All I have is my desktop picture and the top taskbar, but nothing else.  I can do absolutely nothing with it.

I did manage to install the new video driver by going back to the command prompt and telling it to turn off X server again, and to CD to my download folder from the command prompt and run the driver file.... which successfully installed.  Still, I can do nothing with my new driver now.  I've tried a number of things, but nothing works.

Sorry this is so much to read, but I wasn't sure exactly where the problem started.  Though I've had this OS for six months, I'm still a noob when it comes to fully leaving my Windows mind-set. >_>

Any ideas?  Thanks for any help ahead of time.

---

### Post by dagdeniz on 2010-05-08
is right clicking on the taskbar disabled? that way you can add items... (main menu is in the list)

---

### Post by FakeJake93 on 2010-05-08
The only options I get when I right-click the taskbar are "Preferences", "About", "Remove From Panel", "Move" (which is grayed out), and "Lock to Panel".  The only thing preferences lets me do is to "Show all windows from workspaces" as a check box, which is already selected.

EDIT: (rather than double posting)
I managed to log into the session xterm rather than gnome, where I was able to set Mozilla and my home folder under shortcut keys... so I can at least do those two things.  The only thing not having the main menu is preventing me from doing is loading any programs on my laptop, besides the ones I can access via my Wine folder that are Windows based.

---

### Post by FakeJake93 on 2010-05-20
With the update to Ubuntu 9.15, the main menu returned for about five minutes, and then went away yet again.  I found a way to access my programs and files by adding a module to the top menu bar, though.  The module is a drop down main menu; so the desktop menu that was once there is no longer necessary.  So, in case anyone else has this problem, that was an alternate way around the main menu for me.

Anyways, thanks for the advise, dagdeniz.  It was much appreciated.

---

