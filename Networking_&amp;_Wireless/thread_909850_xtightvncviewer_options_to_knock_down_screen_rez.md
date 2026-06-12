---
title: "xtightvncviewer: options to knock down screen rez?"
date: 2008-09-03
forum: Networking &amp; Wireless
---

### Post by wilberfan on 2008-09-03
I have two friends with Macs that I've installed OSXvnc on. They both have very slow broadband connections...

I first ssh into either machine with:  

```
ssh -L 5900:localhost:5900 friend1@friend1.dyndns.org
```

then I

```
xtightvncviewer localhost:5900
```

which brings up their desktop.   But it takes forever to completely render their screen (upwards of a minute?).  It's way more color depth and resolution than I need.

I've looked at the command-line options, but can't make much sense of them, and all the variations I've tried have made no difference.

For example, none of these have changed the rez at all:

```
xtightvncviewer -compresslevel 8 -quality 2 -depth 8 localhost:5900
xtightvncviewer -compresslevel 1 -quality 4 -depth 16 localhost;5900
```

etc...

I'm kinda new to this stuff; can anyone tell me what I'm doing wrong?

---

### Post by rjmoerland on 2009-01-03
Hmm, too bad - no solution posted. I too have the same problem. I have a server running Xvnc. I first set up a VPN connection with the remote network. I SSH into the machine and start an Xvnc session with ```
vncserver :1
``` Whenever I log in with UltraVNC on the Xvnc session, I get decent speed and screen quality regarding the connection speed. However, whatever Linux VNC client I try, I get a terribly slow screen refresh. I can see it being build up line by line or block by block depending on the connection settings. I have tried```
xtightvncviewer 192.168.1.10:1 -quality 0 -compresslevel 9 -encodings tight
``` but I still get a slow screen build-up, without any visible JPEG artifacts that I would expect. What does UltraVNC do differently that xtightvncviewer or krdc do not do?:confused:

---

