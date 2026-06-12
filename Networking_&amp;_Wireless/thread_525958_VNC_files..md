---
title: "VNC files."
date: 2007-08-14
forum: Networking &amp; Wireless
---

### Post by serfczar on 2007-08-14
I get these erros when trying to run vnc


serfczar@isoserver:~$ vncviewer 192.168.1.8:1
192.168.1.8 5901
RFB server supports protocol version 3.8
VNC authentication succeeded
sending client init
Desktop name is x11
Desktop size is 1024 x 768
java.io.IOException: Unknown RFB message type -1
   at vncCanvas.processNormalProtocol(vncCanvas.java:321)
   at vncviewer.run(vncviewer.java:145)
   at java.lang.Thread.run(libgcj.so.70)
java.io.IOException: Unknown RFB message type -1

---

### Post by serfczar on 2007-08-15
> **serfczar said:**
> I get these erros when trying to run vnc


serfczar@isoserver:~$ vncviewer 192.168.1.8:1
192.168.1.8 5901
RFB server supports protocol version 3.8
VNC authentication succeeded
sending client init
Desktop name is x11
Desktop size is 1024 x 768
java.io.IOException: Unknown RFB message type -1
   at vncCanvas.processNormalProtocol(vncCanvas.java:321)
   at vncviewer.run(vncviewer.java:145)
   at java.lang.Thread.run(libgcj.so.70)
java.io.IOException: Unknown RFB message type -1

Got it working, turns out you can't add in the desktop number, i guess I configed it wrong, no multiple desktops :*(

---

