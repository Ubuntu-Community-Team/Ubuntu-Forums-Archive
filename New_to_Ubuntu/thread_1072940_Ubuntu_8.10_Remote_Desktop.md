---
title: "Ubuntu 8.10 Remote Desktop"
date: 2009-02-17
forum: New to Ubuntu
---

### Post by oxsyn on 2009-02-17
I have a server that has Ubuntu Desktop 8.10 installed on it.  It was installed with a keyboard and mouse connected, now it only has ethernet connected.  Normally I simply ssh into the server.

Is there a way to enable (using the command line) remote graphical sessions?

---

### Post by doas777 on 2009-02-17
I don't know about vino, but you can always 
```
sudo apt-get install tightvncserver
```

this should help a lot: [https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

also vino (the build in 'remote desktop') only works after desktop login by default (and since this is a headless box...), but here is a tutorial on setting up a vnc server for multiple resumable remote sessions: [http://ubuntuforums.org/showthread.php?t=122402](http://ubuntuforums.org/showthread.php?t=122402)

good luck

---

### Post by spiderbatdad on 2009-02-17
[https://help.ubuntu.com/community/Vinagre](https://help.ubuntu.com/community/Vinagre)
uses port 5900 by default.

[https://help.ubuntu.com/community/VNC](https://help.ubuntu.com/community/VNC)

---

