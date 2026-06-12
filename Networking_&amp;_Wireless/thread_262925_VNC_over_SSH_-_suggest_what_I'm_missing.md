---
title: "VNC over SSH - suggest what I'm missing"
date: 2006-09-22
forum: Networking &amp; Wireless
---

### Post by meng on 2006-09-22
I am able to SSH to my machine, both by local network and externally (using RSA key authentication). I am also able to use vncviewer for remote graphical desktop. When I try "vncviewer -via (etc)" for secure remote desktop, I seem to pass authentication (with a password) but the X session that is opened has nothing running, just a hashed black-white background. This, again, applies on both local network and externally.

So folks, who's prepared to guess what it is that I've overlooked?

---

### Post by acefreely on 2006-09-22
Here is how I do it from my windows machine at work to my linux box at home...
```

ssh -L 3800:localhost:5901 user@IPaddress
```

This tunnels port 3800 on the local machine to port 5901 on my linux box via port 22.  I suppose you could use any free port on the local machine.

Then when you lauch VNC viewer, connect to 
```

localhost::3800
```

and bam!  you should be connect via secure tunnel to the VNC box...

---

### Post by meng on 2006-09-23
That seems to work. Thanks muchly.

---

