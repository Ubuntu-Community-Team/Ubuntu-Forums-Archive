---
title: "VNC as fast as RDP?"
date: 2008-03-09
forum: Networking &amp; Wireless
---

### Post by adam.mech09 on 2008-03-09
Is there any way to access my linux desktop as quickly as RDP, either with VNC or another protocol?  

I've played around with both SSH and VNC, but neither are anywhere close to as fast as RDP when loading applications, or the desktop itself.  For instance; when sitting at school using my laptop, with my roomate using his, we both connect back to our desktops at home.  My connection, either using VNC or SSH, is never as fast or responsive as his RDP connection.  My computers are both running ubuntu, with my desktop being relatively old and slow (850 mhz, ~8 yrs old) and my laptop being a reasonably quick IBM R60.  His desktop is much faster, but his laptop is about three years older than mine, both using winxp.

Can anyone help me with this?  Is this a matter of which programs i am using as the server and client?  Or is it a protocol issue?

Thanks

---

### Post by scottro on 2008-03-09
There is FreeNX, which can sometimes be a nuisance to set up, due to a lack of docs, at least when I tried on Fedora.  (Eventually I got it working, but haven't tried it on Ubuntu, and there may be better docs for Ubuntu.)

However, if you are sure that you don't need more than two terminal sessions, nomachine.com, which makes the client the FreeNX people recommend, also has a free server--the limitation on the free server is that you can only have two sessions.  AFAIK, that's the only limit.  

In my opinion, its speed is close to, or equal that of RDP.

---

