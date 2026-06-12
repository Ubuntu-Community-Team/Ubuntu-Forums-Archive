---
title: "How to use Remmina Ubuntu to Ubuntu?"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by raymondvillain on 2013-09-30
Have 2 desktop machines, Ubuntu 13.04 on one, 10.04 on the other.

Is it possible to use Remmina between these machines?  I start it up on the box with 13.04 installed, but I don't know what the choices mean.  Is there a user guide for beginners to Remmina?  If I select connection (rdp, ssh, etc.) and follow the steps, I always get an error message "unable to connect to rdp server (or ssh server, etc.)"

---

### Post by steeldriver on 2013-09-30
Remmina is a *client* program - you need a *server* program running on the other computer for it to connect to. For Linux-to-Linux, you are probably best sticking with VNC rather than RDP (which is a Microsoft protocol). I'm not sure whether there was a default VNC server on 10.04 but later versions use Vino e.g. for 12.04 (and probably 13.04) it is accessible from the Dash by typing 'Desktop Sharing' and then checking the box to turn it on.

---

### Post by raymondvillain on 2013-09-30
Thanks so much, steeldriver!  I finally got it to work, had to select VNC.  Thanks again.

---

### Post by steeldriver on 2013-09-30
You're welcome - please be aware though that VNC is not secure, it's fine if you're just using it over your LAN (and have a non-forwarding NAT router / firewall) - but if the machine running the VNC server is in any way exposed to the public internet then you should secure it by SSH tunneling.

---

### Post by raymondvillain on 2013-09-30
O. K. but is that a straightforward thing to do?  If I click on "secure tunneling" in the remmina window the connection fails, but works fine if I don't.  I guess I need to install something or enable SSH tunneling on both machines.

---

