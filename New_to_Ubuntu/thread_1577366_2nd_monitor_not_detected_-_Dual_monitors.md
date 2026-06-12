---
title: "2nd monitor not detected - Dual monitors"
date: 2010-09-18
forum: New to Ubuntu
---

### Post by Gameboyman99 on 2010-09-18
[SIZE=3]Hola,[/SIZE]

I was reading up on how to have dual monitors in Ubuntu, but all I found were old posts that I can't use(E.g., /etc/X11/xorg.conf which is no longer usable/valid). My 2nd monitor isn't even showing up in the **System>Preferences>Monitors** window, and when I click **Detect Monitors** it doesn't do anything. Windows XP(Ugh, I know, but it's the best OS Microsoft created... yet) will detect my 2nd monitor and extend my desktop. Ubuntu won't even detect it...:confused: Any _new_ ways to make it work?

    [SIZE=3]Thx in advance[/SIZE],
        [FONT=Comic Sans MS][SIZE=2][COLOR=DarkOrange]Gameboyman99[/COLOR][/SIZE][/FONT]

---

### Post by themusicalduck on 2010-09-18
Do you know what graphics card you have?

If not, open a terminal and enter this ```
lspci | grep VGA
``` and post the output here.

---

### Post by Gameboyman99 on 2010-09-18
I have three: One soldered to my motherboard(Which didn't work w/ Windows or Ubuntu)
nVidia(Main monitor; the one I'm using)
Matrox(from 1995, 'bout as old as they get but it works w/ windows :/ )

---

### Post by buntunub on 2010-09-18
Use nvidia-settings to configure your 2nd monitor.

---

### Post by formaldehyde_spoon on 2010-09-18
xorg.conf may not be used by default, but it's certainly still usable and valid.

Does Ubuntu recognize the card? (type ''lspci'' or ''lshw'' into a terminal and see if it gets listed) 

Do you have drivers installed for the card?  Try Matrox's site.  Not all Matrox cards have Linux drivers. 

Once the answer to both of these is yes, your next step is probably playing with xorg.conf ;)

---

### Post by Gameboyman99 on 2010-09-19
```
VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
```

```
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```

I've done both of those... ?????

---

### Post by formaldehyde_spoon on 2010-09-19
> **Gameboyman99 said:**
> ```
VGA compatible controller: Matrox Graphics, Inc. MGA 2064W [Millennium] (rev 01)
``````
You do not appear to be using the NVIDIA X driver.  Please edit your X configuration file (just run `nvidia-xconfig` as root), and restart the X server.
```I've done both of those... ?????

You need to be a bit more verbose...

You can't mix multiple version of the nvdia driver, or nvidia with nouveau, (not sure about nvidia + nv), but I assume nvidia + mga is fine (I have no eperience with that, someone else should be able to confirm this is possible.

You need the matrox driver AND the nvidia driver installed before you start playing with xorg.conf. Sounds like you don't have the nvidia driver at the moment... 

The mga driver supports your matrox card (search mga in synaptic), and of course the nvidia driver is available through System > Admin > Hardware Drivers.  You should be ready to edit your xorg.conf then.

---

### Post by Gameboyman99 on 2010-09-21
Umm... I'm gonna give up. Windows just has more experience with this. And is kinda more user-friendly(Don't worry I'll still use Ubuntu xD)

---

