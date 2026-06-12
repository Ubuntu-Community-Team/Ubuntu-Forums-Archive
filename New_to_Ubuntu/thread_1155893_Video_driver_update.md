---
title: "Video driver update?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by SG3 on 2009-05-11
Hey,

   yet again another newbie question : )
   i tried runing couple of games on wine and so far there are couple of issues like the picture is lagging.I want to try updating the video drivers but i'm not quite comfortable touching there.So any suggestions how shall i do it : )

---

### Post by Didius Falco on 2009-05-11
The first thing to do is find out what kind of video card you have. Open a Terminal shell (**Applications/Accessories/Terminal**) and type ```
lspci | grep VGA
```

The | in the middle is a pipe, not an i or l.

Post the results here.

Regards,

Didius

---

### Post by SG3 on 2009-05-11
oh my bad : ) there is all i get from the command.


01:00.0 VGA compatible controller: nVidia Corporation GeForce 8400 GS (rev a1)

---

### Post by skymera on 2009-05-11
ok you have an Nvidia 8400.

Have you installed the driver?

Try disabling Compiz when playing games.

---

### Post by SG3 on 2009-05-11
well the original installing of the os wan't mine work : ) but i'm quite sure that specific vga drivers were not installed : ) only updates :/ will try out the compiz :)

---

