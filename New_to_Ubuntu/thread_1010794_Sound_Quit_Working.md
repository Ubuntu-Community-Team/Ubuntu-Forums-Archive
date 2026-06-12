---
title: "Sound Quit Working"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by zutronius on 2008-12-14
I was playing the game Scorched3d and the game quit working and I had to ctrl+alt+backspace to the login window to get things working again. ever since I did that, I only have sound when I first log into Ubuntu and I cannot listen to music or listen to any sort of sound.

I'm not sure how to go about fixing this. What do I need to do first? I'm running Ubuntu 8.10 on a Compaq f500 laptop.

---

### Post by DaGrimReefah on 2008-12-19
Maybe pulseaudio is acting up?

```
sudo kill pulseaudio
```

I hope this helped.

---

### Post by linux_tech on 2008-12-19
what is output of the following; in terminal type-
       ```
aplay -l 
```    ```
lspci -n 
```  ```
 cat /proc/asound/card0/codec#* | grep Codec
```

---

### Post by linux_tech on 2008-12-19
You should install also gnome-alsamixer if you havn't already.
```
sudo apt-get install gnome-alsamixer
```

---

