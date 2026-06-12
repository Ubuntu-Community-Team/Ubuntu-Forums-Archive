---
title: "Looking for some WICD thoughts or direction"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by bmachia on 2008-04-17
OK, I’ve really have two questions.  (sorry) – But I’m thinking they maybe related.

1) I’ve installed WICD and have been able to manually connect to my internet for a few weeks.  Unfortunately, WICD will not autoconnect or run tray.py upon logon.

So, I created a script (~.kde/Autostart/network.sh)
		#!/bin/sh
               sleep 30
               /opt/wicd/tray.py

I chmod the script to make it executable, but nothing happens at logon.

I have to be missing something REALLY stupid here, but I can’t see it.  Maybe its a permissions thing, do scripts in Autostart need to be run under root (i.e. sudo)?  And if so what the smartest way to implement?

Now, onto question 2
2) /opt/wicd/tray.py runs fine when I start/run it manually from terminal mode.  The icon appears in the lower right-had corner and I can connect easily.  But if I close Terminal mode, then tray.py closes (naturally).  So what is the correct way to start tray.py, so it is not reliant on a terminal window be present?

Bill

---

### Post by MrFSL on 2008-04-18
System > Preferences > Sessions

Add

Name: WICD Tray Icon
Command: /opt/wicd/tray.py

OK

---

### Post by bmachia on 2008-04-18
Well I found my problem, and it was not for lack of trying.

MrFSL, you pointed me in the right direction, but ‘System > Preferences > Setting’ is different when running KDE4.

In my Gutsy, there are two .kde directories (.kde & .kde4).  So, when I put my scripts in .kde/Autostart nothing happened.  That changed completely, when I moved the script(s) file to .kde4/Autostart.

I guess I’m a purest; I don’t like Dolphin, so I never saw the complete list of hidden files.

---

### Post by Kensey on 2008-04-18
To answer your question 2:

> **bmachia said:**
> 2) /opt/wicd/tray.py runs fine when I start/run it manually from terminal mode.  The icon appears in the lower right-had corner and I can connect easily.  But if I close Terminal mode, then tray.py closes (naturally).  So what is the correct way to start tray.py, so it is not reliant on a terminal window be present?

Add an ampersand (&) to the end of the command.  This "backgrounds" the process, detaching it from terminal control.

---

### Post by corney91 on 2008-04-18
Using an ampersand sends it to the background but if you want to close the terminal without closing the program, you need to put the command in brackets so:
```
(*command here* &)
```

---

### Post by Kensey on 2008-04-18
Only if you want the command to run in its own subshell.  I just verified by opening a terminal, running "firefox &", and exiting the terminal -- firefox continued to run.

---

### Post by blasthand on 2008-06-07
Hi All,

I've found the easiest way to have the tray icon to work is to add the following line to the end of your .profile ( ~/.profile ) file:

nohup /opt/wicd/tray.py &

Write the file, logout, login and it should be there. I've done this for both accounts on my system and it appears to work flawlessly.

HTH,

Cheers,
Mark.

---

