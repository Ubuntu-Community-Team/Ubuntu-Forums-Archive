---
title: "Monitor issues"
date: 2009-11-03
forum: New to Ubuntu
---

### Post by khsaunderson on 2009-11-03
I have just installed Wubi and am having problems with my monitor settings (although everything else is working fine).  I have searched all over the place for a resolution, but can't seem to find anything I understand (sorry to say I've been a Windows user up until today).

Basically, whenever I boot my PC up with Ubuntu my monitor says that the screen is out of range, so I can't actually see my new installation at all.  The only way I can get to it is by plugging in another monitor, setting the screen resolution to 1024x768 (the max my old monitor will take).  So, it all looks fine.  However, when I turn my PC off and on again the same thing happens, as the screen resolution hasn't been saved.

I have tried updating the startup resolution to 800x600 to be safe (by downloading the Startup Manager) and that all saves fine.  So it's obviously the main screen resolution that isn't saving.  

All of the forums I've looked at talk about conf files that I don't seem able to find.  I assume it's too much to ask that there's a lovely app sitting out there with a nice GUI that I can use to save my resolution?  Or if not, is there any kind person out there who will give me a total idiots guide on how to do it through the command line.

Thank you in advance.  And sorry for being slow - I am still learning!

Cheers
Kate

---

### Post by cariboo on 2009-11-03
Depending on the graphics adapter, you can set the horizontal and vertical refresh rates in /etc/X11/xorg.conf. eg:

```
Section "Monitor"
    Identifier     "Configured Monitor"
    HorizSync       28.0 - 95.0
    VertRefresh     50.0 - 120.0
EndSection
```

I found using an nvidia graphics adapter, run:

```
nvidia-xconfig
```

from the command line will set generic refresh rates, so it is just a matter of editing the file with the refresh rates for you monitor, which can be found at the manufacturers web site.

---

### Post by khsaunderson on 2009-11-10
Thanks for this.  I'm being a bit slow though - when I go into the /etc/x11 folder there isn't a file called xorg.conf.  I have shown all the hidden files, but the only config file in there is called xwrapper.config

I found something on the web that said it might not exist, and so i should create it by typing "xorg -configure" but i got a message back in the terminal saying "no command 'xorg' found"

Any help would be appreciated

Thanks

---

### Post by khsaunderson on 2009-11-10
As an addition to this, I have found an executable file called xorg in /usr/bin - is that anything I should be looking at?

---

### Post by khsaunderson on 2009-11-13
Hi
can anyone help me with this?
Thanks
Kate :KS

---

### Post by khsaunderson on 2009-11-23
Guess that means I'll stick with windows then :(

---

