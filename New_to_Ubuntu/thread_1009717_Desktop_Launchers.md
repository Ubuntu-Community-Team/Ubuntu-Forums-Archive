---
title: "Desktop Launchers"
date: 2008-12-12
forum: New to Ubuntu
---

### Post by Me_Rock on 2008-12-12
Hey there,

I have a problem and I can't seem to find an answer to it on the web.

Here's my scenario:

I'm new to Linux and I installed Xubuntu on my spare machine to be a small-time server and backup desktop. I'm trying to create a launcher for my Call of Duty 4 server. To launch it in the terminal, I first type "cd /home/user/cod4_lnxded" to get to the directory, and then I launch the executable by typing "./cod4_lnxded +exec config.cfg +map_rotate".

This works great in the terminal, but It's annoying to have to type all that out when I want to launch my server. I need to know how to pack that sequence in to a desktop launcher.

Thanks.

---

### Post by jordanmthomas on 2008-12-12
Make it into a script (say ~/cod4server)
```

#!/bin/bash
cd /home/user/cod4_lnxded
./cod4_lnxded +exec config.cfg +map_rotate

```
chmod +x ~/cod4server
Then, tell your launcher to run ~/codeserver

Alternatively (and probably preferably), you could probably put 
/home/user/cod4_lnxded/cod4_lnxded +exec config.cfg +map_rotate

---

