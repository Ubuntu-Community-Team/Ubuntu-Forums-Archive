---
title: "No compositing in metacity"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by longtom on 2009-08-23
Hi,

I can't activate any visual effects in metacity.

Tried to change my drivers for my intel chipset - no luck.

Here's my display:

```

 description: VGA compatible controller
       product: 82945G/GZ Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list
       configuration: latency=0

```

When I try to activate compiz (which I don't want to do) I get this error:

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 00:02.0 0300: 8086:2772 (rev 02) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x1024) to maximum 3D texture size (2048): Passed.
Checking for nVidia: not present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0

```

Any suggestions welcome.

---

### Post by longtom on 2009-08-24
bump

---

### Post by earthpigg on 2009-08-24
bug report i filed a while back:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/395641](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/395641)

copypasta:

> some users, such as this one:

[http://ubuntuforums.org/showthread.php?t=1203050](http://ubuntuforums.org/showthread.php?t=1203050)

would like to use software (such as awn or gnome-do with the docky theme) that requires compositing, but are unable to use compiz due to hardware requirements.

metacity itself is capable of composing, which would let users install software requiring it, but enabling it is so unintuitive that most users simply think they are out of luck.

_***the current way to do it is outlined here:***_

[http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/](http://tombuntu.com/index.php/2008/03/31/enable-metacity-compositing-in-gnome-222/)

it involves a lot of command line stuff that can scare novice users away.

the option to enable metacity compositing should be in system -> preferences -> appearance -> visual effects.

2 minute mockup:

[http://i109.photobucket.com/albums/n59/earthpiglite/metacitycompositing.jpg](http://i109.photobucket.com/albums/n59/earthpiglite/metacitycompositing.jpg)

---

### Post by earthpigg on 2009-08-24
also, your hippo is rad.

---

### Post by longtom on 2009-08-24
> **earthpigg said:**
> bug report i filed a while back:

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/395641](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/395641)

copypasta:

Thank you.  I stumbled upon that before and tried it.  Still don't get it right to have reflection in my cairo-dock.

I had that before - and than it disappeared after I did...not really sure what...

> 
also, your hippo is rad.


Thanks.  This is Hilda and she is actually a pigmy hippo and lives with us together with Herbert.  That would be here:  
[www.cango.co.za](www.cango.co.za)

Your pig is not bad either!  Certainly stands out from all the squirrels around lately...

---

### Post by longtom on 2009-08-24
bump

---

### Post by longtom on 2009-08-25
bump

---

### Post by alienclone on 2009-09-22
since enabling compositing in metacity following the instructions on Tombuntu i get random flashes in the middle of my screen, it is too fast to see what it is.

---

### Post by alphacrucis2 on 2009-09-22
To enable compositing in metacity:

Applications-> System Tools -> Configuration Editor

When the configuration editor starts:

apps -> metacity -> general. Tick the box that says compositing manager.

If you don't have the Configuration editor installed, the package is called gconf-editor.

---

### Post by kimberlite on 2009-09-22
xcompmgr can be a useful alternative to compiz. It is available from the repos.

---

### Post by longtom on 2009-09-22
> **kimberlite said:**
> xcompmgr can be a useful alternative to compiz. It is available from the repos.

I try anything right now.  Once I have installed it, how would I go about activating it and have a go at the settings?

---

