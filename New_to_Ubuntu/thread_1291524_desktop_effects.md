---
title: "desktop effects"
date: 2009-10-14
forum: New to Ubuntu
---

### Post by wlraider70 on 2009-10-14
I think my desktop effects are slowing the system down. 
Its a new ubuntu install on a Dell.

Transitions are jittery, and Hulu display skips frames. 
However local video playback is pretty good.

I don't know about the video card i think its a 16MB agp card.



how do i disable or minimize effects to see if that's it.

---

### Post by wojox on 2009-10-14
Go to System > Preferences > Appearance > Visual Effects and set to none.

---

### Post by tuxxy on 2009-10-14
> **wlraider70 said:**
> I think my desktop effects are slowing the system down. 
Its a new ubuntu install on a Dell.

Transitions are jittery, and Hulu display skips frames. 
However local video playback is pretty good.

I don't know about the video card i think its a 16MB agp card.



how do i disable or minimize effects to see if that's it.

I had bad Compiz animations using ATI drivers sounds similar to yours.  To disable effects navigate to system > prefs >apperance > visual effects

If you just like to minimize the effects then open compiz config manager at system > prefs > compiz 

You may need to download that application so search for compizconfig-settings-manager in Synaptic or you can open up a terminal and run this

```
sudo apt-get install compizconfig-settings-manager
```

---

