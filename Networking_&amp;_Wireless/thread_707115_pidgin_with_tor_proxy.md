---
title: "pidgin with tor proxy"
date: 2008-02-25
forum: Networking &amp; Wireless
---

### Post by Allus on 2008-02-25
Hello. I use pigin now and then and talk to people I don't really know. I don't know if the person on the other end can know my ip through this or not, but it makes me uncomfortable.

 I used this tutorial:

[http://mytechxp.blogspot.com/2007/10/pidgin-through-proxy.html](http://mytechxp.blogspot.com/2007/10/pidgin-through-proxy.html)

to configure pidgin to use TOR.  After I did this the application connects and communicates fine.  But I don't know how to verify that the app is actually going through a proxy.  

I know that when I have used TOR with FireFox There is usually a little icon in the tray, (on a windows machine), that allows me see the routes any transmission takes. But I don't have anything like this on Gutsy when I am using Pidgin.

How can I verify that Tor is actually being used by this program?

Thanks.

---

### Post by thenetduck on 2008-03-17
I would like to know this too. Thank you for that link. If you find a solution please post

---

### Post by abuakel on 2008-04-22
Any results on this?

---

### Post by maggot_brain on 2008-05-17
Just use wireshark to see the destination of MSN (or whatever IM service you're using) packets.  They should go to 127.0.0.1 port 9050 like in the tutorial.

---

### Post by Megatog615 on 2008-05-20
It does work. However, it tends to cause Pidgin to lock up for me. Didn't happen in Gutsy.

---

### Post by IamAcoconut on 2008-05-20
> **Megatog615 said:**
> It does work. However, it tends to cause Pidgin to lock up for me. Didn't happen in Gutsy.
Well it happens on my Gutsy, but it depends on the protocol I'm using or trying to use.

---

