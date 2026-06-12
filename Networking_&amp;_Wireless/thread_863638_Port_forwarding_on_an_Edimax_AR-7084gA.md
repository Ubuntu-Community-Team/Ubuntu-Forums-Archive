---
title: "Port forwarding on an Edimax AR-7084gA"
date: 2008-07-18
forum: Networking &amp; Wireless
---

### Post by Rhapsody on 2008-07-18
I've recently purchased an Edimax AR-7084gA to replace an Orange Livebox 1.1 in the hopes of getting better wireless networking. I haven't tested that yet, but I have a new problem.

On the old Livebox, I enabled UPnP, KTorrent's UPnP plugin saw the router, and forwarded ports 6881 and 6882. This worked fine. But even though I've enabled UPnP and enabled allowing UPnP applications to auto-configure the router, KTorrent's plugin sees no devices and no ports are forwarded. I also have no idea how to manually forward ports using the Edimax router's web interface.

Otherwise, it works fine. I have regular internet, but torrents are being strangled by the lack of port forwarding. How do I make this router visible to my applications?

---

### Post by superprash2003 on 2008-07-19
hope this helps [http://www.portforward.com/english/routers/port_forwarding/Edimax/AR-7084gA/default.htm](http://www.portforward.com/english/routers/port_forwarding/Edimax/AR-7084gA/default.htm)

---

### Post by ltk5 on 2009-05-26
The problem is how to set up the static ip. Though I'm using ubuntu, and I guess there's different to set up a static connection, I still don't know how, or what to do. Upnp somehow does not work.

any help appreciated

---

### Post by superprash2003 on 2009-05-27
ah , didnt know i'll be answering again after a year :) .. [http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html](http://www.prash-babu.com/2009/01/how-to-setup-static-ip-in-ubuntu.html)

---

### Post by ltk5 on 2009-06-02
Thank you very much. Followed your tutorials (including the comments) and got it working.

Especially the note was a time-saver: 

*Note : Incase the static ip address hasnt been applied , you might need to restart networking by going to the Terminal(Applications->Accessories->Terminal) and typing sudo /etc/init.d/networking restart*

---

