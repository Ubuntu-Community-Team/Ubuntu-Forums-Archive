---
title: "MTU in Network Manager"
date: 2008-11-05
forum: Networking &amp; Wireless
---

### Post by dburnett77 on 2008-11-05
In Ubuntu/Xubuntu 8.10, it seems the default MTU is 576, and my cable modem likes 1500 better.
If I set it via the nm applet, the setting isn't permanent.  I have to do it every log in.  And, I'm not quite sure how to set it in the /etc/network/interfaces config file.  I use:
  iface eth0 inet dhcp
  mtu 1500

but, ifconfig shows 576 still.

I'd prefer to use the nm app, but the changes to MTU aren't permanent.  Is there a way to go about this.

---

### Post by dburnett77 on 2008-11-07
Seems the problem has corrected itself, with the 'automatic' setting yielding appropriate download speeds.

Beforehand, it was abysmal.  With the overall speed about 1/6th what it should have been.

Now, though, as mentioned, it's where it should be.

---

