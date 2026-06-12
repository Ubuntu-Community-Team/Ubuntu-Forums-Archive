---
title: "screen resolution 10.04 and ATI Rage card"
date: 2011-07-26
forum: New to Ubuntu
---

### Post by buffler on 2011-07-26
Posted previously in the wrong place, I guess. If reposting is a no-no please let me know without excessive flaming.
I loaded 10.04 to a Dell 2650. Smooth as butter, except I can't get higher than 640x480. 
I plumbed the depths of the forum, and found I should to edit the xorg.conf file. Guess what, it ain't there...
I finally found a clue: it appears that the kernel now has something to do with it.  This is part of the notice:
"Kernel mode-setting (KMS) shifts responsibility for selecting and   setting up the graphics mode from X.org to the kernel.  When X.org is   started, it then detects and uses the mode without any further mode   changes.  This promises to make booting faster, more graphical, and less   flickery. "
Guess what: IT DON"T WORK!!!!
So, now it's in the kernel instead of a reachable xconf file or some  other location? If the resolution choices are in some other file, where is it and what's it's name? 
Wow. 
can't shut it off, either. "/etc/modprobe.d/radeon-kms.conf" doesn't exist.
I'll take a flickery load, if I can get one, that is.:confused: so I can have decent screen resolution.
Thanks
Don

---

### Post by LowSky on 2011-07-27
```
sudo gedit /etc/X11/xorg.conf
```

if you dont capitalize the X the file will be blank/non-existent.

also ati prior to the HD2xxx series has little support. basically you might be stuck with some issues that cannot be resolved.

---

