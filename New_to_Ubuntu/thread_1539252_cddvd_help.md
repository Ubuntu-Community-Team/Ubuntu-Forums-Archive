---
title: "cd/dvd help"
date: 2010-07-26
forum: New to Ubuntu
---

### Post by hipster dufus on 2010-07-26
i am trying to view photos from my cd or dvd drive. the drives show up in my computer window, when i put a disc in either drive, that drive disapears from  my computer window, but the disc never loads. i have tried to open  the drives with f stop and import photos but there is no acess to the drives from f stop. any help is greatly appreciated and please be patient iam not a geek to any degree. i have no desre to delve into the world of pcs, i just want to look at some pictures and e mail them. if it helps i can view my cameras pictures

---

### Post by dv3500ea on 2010-07-26
Does a CD symbol show up on the desktop (this is what should happen)?
It should create a folder in the /media folder.

---

### Post by hipster dufus on 2010-07-26
nothing shows up on my desktop. when i go to computer file browser i lose the dvd drive. if i put it in my cd drive i lose my cd drive in the computer file browser

---

### Post by hipster dufus on 2010-07-26
when i go to disk utility, none of my optical drives are recognized. f stop will not let me import from the drives either they do not show up in any place i can find them from browsing in f stop.

---

### Post by anewguy on 2010-07-26
If there is no disk in the device does the device show in the file explorer ("places")?  If so, do this and post the output back here:

- put a disk in the drive, let it spin up, etc.

- open a terminal window (Applications/Accessories/Terminal)

- type:

dmesg | tail <press enter>  That "|" character looks like a vertical line on my keyboard above the "\" key - yours may be in a different place.  Copy and paste the output to a reply here, then just type:

exit <press enter> and the terminal window will close.

Don't worry about the weird looking typing - we're just asking to look at the last 10 lines in the system log, and since we're doing this after the device spins up a disk and disapears, we're hoping there may be some sort of message being posted to the log to explain what is happening.

Dave ;)

---

### Post by hipster dufus on 2010-07-26
when i go to places the device does not show up, the floppy drive shows up, that will tell u how old my system is, i do not see any of my optical drives in that folder. thanks

---

### Post by hipster dufus on 2010-07-26
when i open compter fromplaces the cd and dvd drive show but the properties has the location as unknown. do i need some drivers|?

---

### Post by anewguy on 2010-07-26
Did you put a disk in the drive, wait for it to spin up (even though it's not recognized) and the do the dmesg | tail as I asked before?  This will let us know if there is an error being trapped into the log.

---

