---
title: "unbuntu 8.04 not recognizing hard drive during set up."
date: 2009-08-12
forum: New to Ubuntu
---

### Post by Keebs on 2009-08-12
[FONT=Arial][SIZE=3]I am new to Linux and unbuntu, and I am trying to have a dual boot of Windows XP & unbuntu. 
 
I currently have Windows XP 64bit installed on my computer. Now I am trying to install Ubuntu 8.04 64bit. When installing, the partition screen shows nothing, and i am not allowed to create any new partitions. I do not think this should effect it at all, but is there any possibility I am having this problem because i have  SATA HDD?(I do not believe this is the problem, since I did not have this problem when i installed XP) or that I currnetly have one partition, and have free space (not formatted) left for unbuntu [/SIZE][/FONT][FONT=Arial][SIZE=3]?

any help is appreciated.
[/SIZE][/FONT]

---

### Post by zerhacke on 2009-08-12
Did you have to install drivers to get WinXP to see the drive?  If no drive is showing it means Ubuntu didn't detect the SATA controller.  Without that it won't see any of your discs.

Consider that you said it didn't find any hard drives to show the partition layout with setup, this is my best guess.  Try to find a better supported SATA controller.

(Really strange, though, as Linux knows just about every SATA controller out there.)

---

### Post by Keebs on 2009-08-12
I did just try to install another distro to see what would happen (linux mint, which I downloaded but choose unbuntu over mint) and it had the same problem, which I figure means it is not the software, but the computer. so should I look for SATA drivers? or try connection to a different SATA slot? or something else?

---

### Post by Keebs on 2009-08-12
In the thread linked below, they had the same problem, and the guy who figured out the problem said it was in the BIOS, unfortunately he did not tell what he did to fix the problem and i have limited experience/knowledge of BIOS, so i was wondering if anyone knew anything about it.

[http://ubuntuforums.org/showthread.php?t=765711](http://ubuntuforums.org/showthread.php?t=765711) 

thanks.

---

### Post by LowSky on 2009-08-12
go to BIOS, search for SATA connection type or something similar. most likely you using  legacy IDE (which is why XP could install without needing Drivers), switch to AHCI and it will (ok.. should) work


I found this its a good read
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux)

---

### Post by Keebs on 2009-08-12
> **LowSky said:**
> go to BIOS, search for SATA connection type or something similar. most likely you using  legacy IDE (which is why XP could install without needing Drivers), switch to AHCI and it will (ok.. should) work


I found this its a good read
[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface#Common_problems_switching_to_AHCI_under_Linux)


Thank You, that was the problem, so now i have to figure out how to get XP to work on AHCI. lol. That is a new problem I will have to work out, but that is nether here or there. so once again thank you.

---

### Post by ibizatunes on 2009-08-12
Ubuntu 8.04 is quite old now, yes it is the LTS release, but a new version 9.04 may have your SATA controller drivers built in

I would download 9.04 and install that instead on 8.04

---

### Post by LowSky on 2009-08-12
Your Welcome Keebs

AHCI is runnign in SATA mode, XP will not run in SATA mode, because it was never designed to. A few years before this mode change BIOS option we had to ge tthe drivers from our motherboard makers, and load them during the install on a floppy drive. It was really annoying.

all you need to do is this, go to your motherboards creators website and download the drivers. If its an OEM like Dell, go there. They will have them, if not ust learn what controller your motherboard uses and search for the basic driver. Then swtich to IDE mode for windows, boot to windows and installt he new drivers, then (i know annoying) rebooot to bios change back and try out windows, it should work

---

