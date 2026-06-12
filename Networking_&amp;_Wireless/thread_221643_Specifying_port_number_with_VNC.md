---
title: "Specifying port number with VNC"
date: 2006-07-23
forum: Networking &amp; Wireless
---

### Post by ppurvis on 2006-07-23
To reach a particular machine from the outside world on my network (actually 192.168.0.3) I need to specify which port vnc is listening to. I am using the latest Ubuntu release. This works fine when I am contacting a Windows machine, as I can alter the listening port in the vnc server configuration. The question is: How do I specify it in VNC for Ubuntu.
ps: I am very new at Ubuntu, but am learning to love it :)

---

### Post by fabiand on 2006-07-25
Hey,

you might have a look at the vncviewer help.
If you don't wqant to look, tyr the following:
```
vncviewer 192.168.0.3:PORT
```

---

