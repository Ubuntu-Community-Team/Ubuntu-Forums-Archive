---
title: "Issur with wireless connection"
date: 2008-03-29
forum: Networking &amp; Wireless
---

### Post by djpate on 2008-03-29
hello all,

I've just bought a new computer so i decided to put my old one a P4 2.8C as a server at the other side of my house using a usb wifi adapter.

So i installed a fresh copy of 7.10 Server , ndiswrapper and i set it up to connect automaticly on boot to the wifi and this works fine.

just after boot if i go to internet from the server like apt-get update works fine but if i go on my main computer and try to go to my server webserver or openssh it says no route to host.

And i can't ping my server but now the funny thing is that if from my server i ping my main computer it "unlock" something and then i can acces my server from my main computer and ping it.

It doesnt seems to stay like after an hour i can't ping it anymore...

any idea?

---

### Post by dstew on 2008-03-29
Is your server configured to use a static IP address, or does it use DHCP to get its address from your router? Maybe its IP address is changing boot to boot because of DHCP, and when you ping your main computer you are informing it of the current server IP address. You might want to set up the server with a static IP address. Just a guess...

---

### Post by djpate on 2008-03-29
no it's dhcp but i'm pinging the right adress...

---

### Post by djpate on 2008-03-31
anyone ?

---

