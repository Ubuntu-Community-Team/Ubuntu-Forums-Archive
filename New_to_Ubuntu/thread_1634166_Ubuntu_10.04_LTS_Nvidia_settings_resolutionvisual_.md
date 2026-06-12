---
title: "Ubuntu 10.04 LTS Nvidia settings resolution/visual effects quirk"
date: 2010-11-30
forum: New to Ubuntu
---

### Post by privyet on 2010-11-30
Hi guys, I've got a tiny problem I couldn't get my head around and was hoping if one of you could help out. See, I did a fresh install of Ubuntu and installed an nvidia driver through the hardware manager. The recommended version was Version 96 and I got it running. After doing a reboot everything else seemed ok. Desktop effects were at high and so on. Except for one thing though, the Nvidia Settings caps the resolution at 640x480 and below. I opened xorg.conf using nano and noticed that there were only three paragraphs worth of entries so I defaulted into running:

sudo dpkg-reconfigure xserver-xorg

and restarting X. I went to Nvidia settings and checked for the right resolution on my monitor and saved it to the X configuration file. Some error about failing to parse returned. 

Here's the quirk: after doing a reboot, although the resolution was preserved it was that the desktop effects were subsequently disabled in return. From then on, setting it back to "high" wouldn't do anything at all. As if its permanently set to "none". I'm no computer major, and I don't have enough in depth knowledge of Linux to figure this puzzle out nor the office time. But it would certainly be handy if I had help resting this. Any help would be greatly appreciated. Thanks :D

---

### Post by realzippy on 2010-11-30
*Some error about failing to parse returned*


...sounds like the old "parsing" error.
Delete existing xorg.conf,create new one,then open nvidia-settings:

```
sudo rm /etc/X11/xorg.conf
sudo nvidia-xconfig
sudo reboot

```

After rebooting run:
```
gksudo nvidia-settings
```
...then it should apply your desired resolution without parsing-error.

And welcome to UF!

---

### Post by privyet on 2010-11-30
Alright thanks! Though, I still don't understand why the visual effects settings wont actually set into anything other than "none". Think I should remove the driver and redo the whole thing from the start?

---

### Post by realzippy on 2010-12-01
> **privyet said:**
> Alright thanks! Though, I still don't understand why the visual effects settings wont actually set into anything other than "none". Think I should remove the driver and redo the whole thing from the start?

.... because you have run:

sudo dpkg-reconfigure xserver-xorg

Do not run this command when using the nvidia driver,it overwrites
your existing xorg.conf file,which is needed to start the nvidia driver,
which is needed to run desktop effects.The right command would have been:

sudo nvidia-xconfig

---

### Post by privyet on 2010-12-02
Alright I got it. Hey thanks, you're a real pal eh? Cheers!

---

### Post by realzippy on 2010-12-05
Glad you made it;can you mark thread as "solved" (threadtools)?

---

