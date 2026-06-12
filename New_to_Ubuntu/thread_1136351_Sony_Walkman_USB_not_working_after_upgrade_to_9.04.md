---
title: "Sony Walkman USB not working after upgrade to 9.04"
date: 2009-04-24
forum: New to Ubuntu
---

### Post by humphreybc on 2009-04-24
So in 8.10 I would plug in my Sony MP3 Walkman (NWZ-S616F) and it would recognize it, mount it automatically and open it in nautilus for me to drag and drop my songs onto.

In 9.04 it recognizes it as something with a different name "Sony Corp. WALKMAN" and then mounts it, but nothing shows up in the folder.. it's empty. It says up the top "These files are on a Digital Audio Player" and then has a button saying "Open VLC media player" to the right.

Any ideas??

---

### Post by yenliangl on 2009-04-25
Check this out

[https://bugs.launchpad.net/ubuntu/+bug/347902](https://bugs.launchpad.net/ubuntu/+bug/347902)

and the temporary solution is to kill the process of gvfs-gphoto2-volume-monitor

---

### Post by humphreybc on 2009-04-29
This bug still hasn't been fixed... it's very annoying not being able to put songs onto my MP3 player.

---

### Post by apolonio on 2009-05-17
For my NWZ-S616F, It was necessary to kill gvfs-gphoto2-volume-monitor, after that connect the device and that's it. Nautilus will open it as a normal usb memory and you can put music into it again.
I hope we will have an official work around soon, I have some problems with Hal with intrepid as well, it looks like sony walkman is not so ubuntu compatible.
):P

---

### Post by 3rdalbum on 2009-05-17
The "kill gphoto" trick hasn't worked for me, and the "edit this text file" thing temporarily stopped my CDs from automounting. The Walkman bug only affects Gnome, so whenever I need to work with my MP3 player I just load up KDE. Not an elegant solution but it works until somebody pulls their finger out and fixes the problem!

---

### Post by xile_ on 2009-05-19
Killing the _gvfs-gphoto2-volume-monitor_ worked for me.:)
(unplug the device and plug it in again - should be automatically mounted)

Peripheral: NWZ-A815
Ubuntu Ver: 9.04 (jaunty)
Laptop Mod: IBM Thinkpad x61s

---

### Post by shadowlands on 2009-05-19
How do I kill it? Can you provided step by step directions or a link to the directions on how to kill it so I can use my sonywalkman.

---

### Post by 3rdalbum on 2009-05-19
> **shadowlands said:**
> How do I kill it? Can you provided step by step directions or a link to the directions on how to kill it so I can use my sonywalkman.

```
killall gvfs-gphoto2-volume-monitor
```

If that doesn't work, time to install KDE :-)

---

### Post by blackSP on 2009-05-25
I've posted [**this link**]("http://ubuntuforums.org/showthread.php?t=1166391"), got many good tip and decided I want the Sony NWZ-S639F 16gb, their smallest player with excellent (sopund) ratings.

But reading the problems you all have maybe I shouldn't???

What do you think?

---

### Post by C J on 2009-05-26
killall gvfs-gphoto2-volume-monitor

worked for me thanx:D

---

### Post by White Rasta on 2009-06-01
Another way (gui) is to open system monitor
goto processes tab
scroll down to highlight: gvfs-gphoto2-volume-monitor, and click the end process button
plug in player
Rock on

I hope this gets fixed soon, it's a bit of a pain

---

