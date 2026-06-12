---
title: "Cannot Connect to Internet (Desktop)"
date: 2006-11-05
forum: Networking &amp; Wireless
---

### Post by Vinn on 2006-11-05
I installed Edgy on my desktop and it worked fine for a few days until I shut down and left it for about a day or so. When I turned it back on, it wouldn't connect to the internet anymore. I have no idea what's wrong, please help out.

I've got a cable modem, it's connected to my router, and the router is connected to my pc. I have the desktop dual booting into Ubuntu and Windows XP, and in Windows I can connect just fine.

Thanks a lot

---

### Post by quux on 2006-11-05
Do you use dhcp? If so, does the machine correctly acquire an IP address ("sudo dhclient", "ifconfig")? 

If not, is the default route set correctly (the gateway for the default destination in the output of "route" has to point to the IP of your router)? Is your nameserver set correctly ("cat /etc/resolv.conf"), a lot of routers provide a caching/forwarding nameserver to the clients in internal net, so you might as well try setting the IP of your router here.

HTH

---

### Post by Vinn on 2006-11-05
What? I think I know what you just said, hang on let me try it.

EDIT: Hmm, everything seems to be working normally now. Strange. I haven't been using Ubuntu for almost a week because of the internet issue, now I boot it up and it works again. Very weird.

---

