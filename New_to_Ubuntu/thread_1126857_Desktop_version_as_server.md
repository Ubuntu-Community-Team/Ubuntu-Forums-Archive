---
title: "Desktop version as server?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by fareforce on 2009-04-15
Due to the GUI interface, I decided to install the desktop version to use on my server. Here is what I need the server to do:

DCHP (act as a firewall, and router for my windows boxes, so basically a domain controller)
File Server (2 Windows Vista machines, and 1 Mac)
Email server (in the future)

My server has 2 NIC cards, so I have the internet line going to NIC 0, and on NIC 1 I have a switch. From there I have 2 Windows Machines, and 1 Mac. Is there some sort of step-by-step guide on how to do this sort of thing? I am new to this whole linux thing.

---

### Post by SunnyRabbiera on 2009-04-15
yes its entirely possible to turn a desktop install into a server install, and vice versa.

---

### Post by Titan8990 on 2009-04-15
I would only recommend this for a test server. Production servers should be ran headless.

You will quickly realize that GUI applications for server administration are nearly non-existent anyways.

---

### Post by bodhi.zazen on 2009-04-15
> **Titan8990 said:**
> I would only recommend this for a test server. Production servers should be ran headless.

You will quickly realize that GUI applications for server administration are nearly non-existent anyways.

But some people like to use web based interfaces ;)

---

### Post by fareforce on 2009-04-15
So how do I make the desktop a server version?

---

### Post by Titan8990 on 2009-04-15
Uninstall the GUI and install the Ubuntu server kernel.


Web interfaces are good. Until my sql-fu is up to par, phpmyadmin gets me by.

---

