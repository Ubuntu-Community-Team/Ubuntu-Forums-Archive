---
title: "Make static IP address for an Ubuntu 9.04 machine"
date: 2010-05-14
forum: New to Ubuntu
---

### Post by RedOctober on 2010-05-14
I have several Ubuntu 9.04 machines connected to a MS 2003 Server.  On only one of the Ubuntu boxes, I want to make the IP address static, because a locally connected USB printer driver is mapped to it.

How do I make the Ubuntu 9.04 machine's IP address static?

---

### Post by Gone fishing on 2010-05-14
On the net work manager icon on the top toolbar right click a select edit connections.

Select the connection and edit on IPv4 settings you can select fixed ip address and then set up as you wish

---

### Post by Black Hawk on 2010-05-14
Right click on the network manager applet located at the top menu bar. Click edit conections. Under Wierd (Should already be selected) click add. give your connection a name. Under IPv4 settings select meathod "manual" Under the heading "Adresses" click add and fill in your desierd ip, network mask and gateway.

---

### Post by lisati on 2010-05-14
My own preference is to let the router hand out IP addresses, setting it to use a static IP address for a particular machine based (in part) on the machine's MAC address.

Others have mentioned the setting of IP addresses at Ubuntu's end. While this is do-able, it can potentially cause IP address conflict problems if the machine you've used this approach on is likely to be hooked up to someone else's network at some point (e.g. work, school, etc).

---

### Post by RedOctober on 2010-05-14
Good point lisati.  The reason I'd like to keep this one static is because it has a printer connected to it locally, and on the MS 2003 network, a printer definition is "firm" coded to it.

Thanks everyone.  I will try out your suggestion(s) after clinic tonight when the machine becomes available.

---

