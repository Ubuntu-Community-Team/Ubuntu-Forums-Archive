---
title: "screen went black?  please help"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by PermNoob on 2009-03-03
So I was using my SOs comp to setup transmission for her, and she acccidently flipped the powerstrip it was plugged into.  When I rebooted, the only problem I noticed was the background was centered rather than stretched. No big.  So I go into the appearances, reset the background to stretched.  I decided to see if the real problem was that the resolution had somehow changed, as I thought I had a background that fit perfectly.  I whent into screen resolution, and moveddown one from 1024Xsomething big to 1024Xsomething slightly smaller.  
The whole screen started spazzing sideways as if the horizontal hold was fubar, and when I moved the mouse up and down the page would go black from I guess where the mouse was down.  IOW, looking at the screen I could almost see the screen I was on, but not enough to reach the buttons I needed.  about the bottom third of the screen was black.  If I moved the mouse up, the black region would grow up, if I moved it down the black region would grow down.  I tried resetting the resolution using the xrandr -s #, but each attempt yielded nothing, just the screen goign dark then coming back on black.

I have no idea where to go from here.  I assume I accidently changed some other option somehow, but what? refresh rate?  I dont know.  However if this can be fixed from the terminal it is awesome, as I have a hotkey setup to launch one.

---

### Post by llamabr on 2009-03-03
sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by lindsay7 on 2009-03-03
try to set the rsolution in the video driver menu.

---

### Post by PermNoob on 2009-03-03
no luck with the command you gave me, tried it twice typing in the dark.  
However my monitor has an auto config button that fixes the alignment and all that automagickally.  on this pc, hitting the button makes it display a little dialoge box that says auto config and on the bottom 59.9kHz H, 60.0Hz V
when I hit that button on the other comp, it only flashes up for a half second, and says 80.4kHz H and 75.0 Hz V
any light?

---

### Post by lindsay7 on 2009-03-03
Just an idea for you, who knows if this will do any good, but....

Maybe you could start up the computer with a Ubuntu or Kubuntu live disk. It might sart you up with low res and reset the computer so that when you start up normally the system will come back.

---

### Post by rhcm123 on 2009-03-03
Wow, i dunno... one of the main things i liked about windows was that if i changed my settings it gave me 15 seconds to click ok otherwise it would change em back.

---

### Post by PermNoob on 2009-03-03
well, I gave in to doing it the crass way, alt+prntscrn R E I SUB
fixed it, but I still don't know what the original problem was, and I don't like that.

thanks anyways.

---

### Post by llamabr on 2009-03-03
The original problem was that your xorg config file got screwed up somehow.  I meant for you to open a terminal by pressing ctrl-alt f3 and typing that command, not to just type it into the dark.  It would have allowed you to reconfigure the config file.

Your way works too, though.  Good job.

---

### Post by PermNoob on 2009-03-03
oh, I did type that into a terminal, I have F4 setup to launch a terminal, and then typed what you said.  For some reason that didnot work.  I even tried it a third time before giving up.

for posterity, would that revert my settings to the original settings from ubunutu, or to my most recent settings prior to the alteration?

---

