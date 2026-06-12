---
title: "X11 Forwarding: Xming Rejecting Connections"
date: 2007-11-22
forum: Networking &amp; Wireless
---

### Post by Aikon- on 2007-11-22
**[COLOR="Red"]SOLVED:[/COLOR]** Of course I managed to solve this almost as soon as I posted it =/  It turns out I needed to check the "No Access Control" box in the Xming launcher. Alternatively, I assume I could add "ophelia" to Xming's host file (which may be a safer solution).

Hi guys,

I'm trying to setup X11 forwarding so I can run a few basic apps from my Windows laptop when I'm away from my desktop. I've had this working before, but that was with PuTTy and now I'm using Cygwin (and liking it much better).

Hardware setup:  "ophelia" is the desktop running Gutsy, "asuka" is the laptop running Vista.

I am using Xming 6.9.0.31 on my Windows machine (Vista) as my X server. I am connecting to my Linux machine using:

```
ssh -C -Y sarmitage@ophelia
```

No X apps seem to work at all until I issue the command:

```
export DISPLAY=asuka:0.0
```

**First question:** Is there a way to get around having to type that everytime?

**Second question:** I can't actually open any X apps. When I try to (e.g. by typing 'xterm' or 'gedit'), I get the following error message:

```
Xlib: connection to "asuka:0.0" refused by server
Xlib: No protocol specified

cannot open display
```

If I view Xming's log, I see the following corresponding entry:

```
AUDIT: Thu Nov 22 02:31:12 2007: 5636 Xming: client 4 rejected from IP ${ip address of ophelia}
```

How can I make Xming stop rejecting these connections?

-Aikon

---

