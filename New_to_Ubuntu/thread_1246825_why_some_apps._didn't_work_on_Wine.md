---
title: "why some apps. didn't work on Wine ?"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by MBG1987 on 2009-08-22
as you know wine is an virtual machine enable you to run windows programs on linux, but why some windows programs  couldn't work with wine ? is there some libraries missing or dependencies or other windows apps should exist before you can run such a programs ?

---

### Post by ibuclaw on 2009-08-22
WINE is not a virtual machine, emulator, or any type of kindred environment...

It is an application layer to allow windows executables to run on Linux, it is based on the "guess-works" of developers implementing the windows libraries which contain all the calls and routines that are needed for applications to even start in the first place.

WINE is an open source project, and it's developments have been motivated by the needs of the developers and the many. As such it is very WoW and Photoshop orientated. This is the reason why some applications work, possibly by accident. :)

WINE is far from being complete. This is the reason why some applications don't work.

Regards
Iain

---

### Post by diablo75 on 2009-08-22
Actually WINE is not a virtual machine.  Last I checked, it's what is called a "compatibility layer", which tricks most Windows based software into thinking it's running on a Windows system...  Anyway, I'm not the expert on that.

What I do know is that not all software runs on WINE, plain and simple.  There is a application database that you can refer to for checking to see if a program you wish to run on WINE will work:

[http://appdb.winehq.org/](http://appdb.winehq.org/)

If you want a true virtual machine, try Virtualbox or VMware Server and install Windows on that, then install the software you're trying to run.  If all else fails, use a dual-boot partition setup.  And just remember that Windows software was never meant to run in a Linux environment, so if it does run then you should consider yourself lucky.

---

### Post by ibuclaw on 2009-08-22
> **diablo75 said:**
> If you want a true virtual machine, try Virtualbox.
+1
VirtualBox has had OpenGL support for some time now ...

> If all else fails, use a dual-boot partition setup.  And just remember that Windows software was never meant to run in a Linux environment, so if it does run then you should consider yourself lucky.
To add onto that. Rather than trying to get Windows applications to work on Linux, ask yourself "*What native alternatives are there?*" and try/use them instead...

---

### Post by XCan on 2009-08-22
> **tinivole said:**
> +1
To add onto that. Rather than trying to get Windows applications to work on Linux, ask yourself "*What native alternatives are there?*" and try/use them instead...

+1. Although I admit, sometimes there really isn't a proper alternative (yet) for linux, but most of the times there is. :) 

The best way is probably to google an alternative or ask here. As mentioned, you can't expect wine to work flawlessly for everything, and I find virtualbox cumbersome.

---

### Post by cascade9 on 2009-08-22
> **MBG1987 said:**
> as you know wine is an virtual machine enable you to run windows programs on linux, but why some windows programs  couldn't work with wine ? is there some libraries missing or dependencies or other windows apps should exist before you can run such a programs ?

In some cases, yes. In other cases, you will get only partial functionality from apps in wine till you move over some .dlls. I have to move a few over to get foobar2000 to run they way I want it to.

---

### Post by Hendrixski on 2009-08-22
Because Microsoft intentionally make it hard for their competitors to run windows apps.  So yes, there are still things missing in Wine.

Honestly, almost every application you would want to run in Wine has an open source alternative which will work flawlessly on Linux.

---

### Post by steveneddy on 2009-08-22
I use VirtualBox to run Windows apps and recommend that to everyone over Wine every time.

---

### Post by kendoori on 2009-08-22
+1 in VirtualBox. Since I still run Outlook for work, I run VirtualBox in seamless mode, and moved the XP taskbar to the right per the attached. It's reasonably seamless. I do aim to get rid of Outlook and run Zimbra instead, but am not ready. I built a very skinny XP machine for running Windows stuff when I need it and it starts and runs very quickly. Actually pretty amazing.

I have played with the commercial version of Wine, CrossOver Linux and did find that more things ran under it, but as yet have decided to not spend the $40 US for this.

---

