---
title: "Open Office Writer doesn't update screen on doc edit"
date: 2009-10-21
forum: New to Ubuntu
---

### Post by ginestre on 2009-10-21
hello people,

Open Office writer doesn't properly update the screen when I cut text from a document unless I minimise and then remaximise the document itself. But it does update the document in memory, so what I can see on the screen does not correspond to what is in the document in memory. This makes it impossible to use.

I don't know if it's an OOo problem, a Ubuntu problem or something to do with their interfacing badly with each other, or with gnome. Other software doesn't have this issue, so far as I can tell. 

I'm using Open Office Writer (v 3.0.1 from the repositories and updated etc) on Ubuntu 9.04, again patched, running on a Dell Latitude D80 laptop.

Grateful for any ideas: I just can't use it like it is.

---

### Post by HereInOz on 2009-10-21
The first thing I would do is to turn off Compiz, if you are running it, and turn off Visual Effects, so you go back to a basic desktop configuration.

If this makes any improvement, then at least you know where the problems lie.  

I know that some nVidia drivers on some video cards caused odd things to happen with OOWriter, so that could be your issue. 

Also try messing around with the OOWriter View options in Tools > Options > General.

---

### Post by a7ndrew on 2009-10-21
I had a problem like this a while ago, I think it was happening in OO under Windows and Linux. It doesn't seem to be happening to me any more, it may have stopped when I updated to 3.1, I'm not sure. 

On the other hand I had nVidia chip based graphics cards on both systems, so that could have been it as well. I'd try a clean install of OO 3.1.

---

### Post by jonnyara on 2009-10-21
Solutions?

I think this is a known issue with the Nvidia drivers. Either:
1. Try:
System -> preferences -> compizconfig settings manager
Click Utility
Click Workarounds
Check Force Sychronization between X and GLX

or

2. Turn off compiz:
System -> Preferences -> Appearance
Click Visual Effects
Switch to Normal or None.


(from [http://www.proz.com/forum/office_applications/144583-open_office_display_malfunctioning_under_ubuntu.html](http://www.proz.com/forum/office_applications/144583-open_office_display_malfunctioning_under_ubuntu.html) and [http://ubuntuforums.org/showthread.php?t=1221326](http://ubuntuforums.org/showthread.php?t=1221326))

---

