---
title: "Remote desktop"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by Muhammad Ahmed on 2010-03-28
plz let me know how toconfigure the remote desktop so i can see a video of the other computer runnung.I have two pcs connected remotely both ubuntu ,everything works fine but when video is played it stucks(only video) when closed resumes again

---

### Post by nothingspecial on 2010-03-28
Do you need to see a video on the host/server computer?

If not ```
ssh -X -C -c blowfish username@ipaddress_of_other_computer
```

Then ```
mplayer/path_to_video
```

---

### Post by Muhammad Ahmed on 2010-03-28
sorry brother i dont understand programming can u explain graphically

---

### Post by Muhammad Ahmed on 2010-03-28
the video on the other pc is being played from youtube.com pcs are connected on lan and on remote desktop connection video stucks while mouse is moving

---

### Post by Muhammad Ahmed on 2010-03-28
help

---

### Post by NickJones on 2010-03-28
Is it only when you watch video? It may just be too much video processing for your PC to handle.

---

### Post by Muhammad Ahmed on 2010-03-31
i think core 2 duo is enough pocessor with nvidia 8500 gt and 2 GIB if ram ddr2

---

