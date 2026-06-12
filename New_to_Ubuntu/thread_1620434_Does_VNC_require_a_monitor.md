---
title: "Does VNC require a monitor?"
date: 2010-11-13
forum: New to Ubuntu
---

### Post by mathfreak123 on 2010-11-13
Hey, everyone!

I installed ubuntu on my desktop and I've been using it through ssh on my laptop. I've been getting curious lately; can I use VNC to connect to the desktop if I don't have a monitor plugged in for the desktop? Does VNC require a monitor to be plugged in?

---

### Post by kesman on 2010-11-13
No, it doesn't. Just install the vnc server and then a client to the other computer. Ubuntu actually already has a remote desktop installed, you just have to enable it from System -> Preferences -> Remote Desktop. I use tightVNC to connect to my server from windows.

---

### Post by mathfreak123 on 2010-11-13
Would it be possible for me to get a remote desktop before I log in? I've been trying to use x11vnc, but to no avail (I have also checked the firewall).

---

### Post by Goldfissh on 2010-11-13
> **mathfreak123 said:**
> Would it be possible for me to get a remote desktop before I log in? I've been trying to use x11vnc, but to no avail (I have also checked the firewall).

Edit- Disregard this, I had the totally wrong end of the stick.

---

### Post by spiky001 on 2010-11-13
How do you mean I have set up the remote desktop supplied with ubuntu then from the client i open remote desktop select server then it opens the server screen on laptop

---

### Post by kesman on 2010-11-13
So you have managed to do it. What's the remaining problem?

---

### Post by mathfreak123 on 2010-11-13
I can connect at the login screen now.

I followed this guide for a while: [https://help.ubuntu.com/community/VNC/Servers#x11vnc](https://help.ubuntu.com/community/VNC/Servers#x11vnc) . I had some trouble because whenever I logged in, my desktop would close the connection, so I posted here.

Turns out everything works as I expected if I change the option in the x11vnc command from '-once' to '-forever'.

---

