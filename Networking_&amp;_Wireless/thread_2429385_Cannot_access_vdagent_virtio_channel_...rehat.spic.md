---
title: "Cannot access vdagent virtio channel ...rehat.spice ...  Error Finally"
date: 2019-10-17
forum: Networking &amp; Wireless
---

### Post by markackerman8@gmail.com on 2019-10-17
This Error is so common 

"Cannot access vdagent virtio channel /dev/virtio-ports/com.redhat.spice.0"

And very few solutions ... but this worked!

Solution
&#8227; Basically adding the line:
> X-GNOME-Autostart-enabled=false

• To the files:
> /etc/xdg/autostart/spice-vdagent.desktop
> /usr/share/gdm/autostart/LoginWindow/spice-vdagent.desktop

Then stop and disable the service:
```
$ sudo systemctl stop spice-vdagentd
```
```
$ sudo systemctl disable spice-vdagentd
```
```
• sudo gedit /etc/xdg/autostart/spice-vdagent.desktop

```

I hope it helps, Mark

---

### Post by markackerman8@gmail.com on 2019-10-17
Yep The Error is Finally Gone even after 2 restarts

---

