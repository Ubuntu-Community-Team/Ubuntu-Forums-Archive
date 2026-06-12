---
title: "My Speakers Screch when i turn my volume up"
date: 2008-12-26
forum: New to Ubuntu
---

### Post by tarheelblue on 2008-12-26
I Just upgraded to 8.10 adn when i turn my volume up it makes my speakers screach, didnt have the problem with the old 8.04 version

---

### Post by LowSky on 2008-12-26
open up the sound-mixer and lower PCM to about 90-95%

---

### Post by sayems on 2008-12-26
Applications > Accessories > Terminal $ alsamixer 
change it all to 90%

---

### Post by kansasnoob on 2008-12-26
I like Gnome Alsamixer:

```
sudo apt-get install gnome-alsamixer
```

It'll then show up in Sound & Video:

[ATTACH]97692[/ATTACH]

[ATTACH]97693[/ATTACH]

I'd wonder about the External Amp thing:confused:

Anyway you can start some sound running, open the app. and play away. NO luck?

Then look here:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

