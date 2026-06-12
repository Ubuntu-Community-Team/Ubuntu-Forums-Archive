---
title: "NVIDIA resolution won't save"
date: 2011-02-22
forum: New to Ubuntu
---

### Post by jermza on 2011-02-22
This is driving me nuts.

I got myself a 27" Dell with great resolution.  However, every time Ubuntu boots up, it reverts the resolution to a lousy one (and not the one I want), so I have to keep opening the Nvidia X Server Settings and clicking it.

When I "save to X configuration file", a window opens asking me where to save it.  It previously threw some "failed to parse" error, but I followed a post on these forums which seemed fine because it doesn't give me an error anymore.  In fact, it saves fine.

At least, I THINK it does.  When I reboot, it goes back to the incorrect resolution.

I've even pasted that location to the config file in my startup applications and no difference.

ANY help will be greatly appreciated.

---

### Post by TeoBigusGeekus on 2011-02-22
You should open it as root with
```
gksu nvidia-settings
```

---

### Post by jermza on 2011-02-22
> **TeoBigusGeekus said:**
> You should open it as root with
```
gksu nvidia-settings
```
Done that.  Doesn't seem to make any difference...

---

### Post by komputes on 2011-02-22
This is a common problem when using the nvidia binary driver. First you want to start nvidia-settings as administrator.

```
$ sudo nvidia-settings
```

Then you want to set your monitors and save to the X config file. The location of this file should be /etc.X11/xorg.conf - IF nvidia-settings complains at this point about the parsing of the file or that it can't save, the workaround is to move/delete the xorg.conf file:

```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old-fp
```

... and then try saving again.

---

### Post by jermza on 2011-02-22
> **komputes said:**
> This is a common problem when using the nvidia binary driver. First you want to start nvidia-settings as administrator.

```
$ sudo nvidia-settings
```Then you want to set your monitors and save to the X config file. The location of this file should be /etc.X11/xorg.conf - IF nvidia-settings complains at this point about the parsing of the file or that it can't save, the workaround is to move/delete the xorg.conf file:

```
$ sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old-fp
```... and then try saving again.
Done that a few times.  Makes absolutely no difference.

Must I put the location of that file into my startup apps?

---

### Post by jermza on 2011-02-22
Absolutely nothing works.  This is heavily frustrating.  All I want is for the resolution to stay as I've set it, when Ubuntu boots up.

Any more help, please?

---

### Post by spook1980 on 2011-02-22
click save to X configuration file then on the pop up click show preview copy the preveiw then type in a terminal...

sudo gedit /etc/X11/xorg.conf

delete whats in there and paste what u copyed earilyer
and save the file, that should solve all your problems

---

### Post by jermza on 2011-02-22
> **spook1980 said:**
> click save to X configuration file then on the pop up click show preview copy the preveiw then type in a terminal...

sudo gedit /etc/X11/xorg.conf

delete whats in there and paste what u copyed earilyer
and save the file, that should solve all your problems
I've done that over and over again.  I've tried everything in this thread, but NOTHING makes a difference.  When Ubuntu boots up, the incorrect resolution loads and I have to change it manually.

I'm willing to try more things.  Any more help?

---

### Post by lncoll on 2011-02-22
If in any other user you can save the resolution and it works:
Just remove or rename the file ~/.config/monitors.xml

```
user@host~$ mv .config/monitors.xml .config/monitors.xmlbak
```

This file keeps your monitor configuration in a per-user basis.

---

### Post by yzfvie on 2011-02-22
I had the same problem and was never able to solve it until I upgraded to Ubuntu 10.10

---

### Post by jermza on 2011-02-23
> **lncoll said:**
> If in any other user you can save the resolution and it works:
Just remove or rename the file ~/.config/monitors.xml

```
user@host~$ mv .config/monitors.xml .config/monitors.xmlbak
```This file keeps your monitor configuration in a per-user basis.
This "seems" to have worked.  The last couple times, UBuntu has loaded correctly.

Hold thumbs...

---

### Post by spook1980 on 2011-02-23
> **jermza said:**
> I've done that over and over again.  I've tried everything in this thread, but NOTHING makes a difference.  When Ubuntu boots up, the incorrect resolution loads and I have to change it manually.

I'm willing to try more things.  Any more help?

uncheck merge

---

### Post by komputes on 2011-02-24
> **jermza said:**
> I'm willing to try more things.  Any more help?

Which Ubuntu release are you using? (lsb-release -a)
Which nvidia driver version are you using? (jockey-gtk)
What video card do you have? (lspci -nnk)

---

### Post by jermza on 2011-02-25
> **jermza said:**
> This "seems" to have worked.  The last couple times, UBuntu has loaded correctly.

Hold thumbs...

This seems to have worked, for now.

I'm going to mark this as resolved, for the time being.  Thanks for your help.

---

