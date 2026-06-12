---
title: "[SOLVED] How to change screen resolution?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by AlexOslo on 2008-12-06
I am running Ubuntu 8.04 and am having trouble knowing what to do with the Ubuntu instruction page [https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution).

I checked the screens recommended resolution (with screen buttons) and found it to be 1280x1024 85 hz.

> 
Setting xrandr commands in .xprofile

A user's ~/.xprofile file is executed on Xorg startup if it exists and is executable. You can copy and paste xrandr command line strings into this file so they're executed when you log in. For example:

$ xrandr --output VGA-0 --mode 800x600

The line "copy and paste xrandr command line strings into this file (above)" doesn't tell me much. Does anyone know how to locate this "~/.xprofile file"?

Sincerely,
Alex

PS. I started a similar thread last week (but got no reply to this question) at [http://ubuntuforums.org/showthread.php?t=996172](http://ubuntuforums.org/showthread.php?t=996172)

---

### Post by mapes12 on 2008-12-06
In Terminal ```
gksudo displayconfig-gtk
``` then when the GUI pops up select your hardware and desired screen res from there. If that doesn't work then take a look at the settings in your xorg.conf file.

---

### Post by newbee70 on 2008-12-06
> **AlexOslo said:**
> I am running Ubuntu 8.04 and am having trouble knowing what to do with the Ubuntu instruction page 
I checked the screens recommended resolution (with screen buttons) and found it to be 1280x1024 85 hz.



The line "copy and paste xrandr command line strings into this file (above)" doesn't tell me much. Does anyone know how to locate this "~/.xprofile file"?

Sincerely,
Alex

PS. I started a similar thread last week (but got no reply to this question) at [http://ubuntuforums.org/showthread.php?t=996172](http://ubuntuforums.org/showthread.php?t=996172)


Alex, I'm sorry but there is not enough info in your post for me to offer any help. 

if your using gnome I'm sure you went into "system / preferences / screen resolution" and changed or attempted to change your settings there.

What desktop are you running <gnome, kde, other>.

---

### Post by AlexOslo on 2008-12-06
Thank you, Mapes12 and Newbee70, both worked perfectly well (each in their own way)!

Alex

---

