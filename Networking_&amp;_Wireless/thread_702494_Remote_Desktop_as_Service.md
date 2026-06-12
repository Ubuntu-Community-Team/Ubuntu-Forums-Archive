---
title: "Remote Desktop as Service"
date: 2008-02-20
forum: Networking &amp; Wireless
---

### Post by helpmepls on 2008-02-20
Have PC running ubuntu 7.10. I want to VNC into the PC from the lan and wan. The VNC is not running as service or in startup (prefer realvnc if not tightvnc or related compatible vnc for ubuntu 7.10 desktop version). Can someone help me setup/configure VNC so that if system is rebooted it'll start teh service and I can remote in again. Thanks!

---

### Post by stalker145 on 2008-02-20
> **helpmepls said:**
> Have PC running ubuntu 7.10. I want to VNC into the PC from the lan and wan. The VNC is not running as service or in startup (prefer realvnc if not tightvnc or related compatible vnc for ubuntu 7.10 desktop version). Can someone help me setup/configure VNC so that if system is rebooted it'll start teh service and I can remote in again. Thanks!

In Ubuntu, you can go to Preferences ~> Remote (I'm pretty sure it's preferences) and tick the appropriate boxes. This will allow access through VNC to your machine.

Sorry I'm not in front of my machine at the moment and can't give better direction, but it's in that area.

Check back if you still need help.

---

### Post by maybeway36 on 2008-02-20
Try setting up x11vnc. The link is in my sig.

---

### Post by timcredible on 2008-02-20
i would recommend using x11 instead of vnc.  i still can't understand why people continue to try to re-invent the wheel.....

link [here]("http://linux--help.org/joomla2/index.php?option=com_content&task=view&id=12&Itemid=27") for tutorial

---

### Post by maybeway36 on 2008-02-20
XDMCP might be a good idea, but it's hard to get into from a Windows system. You need an X sevrer on the client.

---

### Post by HermanAB on 2008-02-20
Xming and PuTTY works best.

---

