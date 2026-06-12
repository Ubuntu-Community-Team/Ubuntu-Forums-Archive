---
title: "Xubuntu remote desktop?"
date: 2006-12-20
forum: Networking &amp; Wireless
---

### Post by TechnoPenguin on 2006-12-20
I had Ubuntu Edgy on my other PC running in another building and I could use VNC to remotely control it. Now I installed Xubuntu Dapper on it and there is no similar option. I found out that remote VNC vino-server won't work on Xubuntu. What to do? I want to use VNC since I have other pcs runnning VNC server too, and I wouldn't want to change software on all of them.

---

### Post by TechnoPenguin on 2006-12-21
Ok, I found the answer, I used X11vnc, there was a config file I was missing.

---

### Post by Jaymoon on 2006-12-23
Could you please explain more in detail how you got a VNC server running on Xubuntu?

I was able to get X11vnc working...  but once I connect once, then quit...  It closes the VNC server.  Is there a way to keep it permanently running in the background?

---

### Post by Hakimio on 2006-12-23
> **Jaymoon said:**
> I was able to get X11vnc working...  but once I connect once, then quit...  It closes the VNC server.  Is there a way to keep it permanently running in the background?
Use forever switch ;)

Now can someone tell what options should be set in tightVNC viewer to get most of 100Mbps LAN connection (encryption isn't important at all, because firewall is set to accept connections to VNC server only from LAN)?

---

### Post by Threbus5 on 2006-12-23
Hi,
I have been using the x11vnc on the Linux machines and UltraVNC for the win machines and it seems pretty snappy (at least compared to the old remote desktop that accompanied regular Ubuntu).

Did you read the howto by intangible? You may find it helpful. [http://ubuntuforums.org/showthread.php?t=45565&highlight=x11vnc](http://ubuntuforums.org/showthread.php?t=45565&highlight=x11vnc)

Good luck.

---

### Post by BlackHero on 2006-12-23
look this tsclient in xubuntu

---

### Post by Hakimio on 2006-12-24
> **BlackHero said:**
> look this tsclient in xubuntu
And what's so special about it?

---

### Post by grumpymole on 2006-12-28
You can also [use vnc4server and xinetd]("http://grumpymole.blogspot.com/2006/12/xubuntu-remote-desktop-with-vnc4server.html"), which gives a persistent session.

Regards

Warren
[http://grumpymole.blogspot.com](http://grumpymole.blogspot.com)

---

