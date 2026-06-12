---
title: "Ethernet card conflicts with dial-up modem"
date: 2004-12-06
forum: Networking &amp; Wireless
---

### Post by dishbert on 2004-12-06
I have an on-board VIA Rhine ethernet connection on my Ubuntu machine that connects to another PC in my house.  This connection was detected and installed when I converted to Ubuntu.

I connect to the internet using a serial dial-up modem, but every time I boot up, I have to "disable" the network connection to make the modem work as it should.

It's as though the browser, email etc all want to use the network card.

Is there a way to make these 2 devices play nice?

---

### Post by loudnlownoma on 2007-12-31
Sorry to dig up such an old post, but wasn't sure if it was better to do so or to create a new one on the same topic.  Having almost the exact same trouble here, only using a USB modem to connect, and Ethernet to connect to a router for local network access.  Same issue though, if Ethernet is connected and enabled, the dial-up connection loses priority, and I lose connection.  :(  

OP, were you able to find an answer for this at all, or does anyone else have any ideas?  Thanks!

---

### Post by loudnlownoma on 2008-01-02
Anyone?

---

### Post by loudnlownoma on 2008-01-08
Ended up playing around with this a bit this weekend and finally found a solution, just in case anyone ever needs one and happens across the thread.....

I set my Ethernet connection to a static IP address, with no default gateway.  This way, it doesn't replace the gateway the dial-up connection is using, so the connection continues to work, while still allowing me to access my router and other devices.  :)

---

