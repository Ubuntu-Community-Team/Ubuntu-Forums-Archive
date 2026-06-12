---
title: "tightvncviewer sound or rdesktop sound"
date: 2010-05-29
forum: New to Ubuntu
---

### Post by lance bermudez on 2010-05-29
I dont think that tightvncviewer will let me hear the sound from the remote computer. However I was told that rdesktop will let me hear the sound from the remote computer but it will not let me connect.

acer@kacer:/usr/share/man$ rdesktop 192.168.1.# -k en-us -z -f -r sound:remote 
ERROR: 192.168.1.47: unable to connect

acer@kacer:~$ xtightvncviewer -via "lance@192.168.1.# -p #" -encodings tight -compresslevel 9 -quality 9 -x11cursor localhost:0
this one works but no sound from remote computer

Both computers are running linux one is ubuntu the other is kubuntu. One is on 192.168.1.# and the other is 192.168.2.#

what am i doing wrong?? please set me straight.

---

