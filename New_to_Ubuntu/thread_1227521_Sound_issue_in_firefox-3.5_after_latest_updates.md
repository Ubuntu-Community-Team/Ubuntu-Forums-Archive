---
title: "Sound issue in firefox-3.5 after latest updates"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by gobberpooper on 2009-07-30
These new updates have been an absolute pain in the *** for me. First off it disabled my graphics card driver which I was able to fix using GRUB. It also somehow corrupted some of my music but that was easy to fix by opening the songs in audacity and then resaving them.
But now I found another problem. Sound in youtube is very bad in firefox-3.5. I wanted to listen to Afrika Bambaataa's version of the Renegades of Funk after hearing the RATM version, but then it just repeated the same sound over and over for a  few seconds then repeated another sound over and over. It works fine with A Browser 3.5 but it's anoying having to switch back and forth. How do I fix this?

---

### Post by wojox on 2009-07-30
You could try:

```
sudo apt-get install flashplugin-nonfree-extrasound
```

---

### Post by zkriesse on 2009-07-30
> **gobberpooper said:**
> These new updates have been an absolute pain in the *** for me. First off it disabled my graphics card driver which I was able to fix using GRUB. It also somehow corrupted some of my music but that was easy to fix by opening the songs in audacity and then resaving them.
But now I found another problem. Sound in youtube is very bad in firefox-3.5. I wanted to listen to Afrika Bambaataa's version of the Renegades of Funk after hearing the RATM version, but then it just repeated the same sound over and over for a  few seconds then repeated another sound over and over. It works fine with A Browser 3.5 but it's anoying having to switch back and forth. How do I fix this?
It might be the video itself...if not try a different flash player plugin.

---

### Post by gobberpooper on 2009-07-30
> **wojox said:**
> You could try:

```
sudo apt-get install flashplugin-nonfree-extrasound
```

Worked perfectly thank you very much! :D

---

