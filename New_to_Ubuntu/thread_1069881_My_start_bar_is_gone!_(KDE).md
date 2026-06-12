---
title: "My start bar is gone! (KDE)"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by ukemike on 2009-02-14
My start bar is gone! (KDE).  I have the bar at the bottom of the screen set to autohide, and now it won't come out of hiding!  I thought, "strange. well a reboot'll fix this."  It didn't.  If the context menu didn't have "run command" as an option I'd really be stuck, cause I wouldn't even be able to run firefox.

I've tried the things that seem obvious to me.  I refreshed the desktop, I turned on the desktop menubar and from there was able to access system settings, but I wasn't able to find configureation for the start bar.

I'm pretty sure I'm using kubuntu 6.10 if that makes a difference.

---

### Post by hyperyoda on 2009-02-14
> **ukemike said:**
> My start bar is gone! (KDE).  I have the bar at the bottom of the screen set to autohide, and now it won't come out of hiding!  I thought, "strange. well a reboot'll fix this."  It didn't.  If the context menu didn't have "run command" as an option I'd really be stuck, cause I wouldn't even be able to run firefox.

I've tried the things that seem obvious to me.  I refreshed the desktop, I turned on the desktop menubar and from there was able to access system settings, but I wasn't able to find configureation for the start bar.

I'm pretty sure I'm using kubuntu 6.10 if that makes a difference.

[http://ubuntuforums.org/showthread.php?t=247964]("http://ubuntuforums.org/showthread.php?t=247964")

---

### Post by ukemike on 2009-02-14
I read the linked thread.  One post suggested that I right click and 'run command' "kicker." That did nothing I can tell.  Though if I enter "kicker" in the shell it tells me ERROR: kicker is already running.

The other post suggested that the autohide conditions had been set to show the task bar only when the cursor is in a particular corner.  I have moved my cursor to each bit of the screen's perimeter.  No luck.

I decided to fiddle more with this kicker program.  It was already running so I killed the process, and ran it again with these results:
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 169
  Major opcode:  146
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
ewan@blue:~$ *** attempt to put segment in horiz list twice
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  156
  Minor opcode:  6
  Resource id:  0x4c
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x1800099
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x1800099
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x1800099
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  19
  Minor opcode:  0
  Resource id:  0x1800099
X Error: BadPixmap (invalid Pixmap parameter) 4
  Major opcode:  54
  Minor opcode:  0
  Resource id:  0x14002aa

and still no luck

---

### Post by abn91c on 2009-02-14
did you change themes recently? also in the settings check that " windows can cover" in the "more settings" tab chen you right click on the panel>panel settings> more settings

---

### Post by ukemike on 2009-02-14
I haven't changed themes recently.  I don't know where to look for those settings.  They don't appear to be in any of the settings found under "system settings" or under configure desktop.

---

### Post by abn91c on 2009-02-15
> **ukemike said:**
> I haven't changed themes recently.  I don't know where to look for those settings.  They don't appear to be in any of the settings found under "system settings" or under configure desktop.
right click on the lower panel

---

### Post by ukemike on 2009-02-15
> **abn91c said:**
> right click on the lower panel

I hope that the comment above was intended as light humor because the whole point of this thread is that LOWER PANEL ISN'T THERE!!  I'm trying to figure out how to get it back.  

I'm comfortable editing config files, and navigating around the computer in bash, could someone point me to where I can reactivate the lower panel / task bar / start bar or whatever it's called?  Please? With sugar on top???

-Mike

---

### Post by abn91c on 2009-02-15
> **ukemike said:**
> I hope that the comment above was intended as light humor because the whole point of this thread is that LOWER PANEL ISN'T THERE!!  I'm trying to figure out how to get it back.  

I'm comfortable editing config files, and navigating around the computer in bash, could someone point me to where I can reactivate the lower panel / task bar / start bar or whatever it's called?  Please? With sugar on top???

-Mike
right click on the desktop then add panel, if rebooting didt bring lower  panel just rebuild it from new
Oops never mind, thats for 8.10, something I did for a similar problem back in 7.04 was deleting the ./kde folder and rebooting, you will loose some custom setups but KDE will rebuild a default desktop setting when it re-starts

---

### Post by txcrackers on 2009-02-15
This is a **very** wild guess, but in *.kde/share/config/plasmarc* look for a value named **panelVisibility** and set it to "0"

---

### Post by abn91c on 2009-02-15
> **txcrackers said:**
> This is a **very** wild guess, but in *.kde/share/config/plasmarc* look for a value named **panelVisibility** and set it to "0"
He has kubuntu 6.10!!

---

### Post by ukemike on 2009-02-15
That's what I needed!  

I right clicked on the desktop "configure desktop" add desktop menu bar.  Right clicking on the desktop menu bar had the option "add panel"  I added "exteral task bar"  once that was in place I was able to right click on that and "configure panel".  Once I started configuring it and hit 'apply' bingo it was there again.  

Thanks!  

I've also gone and changes my configuration so it works more like I like it.

---

