---
title: "Loud noise when shutdown or restart on ubuntu 9.04"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by Hemenesgard on 2009-09-06
Hi! After i upgraded my Ubuntu from 8 to 9, a sound problem occurred. Every time i shutdown or restart my desktop, the internal speacker do a loud bip(like the common motherboards bip when boots, but much longer). There's something i can do to cancel this, or the new Ubuntu do this sound, intrinsically?
Thank's Bruno

---

### Post by FreewheelinFrank on 2009-09-06
In volume Control, disable PC Speaker.

---

### Post by Hemenesgard on 2009-09-06
Can you explain me with more details please, because my Ubuntu is in portuguese and i didn't find this option. Where do i find the "Volume Control"?

---

### Post by misterfixit on 2009-09-06
> **Hemenesgard said:**
> Can you explain me with more details please, because my Ubuntu is in portuguese and i didn't find this option. Where do i find the "Volume Control"?

Go to your menu and then go to System and then go to Preferences and then go to Sound.  When the Sound control window opens decide if you want sound effects.  You can disable the PC Speaker there.  The PC Speaker is an antiquated or legacy requirement which goes back in history to when PC's did not have sound cards.

Also, look at your top menu bar and locate the small icon of a speaker; you can adjust sound levels there either by left-clicking on the icon or by placing your curson on the icon and then using your middle thunm wheel (if you have one).

Boa Sorte!

Dave

---

### Post by XCan on 2009-09-06
Add 
```
 blacklist pcspkr 
``` into ```
 /etc/modprobe.d/blacklist.conf 
``` Tip: Open the configuration file as root, i.e., ```
 gksudo gedit /etc/modprobe.d/blacklist.conf 
```

---

### Post by Hemenesgard on 2009-09-06
I would like to thank everyone who answered. 

misterfixit, i followed all you said but there's not such an option there. I'm blind, or its not so evident.
 XCan, the codes you gave me worked, thanks! You should only add that i need to write it in a terminal like this:

 [B]sudo gedit /etc/modprobe.d/blacklist.conf

 [/B]to avoid confusions by the noobs like me, because we can't save the file without administrator password.

---

### Post by XCan on 2009-09-07
You're welcome. Fixed my previous post as well, gksudo is generally preferred over sudo when dealing with graphical applications. :)

---

### Post by LewRockwell on 2009-09-07
> **XCan said:**
> You're welcome. Fixed my previous post as well, gksudo is generally preferred over sudo when dealing with graphical applications. :)

[http://ubuntuforums.org/showthread.php?t=1255407](http://ubuntuforums.org/showthread.php?t=1255407)

.

---

