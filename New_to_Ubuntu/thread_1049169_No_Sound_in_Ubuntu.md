---
title: "No Sound in Ubuntu"
date: 2009-01-24
forum: New to Ubuntu
---

### Post by smartygoldenfish on 2009-01-24
Hi.
i have just noticed that sound in ubuntu is nearly gone.
Whenever i play something i get a creepy sound, just like, if u hear a campfire, or you roast something, that dot dot dot sound...is what i get. And the sound gets louder when the song is high pitched. aplay -l in terminal lists my Intel Sound Card and alsamixer is working correctly. But i cant get any sound!!
Help!

---

### Post by linux_tech on 2009-01-24
what is output of :
```

cat /proc/asound/card0/codec#* | grep Codec

```

---

### Post by linux_tech on 2009-01-24
install gnome-alsamixer
```

sudo apt-get install gnome-alsamixer

```
open gnome-alsamixer
```
gnome-alsamixer
```

locate the pcm slider and try adjusting to 75%

---

### Post by smartygoldenfish on 2009-01-25
it worked!
thanks!
hahahahaha!

---

### Post by smartygoldenfish on 2009-01-29
well done

---

