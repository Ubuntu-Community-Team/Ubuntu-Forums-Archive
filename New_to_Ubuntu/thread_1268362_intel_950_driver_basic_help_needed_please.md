---
title: "intel 950 driver basic help needed please"
date: 2009-09-16
forum: New to Ubuntu
---

### Post by Fatalrewind on 2009-09-16
hi ,im currently running 9.10 netbook remix and i want to enable
Uxa as i believe this should give me better graphics performance
the only problem is that i am reading a Ubuntu help page and don't
know how to edit the correct cfg file.

i am trying to follow everything on this link
[https://wiki.ubuntu.com/X/UxaTesting](https://wiki.ubuntu.com/X/UxaTesting)

but i really dont know what to do .. please help total newbee

---

### Post by orlox on 2009-09-16
Fatalrewind, the file you're looking for is /etc/X11/xorg.conf

To edit it, you can do the following:[LIST]
[*]press alt+F2, type the following: "gksudo gedit"
[*]It will ask for your password, and open a text editor. Open the file /etc/X11/xorg.conf
[*]Look for a section that says something like:
```

Section "Device"
        Identifier    "Configured Video Device"
        # ...
EndSection

```
Where "# ..." could be anything (not neccesarily a single line). Modify this section so it looks like this:
```

Section "Device"
        Identifier    "Configured Video Device"
        # ...
        Option        "AccelMethod" "uxa"
EndSection

```
You just need to add the new line with uxa, not modify any of the other lines.
[*]Reboot, and xorg will be reloaded using uxa acceleration.
[/LIST]

---

### Post by aljoriz on 2009-09-16
try using envyNG

---

### Post by orlox on 2009-09-16
> **aljoriz said:**
> try using envyNG

Very bad idea. He has an intel 950 video card, and envyNG is used to install ATI and nvidia propietary drivers. That surely doesn't apply here.

---

### Post by Fatalrewind on 2009-09-17
hi ,i have opened the editor via thew terminal but when
i browse into the x11 directory theres no xorg.conf.

---

### Post by vantsochev on 2009-09-17
Hi, open terminal and type

```
sudo gedit /etc/X11/xorg.conf
```

enter your pswd and proceed with the previous instructions ;)

---

### Post by Fatalrewind on 2009-09-17
hi

ok i have created a basic xorg.conf via a different help file
and done sudo.reboot but now when i open the xorg.conf it is blank
there is no text at all.

also i have just browsed into the X11 directory to see if there is an
actual xorg.conf file but there isn't one there ,i followed these instructions

[https://answers.launchpad.net/ubuntu/+source/xorg/+question/56649](https://answers.launchpad.net/ubuntu/+source/xorg/+question/56649)

---

### Post by 3rdalbum on 2009-09-17
> **Fatalrewind said:**
> hi

ok i have created a basic xorg.conf via a different help file
and done sudo.reboot but now when i open the xorg.conf it is blank
there is no text at all.

Linux is case-sensitive. This means that the "X11" folder is different to the "x11" folder. Make sure you're using the correct case.

---

### Post by Fatalrewind on 2009-09-17
I am definitely in the correct directory and using the correct lettering
but theres no xorg.conf file unless i create one ,if i choose to open
directly via the terminal i get a blank file.

I also wanted to edit the main .conf so i could hide the splash text
when Ubuntu boots up and shuts down as it currently shows system calls
for boot/shutdown and when i followed those instructions on this forum
i had the same problem that all .conf files were showing as blank.

thanks for all the help so far

Paddy

---

