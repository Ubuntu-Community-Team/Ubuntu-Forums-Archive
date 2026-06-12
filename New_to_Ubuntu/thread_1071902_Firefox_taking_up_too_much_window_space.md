---
title: "Firefox taking up too much window space"
date: 2009-02-16
forum: New to Ubuntu
---

### Post by psychx on 2009-02-16
I am using Mozilla Firefox with my Ubuntu 8.10 installation. When I open firefox in "maximized" mode (not full screen mode), it covers my task bars and I have no main toolbar to minimize. I have to hit F11 to fullscreen it, which then gives me back my normal task bars. Then I hit F11 again to bring it to normal, and am able to minimize. It is not a huge problem, but can be somewhat annoying. Any ideas?

---

### Post by hansdown on 2009-02-16
Hi psychx.

Hit f11 twice, then restart firefox.

Should be good from there.

---

### Post by psychx on 2009-02-16
Hey,
Thank you for the quick response, but it is still doing the same thing. I hit F11 twice (even the first time will bring the task bars back), then restart Firefox.. When I open it again, it goes maximized again, and doesn't have the minimize, maximize, or close icons in the upper right, and I don't have any task bars.

I can fix it just by hitting F11 but that can get old.. Thank you for any input!

---

### Post by leonardo_neo on 2009-02-16
This happened to me too 3 days back after firefox upgrade.

But it resolved spontaneously without doing anything. I was going to post a question regarding that, but you posted instead.

---

### Post by danielmolano on 2009-02-16
same thing here and after a few days it just stopped doing it so you probably will just have to wait it out.

---

### Post by RomeReactor on 2009-02-16
Try pressing F11 until it gets out of fullscreen, maximize it and un-maximize it a couple of times, and while un-maximized resize it to your liking; then close Firefox and open it again.

---

### Post by psychx on 2009-02-17
I realized that when I unmaximize the Firefox window, it gets even larger that it was. Well, of course, I tried to resize it; but it will not come down.

---

### Post by RomeReactor on 2009-02-17
While Firefox is un-maximized, are you able to see at least one border/corner of the window? If not, hold ALT and drag the window until you do, then resize it.

---

### Post by binbash on 2009-02-17
compizconfig settins manager > workarounds plugin > untick legacy fullscreen support

---

### Post by psychx on 2009-02-17
Where would compizconfig be? I finally got it resized, just wondering if I should still check out compizconfig settings that you were referring to.

---

### Post by itisbasi on 2009-02-17
Even I had this annoying little problem just for a couple of days, and I had to hit f11 twice everytime I started firefox. I upgraded to the latest firefox(3.0.6) and, no problems after that...

---

### Post by RomeReactor on 2009-02-17
> **psychx said:**
> Where would compizconfig be? I finally got it resized, just wondering if I should still check out compizconfig settings that you were referring to.

It's not installed by default; look for **compizconfig-settings-manager** in Synaptic, or to install it from the terminal:
```
sudo aptitude install compizconfig-settings-manager
```
Then you can find it in 'System->Preferences->CompizConfig Settings Manager'.

---

### Post by psychx on 2009-02-17
Thank you so much!

---

