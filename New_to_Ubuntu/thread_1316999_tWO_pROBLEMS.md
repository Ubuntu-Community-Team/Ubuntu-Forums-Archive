---
title: "tWO pROBLEMS"
date: 2009-11-06
forum: New to Ubuntu
---

### Post by thesaintinscotland on 2009-11-06
Ubuntu 9.10
 
Problem 1 - system is not mounting external USB hard disk automatically.
 
Problem 2 - all windows appear full screen and the little icons in the top right to reduce size and to minimise to toolbar have gone.  I can't find any way to reduce their size to part screen.
 
Question 1 - how do I force system to mount the external hard drive automatically?
 
Question 2 - what's causing my windows to be full screen and how can I correct this behaviour?
 
Many thanks

---

### Post by Sugi on 2009-11-06
What format is your external's partition?  And you should check if it's partitioned correctly.

Try using keyboard shortcut for changing the size of nautilus' windows.  "Alt + Space Bar" Does it bring up any menus?

Sugi

---

### Post by Lateralis on 2009-11-06
Are you still using Jaunty or are you now using Karmic Koala?  

There is a known issue in Karmic affecting just some users.  (I was one of them.)  There is a proposed update (so not in the main repository just yet) for udev which seems to fix the problem for most people including myself.  To get this update you can either:

1) Wait for the update to be moved to the main repository.  Dunno when that will be.
2) Allow updates from the proposed repository and install the updated udev.  To do this, go to System -> Software Sources and click on the Updates tab.  There, check the "Proposed updates" option.  Please note that updates in the proposed repository are just that... proposed updates.  Any update that is safe and been tested to death will be in the main repository.  For this reason, inexperienced users and those not wishing to take part in bug testing/hunting/eliminating should not by default use the proposed updates repository.  If you do decide to go down this route it is strongly advised to disable the proposed repository in your sources list after you get the udev update.  


To mount a disk manually you need to use the *mount* command.  Firstly, you need to identify what the disc is:  

```
sudo fdisk -l
```

Once you know what the disc is - will be something like /dev/sdb1 or such... if you are unsure then post the output in here - then you can mount the device to a directory of your choosing, for example:

```

sudo mkdir /mnt/<name>
mount <device> /mnt/<name>

```

where <name> is some name you want to call the directory and <device> is the location of the disk you discovered using fdisk. 

Hope that helps!

---

### Post by thesaintinscotland on 2009-11-06
> **Sugi said:**
> What format is your external's partition? And you should check if it's partitioned correctly.
 
Try using keyboard shortcut for changing the size of nautilus' windows. "Alt + Space Bar" Does it bring up any menus?
 
Sugi
 
Alt+Spacebar enabled me to resize the window, but I have to do it every time.  Is there a default somewhere I have inadvertently toggled download applications / environments?

---

### Post by decoherence on 2009-11-06
> **thesaintinscotland said:**
> Alt+Spacebar enabled me to resize the window, but I have to do it every time.  Is there a default somewhere I have inadvertently toggled download applications / environments?

have you been experimenting with the Netbook Remix packages by any chance?

If so, disable Maximus by going to System > Preferences > Startup Applications and unchecking it, then log in again.

---

### Post by thesaintinscotland on 2009-11-06
> **decoherence said:**
> have you been experimenting with the Netbook Remix packages by any chance?
 
If so, disable Maximus by going to System > Preferences > Startup Applications and unchecking it, then log in again.
 
That did it!
 
Owe you one.

---

