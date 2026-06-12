---
title: "Rdesktop will not cube turn in fullscreen / windowed"
date: 2010-06-29
forum: New to Ubuntu
---

### Post by Virigoth on 2010-06-29
Hi all,

I've been working on this problem for about 3 hours now and my googlefu is failing me :)  .  I've been using rdesktop in full screen mode, minimizing, and swapping workspaces as a workaround but I'd really like to leave one of my workspaces as a full screen RDP session and be able to cube turn it.  It seems the rdesktop locks out local commands even though I have the switch used to allow window keybinds, or if I do it via terminal I add the -K keybind.  Anyone out there have this working?  I don't mind doing some hackery to get it to work if I need too.  I've searched on here and none of the threads seem to be solved and/or are outdated!  

Thanks for your help,

Viri

---

### Post by lkjoel on 2010-06-29
Do you want to try Compiz?
Compiz has cube and millions of other features.

---

### Post by Virigoth on 2010-07-03
> **lkjoel said:**
> Do you want to try Compiz?
Compiz has cube and millions of other features.

I have compiz enabled on my desktop.  I'm trying to work with a full screen remote desktop through rdesktop to a windows XP Pro box, once I give the rdesktop window "command" by clicking in it all of my window bindings stop working.  I've enabled the allow host window bindings in rdesktop but it still seems to be over-riding that command.  I have to exit the full screen rdesktop, minimize, and use the desktop to turn back screens or bring up the cube to turn it to another workspace.

---

### Post by lkjoel on 2010-07-04
Try:
CTRL+ALT+LEFT
or
CTRL+ALT+RIGHT

---

### Post by nikloveland on 2010-08-17
I was having major issues trying to get it to work on a single side of the cube as well. I could get the cube to flip but the full-screened session would follow me. I also have two monitors and when in full screen mode the other monitor is blanked-out. I decided to switch to [[COLOR="RoyalBlue"]Remmina[/COLOR]]("http://remmina.sourceforge.net/") (found it using Synaptic Package Manager). It saves the sessions, has full screen on one screen and leaves the gnome desktop on the other, I can even set a custom resolution and scroll around on it. I highly recommend it!

---

### Post by jt.waleson on 2011-09-19
Wow, really impressed with Remmina! Excellent package!

---

