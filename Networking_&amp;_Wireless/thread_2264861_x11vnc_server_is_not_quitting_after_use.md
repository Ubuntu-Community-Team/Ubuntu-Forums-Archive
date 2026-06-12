---
title: "x11vnc server is not quitting after use"
date: 2015-02-10
forum: Networking &amp; Wireless
---

### Post by spookybathtub on 2015-02-10
I've installed x11vnc server on my Trusty machine.  I connect through SSH with a command like this:
```
ssh -L  5900:localhost:5900 *remotehost* 'x11vnc -localhost -display :0'
```

But if I press Ctrl+C in the local terminal, x11vnc does not stop properly.  Running **ps aux** on the remote system shows several instances still running.  What is the correct way to stop it?

---

