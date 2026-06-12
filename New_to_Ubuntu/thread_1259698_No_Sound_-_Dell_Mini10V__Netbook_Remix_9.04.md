---
title: "No Sound - Dell Mini10V / Netbook Remix 9.04"
date: 2009-09-06
forum: New to Ubuntu
---

### Post by franklin_m on 2009-09-06
Absolute beginner with Ubuntu. Loaded in a dual boot configuration with my new Dell Mini10V,the model with the slower of the two processors.

Cannot get a single sound to come out of the darned thing in Ubuntu.  WinXP works great.  Help would be greatly appreciated.

[email]frank.mellott@earthlink.net[/email]

Thanks,
Frank

---

### Post by Sealbhach on 2009-09-06
Hi,
We will need to know what version of Ubuntu you have installed.

.

---

### Post by franklin_m on 2009-09-07
I'm running the netbook remix 9.04. Is there more detailed version info available? If so, I just need to know how to find it.

Thanks,
Frank

---

### Post by Sealbhach on 2009-09-07
OK, try this here. It will tell Ubuntu to load up the drivers in the right way.

Open a terminal, you can find this in the menu: Applications/Accessories/Terminal.

Copy and paste this command:

```
gksudo gedit /etc/modprobe.d/alsa-base.conf
```

This will open up a text file, scroll right down to the end of the text and add another line with this text:

[COLOR=#009900]options snd-hda-intel model=dell

[COLOR=Black]Make sure to save the changes and close the file. Reboot.

Hopefully this will get your speakers working.

.
[/COLOR][/COLOR]

---

