---
title: "Too many CD's, now not enough!"
date: 2010-08-21
forum: New to Ubuntu
---

### Post by John Peschken on 2010-08-21
I'm having two problems.  Both started to occur at the same time and relate to my external USB  CD/DVD drive.

1. When I put a disk in the drive, a Brasero dialogue for copying the CD pops up, and I can't seem to make it behave differently either by fiddling in "preferred applications" or the CD icon under places - computer.

2. In Banshee, I had been seeing two entries for the CD drive.  One labeled CD/DVD Drive, the other with the name of th CD.  Now, neither is showing up.

This was all working earlier today, so I don't think I have incompatible hardware.

Ideas?

---

### Post by zeroseven0183 on 2010-08-21
My immediate question is, was there any changes you made before this happen or before you notice this behavior?

Anyway, for number 1 You can disable the action everytime you insert a CD by checking the option **Never prompt or start programs on media insertion** or individually adjust per media type. 

1. Go to Places and click any folder
2. Click Edit and select Preferences
3. in File Management Preferences window, go to Media tab

As for number 2, as far as I understand, it's a bug. But I do hope I'm wrong.
Is Banshee your default media player?

---

### Post by John Peschken on 2010-08-21
Hey, Thanks! 

Your three steps seem to have solved the problem with Brassero popping open.  I really would have expected those settings to be on the "System" menu somewhere, rather than having to go into a folder like that.  I suppose going to the folder is consistent with how Windows does it, but I always thought it was in the wrong place in Windows too.

The double CD's in Banshee are harmless enough now that I have changed Banshee's settings to not automatically import CD's on insertion.  It was annoying mostly because it started two concurrent import sessions.  I had it set that way because I was going to do a marathon CD import session, but I can live without that.  If it's a bug in Banshee, it should  soon go away with updates.

The problems started when I uninstalled Sound Juicer.  I put it back in, and the problems persisted so I'm not sure we can pin it on that program.  The two issues I've had with Ubuntu both occurred when I uninstalled software I didn't want.  I'm a little compulsive that way.  Maybe I should try to relax about that until I understand Ubuntu better.

---

