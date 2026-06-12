---
title: "Wireless server possible?"
date: 2007-06-16
forum: Networking &amp; Wireless
---

### Post by krolben on 2007-06-16
Hi,

I have an old pc that I'm considering using as a file/music/web/mail server. The problem is that it needs to be located in a room where I can only use wireless network access.
I've previously tried this with Win XP, but with the result that I often couldn't connect to the machine from other devices, because the wireless network had been disconnected for a milli second and Windows then blew up.

Can I run Ubuntu Server on the machine and expect it to run at a satisfactory level?

---

### Post by chili555 on 2007-06-16
I have no problems with mine in the garage right next to the extra motor oil. Except for the odd power failure brought on by Hurricane Wilma, it has run perfectly for 2-3 years.

---

### Post by krolben on 2007-06-16
Sounds good! I'll try setting up the machine soon!

Is there anything extra I have to consider due to the fact that I'm on a wireless network? Any installation issues, setup issues or extra things to run?

---

### Post by chili555 on 2007-06-16
Nothing I can think of, just because you are wireless.

I assume you know to set the BIOS to halt on no errors and to resume (reboot) after resumption of power after a power loss. Just make sure you tinker with /etc/network/interfaces until it starts and connects without human intervention. Obviously, you will use a static IP and you can tell it started successfully when you can ping it.

---

