---
title: "Remote desktop from Ubuntu to XP in 8.04"
date: 2008-05-02
forum: Networking &amp; Wireless
---

### Post by Tiziano on 2008-05-02
I have a multiboot notebook which has XP and Ubuntu 8.04 -- I can use the microsoft remote desktop to get to another XP computer on my home network, but not the ubuntu remote desktop.

I have the correct port number (3389), and have tried IP address and machine name, but neither work. 

I click connect and it just sits there a long time and then says it doesn't work. Error message: Connection to host "192.168.1.18:3389" was closed.

(I also think that I was able to remote in with previous versions)

---

### Post by Norst on 2008-05-02
Make sure that when your connecting to the Ubuntu box that you have the protocol set to  **XDMCP**. RPD(v5) is for Windows boxes only from what I know. And is also on another port(UDP port 177 and TCP port 6000). If it's grayed out then:
```
sudo apt-get install xnest
```

XDMCP should then be available as an option in the Terminal Server Client(rdesktop)

---

### Post by Tiziano on 2008-05-02
oops -- I see now that there was "Terminal Server Client" that I should have used instead of "Remote Desktop Viewer" :oops:

---

### Post by firedrow on 2008-05-02
Yeah, the names are confusing.  Actually the Remote Desktop Viewer is for VNC.  But the Terminal Server Client (tsclient for launching from CLI or run box) will do VNC, RDP, XDMCP, etc.

---

### Post by lemming465 on 2008-05-02
I think Norst has the scenario backwards; you aren't trying to get into the laptop, but out of it, using *rdesktop*, right?  I would naively expect it to work; I do it a lot myself.

I assume that *ping 192.168.1.18* works?  If not, solve the ethernet issue first.
Also, does *host $(hostname)* do something sensible?

---

