---
title: "Create Desktop Icon?"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by kamitsukai on 2009-04-11
I want to create a desktop icon for the game Teeworlds but it needs to launch with specific settings using the command below

```
SDL_VIDEO_X11_DGAMOUSE=0 teeworlds
```

How would I do that? as if I try normally I get the error 

```
Failed to execute child process
```

Thanks in advance!

---

### Post by spupy on 2009-04-11
You can use a simple script:
```
#!/bin/bash
SDL_VIDEO_X11_DGAMOUSE=0 teeworlds
```
Don't forget to make it executable (from the Properties dialog in nautilus or with "chmod +x scriptname" from the command line)

---

### Post by kamitsukai on 2009-04-11
Your a star, thanks:KS

---

