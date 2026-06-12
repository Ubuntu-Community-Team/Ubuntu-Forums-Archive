---
title: "Cannot open file explorer 'window' nor the Panel application"
date: 2008-12-18
forum: New to Ubuntu
---

### Post by sproaty on 2008-12-18
I've installed Ubuntu 8.10 from XP SP3 using the Wibu installer. Everything went okay, upon logging in for the first time there was around 190 updates detected for me to install, which I installed. Next, I installed the latest Nvidia graphics drivers and the unrestricted files in an attempt to get mp3 files and such working (still no luck there, but that's another issue). 

I then just played around a bit. I changed one system setting from gconf-edit - which was the boolean value for placing an icon for the Deleted Items onto the desktop. I then played around with the default panels a bit, merging the 2 default panels into one, and installed the "main menu" panel widget, which combines apps/places/system into a single icon. I installed Python-pygame and a few programming programs

That's about all I've done really, and now when I try and load -any- kind of "file explorer/browser" window, I get "opening Documents..." (or whatever the folder name is) in the taskbar for around 10 seconds, then it disappears. I also tried adding a shortcut to firefox onto the desktop from the right click menu in the applications start menu, but that wasn't working either. Similarly, when I try and open the Panel application the same opening panel... taskbar item appears for 10 seconds. I can modify, add and delete panels though from my "taskbar" bottom panel, yet can't launch the main window


I'm very new to Linux, I can browse through directories using the terminal using the ls, pwd, cd commands, and using man to lookup some programs, but that's my limitation really. I'd consider myself well-versed with XP so using the GUI is pretty easy, but since it's not working I'm struggling doing everything with the terminal. Oddly enough, other programs don't seem to be affected, as I extracted a .tar using the "archive manager" program and then opened the contents of the extracted file using the terminal. I just don't know where to start to look for this particular problem, nor what diagnostics I can give besides the descriptions above

My PC - overclock is 24hr hour Prime95 stable:

Athlon X2 3800+ (2.52GHz @ 1.34v)
DFI LanParty nForce4 SLI-D
Leadtek 8800GT
2x1GB OCZ Platinum PC3200 Rev2 (210MHz @ 2.7v) 
Creative X-fi Music 
Silverstone Strider 560W 
Samsung 19" 8ms

---

### Post by sproaty on 2008-12-18
Actually, when I said that adding firefox as a shortcut on the desktop wasn't working, it turns out that it was...

[[IMG]http://img352.imageshack.us/img352/8068/desktopxk1.th.png[/IMG]](http://img352.imageshack.us/my.php?image=desktopxk1.png)

oh, erm, wow...seems I fixed it. I deleted the key "trash_icon_name" in gconf-editor and re-created it and somehow the file browser's working again. 

However, even after restarting Nautilus using these commands:

nautilus -q
nautilus &

the desktop will not show any icons. I can view the files on the desktop through the terminal, as in the screenshot above (that was before I "fixed" things), view them through the file browser as well but not on the actual desktop!

---

