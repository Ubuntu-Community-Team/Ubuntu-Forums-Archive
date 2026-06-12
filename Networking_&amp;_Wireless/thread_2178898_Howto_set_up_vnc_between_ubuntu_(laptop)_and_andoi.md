---
title: "Howto set up vnc between ubuntu (laptop) and andoid smartphone without internet acces"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by peterlesterhuis on 2013-10-05
Hi,
I have a program running on my ubuntu-laptop and I want to view and control this program on my android smartphone. There is no access to the internet. This is what makes it difficult for me. When you have internet access you can choose any vnc you like, even teamviewer (with wine). 
Is this possible without internet access?

Thanks,

Peter

---

### Post by ian-weisser on 2013-10-06
Yes, if they are on the same LAN.
No, if they share no common network.

You can use ssh, vnc, and other login/control methods without internet access. You just cannot use teamviewer.
The best method to use depends on your network, on the application you wish to control, and on the capabilities of the system doing the controlling.

For example, controlling a torrent server using VNC seems rather a waste of resources; most decent torrent servers are easily controlled using web, ssh+ncurses, or ssh+cli interfaces.

---

### Post by peterlesterhuis on 2013-10-08
> **ian-weisser said:**
> Yes, if they are on the same LAN.
No, if they share no common network.

Thanks for your reply, which I think is pretty clear. And it is a good starting point. The problem is that I can't manage to create a (wireless) LAN without internet access. When I try to create a new wifi network I get an error with something like it is not possible to create an hotspot with this device. I tried to set up a LAN with a router (TP-link: TL-WR702N). But I couldn't get it to work.
I wonder if you have a suggestion how I should set this up (with or without the router).

Peter

---

### Post by ian-weisser on 2013-10-08
Is this going to be a permanent LAN? Or a temporary (ad-hoc) LAN?

---

### Post by peterlesterhuis on 2013-10-08
I think permanently. On my boat I have a laptop with navigation software (OpenCPN) running in the cabin and I want to view and control this with my android smartphone in the cockpit.
Everytime  I go sailing I want to use this LAN.

---

