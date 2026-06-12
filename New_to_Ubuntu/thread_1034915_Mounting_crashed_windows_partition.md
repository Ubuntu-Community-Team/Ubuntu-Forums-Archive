---
title: "Mounting crashed windows partition"
date: 2009-01-09
forum: New to Ubuntu
---

### Post by AlanRick on 2009-01-09
Hi,
(be merciful - absolute newbie)

I'm using ubuntu because windows xp on this pc crashes every 5 mins and neither I nor my repair shop can fix the blue-screen issue.

Now I have a data partition in windows xp that I can access in windows but can't access in ubuntu.


When I try to mount the partition from the places menu the error reads...

cannot mount volume

> $LogFlie indicates unclean shutdown (0,0) Failed to mount '/dev/sda1': Operation not supported Mount is denied because NTFS is marked in use. Choose one action: Choice 1: if you have Windows then disconnect the external devices by clicking on the 'Safely Remove Hardware' icon in the Windows taskbar then shutdown Windows cleanly. Choice 2" if you don't have Windows then you can use the 'force' option for your own responsibility . For example type on the command line:
mount -t ntfs-3g /dev/sda1 /media/disk -o force (the response is only root can do that)
....
Fair enough. 
My first preference is choice 1 but I don't understand what it means. "*if you have windows*..." Does that refer to the windows in Ubuntu or is that referring to Microsoft Windows? Or is this Wine?

Where is the "*Windows taskbar*"? I can't find this "Safely Remove Hardware" icon anywhere on my Ubuntu desktop (possibly because mount failed).

Any help appreciated. Or should I just go for option 2?
Alan

---

### Post by fatgeek on 2009-01-09
> **AlanRick said:**
> Hi,
(be merciful - absolute newbie)

I'm using ubuntu because windows xp on this pc crashes every 5 mins and neither I nor my repair shop can fix the blue-screen issue.

Now I have a data partition in windows xp that I can access in windows but can't access in ubuntu.


When I try to mount the partition from the places menu the error reads...

cannot mount volume


....
Fair enough. 
My first preference is choice 1 but I don't understand what it means. "*if you have windows*..." Does that refer to the windows in Ubuntu or is that referring to Microsoft Windows? Or is this Wine?

Where is the "*Windows taskbar*"? I can't find this "Safely Remove Hardware" icon anywhere on my Ubuntu desktop (possibly because mount failed).

Any help appreciated. Or should I just go for option 2?
Alan

The directions are meant to be performed in Windows.

---

### Post by AlanRick on 2009-01-09
Many thanks. (I did say I was new  :redface:) 
So it was the XP Windows *system tray* that the message was referring to.
The "safely remove hardware" can't be used for hard drives so once I'd re-started XP Windows I simply exited properly (before the BSOD) and that solved the Ubuntu problem. I could now mount the drive in Ubuntu without the error message.
Thanks again.

---

