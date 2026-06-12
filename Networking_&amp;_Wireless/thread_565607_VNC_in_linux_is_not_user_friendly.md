---
title: "VNC in linux is not user friendly"
date: 2007-10-02
forum: Networking &amp; Wireless
---

### Post by fung1223 on 2007-10-02
Hi all, I found that the vncviewer is not powerful/user friend than Windows one. Such like scroll up/down, it is quite trouble to do it on linux version(using right/left button of mouse). Do I need to configure something to let me more powerful or user friendly? Tks!!

---

### Post by noob12 on 2007-10-02
The default one is terrible, but there are alternatives that you just need to install.

I use **xvnc4viewer**; a lot of people like **xtightvncviewer**.  Both are available from the repositories.

For xvnc4viewer, for example, I did:

```

sudo aptitude install xvnc4viewer

```

This has proper scroll bar, etc.

---

### Post by maybeway36 on 2007-10-02
The GNOME remote desktop client is primarily for RDP, and VNC is an afterthought. For Krdc, the KDE client, it's the other way around.

---

### Post by fung1223 on 2007-10-03
Tks!!! That's what I want!! really thanks!!

---

