---
title: "Slight flicker in Video/DVD playback with Totem, VLC &amp; Mplayer"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by JohnRory1971 on 2009-01-01
I'm getting a slight flicker in Video/DVD playback with Totem, VLC & Mplayer. It happens particulary if there is a lot of movement or the camera is panning around. Very annoying! How do I fix it please?

Additional Info:

I have 3 D desktop set up with Compiz. Some posts mention this as a problem.

I ditched Windows Vista for Ubuntu 8.10

I have Dell laptop Inspiron 1525 with Intel Mobile GM965/GL960 Integtated Graphics Controller

---

### Post by Delever on 2009-01-01
Make sure "Sync To VBlank" is selected in Compiz Configuration, General options, Display settings.

Does it appear over time and disappear if you restart computer?

---

### Post by JohnRory1971 on 2009-01-01
I tried turning "Sync to VBlank" on but it made no difference.

Flicker or slight horizontal lines always happens when there is movement in the film. It does not go away on restart

---

### Post by parajuito on 2009-01-01
Try editing you xorg file and put: Option "TexturedVideo" "off" under device section.

---

### Post by Delever on 2009-01-01
> **parajuito said:**
> Try editing you xorg file and put: Option "TexturedVideo" "off" under device section.

```
gksudo gedit /etc/X11/xorg.conf
```

In case you are wondering how to start editing.

---

### Post by JohnRory1971 on 2009-01-01
There is nothing in the device section of the xorg.conf file. All I have is the following:

Section "Device"
	Identifier	"Configured Video Device"
EndSection

---

### Post by parajuito on 2009-01-01
add this line inside the device section:
> 
Option "TexturedVideo" "off"

---

### Post by JohnRory1971 on 2009-01-01
Thanks but adding this option made no difference. Any other ideas out there please?

---

### Post by Delever on 2009-01-01
> **JohnRory1971 said:**
> Thanks but adding this option made no difference. Any other ideas out there please?

Well, logout - login, of course. No more ideas from me though.

---

### Post by my_key on 2009-01-01
I have this too, because my video card isn't very fast (and ATI). If I turn effects (compiz) off, I don't have any flicker. Also I get better effects by using Totem with the xine backend.

Good luck and happy new year!

Michael

---

### Post by ubuntu-freak on 2009-01-01
Can you confirm whether this flickering occurs when visual effects are turned off? Flickering during video playback is usually Compiz-related. If you install fusion-icon, you can quickly disable effects when you're about to play games and watch HQ videos etc.
 
If you're noticing this flickering or any artifacts with mainly AVI videos, try playing them with VLC and enable deinterlacing in "Video > Deinterlace > Blend".

---

### Post by JohnRory1971 on 2009-01-01
> Can you confirm whether this flickering occurs when visual effects are turned off? Flickering during video playback is usually Compiz-related. If you install fusion-icon, you can quickly disable effects when you're about to play games and watch HQ videos etc.

If you're noticing this flickering or any artifacts with mainly AVI videos, try playing them with VLC and enable deinterlacing in "Video > Deinterlace > Blend".

I turned visual effects off but still getting this movement related flicker.

---

### Post by Rob_H on 2009-01-01
I had a similar horizontal flickering problem in VLC and solved it by going to Preferences > Video and switching the output to "XVideo extension video output". Can't remember what it was set to originally, but it looked much better afterwards. My setup is different from yours, though. I'm running Compiz, but with an NVIDIA chipset/drivers. If XVideo doesn't help, you could try experimenting with the other output settings there. Good luck.

---

### Post by JohnRory1971 on 2009-01-01
> had a similar horizontal flickering problem in VLC and solved it by going to Preferences > Video and switching the output to "XVideo extension video output". Can't remember what it was set to originally, but it looked much better afterwards. My setup is different from yours, though. I'm running Compiz, but with an NVIDIA chipset/drivers. If XVideo doesn't help, you could try experimenting with the other output settings there. Good luck

Nothing seems to be working for me. Is there anyone out there who has Intel GM965/GL960 Integrated graphics card and who has this problem but fixed it?

---

### Post by jakeman66 on 2009-01-02
> **JohnRory1971 said:**
> Nothing seems to be working for me. Is there anyone out there who has Intel GM965/GL960 Integrated graphics card and who has this problem but fixed it?

Open VLC Preferences, select advance mode, open the video options then select Output mode.

Play with the different output modes.  X11 works best for me.

---

### Post by Tom Tiger on 2009-01-08
I had the same problem,  I switched to Xshm in Xine and Mplayer, this fixes the problem, however Mplayer can't play full screen after that.

But since Xine works....  fine by me.

btw,  this is on an ATI 2400 XT card with Compiz enabled.

---

