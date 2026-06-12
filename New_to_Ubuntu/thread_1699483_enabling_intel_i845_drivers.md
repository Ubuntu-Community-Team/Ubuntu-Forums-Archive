---
title: "enabling intel i845 drivers"
date: 2011-03-03
forum: New to Ubuntu
---

### Post by mrstir57 on 2011-03-03
I am brand new to ubuntu  and wondering if this [https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Testing%20upstream%20patch%20for%20i855   ]("https://wiki.ubuntu.com/X/Bugs/Mavericki8xxStatus#Testing%20upstream%20patch%20for%20i855")
will work for the i845. Also it says to "create a file"? how do i go about doing this?

---

### Post by wojox on 2011-03-03
Sure, open a terminal and paste this in:

```
gksudo gedit /etc/X11/xorg.conf
```

Then copy and paste this in:

```

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "vesa"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

```

Save it and reboot. :P

---

### Post by mrstir57 on 2011-03-03
so i copy and paste  the first part and hit enter, then copy and paste the second part in the new window and save? Sorry for the dumb questions i have never used the command line before.

---

### Post by wojox on 2011-03-03
> **mrstir57 said:**
> so i copy and paste  the first part and hit enter, then copy and paste the second part in the new window and save? Sorry for the dumb questions i have never used the command line before.

Yes, you need to create the file with root privileges so that will do it for you.

That's why I said copy/paste. I knew it would be easier. :)

---

### Post by mrstir57 on 2011-03-03
thanks for the help. :)

---

### Post by migrate from windows on 2011-03-03
If you want to enable the intel driver use 'intel' in the place of 'Vesa' in your config file.

---

