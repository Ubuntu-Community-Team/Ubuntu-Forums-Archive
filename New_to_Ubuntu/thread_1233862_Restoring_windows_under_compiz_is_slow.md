---
title: "Restoring windows under compiz is slow"
date: 2009-08-07
forum: New to Ubuntu
---

### Post by Falc7 on 2009-08-07
When i turn on compiz, there is a delay when restoring minimised windows, its quite annoying, can it be fixed?
I have a dell studio 15
ATI radeon 4750 with the driver that is presented under hardware drivers

---

### Post by furuno on 2009-08-07
If it's about the animation delay, simply open you Compiz Config Settings Manager, then go into Animation > Minimize Animation > Select the settings on Animation Selection > Click Edit > Change the duration (it is in milisecond) to a lower number. You can do it with other animation effect too, just play around.

If you don't have the CCSM, install it by typing :
```
sudo apt-get install compizconfig-settings-manager
```
It can be found under System > Preferences

Btw I'm using 4830 and I don't have any slowdown even tough I force 8x AA & 16x AF so I have better effects. It should be also good on 4750. Compiz is not Crysis anyway...

---

### Post by Falc7 on 2009-08-07
Thanks for your reply
The minimise animation is turned off; but its not really about the speed the window takes to minimise, as the delay is only noticeable in the time it takes to restore the window.

I have only a very few options turned on in compiz though, opacity, fade to desktop, window decoration, and a few others at the very bottom of compiz manager.

I could take a video if it would help?

---

### Post by furuno on 2009-08-07
There's might be some kind of driver problems. Try pasting the result of this command :
```
fglrxinfo
```

---

### Post by Falc7 on 2009-08-07
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon HD 4500 Series
OpenGL version string: 2.1.8575

```

---

### Post by furuno on 2009-08-07
Whoa it's says that your graphic card is 4500 series. Are you sure that you're using 4750? If you're really using the 4750 that it's most probably driver problem. Driver from ubuntu not as up-to-date as driver from AMD/ATI, and 4750 is a new card... 

You might want to try uninstalling that driver and reinstall using the third method from [this article]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#Install%20from%20ati.com%20(latest%20version%20of%20drivers)") (install from ati).

---

### Post by Falc7 on 2009-08-07
Sorry the card is indeed a ATI mobility radeon HD 4570

---

### Post by snowmanZOMG on 2009-08-07
I am also having this problem.  I run an ATI/AMD HD3850 AGP.  I just downloaded the drivers from the AMD website.  It is a very artificial and annoying pause.  It is a SOLID 1.5 to 2 seconds wait from me clicking until the window actually maximizes.  Is it just poor driver support?  It really does feel like I'm running my machine without drivers on Windows XP, where minimizing and maximizing is just slow and painful.  Scrolling can also be slow.

```
dkim@dkim:~$ glxinfo | grep -i direct
3:direct rendering: Yes
dkim@dkim:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon HD 3850 AGP
OpenGL version string: 2.1.8787

```

---

### Post by AzN1337c0d3r on 2009-11-03
Bumped for ATI Mobility Radeon 3450 on a Dell 1535 too. Maximize is also unacceptably slow.

---

### Post by Can+~ on 2010-01-06
I'm experiencing some black shadow instead of transparency (for example, when the gksudo prompt appears, the screen turns black instead of transparent) using the current fglrx in the repository.

Is worth the hassle to upgrade to the fglrx 9.12 driver? Are these issues solved?

(Ati Radeon Mobility 4500 HD on a Dell Studio)

EDIT: Whoops, seems that I had the blur plugin enabled, which lead to some weird issues. Disabling this plugin removes the black shadow.

But my question is still valid, is it safe to move to fglrx 9.12?

---

### Post by dstein on 2010-02-01
I am also experiencing the same problem with a Radeon 4350. Does anyone know of a solution? Any /etc/X11/xorg.conf settings that I can add that will prevent this delay? I also have a similar delay when maximizing windows. Thanks.

---

### Post by caravel on 2010-02-01
I have the same issue under Debian 5 with compiz, fglrx and my HD 3650.  I think it's a bug, but I bascially don't use compiz anyway so I haven't bothered trying to fix it yet:

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/381003](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/381003)

---

