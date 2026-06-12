---
title: "[SOLVED] access server from outside world through router"
date: 2008-06-10
forum: Networking &amp; Wireless
---

### Post by oodlesOfmoodles on 2008-06-10
I'm sure this is a simple process but I've scoured the web (google) and haven't found an answer.

I just set up an 8.04 server on an old Dimension 2200 and had it install LAMP and OpenSSH. 

We use a Linksys WRT54G router which broadcasts wirelessly and also has 4 wired ports along with a port for the internet (we use "high-speed" satellite broadband). I've plugged in the server box to one of the wired ports.

What I want to know is how I can access ssh/apache from say my workplace... is it even possible?

Thanks guys!

---

### Post by dudude on 2008-06-10
It is possible. You must forward the ports on the router from the internet to your server.

Instructions on how to do so can be found at [http://portforward.com/]("http://portforward.com/").

It must also be done once for every port that you want to forward. In this case I believe they are ports 80 and 22.

---

