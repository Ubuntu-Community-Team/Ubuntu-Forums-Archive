---
title: "VNC + Beryl/Compiz = ???"
date: 2007-08-26
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2007-08-26
I recently installed VNC on a computer that normally runs Beryl automatically when the user logs in.  On the server side with Beryl running, activity on the desktop appears just fine after a client has connected using VNC.  But on the client side, you have a seemingly static image of their desktop that never changes.  Mouse movement can be seen (and technically, clicks can be sent...but you can't tell what you're clicking on because the desktops reactions to the clients activities aren't transmitted visually).

I found that you can easily fix this by going into Beryl's settings manager and telling it to use Metacity as its window manager.  But I was wondering if there is a way to make this simpler for someone who isn't a power user.  Perhaps Beryl could automatically switch for the user in the event of an incoming VNC session request?

---

### Post by Zorael on 2007-08-26
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/77442](https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/77442) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I think it's a known issue: [https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/77442](https://bugs.launchpad.net/ubuntu/+source/vnc/+bug/77442).

Some recommended to try the x11vnc server instead, haven't tried it yet myself though.

---

