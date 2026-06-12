---
title: "Static IP and Port Forwarding?"
date: 2008-11-24
forum: Networking &amp; Wireless
---

### Post by Surion84 on 2008-11-24
I recently installed ubuntu on my laptop and everything is working fine cept a few minor details that were fixed due to the great community support. Though one thing i really need help with is that i love bit torrenting its my life line i was wondering how to go about creating a static ip in ubuntu and the forwarding the ports to set up deluge or azureus to run at full capcity.

---

### Post by superprash2003 on 2008-11-25
this should help you [http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html](http://prash-babu.blogspot.com/2008/11/how-to-setup-static-ip-address-in-linux.html)

---

### Post by cmittle on 2008-11-25
If you have a Linksys router I can tell you how to forward the ports if you're not familiar with that.

---

### Post by Surion84 on 2008-11-25
The link was helpful but i don't know if it matters that im on a wireless network and the line it was telling me to look for wasn't there.  Instead i had

auto lo
iface lo net loopback

so should i just do what the set up told me to do or do i have to do something else?

---

### Post by wieman01 on 2008-11-25
Which version of Ubuntu?

There isn't anything in that file, because your networking applet (aka Network Manager) removes them. Don't mess with that file if you own a laptop, because it's rather inconvenient.

You should be able to set a static IP address in 8.10 though. Have you checked?

---

