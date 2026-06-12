---
title: "nvidia accelerated driver"
date: 2011-03-13
forum: New to Ubuntu
---

### Post by firefya on 2011-03-13
the nvidia accelerated driver for my ASUS laptop cannot be enabled. I tried using the additional drivers app, but I get a failure to enable message.

Is there a sudo code i can use to bypass this?

BTW my comp uses NVIDIA optimus, so  the gfx card is built into the motherboard,

---

### Post by PunkLV on 2011-03-13
By "nvidia accelerated driver" you mean the ones Ubuntu suggested as a "Restricted drivers available" balloon pop-up?
If that is the case, then telling exactly what nvidia card and laptop model are you using will help.

---

### Post by firefya on 2011-03-13
Asus AF2-Jc X1

Nvidia 310m

after installing the recommended updates the additional driver app worked, issue is, upon restarting my terminal came up.

I have no idea what to do, do i need to configure the driver manually?

---

### Post by PunkLV on 2011-03-13
```

```
```
sudo service gdm3 stop
```
If you receive "Unrecognized service" use **gdm**
```

sudo apt-get install gcc g++
sudo apt-get install linux-headers-`uname -r`
```

If you are prompted with [Y/N] for installing new headers -- install, then reboot and continue.
Else:
```
sudo apt-get install nvidia-glx
sudo service gdm3 start
```
Post results when you get to this point.

---

### Post by firefya on 2011-03-13
package is not available, but is referred to by another package, this may mean that the package is missing, has een obsoleted, or is only available from another source.
no installation candidate

do I just need to start over? the boot file is on a usb

---

### Post by PunkLV on 2011-03-13
Which package exactly?

---

### Post by firefya on 2011-03-13
right now im trying to access my desktop and exit the terminal.

IM AT GROUND ZERO why?

---

### Post by PunkLV on 2011-03-13
Please answer yes/no
1: Do you get past GRUB bootmenu?
2: At the moment when Desktop Environment is about to load; does the screen stays black/dribbles/distorts/anything alike?
3: By pressing ALT+CTRL+F1 are you prompted to log in?

---

### Post by firefya on 2011-03-13
1. never get past the boot menu
2. desktop environment never loads
3. no

---

### Post by PunkLV on 2011-03-13
Right.
Then please tell what do you mean by
> the boot file is on a usb
Otherwise, probably, you will have to boot LiveCD and fix things from there, or reinstall. The last option seems too harsh at this point though.

And we need someone more experienced with GRUB and installing from USB-pen

---

