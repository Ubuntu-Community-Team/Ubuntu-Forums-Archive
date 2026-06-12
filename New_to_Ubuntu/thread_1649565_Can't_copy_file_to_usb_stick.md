---
title: "Can't copy file to usb stick"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by drmax on 2010-12-20
Hello,
I am trying to copy a .doc file to my usb stick so I can copy it to my windows computer and print it.

I can't figure out what to do to get the usb stick to work.
When I go to places computer I can see "usb 2.0 sd mmc reader".
When I right click I do not get an option to paste the .doc file.
It does not seem to be recognized, when I go to places computer properties permissions it says permissions could not be determined.
I searched here and google, but could not figure it out.
I am using Karmic Koala.  The stick is made by zeikos.
Any help would be greatly appreciated, and please assume nothing, I'm sure you can tell I am a total beginner.
Thanks,
drmax

---

### Post by cariboo on 2010-12-20
Probably the easiest way to copy the file is to run nautilus as root. Press Alt-F2 and type:

```
gksu nautilus
```

enter your password, and you're ready to go.

---

### Post by drmax on 2010-12-20
Thanks for your reply Cariboo907.
I tried as you suggested, no change.  I only have the option for a few of the choices, that is they are black, I can "open, rename, properties, etc".  The option to paste is not even a choice in the list, greyed or black.
drmax

---

### Post by jarviser on 2010-12-20
Usual trick is to plug in the stick after booting, that way _you_ mount the stick and not Root.
So take it out, reboot, then plug in and wait a moment or so.

"SD reader" doesn't sound like a stick, however assuming it is a viable SD reader device with an SD card in it, after plugging in you should get an icon on the desktop. Double click on that (or double click on the icon in Places/Computer) and it should open OK.

Another thing to watch out for is if you delete anything from the drive it sometimes gets shifted to a .trash folder in the stick which is only visible if you Ctrl+H to view hidden files. So always right-click on the icon and hit Eject and the deleted items folder is usually offered up for deletion

---

### Post by Golem XIV on 2010-12-20
It looks like you are trying to write to a USB SD card reader.

If this is so, make sure that the SD card is not write protected (it has a small slider on one of the sides to enable and disable write protect).

---

### Post by jarviser on 2010-12-20
..or is there an SD card in it?

---

### Post by amjjawad on 2010-12-20
> **drmax said:**
> Hello,
I am trying to copy a .doc file to my usb stick so I can copy it to my windows computer and print it.

I can't figure out what to do to get the usb stick to work.
When I go to places computer I can see "usb 2.0 sd mmc reader".
When I right click I do not get an option to paste the .doc file.
It does not seem to be recognized, when I go to places computer properties permissions it says permissions could not be determined.
I searched here and google, but could not figure it out.
I am using Karmic Koala.  The stick is made by zeikos.
Any help would be greatly appreciated, and please assume nothing, I'm sure you can tell I am a total beginner.
Thanks,
drmax

1) Plug it to your Windows Computer
2) Make sure it does work
3) DO NOT take it out unless you choose: Safely Remove
4) Try it now on Ubuntu.

---

### Post by drmax on 2010-12-20
Thank you very much for your help Golem XIV and jarviser.  In my ignorance I was definitely trying to copy to a sd reader, not a sd memory stick, I now know the difference.  I plugged in a memory stick and was immediately able to copy the file over, and then read it on my windows machine, using the guidance provided.  Please don't hurt your eyes as you roll them.
I can't tell you how kind it is of you to take your time to help a poor lost soul like me.
Happy Holidays,
drmax

---

