---
title: "touchpad right click not working"
date: 2011-01-29
forum: New to Ubuntu
---

### Post by viditgoyal3009 on 2011-01-29
Hello,

I am using Ubuntu 10.10 on my HP DV6 3050TX. The problem is the right click on the touch pad is not working but an external mouse is allowing me right click. Is it some kind of a driver issue?? How can i fix this problem??

---

### Post by [Snc] on 2011-01-29
Here is something you might find interesting [http://ubuntuforums.org/showthread.php?t=365867](http://ubuntuforums.org/showthread.php?t=365867)

---

### Post by mexicanseaf00d on 2011-01-29
is it a Synaptics 'clickpad'? On my HP DV7 right clicking with the pad-buttons did not work anymore since 10.10. Took a me quite some time to figure out that I was supposed to **tap the lower right corner** of the touchpad!

Never figured out how to set up the buttons again

---

### Post by ontwowheels on 2011-01-29
> **mexicanseaf00d said:**
> is it a Synaptics 'clickpad'? On my HP DV7 right clicking with the pad-buttons did not work anymore since 10.10. Took a me quite some time to figure out that I was supposed to **tap the lower right corner** of the touchpad!

Never figured out how to set up the buttons again


Holy cr@p, you are right!!!  I just tried it and it worked....on a HP dv5-2074dx

---

### Post by viditgoyal3009 on 2011-01-29
> **mexicanseaf00d said:**
> is it a Synaptics 'clickpad'? On my HP DV7 right clicking with the pad-buttons did not work anymore since 10.10. Took a me quite some time to figure out that I was supposed to **tap the lower right corner** of the touchpad!

Never figured out how to set up the buttons again
yeah..mine is HP DV6 and it is synaptics

---

### Post by Zhono on 2011-02-07
Does anyone know how to get it so you actually click the button, instead of tapping? Tapping worked okay on the livecd, but after installing, it's very iffy. At first I didn't even think it worked at all.

---

### Post by mexicanseaf00d on 2011-02-07
I tried various things, nothing worked so far.

If it is of any use to you, right clicking with two-finger-tap works much better than the lowerrightcorner tap.

There is a **synaptics-dkms** module in the "utouch team" ppa ([https://launchpad.net/~utouch-team/+archive/utouch]("https://launchpad.net/~utouch-team/+archive/utouch"). I just configured synaptics to do the twofingertap-rightclick and have no idea if other multitouch-gestures would work; or even if it is finally possible to get the right button function back with this driver (I gave up trying).

If I remember correctly, ```
synclient TapButton2=3
``` should set "right click" when tapping with two fingers.

more info about synclient etc [here]("https://wiki.archlinux.org/index.php/Touchpad_Synaptics")

---

### Post by Zhono on 2011-02-07
> **mexicanseaf00d said:**
> I tried various things, nothing worked so far.

If it is of any use to you, right clicking with two-finger-tap works much better than the lowerrightcorner tap.

There is a **synaptics-dkms** module in the "utouch team" ppa ([https://launchpad.net/~utouch-team/+archive/utouch]("https://launchpad.net/~utouch-team/+archive/utouch"). I just configured synaptics to do the twofingertap-rightclick and have no idea if other multitouch-gestures would work; or even if it is finally possible to get the right button function back with this driver (I gave up trying).

If I remember correctly, ```
synclient TapButton2=3
``` should set "right click" when tapping with two fingers.

more info about synclient etc [here]("https://wiki.archlinux.org/index.php/Touchpad_Synaptics")

Thanks man, that helped. I installed that, and some driver to allow/improve multitouch. I never managed to change any settings, but two finger tap is now right-click, and tapping in the right corner seems to work really well now too. Still looking for a way to make the actuall right-click button work.

---

### Post by mexicanseaf00d on 2011-02-11
I'm checking out an OpenSuse live USB image with gnome3 right now, and here the right button works like it should be! Weird

I am not sure which config files i should look at / copy to ubuntu, if that is even possible

---

### Post by mexicanseaf00d on 2011-02-11
I believe this openSuse version uses a different synaptics driver - synclient -l revealed additional options:
 ```
>     TouchButtonArea         = 20
>     TouchButtonSticky       = 64
>     LEDStatus               = 0
>     LEDDoubleTap            = 1
```

Alas, they do not work with current ubuntudrivers. "LEDDoubleTap" activates the little touchpad-off area on the clickpad (just like in windows).

---

### Post by viditgoyal3009 on 2011-02-11
the double tap right click is extremely irritating. Doesn't anyone know how to get right click button work on a touchpad??

---

