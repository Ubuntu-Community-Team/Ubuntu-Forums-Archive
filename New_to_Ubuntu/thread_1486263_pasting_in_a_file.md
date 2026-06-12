---
title: "pasting in a file"
date: 2010-05-17
forum: New to Ubuntu
---

### Post by 2roombas on 2010-05-17
I just read this as a possible work around to a problem I'm having. I'm too new at this so I'm a tad confused?! Can someone please explain to me how I go about pasting this in the file they tell me to? The copy/paste I understand, sure, but how and where do I get this file to paste into?
> Workaround E: Disable DRI
Paste the following into /etc/X11/xorg.conf:


Section "Device"
        Identifier      "Configured Video Device"
        Driver          "intel"
        Option          "DRI" "off"
EndSection
This disables 3D acceleration and will make graphics generally slower, but has been reported to help by some users.

---

### Post by drs305 on 2010-05-17
This is a system file so you have to use admin privileges to edit it. 

Open your text editor as root from a terminal (Applications, Accessories, Terminal). You will be asked to provide the password. You won't see anything in the terminal as you type it - just press ENTER when you are finished typing it.

The first command will make a backup copy of the original.

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.original
gksu gedit /etc/X11/xorg.conf
```

Note: Be sure you know what you are about to do when working with Video and/or xorg. If you can't see it, you can't fix it!  ;-)

---

### Post by 2roombas on 2010-05-17
Thanks. I'm having the same problem as the people in this thread [HERE]("http://ubuntuforums.org/showthread.php?t=1471219") and I thought maybe doing those steps from this [LINK]("https://wiki.ubuntu.com/X/Bugs/Lucidi8xxFreezes") that someone posted on the thread might help me. I had tried "a" but that didn't help.

I honestly do not know what I'm doing if I were to do those mentioned steps though, so I think I'll just hold steady with my trusty ol' 9,04 until support runs out for it. Perhaps I'll just have to get a new computer if no one ever figures out this problem the intel graphics card users are having.

---

