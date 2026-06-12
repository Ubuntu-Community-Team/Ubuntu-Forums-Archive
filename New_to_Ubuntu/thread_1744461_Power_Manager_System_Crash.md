---
title: "Power Manager/ System Crash"
date: 2011-04-30
forum: New to Ubuntu
---

### Post by Blue Summer on 2011-04-30
Hi all randomly everything went wrong, it said something like power monitor or something has crashed, looked like a battery. I'm not even on a laptop! Now when I log in it's a wierd version of my desktop like windows safe mode and it lags like hell, when I try and log out it just stalls on log out, I can't really open any programs and I've got no idea what's going on.

---

### Post by madjr on 2011-04-30
bad upgrade right?

---

### Post by Blue Summer on 2011-04-30
Nah, didn't ugprade anything! Internet went off so I logged out to try and restart because it wouldn't come back on and then had these problems!

---

### Post by oldsoundguy on 2011-04-30
Try re-booting and when the grub menu comes up, select repair of your latest kernel.  Sounds like a bad shut down.

---

### Post by Blue Summer on 2011-04-30
Will do mate, any idea what the command is? The startup times are usually pretty fast i'll probably miss it

edit: Yeah, I don't see any option like that, after the BIOS screen I see some I/O things for a second and then the ubuntu screen with the dots loading underneath then my login screen

---

### Post by stoneage on 2011-04-30
To get to the grub menu, I think you have to hold down the SHIFT key after the BIOS loads.

---

### Post by Peter09 on 2011-04-30
When you get into recovery mode, by holding down the shift key and then selecting the second option down in the grub list (use the arrow keys) and hit enter.

You should get to a menu, one of which is 'repair broken packages (or similar)'. Try that, with any luck you will not have significantly damaged the system to a point where it cannot be repaired.

---

### Post by Blue Summer on 2011-04-30
Yeah it's "Power Manager" which is crashing.

After a few restarts I finally managed to get on the loading screen, click on the first recovery mode and after a bit of loading it said "Indirect register access" or something and failed.

Can't seem to get back on the grub loading menu at the min

edit: managed to get on, trying another recovery mode version, working! Trying to repair broken packages now
edit2: it's supposed to be connecting to archive.canonical.com but it obviously can't due to the fact it's not connected to my wireless network

I can get into Xterm if that helps on the login screen

---

### Post by uRock on 2011-04-30
I changed the thread title for you, so that it is a bit more descriptive. :)

---

### Post by Peter09 on 2011-04-30
OK - looks like you will need to get`to a wired connection to do the repair, other than that it looks optimistic that  you can recover.

---

### Post by Blue Summer on 2011-04-30
Haha thanks uRock.

Unfortunatly I can't get a wired connection. got all my college work on there, really don't want to have to reformat

---

### Post by Peter09 on 2011-04-30
First thing to do is get a 'Live CD' up and running and copy your work (home folder) to somewhere safe. Then most probably a complete rebuild. Assuming you have everything at hand its most probably a couple of hours work.

---

### Post by Blue Summer on 2011-04-30
Lol I think I'm done with Linux after this, I think I've got a small parition so will just install windows 7 and copy my stuff over I guess. Ubuntu is just more hassle then it's worth.

---

