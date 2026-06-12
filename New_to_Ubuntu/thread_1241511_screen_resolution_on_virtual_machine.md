---
title: "screen resolution on virtual machine"
date: 2009-08-16
forum: New to Ubuntu
---

### Post by andjer on 2009-08-16
Right, I've successfully installed Ubuntu server and the desktop GUI on a virtual machine. However, I only get an 800x600 resolution. I appreciate that it's because it's a virtual machine and doesn't have access to my hardware drivers that it doesn't know what resolutions it can offer.

How do i give it the right info so that i can increase the screen size?

---

### Post by NovaAesa on 2009-08-16
You will need to install the guest additions to get things like nice screen resolution. I currently am not using Ubuntu, so I can't point out exactly how to install them. I do remember that there is an option in the VBox dialog boxes that allows the guest additions to be downloaded without you having to go look for them somewhere on the internet. Once downloaded, Vbox should automatically mount the ISO, in which case you just need to run the executable on the iso.

---

### Post by longtom on 2009-08-16
> **andjer said:**
> Right, I've successfully installed Ubuntu server and the desktop GUI on a virtual machine. However, I only get an 800x600 resolution. I appreciate that it's because it's a virtual machine and doesn't have access to my hardware drivers that it doesn't know what resolutions it can offer.

How do i give it the right info so that i can increase the screen size?

Had the same problem not too long ago:

[http://ubuntuforums.org/showthread.php?t=1226099](http://ubuntuforums.org/showthread.php?t=1226099)

did it for me.

Good luck

---

### Post by Barafu Albino Cheetah on 2009-08-16
In case of ubuntu, it just works as this
```
cd /media/cdrom
sudo sh VBoxGuestAdditions.sh //don't remember the filename
```
For some other distros (Fedora, Gentoo with hal-based X )things are many times worse

I issue an additional question - is there a way in VirtualBox to set host resolution to 1024*768, guest to 640*480 (for example) and keep guest in fullscreen expanded on the whole screen, not as a small picture with black border? Currently I switch host resolution, and it is annoying thing to do, because it messes up many other things.

---

### Post by andjer on 2009-08-17
> **longtom said:**
> Had the same problem not too long ago:

[http://ubuntuforums.org/showthread.php?t=1226099](http://ubuntuforums.org/showthread.php?t=1226099)

did it for me.

Good luck
I've tried this, installed build-essential linux-header-etc. and installed guest additions. Now when I go to manage my display I only get a 640x480 option - I don't even get 800 x 600 anymore!

I can't be doing with a titchy little ubuntu screen on a large widescreen monitor!

---

### Post by longtom on 2009-08-17
> **andjer said:**
> I've tried this, installed build-essential linux-header-etc. and installed guest additions. Now when I go to manage my display I only get a 640x480 option - I don't even get 800 x 600 anymore!

I can't be doing with a titchy little ubuntu screen on a large widescreen monitor!

In your VB go to Machine > Adjust Window Size or press Host A.  Then resize the window and the resolution should be changing.

Good luck.

---

### Post by andjer on 2009-08-17
Excellent - thanks all - working fine now!!

---

