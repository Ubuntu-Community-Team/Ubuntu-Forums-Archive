---
title: "where is remote desktop settings??"
date: 2014-03-03
forum: Networking &amp; Wireless
---

### Post by sdowney717 on 2014-03-03
[http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/](http://www.makeuseof.com/tag/ubuntu-remote-desktop-builtin-vnc-compatible-dead-easy/)

dead easy, but I am running gnome.
Nothing is in settings for preferences

---

### Post by sdowney717 on 2014-03-03
Right now I  want to connect from an ubuntu to another ubuntu pc.

And in future, maybe windows to ubuntu, and ubuntu to windows.

I dont see where to authorize this in settings, nothing like the article is saying.

---

### Post by steeldriver on 2014-03-03
Have you tried executing

```
vino-preferences
```

from a terminal?

---

### Post by sdowney717 on 2014-03-03
says command not found

also type vino, same thing

try to install vino and it says already installed

ok, I misspelled, so I set properly, thanks, will try now.

---

### Post by sdowney717 on 2014-03-03
That linked article is useless for me.
Remmina is the only remote desktop app I have.

Anyway, remmina does not automatically show available pc's for me. Article says it will show available pc's to connect.

Any more ideas on what t do?

---

### Post by steeldriver on 2014-03-03
Remmina is a remote desktop (VNC/RDP) *client *- you need a corresponding *server *(such as vino-server, x11vnc etc.) running on the target box as well, and either open/forwarded port(s) or a suitable tunnel.

Let's start with (1) what version and flavor of Ubuntu (2) how the computers are connected (within a LAN? over the public internet e.g. work to home?)

---

### Post by sdowney717 on 2014-03-03
took some pics.

the entry was from when I used this on another PC weeks ago, but I was in ubuntu desktop not gnome.

I have no idea, does the other ubuntu pc missing something?

---

### Post by steeldriver on 2014-03-03
Have you tried selecting VNC protocol instead of RDP? The default Ubuntu remote desktop server (vino-server) uses VNC (RDP is a Microsoft protocol)

---

### Post by sdowney717 on 2014-03-03
That did it, it needs to use vnc!, not rdp.

Which one is best experience, resolution wise?
I saw there are many of these here
[http://www.mynitor.com/2010/02/07/15-remote-desktop-solutions-for-linux/](http://www.mynitor.com/2010/02/07/15-remote-desktop-solutions-for-linux/)

---

### Post by sdowney717 on 2014-03-03
It does not stream 1080p video well.
I was thinking of controlling this pc for mythtv, both PC are in same room on a gigabit switch.
What I can do is connect and disconnect and then video smooths out.

will any rdp stream 1080p smoothly?

---

### Post by sdowney717 on 2014-03-03
> **steeldriver said:**
> Remmina is a remote desktop (VNC/RDP) *client *- you need a corresponding *server *(such as vino-server, x11vnc etc.) running on the target box as well, and either open/forwarded port(s) or a suitable tunnel.

Let's start with (1) what version and flavor of Ubuntu (2) how the computers are connected (within a LAN? over the public internet e.g. work to home?)

Both PC are ubuntu 14.04
Both are joined on gigabit LAN through gigabit switch

Actually this vnc is very laggy.
If only Chrome remote desktop worked going to an ubuntu machine, as it is fast and smooth enough I can watch live TV off the WMC PC downstairs on my ubuntu PC upstairs.

---

