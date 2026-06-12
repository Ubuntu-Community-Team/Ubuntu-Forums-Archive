---
title: "Virtual box not working"
date: 2010-08-03
forum: New to Ubuntu
---

### Post by flyfishingphil on 2010-08-03
See info in signature re system.

Have 10.04, w/updates, and the VBox worked fine until recently. Now when I start it up get get a couple of error messages:

[COLOR="Red"]Failed to open a session for the virtual machine ffpxp.
The virtual machine 'ffpxp' has terminated unexpectedly during startup with exit code 1. (The result code is the detailed info from this statement)

Result Code: 
NS_ERROR_FAILURE (0x80004005)
Component: 
Machine
Interface: 
IMachine {6d9212cb-a5c0-48b7-bbc1-3fa2ba2ee6d2}

This is the second one that pops up:

Kernel driver not installed (rc=-1908)

The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

'/etc/init.d/vboxdrv setup'

as root. Users of Ubuntu, Fedora or Mandriva should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.[/COLOR]

[COLOR="Black"]
I have downloaded the newer version, and tried to install it, but get the same message every time I try where it says "Denied. Permission required" etc.

I have several programs in the VBox that I need. OS in VBox is WinXP and that is required for my cell phone and several others that I use for my website and other "office" needs.

Any suggestions?[/COLOR]

---

### Post by Michael Dooley on 2010-08-03
As per the error message - there may be a problem with your vboxdrv file. Have you run the requested command in the terminal? 

```
sudo /etc/init.d/vboxdrv setup
```

What is your procedure for installing newer versions by the way? I usually just double-click on the newer *.deb file downloaded from the Oracle virtualbox.org site. 

The "permission denied" error message may hold a clue for you to follow. Perhaps you should gain root user privileges by using sudo if you install via terminal.

Thats about all I can think of off the top of my head...

Good luck phil.

---

### Post by flyfishingphil on 2010-08-03
> **Michael Dooley said:**
> As per the error message - there may be a problem with your vboxdrv file. Have you run the requested command in the terminal? 

```
sudo /etc/init.d/vboxdrv setup
```

What is your procedure for installing newer versions by the way? I usually just double-click on the newer *.deb file downloaded from the Oracle virtualbox.org site. 

The "permission denied" error message may hold a clue for you to follow. Perhaps you should gain root user privileges by using sudo if you install via terminal.

Thats about all I can think of off the top of my head...

Good luck phil.
Michael,

Thanks for the reply. Your answer is one of those that makes a person feel like a 40 watt bulb in a 5 watt outlet! (Not very bright!) Had tried to do the "/etc/init" but had forgotten that little part called "sudo" at the start. DUH! 

Works great now. Hope I remember the "sudo" part next time it's left out of the suggestions.

Thanks again.

---

### Post by Michael Dooley on 2010-08-04
>  Thanks for the reply. Your answer is one of those that makes a person feel like a 40 watt bulb in a 5 watt outlet! (Not very bright!) Had tried to do the "/etc/init" but had forgotten that little part called "sudo" at the start. DUH! 

Works great now. Hope I remember the "sudo" part next time it's left out of the suggestions.

Thanks again.

Cool. I'm glad you found your way out of this problem phil. 

Happy to have been of some help.

---

