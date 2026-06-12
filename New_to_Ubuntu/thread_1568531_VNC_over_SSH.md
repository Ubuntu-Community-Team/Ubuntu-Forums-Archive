---
title: "VNC over SSH"
date: 2010-09-05
forum: New to Ubuntu
---

### Post by adamjkok on 2010-09-05
I am worried about my VNC sessions being spied on using packet sniffers. I'd also like to be able to safely perform admin tasks that require my password over VNC. The VNC server that needs to be tunneled is tightvncserver (I don't want an education about Vino, tightvncserver has many advantages that I rely on). Also, the client runs Windows 7.

---

### Post by cj.surrusco on 2010-09-05
> **adamjkok said:**
> I am worried about my VNC sessions being spied on using packet sniffers. I'd also like to be able to safely perform admin tasks that require my password over VNC. The VNC server that needs to be tunneled is tightvncserver (I don't want an education about Vino, tightvncserver has many advantages that I rely on). Also, the client runs Windows 7.

I might be understanding you incorrectly, but if you want to use VNC over SSH, it has to be configured on the client end, as long as the server end already has SSH configured, of course.

---

### Post by perspectoff on 2010-09-05
> **adamjkok said:**
> I am worried about my VNC sessions being spied on using packet sniffers. I'd also like to be able to safely perform admin tasks that require my password over VNC. The VNC server that needs to be tunneled is tightvncserver (I don't want an education about Vino, tightvncserver has many advantages that I rely on). Also, the client runs Windows 7.

See

[http://ubuntuguide.org/wiki/Ubuntu:Lucid#VNC](http://ubuntuguide.org/wiki/Ubuntu:Lucid#VNC)

---

