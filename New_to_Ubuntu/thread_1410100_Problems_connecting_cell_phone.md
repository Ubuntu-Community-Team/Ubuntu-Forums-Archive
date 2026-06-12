---
title: "Problems connecting cell phone"
date: 2010-02-18
forum: New to Ubuntu
---

### Post by kamikazedce on 2010-02-18
OK ive been searching the forums for an hour and cant find anything that works. when i connect my phone, the razzle, nothing happens. absolutely nothing. the phone is in the right mode, ive tried all my usb ports, and still nothing. can someone tell me how to fix this?????

---

### Post by Calmor on 2010-02-18
I had to look the Razzle up, as I'd never heard of it before.  What are you trying to do with it (tether or just connect to the SD card), and what is the result of running lsusb in a terminal window after connecting the device?

---

### Post by kamikazedce on 2010-02-18
i want to connect to the sd card so i can put music on it.

before and after lsusb
doug@doug-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
doug@doug-laptop:~$ lsusb
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 007: ID 106c:320c Curitel Communications, Inc. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
doug@doug-laptop:~$

---

### Post by Calmor on 2010-02-18
I couldn't find anything on the web with that device ID listed.  Unfortunately I can't be of much help here, but at least the system is recognizing it.  It may be a conflict with a module trying to tether, or it may be a driver issue since the phone appears not to identify itself as removable media.  It also seems like a brandy-new phone, so information is limited unless the manufacturer provides information or it conforms to an already-implemented standard.

When you plug it into a Windows computer, does it require software installation to access the SD card?

---

### Post by kamikazedce on 2010-02-18
no it comes right up. it was working last night which is the strange part about it. i would plug it in and a file browser would open up and everything would be there. and now nothing is working.

---

### Post by kamikazedce on 2010-02-18
ok i got it to come up but theres another problem. all the music is gone but it still says i only have half a gig. its a 1 gig sd card

---

### Post by Calmor on 2010-02-18
Do you have a reader on the PC?  Is it possible to remove the SD card and read it directly, to take the phone out of the loop?  What did you do to get it to come up?

---

### Post by kamikazedce on 2010-02-18
yeah the file browser came up. i removed the sd card while the phone was connected and put it back in. but now its telling me i have half the space i should have. the only thing in the music folder is the device logo and icon. when i hit ctrl+h nothing happens.

---

### Post by Calmor on 2010-02-18
I was thinking to take the card out of the phone and put it into another card reader connected directly to the computer (or another PC perhaps) to see what's going on.

Also, will the phone still play music?

---

### Post by kamikazedce on 2010-02-18
im sure it will but theres no music in it. the files are not there but something is still taking up half the space on the card

---

### Post by Calmor on 2010-02-18
Is there a hidden folder called .Trashxxxx that has all of the music in it, deleted?  Does the card say ~500MB free space, or does it actually say that the partition is smaller than 1GB (900M or so typically)

---

### Post by kamikazedce on 2010-02-18
there was and i deleted it. the card still says 483.5 MB free space as opposed to the GB i should have

---

