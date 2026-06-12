---
title: "Cross Country SSH??"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by beetlespace on 2008-11-03
I have a friend in AZ who is a recent Ubuntu convert (YEAAAY!) who needs my help setting some stuff up for her. She is a very "newbie" person when it comes to Linux. I'm not that great either. I live in VA so driving over to do things for her is not an option so connection over the internet is our only option.

Soooo... what's the best options for remote connection to her laptop? Whatever it is, it needs to be VERY simple for her to setup on her end. Here are the specs I am aware of:

**Her side:**
Laptop connecting to a wireless router via cable internet.
Unknown data transfer speed
Unknown network configuration (IP addresses type of router, any firewalls etc.)
Ubuntu 8.04

**My side:**
Laptop connected directly via Verizon 3G wireless USB modem.
Data transfer around 100kb/s
Ubuntu 8.04

I don't really need desktop sharing, just command line access would do. Mainly I would like to install packages I know she will need like DVD reading, and the like.

Any help or suggestions with links would be great.

Thanks!
Mike

---

### Post by superprash2003 on 2008-11-03
port forwarding is required in most cases.. easiest way to go about it is to enable remote desktop under system->preferences->remote desktop.. and then opening port 5900 on her wifi router.. then to connect all you need to do is type vncviewer x.x.x.x:0 where x.x.x.x is her external ip which you can get by telling her to go to [www.whatismyip.com](www.whatismyip.com)

---

