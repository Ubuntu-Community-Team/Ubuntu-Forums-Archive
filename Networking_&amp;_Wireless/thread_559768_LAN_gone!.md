---
title: "LAN gone!"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by f37u5g0d on 2007-09-25
I just burned a live cd of ubuntu linux.  I was checking it out (without installing to the hard drive) and loved it but then when I returned to windows I noticed my wired internet connection was completely gone (from the network connections window).  It was working on linux.  I try to create a new connnection by running the wizard and no icon is created.  I then went back and booted from the CD into ubuntu again only to discover it to had lost my ethernet connection!  Where did it go?!?!  help!

---

### Post by noob12 on 2007-09-26
Try checking your BIOS and reenabling the onboard network device.

---

### Post by f37u5g0d on 2007-09-26
I tried that and it worked once.  But then I ran ubuntu (from the CD) again and it was gone from both windows and linux (again).  But now it's also missing from the bios!  I might have just accidentally changed some settings around in the bios that made it hidden from view but I doubt it.  Also I noticed I have a piece of hardware that is missing drivers.  Something called "PCI Simple Communications Controller."  Although I don't think this is the problem.  My LAN  is onboard, not PCI.

---

### Post by noob12 on 2007-09-26
You may need to reset the BIOS to see the setting again and reenable it.

---

### Post by f37u5g0d on 2007-09-27
Hey thanks.  I had to turn off the comp with the switch on the powersupply (without properly shutting down windows) to get the ethernet option to show up on the bios.  I tried using the restore "bios to factory settings"  option but it didn't work.  Thanks again anyway.

---

### Post by noob12 on 2007-09-27
Glad you go it back.  It would be great if you could file a bug on launchpad.

---

### Post by f37u5g0d on 2007-09-27
It would be even greater if I knew hot to do that!  But seriously what's launchpad?

---

### Post by noob12 on 2007-09-27
Launchpad hosts the Ubuntu bug database.    [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu)  

I don't know what your problem is and you may get better responses there.
At least two other users have reported similar problems on threads I happen to have hit but couldn't really help with.  

See this thread.  I'm not sure if this is a related root cause or just the same symptoms.  I flailed there too:  [http://ubuntuforums.org/showthread.php?t=558769](http://ubuntuforums.org/showthread.php?t=558769)

Someone with the problem needs to file the bug though because they probably will require more information and feedback.

Other forum readers?  Clues anyone?

---

