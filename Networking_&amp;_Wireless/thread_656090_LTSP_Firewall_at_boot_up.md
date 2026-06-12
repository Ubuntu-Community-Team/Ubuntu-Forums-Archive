---
title: "LTSP: Firewall at boot up"
date: 2008-01-02
forum: Networking &amp; Wireless
---

### Post by JoeGregory on 2008-01-02
Hi all,

After having much trouble troubleshooting my  LTSP set-up I finally got it working on the day before christmas. However, initially this only worked with my Firewall off. 

After some research, I finally got Firestarter set-up to do what I want and could run the clients with the firewall on. But I still have one problem which I really need to fix.

I would like to firewall to start on the server during boot up so the root user doesn't need to log-in. Ideally it should operate as a headless server. 

Currently I have to boot-up, log-in, run firestarter and finally the command line

  "sudo /etc/init.d/networking restart"

I think this has something to do with Firestarter failing because one or the other of my interfaces is down (Internet via wireless NIC, LTSP on local wired LAN)

Can anyone give me some guidance here?

AMD64 Server running Ubuntu 7.10 & ltsp 5.0

Thanks

---

