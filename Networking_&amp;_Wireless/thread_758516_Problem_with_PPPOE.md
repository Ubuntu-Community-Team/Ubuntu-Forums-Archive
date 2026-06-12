---
title: "Problem with PPPOE"
date: 2008-04-18
forum: Networking &amp; Wireless
---

### Post by Adman on 2008-04-18
Hi all

I have a ADSL modem that acts as both a router and a bridge.  I have it running as a router at the moment.  However, I would like to connect to the internet with it as a bridge, and so I've been trying to use pppoeconf.

When I enable a pppoe connection (ppp0) using pon dsl-provider, my internet dies -- nothing routes through the new connection.  If I disable it, the internet starts working again since its using the router (eth0) connection.

Can anyone please help me and tell me what I am doing wrong?
Thanks

---

### Post by superprash2003 on 2008-04-18
thats probably cause your trying to connect with the same ISP username and password at the same time..you can either tell the router to dial or ubuntu to dial..

---

### Post by Adman on 2008-04-18
Thanks for your help

Even if I dial a different username and password, the connection traffic still goes through the router rather than through the Ubuntu pppoe connection.

Is there anyway to switch the traffic over to the other connection?

I live in South Africa where they cap our international usage at low data transfer  - 3 GB per month for me - and so I have to change accounts often...

Thanks

---

### Post by Paris Heng on 2008-04-18
> **Adman said:**
> Thanks for your help

Even if I dial a different username and password, the connection traffic still goes through the router rather than through the Ubuntu pppoe connection.

Is there anyway to switch the traffic over to the other connection?

I live in South Africa where they cap our international usage at low data transfer  - 3 GB per month for me - and so I have to change accounts often...

Thanks

Hi, go into the file (i not very sure is which file) of PPPoE, delete the previous saved User name and Password.

---

### Post by Adman on 2008-04-18
Maybe I am misunderstanding, but I don't think that helped... 

Thanks though

---

### Post by superprash2003 on 2008-04-18
when you want to use the pppoe connection in ubuntu, you need to disconnect the connection in your router..then traffic will route through the connection you created in ubuntu

---

