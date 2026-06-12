---
title: "Which VNC server/client combo to use?"
date: 2007-01-04
forum: Networking &amp; Wireless
---

### Post by Crakie on 2007-01-04
I did quite a bit of reading up on VNC, but I am confused as to install which VNC server.

I experimented with x11vnc, but I couldn't get it to work. I left my computer on, logged in as the sole user, and at work tried to connect via a SSH tunnel (created with Putty). The SSH part went fine and I could start x11vnc, but I got an error when trying to connect to it with the UltraVNC client (for Windows). IIRC it said something about server and client perhaps not being compatible? I cannot find any really easy step-by-step instructions on how to create a proper VNC server, configure it and then connect to it through a SSH tunnel.

x11vnc seems my cup of tea, since it does not require an additional user and is able to share the current X session. Any experiences with VNC clients that work well with it? Or perhaps any suggestions for another VNC server/client combo that should work without too much configuration steps?

---

### Post by kebes on 2007-01-04
I use the server "tightvncserver" and the viewer "xvncviewer" (or I use the tightVNC viewer if I'm on a windows machine). I use these because they are what I'm used to, and they are easy to install in Ubuntu:
sudo aptitude install xvncviewer
sudo aptitude install tightvncserver

These may not be the "best" but they work nicely for me. The tightvncserver cannot attach to the normal X session, however, so this may not be what you want.


However you could give the TightVNC viewer a try and see if it can connect properly to your x11vnc instance.

---

### Post by Crakie on 2007-01-04
Is there any way to 'copy' a useraccount, only changing it's name? The new account would have the same desktop, permissions, is allowed sudo etc. Ideally, any changes in the original account would be reflected in the 'shadow' user account, but that is probably a lot to ask :)

---

### Post by kebes on 2007-01-04
Short answer: not that I know of.


For tightvncserver you don't need to create a new user account. You can run it from your normal user account and when you login the desktop, settings, etc. are all exactly as if you were sitting at the computer. (The only thing it cannot do is grab control of the actual X session running on the monitor... but the duplicate X session it creates is basically the same.)

Does that answer your question? (My apologies if I've misunderstood.)

---

