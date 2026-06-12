---
title: "Want maximum output of s-video resolution on lcd"
date: 2011-06-01
forum: New to Ubuntu
---

### Post by ravikalsi27 on 2011-06-01
i have lenovo 3000n 1000 laptop,its VGA port is not working and i use S-video to connect to lcd 22 inch

but the output screen is to low on LCD, i mean the black border on the corner of lcd....i want full screen on LCD but dont know how..........

works well in Windows 7 ..........but on ubuntu dont know how to....because in windows i install GM945 drivers chipset graphics

but how to ubuntu??? please help????

---

### Post by TeoBigusGeekus on 2011-06-01
Have you installed any restricted drivers for your card?

---

### Post by Maheriano on 2011-06-01
S-Video is only 480i, why would you want to pixelate it?

---

### Post by ravikalsi27 on 2011-06-03
but when i use windows 7 the video output is full screen on my 22'' LCD,but on ubuntu the black border of one inch on the lcd appears.......dont know why.........

---

### Post by Maheriano on 2011-06-03
That's because S-Video's bandwidth is only 480* lines of resolution, more specifically 640x480*. Ubuntu is doing the right thing and keeping it at the same ratio it's meant to be displayed at, Windows is stretching it to hell to fill the screen. It's still 480* lines, just stretched over a larger area so the more you stretch it, the worse it will look. If I were you I'd keep the black bars, the picture will be clearer.

This is why I don't know why people by huge televisions......the picture coming from your cable box is only 1920x1080, you're stretching and distorting your perfect picture by displaying it on a television too large. I could never figure that out, I still can't figure it out. Doesn't make sense.

*- It's actually 240 lines because it's interlaced meaning only half the lines are drawn at any given time. 480p would be true 480 lines.

---

